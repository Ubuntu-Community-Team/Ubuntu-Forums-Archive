---
title: "Unable to Install Sbackup"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by billbog on 2008-10-20
Hi - I am unable to run sbackup having installed it from the repos .I get the following error message in system log :
 network lists. 
Oct 20 18:02:00 bill NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct 20 18:17:01 bill /USR/SBIN/CRON[23347]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 20 18:24:33 bill kernel: [ 1519.406187] simple-backup-c[31582]: segfault at 00000000 eip 00000000 esp b67b42dc error 4
Oct 20 18:38:08 bill kernel: [ 2333.714948] simple-backup-c[13994]: segfault at 00000000 eip 00000000 esp b5d542dc error 4

---

### Post by billbog on 2008-10-22
Hey I think I have solved this : I removed a blank CD from the CD drive and it works! :) Another symptom was that Ubuntu took ages to load.

---

