cat > zoho_questions.md <<'EOF'
# SOFTWARE TESTING ENGINEER – ZOHO ROLE
## Interview Questions with Answers & Live Examples

### BEGINNER LEVEL — 10 QUESTIONS

1. **What is the difference between Verification and Validation?**  
**Answer:** Verification checks if we are building the product right. Validation checks if we built the right product.  
**Live Example:** Verify acceptance criteria exists; validate by executing the feature and confirming it meets user needs.

2. **What are the different levels of testing?**  
**Answer:** Unit, Integration, System, Acceptance.  
**Live Example:** Unit test validation functions, integration test DB+service, system test full flow, acceptance test against requirements.

3. **What is a Test Case and what should it contain?**  
**Answer:** A Test Case contains steps, inputs, expected output, preconditions, and postconditions.  
**Live Example:** Test login: precondition (user exists), steps (enter credentials), expected (redirect to dashboard).

4. **What is Severity vs Priority?**  
**Answer:** Severity = impact on system. Priority = order of fixing based on business needs.  
**Live Example:** Payment gateway down -> Severity: High, Priority: Critical. Minor UI typo -> Severity: Low, Priority: Low.

5. **What is Regression Testing?**  
**Answer:** Re-running tests to ensure recent changes didn't break existing functionality.  
**Live Example:** After bug fix in reports, re-run report-related test cases or automated regression suite.

6. **What is the Bug Life Cycle?**  
**Answer:** Typical states: New → Assigned → Open → Fixed → Retest → Verified → Closed (or Reopened).  
**Live Example:** Raise a bug in JIRA, assign to dev, verify fix, close after confirmation.

7. **What is Traceability Matrix (RTM)?**  
**Answer:** A mapping between requirements and test cases to ensure coverage.  
**Live Example:** Map Req1 -> TC1, TC2; Req2 -> TC3 to show coverage.

8. **What are Positive and Negative Test Cases?**  
**Answer:** Positive cases use valid input; negative cases use invalid or unexpected input.  
**Live Example:** For email field: positive - valid email; negative - missing '@', long strings, SQL attempts.

9. **What is Smoke Testing?**  
**Answer:** A quick set of tests to ensure the build is stable enough for further testing.  
**Live Example:** After deploy, check login, main navigation, and a key transaction flow.

10. **What is Exploratory Testing?**  
**Answer:** Unscripted testing where test design and execution happen simultaneously.  
**Live Example:** Spend 30 minutes exploring a new feature, logging unexpected behaviors and hypotheses.

### MEDIUM LEVEL — 10 QUESTIONS

1. **How do you design test cases for an API endpoint?**  
**Answer:** Cover positive, negative, boundary, authentication, headers, status codes, and error scenarios.  
**Live Example:** For POST /users: test valid create, missing fields, duplicate email, invalid JSON, large payload, unauthorized request.

2. **How would you test a file upload feature?**  
**Answer:** Test valid/invalid types, min/max sizes, interrupted uploads, filename edge cases, and virus scanning behavior.  
**Live Example:** Upload a 0-byte file, a large file near limit, a disallowed .exe file, and simulate network interruption.

3. **How do you prioritize test cases for a release?**  
**Answer:** Prioritize by business impact, frequency of use, risk areas, and past defect history.  
**Live Example:** Mark login, checkout/payment, and profile edits as Critical; secondary features as Medium.

4. **What is SQL testing and how to perform it?**  
**Answer:** Validate DB CRUD operations, constraints, triggers, and data integrity.  
**Live Example:** After creating a user via UI, run SELECT queries to verify the user row and fields.

5. **How do you test across different environments (Dev/QA/Prod)?**  
**Answer:** Use environment-specific configs/variables, data isolation, and validate environment migrations.  
**Live Example:** Switch Postman environment variables (baseUrl, token) to run same collection in Dev and QA.

6. **How would you test performance for a web page?**  
**Answer:** Define SLAs, run load tests, measure response percentiles, throughput, and error rates.  
**Live Example:** Use a load tool to simulate 1000 concurrent users and analyze 95th/99th percentile latencies.

7. **What is SQL injection and how do you test for it?**  
**Answer:** SQL injection injects SQL through inputs; test by sending malicious payloads and checking DB behavior.  
**Live Example:** Submit "' OR '1'='1" in a search field and ensure parameterized queries prevent unauthorized data exposure.

8. **How to test OAuth-protected APIs?**  
**Answer:** Validate token issuance, expiration, refresh flow, scopes, and unauthorized access.  
**Live Example:** Obtain token, call endpoint, let token expire, verify access fails, then refresh token and retry.

9. **How do you write effective defect reports?**  
**Answer:** Include clear title, steps to reproduce, expected vs actual, environment, severity, logs/screenshots, and test data.  
**Live Example:** Provide curl command, request/response payloads, screenshot, and exact reproduction steps.

10. **How does testing fit into CI/CD?**  
**Answer:** Automate unit/integration/e2e tests in pipeline to catch regressions before deploy.  
**Live Example:** Commit triggers pipeline → run tests → on pass deploy to staging → automated smoke tests run.

### ADVANCED LEVEL — 10 QUESTIONS

1. **How to design a test strategy for a multi-tenant SaaS application?**  
**Answer:** Ensure tenant isolation tests, RBAC, per-tenant configs, scalability, and data partitioning verification.  
**Live Example:** Create Tenant A and Tenant B, perform operations in A and verify no data appears in B.

2. **How would you automate an end-to-end suite for a complex workflow?**  
**Answer:** Break into reusable API components, mock unstable external services, and use UI only for critical flows.  
**Live Example:** Automate "create order → process payment → ship" via API calls, assert DB and notifications at each step.

3. **How do you manage test data at scale?**  
**Answer:** Use seeded DBs, factories, idempotent setup/teardown, and anonymized production snapshots.  
**Live Example:** Seed database with 1000 users before running a suite and clean up after tests.

4. **What are key design choices for a test automation framework?**  
**Answer:** Layered architecture, page-object or component model, test data management, CI integration, and reporting.  
**Live Example:** Show folder structure: tests/, pages/, fixtures/, utils/ and a sample pytest using page objects.

5. **How to measure and improve test coverage and quality?**  
**Answer:** Use code coverage, risk-based mapping, mutation testing, and monitor defect escape rate.  
**Live Example:** Run coverage tool (pytest --cov) and add tests for uncovered critical modules.

6. **How do you detect and reduce flaky tests?**  
**Answer:** Track flakiness, add retries, isolate tests, use stable locators, and remove timing dependencies.  
**Live Example:** Replace sleeps with explicit waits in UI tests and demonstrate stability over repeated runs.

7. **How to validate database migrations in production?**  
**Answer:** Dry-run in staging, backup before migration, canary rollouts, and run verification scripts post-migration.  
**Live Example:** Run migration on snapshot DB and compare row counts and key constraints before and after.

8. **How to add observability for test runs?**  
**Answer:** Collect metrics (duration, pass rate, flakiness), push to metrics store, and visualize in dashboards.  
**Live Example:** Configure test runner to emit Prometheus metrics and build Grafana panels for pass/fail trends.

9. **How to secure testing pipelines and test data?**  
**Answer:** Use secrets management, mask/anonymize PII, restrict access, and use ephemeral environments.  
**Live Example:** Retrieve API keys from a vault in CI and fail pipeline if secrets are missing.

10. **How to evaluate a new testing tool for adoption?**  
**Answer:** Pilot with representative tests, measure runtime, flakiness, integration, learning curve, and cost.  
**Live Example:** Run a 2-week pilot migrating five critical tests to Playwright and compare results.
EOF
