---
title: "&quot; pam_radius_auth: Failed to open RADIUS IPv6 socket&quot;"
date: 2023-08-07
forum: Installation &amp; Upgrades
---

### Post by prashanma on 2023-08-07
Hi Team,

We've encountered the following error after disabling IPv6. Previously, it was working fine when IPv6 was enabled. However, in our environment, IPv6 is not in use:
"pam_radius_auth: Failed to open RADIUS IPv6 socket: Address family not supported by protocol."


We've also noticed that there's no traffic appearing in the RADIUS server logs.


Here are the server details:


**Output of cat /etc/os-release:**


PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy


**Output of uname -r:**


5.15.0-78-generic


**Output of apt list --installed | grep pam-radius:**


libpam-radius-auth/jammy,now 2.0.0-1 amd64 [installed]


We're seeking guidance on how to resolve this error. Any assistance would be greatly appreciated.


Thank you.
[COLOR=#374151][FONT=Söhne]
[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2023-08-07
See if this helps: [https://github.com/FreeRADIUS/freeradius-server/issues/4397](https://github.com/FreeRADIUS/freeradius-server/issues/4397)

---

### Post by prashanma on 2023-08-08
> **1fallen said:**
> See if this helps: [https://github.com/FreeRADIUS/freeradius-server/issues/4397](https://github.com/FreeRADIUS/freeradius-server/issues/4397)

Thank you. I have applied the latest git hub pam_radius. It worked

---

### Post by ActionParsnip on 2023-08-08
Please mark as solved if the issue is sorted :)

---

