---
title: "Lubuntu CD Won't boot"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by Stevensthunar on 2013-10-22
So i decided to give lubuntu 13.10 a try.I downloaded the ISO from the website, written it to a CD-RW, rebooted.
But the CD didn't boot.It booted to the existing OS instead(ubuntu 12.10).So what can i do?

---

### Post by Bashing-om on 2013-10-22
Stevensthunar; Hi !

Sounds like you do not have a bootable CD .. or not setting the boot priority in bios to the CD.
check:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

to insure there are no defects in that medium.
[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Stevensthunar on 2013-10-22
md5sum is the same. Boot prior is 1.CDROM 2. Hard Disk

---

### Post by erasmusp on 2013-10-22
Could perhaps double check if that CD boots on another PC/laptop?

---

### Post by Bashing-om on 2013-10-22
Stevensthunar;
In addition to erasmusp's contribution:
Check the disk integrity:
Boot the liveCD, as soon as the bios screen clears depress and hold the left shift key  -> language screen, escape key to accept the default -> boot options screen -> check disk for defects.

[INDENT][INDENT]where there are solutions there are no problems 
[/INDENT][/INDENT]

---

### Post by Stevensthunar on 2013-10-22
Hey! I found out i just had a burning problem.I reburned and it boots perfectly. Thanks for help!

---

### Post by Lars Noodén on 2013-10-22
Some of them are oversized and won't fit on a CD, but that applies only to the PowerPC images and the Desktop AMD64 image.  Do you have one of those or something else?

---

