# Building a SOC + Honeynet in Azure (Live Traffic)

![image](https://github.com/sMedrano101/Cloud-Soc-Honeynet/assets/60121429/2f76152b-02d2-4238-9a93-85f0cc7d0203)



## Introduction


Welcome to my Soc + Honeynet in Azure Project! I've built a compact honeynet in Azure, integrating logs from various sources into a Log Analytics workspace for Microsoft Sentinel. The project involves:

Data Sources:

-SecurityEvent (Windows Event Logs)
-Syslog (Linux Event Logs)
-SecurityAlert (Log Analytics Alerts)
-SecurityIncident (Sentinel Incidents)
-AzureNetworkAnalytics_CL (Malicious Flows)

Workflow:

-Measured security metrics in an insecure environment for 24 hours
-Applied security controls to harden the environment
-Measured metrics again for 24 hours


## Architecture Before Hardening / Security Controls
![image](https://github.com/sMedrano101/Cloud-Soc-Honeynet/assets/60121429/8ab3a018-6912-4066-ad57-0f16d1e63298)


## Architecture After Hardening / Security Controls
![image](https://github.com/sMedrano101/Cloud-Soc-Honeynet/assets/60121429/9d75b355-da8a-40b8-8840-87f9aea9f85b)


The architecture of the mini honeynet in Azure consists of the following Azure components and regulations:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace KQL Queries
- Azure Key Vault
- NIST SP 800-53 Revision 5 for Security Controls
- NIST SP 800-61 Revision 2 for Incident Handling Guidance
- Azure Storage Account
- Microsoft Sentinel


BEFORE Metrics:
In the initial state, all resources were deployed openly to the internet. Virtual Machines had both Network Security Groups and built-in firewalls wide open, and other resources had public endpoints visible to the internet, making Private Endpoints unnecessary.

AFTER Metrics:
Following improvements, Network Security Groups were strengthened, allowing only traffic from my admin workstation. Additionally, all other resources were secured through their built-in firewalls and Private Endpoint protection.

## Attack Maps Before Hardening / Security Controls

![image](https://github.com/sMedrano101/Cloud-Soc-Honeynet/assets/60121429/3f4aeb20-f39c-4015-97f9-f63f00bb4ec4)<br>
![image](https://github.com/sMedrano101/Cloud-Soc-Honeynet/assets/60121429/229c8e6b-54df-4492-a1a0-24aba013bf4a)<br>
![image](https://github.com/sMedrano101/Cloud-Soc-Honeynet/assets/60121429/112f0ebb-996d-4d99-ae6b-8eb62ccb4645)<br>
![image](https://github.com/sMedrano101/Cloud-Soc-Honeynet/assets/60121429/19a0bfe5-6ea3-4aec-ad3f-504fe1c0af44)<br>


## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
Start Time 12/4/2023, 10:40:11 AM
Stop Time 12/5/2023 10:40:11

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 65785
| Syslog                   | 1802
| SecurityAlert            | 8
| SecurityIncident         | 195
| AzureNetworkAnalytics_CL | 1884

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
Start Time 12/8/2023, 12:46:46 AM
Stop Time	12/9/2023 0:46:46

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 11577
| Syslog                   | 0
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

## Conclusion


In this project, a compact honeynet was built in Microsoft Azure, and log sources were seamlessly integrated into a Log Analytics workspace. Microsoft Sentinel played a crucial role in triggering alerts and generating incidents based on the ingested logs. 

The project involved measuring metrics in the insecure environment before and after implementing security controls. Notably, the application of security measures led to a significant reduction in the number of security events and incidents, underscoring their effectiveness.

It's important to acknowledge that if the network resources were extensively used by regular users, there might have been an increase in security events and alerts within the 24-hour period following the implementation of the security controls.
