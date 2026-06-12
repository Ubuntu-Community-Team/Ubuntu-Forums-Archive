---
title: "Ubuntu 14.04 Samba Printer Issue"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by archer123 on 2014-04-28
I have been using 12.04 since its release. It connects to a samba printer (a Canon iP4850) presented by a QNAP NAS. This works fine.

I have recently created a clean install of 14.04 with no problems. I want to connect to the same Samba printer. Unfortunately it does not work. I have tried using the drivers provided by Canon (as used on my 12.04 install) but this did not work. When I do test print I briefly see the message  *"session setup failed*: NT_STATUS_LOGON_FAILURE" in the Printer State field of Printer Properties quickly followed by "Idle - Error writing spool: NT_STATUS_DISK_FULL". I have found some posts about updating the domain in the smb.conf file but this also did not work. 

Does anyone have any suggestions?

---

### Post by archer123 on 2014-04-29
I have now managed to get the printer to work but not via Samba. QNAP support Bonjour printing and this has allowed the printer to spring into life. Still don't know why Samba did not work.

---

