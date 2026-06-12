---
title: "Problem with Samba after python3 update"
date: 2020-10-07
forum: Installation &amp; Upgrades
---

### Post by Hans_van_Leeuwen on 2020-10-07
On 6 October2020 on an Ubuntu 16 system with kernel 4.4.0-187-generic,
by "unattended-updates", python3-urllib3 1.13.1-2ubuntu016.04.3
is updates to            python3-urllib3 1.13.1-2ubuntu016.04.4

After this update Samba doesn't work any more.
Registering of the Samba server at the Domain Controller no longer works.

# net ads join -U admsamba
Enter admsamba's password:
Failed to join domain: failed to lookup DC info for domain 'SAMBA-DOMEIN.LOCAL' over rpc: Undetermined error

From the website below I downloaded the former version python3-urllib3 1.13.1-2ubuntu016.04.3'
[https://Launchpad.net/ubuntu/xenial/amd65/python3-urllib3](https://Launchpad.net/ubuntu/xenial/amd65/python3-urllib3)

With dpkg I installed the former/correct version 3 over the new/wrong version 4.

#dpkg -i python3-urllib3_1.13.1-2ubuntu016.04.3_all.deb
dpkg: warning: downgrading python3-urllib3 from 1.13-1-2ubuntu0.16.04.4 to 1.13.1-2ubuntu016.04.3
(Reading database ... 168370 files and directories currently installed.)

The command below shows that the former version 3 is installed and the new version 4
is available.
# apt policy python3-urllib3
python3-urllib3
  Installed: 1.13.1-2ubuntu0.16.04.3
  Candidate: 1.13.1-2ubuntu0.16.04.4

After the downgrade, it was possible again to register the Samba server at the domain controller.

# net ads join -U admsamba
Enter admsamba's password:
Using short domain name -- SAMBA-DOMAIN
Joined 'system1'to dns domain 'samba-domain.local'

It seems that python3-urllib3 1.13.1-2ubuntu016.04.4 contains a problem.
Maybe the security update is to strict.

Do you have the same problem?
Wat is the correct channel to report this issue?

---

### Post by linuxlion2 on 2020-10-07
Yes, I have the same Problem.
Report this bug on  [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

