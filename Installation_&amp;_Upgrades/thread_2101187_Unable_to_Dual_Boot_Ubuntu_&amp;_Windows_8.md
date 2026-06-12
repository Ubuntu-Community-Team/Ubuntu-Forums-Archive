---
title: "Unable to Dual Boot Ubuntu &amp; Windows 8"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by ulzaron on 2013-01-04
Hi, I am having a problem dual booting Ubuntu onto my new windows 8 machine. It is a UEFI based machine with 128 GB SSD. 
I ran boot-repair as asked to but it did not work.
The following pastebins were generated:-

1. Ran once from "try ubuntu via bootable DVD"
-http://paste.ubuntu.com/1494446/

2. Ran twice from "try ubuntu via bootable DVD"
-http://paste.ubuntu.com/1494470/

Ubuntu is not able to detect windows 8, the computer boots straight to windows 8 upon installation of ubuntu. I know ubuntu has been successfully installed on a partition that I created for it via the installer.

Could anyone help me out? 

Thank you.

---

### Post by YannBuntu on 2013-01-04
> **ulzaron said:**
> the computer boots straight to windows 8 upon installation of ubuntu.

Please run Boot-Repair --> Advanced options --> tick "Backup and rename EFI files" --> Apply.
Indicate the new URL that will appear, then reboot the pc and tell us what you observe?

---

