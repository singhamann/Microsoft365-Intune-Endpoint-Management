# Microsoft 365 Intune Endpoint Management Lab

## Project Overview

This project demonstrates a hands-on Microsoft 365 Business Premium lab focused on cloud identity, device enrollment, compliance management, and endpoint configuration using Microsoft Intune.

The lab simulates common entry-level IT support and MSP tasks, including creating users, assigning licenses, enabling MDM enrollment, enrolling a Windows device, creating compliance policies, and deploying a configuration profile.

---

## Technologies Used

- Microsoft 365 Business Premium
- Microsoft Intune Admin Center
- Microsoft Entra ID
- Windows 10
- Mobile Device Management (MDM)
- Device Compliance Policies
- Configuration Profiles
- Wi-Fi Profile Deployment
- BitLocker / Device Encryption Requirements
- Microsoft Defender / Endpoint Security Concepts

---

## Lab Environment

**Tenant / Organization:** Great River Financial Services Inc.  
**Microsoft 365 License:** Microsoft 365 Business Premium  
**Managed Device:** Windows 10 HP Laptop  
**Device Name:** AMAN-JUDGE  
**Management Platform:** Microsoft Intune  
**Ownership Type:** Personal lab device

---

## Objectives

The goal of this project was to build a realistic Microsoft 365 endpoint management lab that shows the full workflow from tenant setup to device management.

Main objectives:

- Confirm access to Microsoft 365 Admin Center and Intune Admin Center
- Configure Intune MDM automatic enrollment
- Connect a Windows device to a work or school account
- Enroll the Windows device into Microsoft Intune
- Create a cloud test user
- Assign Microsoft 365 Business Premium licensing
- Create and assign a Windows compliance policy
- Configure password and encryption compliance requirements
- Configure a Wi-Fi profile using Intune configuration profiles
- Verify that the enrolled Windows device reports as compliant

---

## Implementation Steps

### 1. Microsoft 365 Admin Center Access

The Microsoft 365 Admin Center was used to manage users, licenses, and tenant-level administration.

![Microsoft 365 Active Users](screenshots/01-active-users-admin-center.png)

---

### 2. Intune Admin Center Access

The Intune Admin Center was opened to manage devices, compliance policies, configuration profiles, and endpoint settings.

![Intune Admin Center Overview](screenshots/02-intune-admin-center-overview.png)

---

### 3. MDM Automatic Enrollment Configuration

MDM user scope was configured so Windows devices could automatically enroll into Intune when a work or school account was connected.

![MDM User Scope Configuration](screenshots/03-mdm-user-scope-automatic-enrollment.png)

Configuration used:

- MDM user scope: **All**
- MDM discovery URL: default Microsoft value
- MDM compliance URL: default Microsoft value
- WIP user scope: **None**

---

### 4. Windows Device Enrollment

The Windows laptop was connected through:

```text
Settings → Accounts → Access work or school
```

The device was connected using the Microsoft 365 work account.

![Access Work or School Setup](screenshots/04-access-work-or-school-setup.png)

During enrollment, Windows prompted for a PIN using Windows Hello.

![Windows Hello PIN Setup](screenshots/05-windows-hello-pin-setup.png)

After setup, the work or school account appeared as connected on the device.

![Work or School Account Connected](screenshots/06-work-school-account-connected.png)

---

### 5. Device Enrollment Verification

The enrolled Windows device appeared in Intune under Windows devices.

![Windows Device Compliant](screenshots/07-intune-windows-device-compliant.png)

The device showed:

- Managed by: **Intune**
- Ownership: **Personal**
- Compliance: **Compliant**
- OS: **Windows**

---

### 6. User Creation and License Assignment

A cloud test user was created in the Microsoft 365 Admin Center.

![Create User Basics](screenshots/08-create-user-basics.png)

A Microsoft 365 Business Premium license was assigned to the test user.

![Assign Business Premium License](screenshots/09-assign-business-premium-license.png)

The user settings were reviewed before finishing the account creation process.

![User Review and Finish](screenshots/10-user-review-and-finish.png)

---

### 7. Compliance Policy Creation

A Windows compliance policy was created from Intune.

![Create Compliance Policy](screenshots/11-create-compliance-policy-platform.png)

Policy name:

```text
Windows Device Compliance
```

Description:

```text
This policy enforces basic security requirements for Windows devices, including password policies, BitLocker encryption, and Defender antivirus settings.
```

![Compliance Policy Basics](screenshots/12-compliance-policy-basics.png)

---

### 8. Compliance Policy Settings

The compliance policy included basic security requirements.

![Compliance Policy Settings](screenshots/13-compliance-policy-settings.png)

Configured settings included:

- Minimum OS version: Windows 8.1 and later policy type
- Require password to unlock device
- Block simple passwords
- Minimum password length: 8
- Password type: Alphanumeric
- Required non-alphanumeric characters: 1
- Inactivity timeout before password required: 15 minutes
- Password expiration: 60 days
- Previous password reuse prevention: 3 passwords
- Require encryption of data storage on device

---

### 9. Noncompliance Actions

Actions for noncompliant devices were configured.

![Noncompliance Actions](screenshots/14-noncompliance-actions.png)

Configured actions included:

- Mark device noncompliant immediately
- Remotely lock the noncompliant device after 3 days

---

### 10. Compliance Policy Review

The compliance policy settings were reviewed before creation.

![Compliance Policy Review](screenshots/15-compliance-policy-review-create.png)

---

### 11. Wi-Fi Configuration Profile

A Windows Wi-Fi configuration profile was created in Intune.

![Create Wi-Fi Configuration Profile](screenshots/16-create-configuration-profile-wifi.png)

Profile name:

```text
Company Wi-Fi Profile
```

Description:

```text
This profile configures the Wi-Fi settings for managed Windows devices.
```

![Wi-Fi Profile Basics](screenshots/17-wifi-profile-basics.png)

The Wi-Fi profile XML was added to the configuration profile.

![Wi-Fi Profile XML Configuration](screenshots/18-wifi-profile-xml-configuration.png)

Example XML used:

```xml
<WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <SSID>
    <name>GRFS Wi-Fi</name>
  </SSID>
  <connectionType>ESS</connectionType>
  <security>
    <authEncryption>
      <authentication>WPA2PSK</authentication>
      <encryption>AES</encryption>
    </authEncryption>
    <sharedKey>
      <keyType>passPhrase</keyType>
      <protected>false</protected>
      <keyMaterial>GRFS12-34</keyMaterial>
    </sharedKey>
  </security>
</WLANProfile>
```

> Note: This Wi-Fi profile was created for lab demonstration purposes.

---

### 12. Final Device Status

The managed Windows device successfully appeared in Intune and reported as compliant.

![Managed Windows Device Final Status](screenshots/19-managed-windows-device-final-status.png)

Final device status:

- Device name: **AMAN-JUDGE**
- Managed by: **Intune**
- Ownership: **Personal**
- Compliance: **Compliant**
- OS: **Windows**
- Last check-in confirmed

---

## Results

The lab successfully demonstrated Microsoft Intune endpoint management using a Microsoft 365 Business Premium tenant.

Completed outcomes:

- Microsoft 365 tenant configured
- Intune Admin Center accessed
- MDM automatic enrollment enabled
- Windows laptop enrolled into Intune
- Device compliance verified
- Test user created
- Business Premium license assigned
- Windows compliance policy created
- Wi-Fi configuration profile created
- Managed device confirmed as compliant

---

## Skills Demonstrated

- Microsoft 365 Administration
- Microsoft Intune Administration
- Microsoft Entra ID basics
- User account creation
- License assignment
- Windows device enrollment
- MDM configuration
- Device compliance policy creation
- Password policy configuration
- Encryption compliance enforcement
- Configuration profile deployment
- Endpoint monitoring
- Documentation for IT support workflows

---

## Resume Project Summary

**Microsoft 365 Intune Endpoint Management Lab**

- Configured a Microsoft 365 Business Premium tenant and accessed Microsoft Intune Admin Center.
- Enabled MDM automatic enrollment and enrolled a Windows 10 laptop into Intune.
- Created a Windows compliance policy requiring password complexity and device encryption.
- Created a Wi-Fi configuration profile to demonstrate centralized device configuration.
- Created a Microsoft 365 test user and assigned a Business Premium license.
- Verified enrolled device status, Intune management, compliance state, and last check-in from the Intune Admin Center.

---

## Notes

This was completed in a personal lab environment for hands-on learning and portfolio documentation. The setup reflects common Microsoft 365 and Intune tasks used in help desk, MSP, and junior endpoint administrator roles.
