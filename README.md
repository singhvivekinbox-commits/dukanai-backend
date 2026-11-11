# DukanAI Backend

Starter project using Java 21, Spring Boot 3.5.7, Maven and MySQL.

## Package structure

```text
src/main/java/com/dukanai/
├── config/
├── controller/
├── service/
├── repository/
├── entity/
├── dto/
├── exception/
└── DukanaiApplication.java
```

## Requirements
- JDK 21
- Maven 3.9+
- MySQL 8.x

## Create database
Run in MySQL:
```sql
CREATE DATABASE dukanai_db;
```

## Configure credentials (Windows PowerShell)
```powershell
$env:DB_USERNAME="root"
$env:DB_PASSWORD="your_mysql_password"
$env:DB_URL="jdbc:mysql://localhost:3306/dukanai_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC"
```

Do not commit real credentials. Defaults in application.yml are local-development placeholders.

## Run
```bash
mvn spring-boot:run
```
Or:
```bash
mvn clean package
java -jar target/dukanai-backend-0.0.1-SNAPSHOT.jar
```

## Verify
GET http://localhost:8080/api/health

Expected JSON:
```json
{"status":"UP","application":"DukanAI backend"}
```

## Notes
- `/api/health` and `/actuator/health` are public.
- Other endpoints require HTTP Basic authentication in this starter. Replace this development setup with JWT/OAuth2 before production.
- `ddl-auto: update` is for local development only. Use Flyway or Liquibase migrations in production.
- Next: implement User entity/repository/service/controller, DTO validation, centralized exception handling, JWT and integration tests.
