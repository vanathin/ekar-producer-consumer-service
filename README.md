# Microservice: consumer-producer-service
This is a demo microservice for the consumers-producers currently accessing atomic counter.

### Tech stack used:
1. Java 8
2. Spring Boot 2.4.2
3. Spring REST API (Spring Web)
4. Lombok 1.18.16
5. Spring Data JPA & MySQL-8
7. Dockerized (docker-compose.yml and Dockerfile is included)
8. TDD approach using JUnit 5, Mockito, and Spring Boot Test
10. Spring boot starter validation for request validation  

### Steps to run micro-service along with `MySQL` as containers in docker using `docker compose`:
##### Step 1: Open the terminal (or) Command Prompt
##### Step 2: Enter the project directory, 
    cd <project_directory>

##### Step 3: To clean and package the micro-service locally
    mvnw clean package

##### Step 4: Use `docker compose` to build and run both MySQL & micro-service as a docker containers:
    docker-compose up --build
Note: Above docker compose command will run the containers namely,
   1. `ekar-mysql` container for mysql and its port is `3306`
   2. `ekar-producer-consumer-service` container for microservice and its port is `8080`

---

### OpenAPI 3.0 Documentation URL:

http://localhost:8080/swagger-ui/index.html?configUrl=/v3/api-docs/swagger-config  
![API_Documentation img missing](https://raw.githubusercontent.com/vanathin/ekar-producer-consumer-service/main/img/swagger-ui.jpg)
Note: Also [Postman Collection](https://raw.githubusercontent.com/vanathin/ekar-producer-consumer-service/main/Ekar.postman_collection.json) has been pushed into the repository for your reference.

---

### MySQL Database CLI to verify the transaction information:
##### Prerequisite: 
Docker has to be there on the host machine
##### Step 1: Open a new terminal (or) new Command Prompt (without disturbing the earlier one)
##### Step 2: Connect to `ekar-mysql` container using docker cli command, 
    docker exec -it ekar-mysql /bin/bash
##### Step 3: Connect to mysql server
    mysql -usa -ppassword -h localhost -P3306
##### Step 4: Display all the available databases,
    show databases;
##### Step 5: Switch to ekardb
    use ekardb;
##### Step 6: List all the available tables
    show tables;
##### Step 7: Run the select queries to verify the data
    select * from request_log; select * from counter_log;
Note: Preserve this state until you complete your testing.
##### Step 8: Exit from the mysql cli
    exit
##### Step 9: Exit from the mysql container
    exit

![MySQL CLI Output](https://raw.githubusercontent.com/vanathin/ekar-producer-consumer-service/main/img/mysql_db_log.jpg)

---


### Program outputs

#### Less consumers and more producers
![Less consumers and more producers](https://raw.githubusercontent.com/vanathin/ekar-producer-consumer-service/main/img/More_Producer_Less_Consumer.JPG)

#### More consumers and less producers
![More consumers and less producers](https://raw.githubusercontent.com/vanathin/ekar-producer-consumer-service/main/img/Less_Producer_More_Consumer.JPG)

#### Equal consumers and producers
![Equal consumers and producers](https://raw.githubusercontent.com/vanathin/ekar-producer-consumer-service/main/img/Equal_Producer_Consumer.JPG)

---
