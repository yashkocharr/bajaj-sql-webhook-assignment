# Bajaj Finserv Health – Webhook SQL Submission (JAVA)

## ✅ Overview
This Spring Boot app is developed for the Bajaj Finserv Health Java Qualifier Assignment. It:

- Automatically sends a POST request to generate a webhook on startup
- Receives a `webhook` URL and `JWT access token`
- Submits the final SQL query (for the assigned problem) using the access token
- Is fully automated — no controller or manual trigger required
- Uses `RestTemplate` for API communication

---

## 🚀 Technologies Used

- Java 17
- Spring Boot 3.x
- Maven
- REST API
- JWT Authorization
- GitHub for version control

---

## 🧠 Final SQL Query

```sql
SELECT 
    e1.EMP_ID,
    e1.FIRST_NAME,
    e1.LAST_NAME,
    d.DEPARTMENT_NAME,
    COUNT(e2.EMP_ID) AS YOUNGER_EMPLOYEES_COUNT
FROM EMPLOYEE e1
JOIN DEPARTMENT d ON e1.DEPARTMENT = d.DEPARTMENT_ID
LEFT JOIN EMPLOYEE e2 
    ON e1.DEPARTMENT = e2.DEPARTMENT
    AND e1.DOB < e2.DOB
GROUP BY e1.EMP_ID, e1.FIRST_NAME, e1.LAST_NAME, d.DEPARTMENT_NAME
ORDER BY e1.EMP_ID DESC;
