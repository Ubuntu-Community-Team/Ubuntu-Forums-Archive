---
title: "can't find iso on usb drive"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by asolarian on 2012-12-05
Hi All:

I prepared a bootable USB drive using syslinux, have put in the vmlinuz, initrd.gz, and syslinux.cfg files with the proper commands and am able to boot into the graphical installation interface. However, find-iso can't find the iso file that I have on the USB drive. I can see the file if I go into the console with alt-F2. I was under the impression that a simple cp operation was sufficient to put the iso file on the USB drive. Is this incorrect?

Thanks!

---

### Post by asolarian on 2012-12-05
I was wrong about what the problem is. The .iso is found, mounted in /cd-rom but there is a problem loading components. I found a post elsewhere on the internet that some files in /pool/main/l/linux were misnamed, but I don't have a linux folder there, only a lupin folder. I have checked the Md5.

Any ideas?

---

### Post by Abhinav Kumar on 2012-12-05
Hi asolarian,

What are you trying to do? You can also prepare a bootable pendrive using Unetbootin.

Regards,
Abhinav

---

### Post by asolarian on 2012-12-05
I'd like to install Ubuntu on a hard drive using a USB drive since I don't have a cd-rom drive.

---

### Post by Abhinav Kumar on 2012-12-05
You can use universal usb installer to prepare a bootable linux pendrive from Windows.
For preparing bootable linux pendrive from linux platform, you can use unetbootin.

Abhinav

---

