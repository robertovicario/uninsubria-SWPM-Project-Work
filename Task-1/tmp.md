# Functional Size Measurement Report: IoT Multicloud Security System with Facial Recognition

---

## Slide 1: Basic Functional Components

### Internal Logical Files (ILF)
- **User Data**: Contains information about authorized users, including names, credentials, and access profiles. It is essential for identity verification.
- **Access Log and Notifications**: Stores access events with timestamps and user details (or attempts at unauthorized access). Useful for auditing and tracking historical events.

### External Interface Files (EIF)
- **External Cloud Data**: Data stored and managed by external cloud providers, offering storage and backend functionality (e.g., AWS, Google Cloud).
- **IoT Devices**: Interfaces with data from IoT devices, possibly managed by other systems but used for data collection, like sensors or cameras.

### External Inputs (EI)
- **Video Input from IoT Cameras**: Incoming video streams feed the facial recognition algorithm to identify individuals.
- **Configuration Input from Administrators**: Allows administrators to set security thresholds, configure authorized users, and manage alert escalations.

### External Outputs (EO)
- **Real-Time Security Notifications**: Sends notifications (via SMS, email, or app) to administrators in case of unauthorized access, including details like time and location.
- **Periodic Access Reports**: Regularly generated reports on access activity, including statistics on authorized and unauthorized access attempts.

### External Inquiries (EQ)
- **Access History Consultation**: Enables querying the historical log to verify who accessed or attempted to access the system.
- **Security Configuration Inquiry**: Provides configured security information (e.g., alert level escalations, authorized users).

---

## Slide 2: Boundary Definition


1. **Boundary Definition**:
   - The boundary includes all components managed directly by the security system. Systems or user domains outside this boundary interact with the system but are not under direct control.
2. **External Interactions**:
   - The system may receive data from IoT devices (e.g., video streams) and send alerts to administrators via messaging or email services, but these external devices and services lie outside the boundary.
3. **User Domains**:
   - Users interact with the system to configure settings, view reports, and receive notifications. However, the user domain is separate as they cannot modify internal logic or data without using defined interfaces.
4. **Internal Components**:
   - Data on users and logs of access and security events are maintained within the boundary, as they are part of the system’s internal logic and accessible only through system functions.

---

## Slide 3: Components Schema
**[Insert diagram of Basic Functional Components and Boundary here]**

---

## Slide 4: Processing Table

| Form of Processing Logic                                     | EI  | EO  | EQ  |
|-------------------------------------------------------------|-----|-----|-----|
| **1. Validations are performed**                            | c   | c   | c   |
| **2. Mathematical formula and calculations are performed**  | c   | m*  | n   |
| **3. Equivalent values are converted**                      | c   | c   | c   |
| **4. Data is filtered and selected by using specified criteria to compare multiple sets of data** | c | c | c |
| **5. Conditions are analyzed to determine which are applicable** | c | c | c |
| **6. At least one ILF is updated**                          | m*  | m*  | n   |
| **7. At least one ILF or EIF is referenced**                | c   | c   | m   |
| **8. Data or control information is retrieved**             | c   | c   | m   |
| **9. Derived data is created**                              | c   | m*  | n   |
| **10. Behavior of the system is altered**                   | m*  | m*  | n   |
| **11. Prepare and present information outside the boundary**| c   | m   | m   |
| **12. Capability to accept data or control information that enters the application boundary** | m | c | c |
| **13. Resorting or rearranging a set of data**              | c   | c   | c   |

legenda della tabella

---

## Slide 5: Description of REF, DET, and FTR

### Record Element Types (RETs)
- Each group of data for an authorized user (e.g., name, photo, access permissions) in the **User Data** file is an RET.
- Each record in the **Access Log and Notifications** representing an access event or attempt (with timestamp, user, and result) is an RET.

### Data Element Types (DETs)
- For the **New User Registration** transaction, DETs include fields like username, photo, email, and access level.
- For the **Unauthorized Access Notification**, DETs include event timestamp, alert level, incident location, and notification type (SMS, email).

### File Types Referenced (FTRs)
- For **Facial Recognition**, the system references **User Data** as an FTR to verify identity.
- For **Access History Consultation**, the system references the **Access Log and Notifications** to display past events.

---

## Slide 6: UFP and Complexity for ILF

| Record Element Types (RET)  | Data Elements (DET) 1-19 | Data Elements (DET) 20-50 | Data Elements (DET) Greater than 50 |
|-----------------------------|--------------------------|---------------------------|-------------------------------------|
| **1**                       | Low (7)                 | Low (7)                   | Average (10)                       |
| **2-5**                     | Low (7)                 | Average (10)              | High (15)                          |
| **More than 5**             | Average (10)            | High (15)                 | High (15)                          |

<br>

| ILF Component                  | RETs | DETs | Complexity |
|--------------------------------|------|------|------------|
| **Authorized User Data**       | 3    | 25   | Medium (10) |
| **Access Log and Notifications** | 6  | 35   | High (15)   |

---

## Slide 7: UFP and Complexity for EIF

| Record Element Types (RET)  | Data Elements (DET) 1-5 | Data Elements (DET) 6-19 | Data Elements (DET) Greater than 19 |
|-----------------------------|-------------------------|---------------------------|-------------------------------------|
| **1**                       | Low (5)                | Low (5)                   | Average (7)                        |
| **2-5**                     | Low (5)                | Average (7)               | High (10)                          |
| **More than 5**             | Average (7)            | High (10)                 | High (10)                          |

<br>

| EIF Component                    | RETs | DETs | Complexity |
|----------------------------------|------|------|------------|
| **Cloud Provider Configurations** | 2    | 10   | Medium (7) |
| **IoT Device Data**              | 1    | 15   | Low (5)    |

---

## Slide 8: UFP and Complexity for EI
| Files Type Referenced (FTR) | Data Elements (DET) 1-4 | Data Elements (DET) 5-15 | Data Elements (DET) Greater than 15 |
|-----------------------------|-------------------------|---------------------------|-------------------------------------|
| **Less than 2**             | Low (3)                | Low (3)                   | Average (4)                        |
| **2**                       | Low (3)                | Average (4)               | High (6)                           |
| **Greater than 2**          | Average (4)            | High (6)                  | High (6)                           |

<br>

| EI Component                      | DETs | FTRs | Complexity |
|-----------------------------------|------|------|------------|
| **Video Feed for Facial Recognition** | 10   | 2    | Medium (4) |
| **Security Parameter Configuration**  | 5    | 1    | Low (3)    |

---

## Slide 9: UFP and Complexity for EO
| Files Type Referenced (FTR) | Data Elements (DET) 1-5 | Data Elements (DET) 6-19 | Data Elements (DET) Greater than 19 |
|-----------------------------|-------------------------|---------------------------|-------------------------------------|
| **Less than 2**             | Low (4)                | Low (4)                   | Average (5)                        |
| **2**                       | Low (4)                | Average (5)               | High (7)                           |
| **Greater than 2**          | Average (5)            | High (7)                  | High (7)                           |
<br>

| EO Component                       | DETs | FTRs | Complexity |
|------------------------------------|------|------|------------|
| **Real-Time Alarm Notifications**  | 6    | 2    | Medium (5) |
| **Access and Security Report**     | 20   | 3    | High (7)   |

---

## Slide 10: UFP and Complexity for EQ


| Files Type Referenced (FTR) | Data Elements (DET) 1-5 | Data Elements (DET) 6-19 | Data Elements (DET) Greater than 19 |
|-----------------------------|-------------------------|---------------------------|-------------------------------------|
| **Less than 2**             | Low (3)                | Low (3)                   | Average (4)                        |
| **2**                       | Low (3)                | Average (4)               | High (6)                           |
| **Greater than 2**          | Average (4)            | High (6)                  | High (6)                           |

<br>

| EQ Component                          | DETs | FTRs | Complexity |
|---------------------------------------|------|------|------------|
| **Access History Consultation**       | 7    | 2    | Medium (4) |
| **Current Security Configurations View** | 4  | 1    | Low (3)    |

---

## Slide 11: Function Points (FP) Calculation

| Element | Low   | Average   | High   | Total |
|---------|-------|-----------|--------|-------|
| Input   | 1 x 3 | 2 x 4     | 1 x 6  | 17    |
| Output  | 1 x 4 | 1 x 5     | 0 x 7  | 9     |
| Inquiry | 1 x 3 | 1 x 4     | 1 x 6  | 13    |
| ILF     | 0 x 7 | 1 x 10    | 1 x 15 | 25    |
| EIF     | 1 x 5 | 0 x 7     | 1 x 10 | 15    |
| **FP Total**  |       |           |        | **79** |

The total Function Points (FP) for the project is calculated to be **79 FP**, representing the overall functional size of the system.

---

## Slide 12: Final Considerations

The Function Point Analysis (FPA) for the "IoT Multicloud Security System with Facial Recognition" project provides a comprehensive measurement of its functional size, totaling 79 Function Points. This calculation supports estimations for project cost, resource allocation, and complexity. Additionally, defining boundaries and categorizing internal and external interactions ensures that the system operates efficiently within its scope, maintaining clear lines between internal management and external dependencies.
