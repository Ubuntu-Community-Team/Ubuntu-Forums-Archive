---
title: "UBUNTU instalation problem"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by arturs111 on 2008-06-21
when i installed ubuntu 8.04, after loading screen appear
check root=bootary cat /proc /cmdline
or missing modules,devices: cat/proc/modules1s/dev
ALERT! /dev/disk/by-uuid( by-uuid don`t know it`s  writes like that:))/ 8aca5coa-db48-4f8d-8546-8071d979008e does not exist Dropping to a shale :(

p.s maybe some writing  mistakes

what i shall do? :confused:

---

### Post by avtolle on 2008-06-21
Assuming that if you downloaded the iso yourself and burned the CD therefrom yourself after checking the md5sum of the iso before burning, and after burning at a low speed (4x works for me) you checked the integrity of the CD for errors before booting, there are some other things you might try. When booting, hit F6, and at the end of the boot line, add "all-generic-ide" (without the quotation marks) at the end of the line, select b for boot, and see if it can boot and install. There is a plethora of boot line parameters to pass to try to resolve this, but let's try that one first, after checking the md5sum of the iso and the cd integrity, of course.

EDIT: [https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/) may be helpful to you as well.

---

### Post by arturs111 on 2008-06-21
sorry im newbie at linux ,1st instal, can you explain how to check it .

---

### Post by avtolle on 2008-06-21
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) on how to check md5sum (along with a link to the correct ones).

EDIT: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) on how to check the CD integrity.

---

### Post by arturs111 on 2008-06-21
cheked it match, and its no error found .. so what next?

---

### Post by avtolle on 2008-06-21
Restarting the system with the CD in the drive, press F6 at the start screen, which should give you a new screen; at the bottom of which will be a boot string. Add "all-generic-ide" (w/o the quotation marks) at the end of that line, then select b for boot, and see if it boots without the error message.

---

### Post by arturs111 on 2008-06-21
again apear busybox it wont start!!

---

### Post by arturs111 on 2008-06-22
bump

---

