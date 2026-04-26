# User Stories - E-Commerce User Login & Checkout

## Feature: User Login

### User Story ID: US_LOGIN_001
**Title:** Standard Email/Password Login  
**User Story:**  
As a **registered customer**  
I want **to log in using my email and password**  
So that **I can access my profile and saved information**

**Acceptance Criteria:**
* **Scenario: Successful Login (Happy Path)**
  * Given I am on the login page
  * When I enter a valid email and matching password
  * Then I should be redirected to my account dashboard
  * And I should see a success message welcoming me

* **Scenario: Invalid Credentials (Negative)**
  * Given I am on the login page
  * When I enter an email and password that do not match
  * Then I should see an error message: "Invalid email or password"
  * And I should not be logged in

* **Scenario: Account Lockout (Security)**
  * Given I am on the login page
  * When I enter incorrect credentials for 5 consecutive attempts
  * Then my account should be temporarily locked
  * And I should receive an email notification regarding the lockout

---

### User Story ID: US_LOGIN_002
**Title:** Social Login Integration  
**User Story:**  
As a **customer**  
I want **to log in using Google or Facebook**  
So that **I can quickly access my account without remembering a new password**

**Acceptance Criteria:**
* **Scenario: New User Registration via Social Login**
  * Given I am a first-time user
  * When I click the "Sign in with Google" button
  * And no account exists with my Google email
  * Then the system should automatically create a new account
  * And log me in immediately

---

## Feature: Guest Checkout

### User Story ID: US_GUEST_001
**Title:** Non-Registered Checkout  
**User Story:**  
As a **guest user**  
I want **to complete a purchase without creating an account**  
So that **I can finish my order quickly**

**Acceptance Criteria:**
* **Scenario: Checkout as Guest**
  * Given I have items in my shopping cart
  * When I click "Proceed to Checkout"
  * And I select "Checkout as Guest"
  * Then I should be prompted for a valid email address
  * And I should be allowed to proceed to shipping information

---

## Feature: Shopping Cart

### User Story ID: US_CART_001
**Title:** Real-time Cart Management  
**User Story:**  
As a **customer**  
I want **to manage items in my shopping cart**  
So that **I can review and adjust my order before purchasing**

**Acceptance Criteria:**
* **Scenario: Item Quantity Update**
  * Given I have an item in my cart
  * When I change the item quantity from 1 to 2
  * Then the cart total should update immediately to reflect the new price

* **Scenario: Out of Stock Notification**
  * Given I have an item in my cart
  * When that item goes out of stock in the inventory system
  * Then I should receive a notification on the cart page before proceeding to checkout

---

## Feature: Checkout Flow & Address Validation

### User Story ID: US_CHKT_001
**Title:** Multi-step Checkout with Address Validation  
**User Story:**  
As a **customer**  
I want **my shipping address verified and processing handled securely**  
So that **I receive my order at the correct location without payment issues**

**Acceptance Criteria:**
* **Scenario: Address Validation Warning**
  * Given I am on the shipping info step
  * When I enter a postal code that does not match the city
  * Then the system should display a warning "Address could not be validated"
  * And allow me to proceed manually if I confirm it is correct

* **Scenario: Failed Payment Handling**
  * Given I am on the final review page
  * When my payment is declined by the processor
  * Then I should see a clear error message explaining the failure
  * And my cart contents should remain intact for me to try again

---

## QA Enhancement & Risks
* **Risk (High):** Session hijacking if "Remember Me" functionality isn't properly scoped with secure cookies.
* **Risk (Medium):** Guest users completing orders but failing to create an account if the prompt is too intrusive or unclear.
* **Edge Case:** Applying multiple coupons simultaneously (PRD doesn't specify if this is allowed).
* **Missing Clarification:** Exactly how many failed login attempts result in a lockout (suggesting 5).
