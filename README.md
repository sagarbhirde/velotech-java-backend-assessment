# velotech-java-backend-assessment
Candidate assessment test


# Java Spring Boot Backend Assessment

## 1. Objective

Build a **RESTful Invoice Management API** using Java and Spring Boot.

The purpose of this assessment is to evaluate your ability to:

* Understand business requirements
* Design and implement REST APIs
* Write clean and maintainable Java code
* Apply object-oriented programming principles
* Work with a relational database
* Implement validation and exception handling
* Write meaningful tests
* Make appropriate technical and design decisions
* Explain your implementation and assumptions

---

## 2. Technical Requirements

Use the following technologies:

* **Java:** 17 or higher
* **Spring Boot:** 3.x
* **Build Tool:** Maven or Gradle
* **Database:** PostgreSQL, MySQL, or H2
* **Testing:** JUnit 5
* **Version Control:** Git

You may use additional libraries when required. Please document any additional dependencies and why they were used.

---

# 3. Business Requirement

We need a backend system to manage customer invoices.

An invoice contains:

* Invoice ID
* Customer Name
* Amount
* Currency
* Status
* Creation Date

The supported invoice statuses are:

```text
PENDING
PAID
CANCELLED
```

---

# 4. Required APIs

## 4.1 Create Invoice

### Endpoint

```text
POST /api/invoices
```

### Request

```json
{
  "customerName": "ABC Technologies",
  "amount": 25000,
  "currency": "INR"
}
```

The newly created invoice should have an appropriate initial status.

Return the created invoice with its generated ID.

---

## 4.2 Get Invoice

### Endpoint

```text
GET /api/invoices/{id}
```

Return the invoice corresponding to the supplied ID.

If the invoice does not exist, return an appropriate HTTP response and meaningful error information.

---

## 4.3 Search Invoices

### Endpoint

```text
GET /api/invoices
```

The API should support:

* Status filtering
* Customer filtering
* Pagination
* Sorting

Example:

```text
GET /api/invoices?status=PENDING&page=0&size=10
```

You may decide the exact API response structure.

Document your decision in the README.

---

# 5. Update Invoice Status

### Endpoint

```text
PATCH /api/invoices/{id}/status
```

Example request:

```json
{
  "status": "PAID"
}
```

The API must validate whether the requested status change is allowed.

Define and document the status transition rules that you consider appropriate.

---

# 6. Invoice Summary

### Endpoint

```text
GET /api/invoices/summary
```

The API should provide a summary containing at least:

* Total number of invoices
* Total invoice amount
* Total paid amount
* Total pending amount

Example:

```json
{
  "totalInvoices": 100,
  "totalAmount": 500000,
  "paidAmount": 350000,
  "pendingAmount": 150000
}
```

Consider the efficiency of the implementation when calculating these values.

---

# 7. Validation

Implement appropriate request validation.

At minimum, consider:

* Customer name should not be blank
* Amount should be greater than zero
* Currency should be valid
* Status should be valid
* Required fields should be validated

Return meaningful validation errors to the API consumer.

---

# 8. Error Handling

Implement appropriate error handling for scenarios such as:

* Invoice not found
* Invalid request
* Invalid status
* Invalid status transition
* Database/application errors where appropriate

The API should return a consistent error response.

For example:

```json
{
  "timestamp": "2026-09-17T10:30:00",
  "status": 404,
  "error": "INVOICE_NOT_FOUND",
  "message": "Invoice with id 123 was not found"
}
```

The exact structure is your design decision.

---

# 9. Database

Persist invoice information in a relational database.

The application should be runnable by another developer without manually creating database tables.

Provide either:

* Database migration scripts, or
* Schema/initialization scripts

Document the database setup and configuration.

Do not commit passwords, secrets, or sensitive credentials to GitHub.

---

# 10. Testing

Write automated tests for important business functionality.

At minimum, cover:

* Successful invoice creation
* Invalid invoice creation
* Invoice not found
* Valid status transition
* Invalid status transition
* Invoice summary

You may add integration/API tests where appropriate.

---

# 11. Code Quality

The solution should demonstrate:

* Clean and readable code
* Appropriate separation of responsibilities
* Meaningful naming
* Proper exception handling
* Appropriate use of interfaces/abstractions where useful
* Maintainable project structure
* Avoidance of unnecessary complexity

There is no mandatory package structure. Choose an approach that you consider appropriate and explain significant design decisions.

---

# 12. API Documentation

Document the available APIs.

You may use:

* Swagger/OpenAPI

or

* README documentation

Include example requests and responses.

---

# 13. Logging

Add appropriate application logging.

Logging should help troubleshoot application behaviour without exposing sensitive information.

---

# 14. Git Practices

Use Git throughout the development of the assessment.

Create meaningful commits that demonstrate the progression of your implementation.

For example:

```text
Initial Spring Boot project setup
Implement invoice creation
Implement invoice retrieval
Add invoice search and pagination
Implement status management
Add validation and exception handling
Add unit tests
Add API documentation
```

Avoid committing the entire solution as one large commit.

Do not commit:

```text
target/
.idea/
*.iml
.env
application secrets
passwords
API keys
```

---

# 15. README Requirements

Your repository README should contain:

### Project Overview

Briefly explain the solution.

### Architecture

Explain the major components and how they interact.

### Technology Choices

Explain important technology/library choices.

### Setup Instructions

Explain how to:

1. Clone the repository
2. Configure the database
3. Start the application
4. Run the tests

### API Documentation

List the implemented endpoints with examples.

### Database

Explain the schema/design and any important decisions.

### Assumptions

Document assumptions made while interpreting the requirements.

### Design Decisions

Explain important implementation decisions and trade-offs.

### Known Limitations

Mention anything you intentionally did not implement.

### Production Considerations

Explain what you would improve before deploying the application to a production environment.

---

# 16. Submission

Push the completed implementation to the assigned GitHub repository.

Before submitting, verify that:

* The application starts successfully
* APIs work as expected
* Tests execute successfully
* Database setup is documented
* No credentials or secrets are committed
* README contains complete setup and usage instructions
* Git history contains meaningful commits

---

## Assessment Discussion

The submitted implementation will be discussed during the technical interview.

You should be able to explain:

* Your implementation
* Your design decisions
* Your assumptions
* Your database design
* Your error-handling approach
* Your testing strategy
* Potential scalability and production considerations

Additional scenarios or requirement changes may be introduced during the discussion.
