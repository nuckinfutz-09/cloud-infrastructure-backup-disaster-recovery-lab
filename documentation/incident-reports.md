# Cloud Infrastructure – Incident Reports & RCA

## Overview

This document records troubleshooting, backup and disaster recovery activities performed during the AWS and VMware cloud infrastructure lab.

---

## Incident 1 – AWS EC2 HTTP Connectivity Failure

**Service:** AWS EC2 / IaaS  
**Severity:** Medium  
**Status:** Resolved

### Symptoms
The Nginx web server was running, but HTTP access from the browser was unsuccessful.

### Investigation
- Checked EC2 instance status.
- Reviewed the associated Security Group.
- Inspected inbound traffic rules.
- Identified that HTTP port 80 was not permitted.

### Root Cause
The EC2 Security Group did not allow inbound HTTP traffic on port 80.

### Resolution
Added an inbound Security Group rule allowing HTTP traffic on port 80.

### Prevention
- Verify Security Group rules during deployment.
- Document required network ports.
- Include connectivity checks in infrastructure validation.

---

## Incident 2 – AWS EC2 Nginx Service Failure

**Service:** AWS EC2 / Linux  
**Severity:** Medium  
**Status:** Resolved

### Symptoms
The web server was not responding as expected.

### Investigation
- Checked Nginx service status.
- Inspected service and configuration.
- Investigated the web server failure.

### Root Cause
An Nginx service/configuration issue affected web server availability.

### Resolution
Corrected the identified service/configuration issue and verified Nginx operation.

### Prevention
- Monitor service health.
- Validate configuration changes.
- Verify HTTP availability after maintenance.

---

## Incident 3 – AWS EC2 Backup and BaaS Validation

**Service:** AWS EC2 / EBS Backup  
**Severity:** Planned Backup Test  
**Status:** Snapshot created

### Objective
Demonstrate backup protection for an AWS EC2 workload using EBS snapshots.

### Investigation and Actions
- Identified the EBS storage associated with the EC2 workload.
- Created an EBS snapshot.
- Checked the snapshot status in the AWS Console.
- Confirmed that the snapshot reached the Available state.

### Backup Approach
EBS snapshots provide point-in-time backup capability for EBS volumes.

### Outcome
The snapshot was successfully created and its availability status was verified.

### Prevention and Best Practices
- Schedule regular backups.
- Monitor backup completion.
- Define backup retention policies.
- Perform periodic restore tests.

---

## Incident 4 – AWS EC2 Instance Loss and DRaaS Recovery

**Service:** AWS EC2 / Disaster Recovery  
**Severity:** High  
**Status:** Recovery completed

### Scenario
Simulated loss of the original EC2 instance to demonstrate infrastructure recovery.

### Investigation
- Identified the original EC2 instance.
- Used the previously created custom AMI.
- Reviewed the available recovery image.

### Root Cause
The original EC2 instance was intentionally terminated as part of a disaster recovery simulation.

### Recovery Actions
- Launched a replacement EC2 instance using the custom AMI.
- Named the replacement instance `lab-web-server-recovered`.
- Checked the instance state.
- Verified that the replacement instance passed its EC2 status checks.

### Outcome
Successfully provisioned a replacement instance from the custom AMI.

### Prevention and Best Practices
- Maintain updated machine images.
- Define recovery procedures.
- Test recovery processes periodically.
- Document recovery responsibilities and dependencies.

### Limitation
Cross-region AMI copying was attempted but blocked by an AWS Service Control Policy. Cross-region disaster recovery was not demonstrated.

---

## Incident 5 – VMware Ubuntu Infrastructure Validation

**Service:** VMware Fusion / Ubuntu Linux  
**Severity:** Infrastructure Validation  
**Status:** Passed

### Environment
- VMware Fusion Pro
- Ubuntu Server 24.04 LTS ARM64
- 2 vCPUs
- 4 GB RAM
- 40 GB virtual disk

### Validation Activities
- Verified CPU and memory allocation.
- Expanded the Linux LVM root filesystem.
- Verified available disk capacity.
- Installed and enabled SSH.
- Configured UFW firewall rules.
- Installed and verified Nginx.
- Tested HTTP access from the Mac host.
- Verified internet connectivity.

### Outcome
The Ubuntu virtual machine operated successfully, Nginx was active, and the web server was accessible from the host machine.

---

## Key Skills Demonstrated

- AWS EC2 infrastructure troubleshooting
- IaaS fundamentals
- EBS snapshot backup concepts (BaaS)
- AMI-based recovery concepts (DRaaS)
- VMware virtualization
- Ubuntu Linux administration
- Nginx service troubleshooting
- Security Group and firewall configuration
- Incident investigation and RCA documentation
- Recovery validation

---

**Project Type:** Hands-on cloud infrastructure lab  
**Environment:** AWS and VMware Fusion  
**Purpose:** Cloud Engineer L1 technical portfolio
