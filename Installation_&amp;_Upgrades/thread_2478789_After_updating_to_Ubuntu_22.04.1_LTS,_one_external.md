---
title: "After updating to Ubuntu 22.04.1 LTS, one external drive won't mount"
date: 2022-09-05
forum: Installation &amp; Upgrades
---

### Post by mwilliams1220 on 2022-09-05
[COLOR=#232629][FONT=-apple-system]####SOLVED#####SOLVED#####

After updating to Ubuntu 22.04.1 this morning, one of my external hardrives won't mount. WHen i switcherd to Windows 10, it mouted fine, checked the cables, etc. and everything looked good. Disks sees it (10 TB Hard Disk /dev/sdb) but throws this error message when I try to mount it from there: "Error mounting system-managed device /dev/sdb1:unknown error when mounting /mnt/2021_09_Elements (udisks-error-quark,0).[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The disk is backed up (I replace drives every three years, keep the older one for back up), but I am hesitant to try the Check/Repair Filesystem options without some guidance.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Also, this disk contains media files for my Plex server.[/FONT][/COLOR]

---

### Post by ActionParsnip on 2022-09-05
What file system are you using on the troublesome drive, please?

---

### Post by mwilliams1220 on 2022-09-05
This issue was my hostname was not in /etc/hosts.  Once I fixed that, the drive mounted on logon.

---

### Post by mIk3_08 on 2022-09-06
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

