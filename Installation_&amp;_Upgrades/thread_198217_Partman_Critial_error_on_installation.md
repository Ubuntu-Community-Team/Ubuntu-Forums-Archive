---
title: "Partman Critial error on installation"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by kwilliams0 on 2006-06-16
Hello,

I tried to install ubuntu using both the server and the desktop CDs, but both fail when trying to load the partition wizard.  I added the Debug line on the kernel load line and the last line before the install hung was: GET partman_auto/disk.  

I then looked into the partman log file and saw the following:

parterd_server: Read command: PARTITIONS
parted_server: The device ubuntu is not opened.
parted_server: Line 1188.  CRITICAL ERROR!!!  EXITING.

I believe Partman is the root issue here.  Does anyone know what is causing this, and how to resolve it?

Thanks in advance!

---

