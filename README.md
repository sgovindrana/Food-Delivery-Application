# Food Delivery Application

> **Quick Repo Map – jump straight to the code you need:**

| Layer | Repository | What you’ll find there |
|-------|------------|------------------------|
| **Frontend UI** | [food‑delivery‑application‑fe](https://github.com/sgovindrana/food-delivery-application-fe) | Angular 16 client – lists all restaurants, displays menus, manages cart, and places orders |
| **Eureka Service Registry** | [eureka‑service](https://github.com/sgovindrana/eureka-service) | Eureka server for micro‑service discovery |
| **Restaurant Listing MS** | [restaurant‑listing‑microservice](https://github.com/sgovindrana/restaurant-listing-microservice) | Lists restaurants on the UI; returns restaurant details, address, and metadata |
| **Food Catalogue MS** | [food‑catalogue‑microservice](https://github.com/sgovindrana/food-catalogue-microservice) | Provides a selected restaurant’s full menu and restaurant details to the UI |
| **User MS** | [userinfo‑microservice](https://github.com/sgovindrana/userinfo-microservice) | Stores user profiles (ID, name, password, delivery address) and cart information |
| **Order MS** | [order‑microservice](https://github.com/sgovindrana/order-microservice) | Receives “Order Now” requests, persists order details, selected food items, restaurant info, and user ID in MongoDB |
| **CI/CD & K8s Manifests** | [deployment‑configurations](https://github.com/sgovindrana/deployment-configurations) | Jenkins → JUnit/ SonarQube → Docker/ECR → Kubernetes manifests → ArgoCD → AWS EKS pipeline |


-----------------------------------------------------------------------------------------------------------------------------------


**Food Delivery Application** is a full-stack application built using **Microservices Architecture**. It allows users to browse restaurants and menus, add multiple items to the food catalogue cart, and place food orders, receiving a successful order confirmation dialogue. The application is developed using modern technologies and deployed on AWS for enhanced scalability and reliability.

## Technologies Used

- **Frontend**:  
  - **Angular 16**, **TypeScript**,  **Javacript**, **HTML5**, **CSS3**
  
- **Backend**:  
  - **Java 17**, **Spring Boot**, **Microservices**, **Hibernate**, **Junit Test Case (Code Coverage > 80%)**
  
- **Databases**:  
  - **RDBMS - MySQL (RDS)**, **NoSQL - MongoDB (Atlas, MongoCompass)**
  
- **CI/CD**:  
  - **Jenkins** (Continuous Integration), **SonarQube** (Code Quality), **ArgoCD** (Continuous Deployment)
  
- **Containerization & Orchestration**:  
  - **Docker**, **Kubernetes (AWS EKS on EC2)**

- **Cloud**:  
  - **AWS (IAM, RDS, EC2, ALB, EKS)**
-----------------------------------------------------------------------------------------------------------------------------------
## Application Architecture

![Screenshot 2025-05-02 at 1 25 36 PM](https://github.com/user-attachments/assets/fb7d08a2-9488-48e9-9a8d-461785d67de6)


*This screenshot below shows the architecture of the entire CI/CD deployment pipeline**.
![Screenshot 2025-05-02 at 1 26 16 PM](https://github.com/user-attachments/assets/fb93f82f-f055-4bc9-9ee2-2bd49468912d)


## Components

### Frontend

The **Frontend** component is built using **Angular**, **TypeScript** & **JavaScript** providing an interactive user interface for:
[GitHub Repo](https://github.com/sgovindrana/food-delivery-application-fe)

- Browse restaurants and view menus to explore food options.
- Add multiple items to the food catalogue cart for easy order management.
- Place an order and receive a successful order confirmation dialogue upon completion.

### Backend

The **Backend** consists of several **Microservices** developed using **Java Spring Boot**, including:

- **Eureka Service**: Service registry & discovery. [GitHub Repo](https://github.com/sgovindrana/eureka-service)  
- **Food Catalogue Service**: Manages food items & restaurant info. [GitHub Repo](https://github.com/sgovindrana/food-catalogue-microservice)  
- **Order Service**: Handles order placement, status updates & saves orders in MongoDB. [GitHub Repo](https://github.com/sgovindrana/order-microservice)  
- **User Service**: Manages user profiles and supports adding food items to the user’s cart. [GitHub Repo] [GitHub Repo](https://github.com/sgovindrana/userinfo-microservice)  
- **Restaurant Listing Service**: Manages restaurant data & listing details. [GitHub Repo](https://github.com/sgovindrana/restaurant-listing-microservice)  
  
### Microservices & Deployment

The application is designed with **Microservices Architecture** and deployed on **AWS Kubernetes (EKS)**, ensuring scalability and high availability. 

- **Eureka Service** for service discovery and registration.
- **Docker** is used for containerizing microservices.
- **Jenkins** is used for the **CI pipeline** to automate the build and test process.
- **ArgoCD** is used for **CD** to automate the deployment of the microservices on AWS.
-----------------------------------------------------------------------------------------------------------------------------------
## Deployment & Configuration
- **Deployment Configurations**: Orchestrates end-to-end CI/CD—on each code push, Jenkins runs the build, increments the app version, builds & pushes new Docker images to ECR, commits updated Kubernetes manifests (with the new image tag) into this repo, and ArgoCD continuously monitors and syncs these changes to AWS EKS. [GitHub Repo](https://github.com/sgovindrana/deployment-configurations)

## Deployment Flow
----
1. **Code Commit**  
   - Push to any service repo triggers the Jenkins pipeline defined in the  
     [deployment‑configurations](https://github.com/sgovindrana/deployment-configurations) repo.  
2. **Build Stage**  
   - Compile sources  
   - Execute **JUnit** unit / integration tests  
3. **Quality Gate**  
   - Run **SonarQube** static analysis  
   - Pipeline continues only if all quality gates pass  
4. **Containerization**  
   - Build a version‑bumped Docker image  
   - Push the image to **Amazon ECR**  
5. **Manifest Update & Commit**  
   - Inject the new image tag into Kubernetes YAMLs  
   - Commit the updated manifests back to the *deployment‑configurations* repo  
6. **Continuous Deployment**  
   - **ArgoCD** detects the commit and syncs the manifests  
   - Performs a zero‑downtime rolling update on **AWS EKS** (EC2 worker nodes)  
7. **Service Discovery**  
   - Fresh pods start and automatically register with **Eureka** for seamless inter‑service communication  
-----------------------------------------------------------------------------------------------------------------------------------

## Screenshots

### 1. **Microservices Registered on Eureka**  
*This screenshot shows the registered microservices on Eureka, deployed on **AWS EKS (EC2 worker nodes)**.
![Screenshot 2025-05-01 at 6 46 55 PM](https://github.com/user-attachments/assets/6d62826c-a89c-4818-aabd-9e1ae432509f)

### 2. **Jenkins CI Pipeline**  
*This screenshot shows the Jenkins CI pipeline running the build, tests, and SonarQube code analysis.*
![Screenshot 2025-05-01 at 6 49 00 PM](https://github.com/user-attachments/assets/7fa48229-b6b1-431a-8a0a-ba21bb10aeea)
![Screenshot 2025-04-29 at 3 41 57 PM](https://github.com/user-attachments/assets/4ae4a3d7-57a5-4cbf-a997-196960efb66e)

### 3. **SonarQube Code Quality Report**  
*This screenshot shows the code quality report generated by SonarQube.*
![Screenshot 2025-05-01 at 6 48 48 PM](https://github.com/user-attachments/assets/7084c2d9-3814-4ca6-a230-5394a26c5a1c)


### 4. **ArgoCD Deployment on AWS**  
*This screenshot shows the registered microservices on Eureka, deployed on* **AWS EKS (EC2 worker nodes)**
![Screenshot 2025-04-30 at 6 12 49 PM](https://github.com/user-attachments/assets/ebd4df9c-6904-4173-a3a5-cb0eb897688c)

### 5 **Final Application**
![Screenshot 2025-04-17 at 5 20 59 PM](https://github.com/user-attachments/assets/f7b39675-1339-4be4-b9c1-34ea034a46a9)
![Screenshot 2025-05-02 at 1 32 51 PM](https://github.com/user-attachments/assets/36882d8f-1a21-4628-b476-e6aa40fc172a)
![Screenshot 2025-05-02 at 1 32 58 PM](https://github.com/user-attachments/assets/078d9f58-e70c-470c-9ca4-35b8cd843a2a)


-----------------------------------------------------------------------------------------------------------------------------------

### Other Miscellaneous Screenshots

### Junit Test Case ( Code Coverage More Than 80% )
*This screenshot shows the Multiple Junit Test Cases with Code Coverage more than 80%.*
![Screenshot 2025-04-29 at 4 28 39 PM](https://github.com/user-attachments/assets/dc46802d-a6f2-460f-840b-978e0e7cbb68)

### Docker Hub 
*This screenshot shows the Multiple Docker Images with their Latest Version.*
![Screenshot 2025-05-01 at 6 49 31 PM](https://github.com/user-attachments/assets/f034a452-c30c-4663-ad6e-c01bfd20dce9)

-----------------------------------------------------------------------------------------------------------------------------------

   
## Getting Started
----
Follow the steps below to set up and run the project locally **or** deploy it on AWS.

## Prerequisites
----
- **Node.js** & **Angular CLI** – build / run the frontend  
- **Java 17 +** & **Spring Boot** – develop the backend microservices  
- **Docker** – containerise services  
- **Kubernetes (AWS EKS)** – orchestrate containers  
- **AWS CLI** & **kubectl** – manage AWS and your EKS cluster  
- **Jenkins** – continuous integration  
- **SonarQube** – static code analysis  
- **ArgoCD** – continuous deployment

## Installation
----
1. Clone this repository to your local machine.
2. Install the project dependencies using `npm install`.
3. Run the project locally using `ng serve`.
4. Access the application in your web browser at [http://localhost:4200].

## Contributing

Contributions are welcome! If you'd like to contribute to this project, please follow these steps:
1. Fork the repository.
2. Make your changes and improvements.
3. Raise a Pull Request (PR) with a clear explanation of your changes.
4. Contact the project maintainer, Govind Rana (s.govindrana@gmail.com), for PR approval.

## Contact

For questions or inquiries, please contact **Govind Rana** at **s.govindrana@gmail.com**.

Thank you for using the **Food Delivery Application!* :)
