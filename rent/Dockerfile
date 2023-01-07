FROM maven:3 AS build
WORKDIR /code
COPY . /code/
RUN mvn install

FROM openjdk:17-jdk-slim-buster

WORKDIR /app
COPY . .
RUN mvn clean package
RUN cp ./target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "/app/app.jar"]