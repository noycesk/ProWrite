# Use official JDK 21 image
FROM eclipse-temurin:21-jdk-alpine

# Install Maven
RUN apk add --no-cache maven

# Set working directory
WORKDIR /app

# Copy only the pom to cache dependencies
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy source code
COPY src ./src

# Build the project without tests
RUN mvn clean package -DskipTests

# Run the jar
CMD ["java", "-jar", "target/prowrite.jar"]
