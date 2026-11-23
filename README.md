# Ubuntu Server Security Hardening & Assessment

## Project Overview

This project demonstrates the deployment, configuration, and security hardening of an Ubuntu Linux server in a virtualized environment.

The objective was to reduce the server's attack surface, strengthen remote access security, implement intrusion prevention controls, and evaluate the effectiveness of security improvements through vulnerability and configuration auditing.

## Lab Environment

| Component | Configuration |
|---|---|
| Host Operating System | macOS |
| Virtualization | UTM |
| Guest Operating System | Ubuntu Server 26.04.1 LTS |
| Architecture | ARM64 (aarch64) |
| Network | Private virtual network |
| Remote Administration | OpenSSH |
| Firewall | UFW |
| Intrusion Prevention | Fail2Ban |
| Security Auditing | Lynis |

## Security Objectives

- Secure remote administration using SSH public-key authentication.
- Disable password-based SSH authentication.
- Prevent direct root SSH login.
- Configure host-based firewall protection.
- Implement automated SSH intrusion prevention.
- Apply Linux kernel security settings.
- Perform security assessments and validate remediation results.

## Security Implementation

### 1. Network Security — UFW

Configured Uncomplicated Firewall (UFW) to restrict incoming connections while maintaining authorized SSH access.

**Verified configuration:**
- Firewall status: Active
- Default incoming policy: Deny
- Default outgoing policy: Allow
- SSH TCP port 22: Allowed

### 2. SSH Hardening

Implemented SSH access controls to reduce unauthorized remote access risks.

**Verified configuration:**

| SSH Setting | Value |
|---|---|
| PermitRootLogin | no |
| PubkeyAuthentication | yes |
| PasswordAuthentication | no |
| KbdInteractiveAuthentication | no |

Generated an Ed25519 SSH key pair and successfully tested public-key authentication from the macOS host.

Verified that password-based SSH authentication was rejected.

### 3. Intrusion Prevention — Fail2Ban

Installed and configured Fail2Ban to monitor SSH authentication failures and provide automated protection against repeated unauthorized login attempts.

**Verified results:**
- SSH jail enabled.
- Fail2Ban operational.
- SSH monitoring active.

### 4. Linux Kernel Hardening

Reviewed and verified Linux kernel security parameters.

| Security Parameter | Verified Value |
|---|---|
| kernel.randomize_va_space | 2 |
| fs.protected_symlinks | 1 |
| fs.protected_hardlinks | 1 |
| kernel.kptr_restrict | 2 |

Configured persistent kernel pointer restrictions using sysctl.

### 5. Security Auditing — Lynis

Performed security assessments using Lynis to identify configuration weaknesses and opportunities for system hardening.

**Assessment results:**

| Metric | Initial Assessment | Final Assessment |
|---|---|---|
| Hardening Index | 65 | 70 |
| Improvement | — | +5 points |

The improvement was achieved after implementing additional security controls and validating their configuration.

The Lynis Hardening Index reflects the adoption of recommended security controls and should not be interpreted as a percentage of protection against attacks.

## Security Validation

The following checks were performed:

- Verified active UFW firewall rules.
- Confirmed successful SSH public-key authentication.
- Confirmed password-based SSH authentication was disabled.
- Verified direct root SSH login was disabled.
- Checked Fail2Ban SSH jail status.
- Validated kernel security parameters.
- Repeated the Lynis security assessment.

## Evidence

The `02-Screenshots` directory contains screenshots documenting system configuration, security controls, command execution, and assessment results.

The `01-Project-Report` directory contains the technical security assessment report.

## Skills Demonstrated

- Linux Server Administration
- Network Configuration and Troubleshooting
- SSH Security and Key Management
- Firewall Configuration
- Intrusion Prevention
- Operating System Hardening
- Security Auditing
- Technical Troubleshooting
- Security Documentation

## Security & Scope

This project was conducted in a controlled virtual lab environment for educational and practical cybersecurity training purposes.

All configurations and security assessments were performed on systems under my control.

Sensitive information, including private keys, credentials, and confidential configuration data, is excluded from the public documentation.

## Future Improvements

- Implement centralized system logging.
- Configure automated security updates.
- Introduce file integrity monitoring.
- Review remaining Lynis recommendations.
- Conduct additional security validation after system changes.