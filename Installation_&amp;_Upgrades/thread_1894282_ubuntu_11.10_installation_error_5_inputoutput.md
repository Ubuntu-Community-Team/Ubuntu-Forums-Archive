---
title: "ubuntu 11.10 installation error 5 input/output"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by chetancx on 2011-12-12
I'm trying to install Ubuntu 11.10. i am getting the following error:
This particular error is often due to a faulty CD/DVD disk or drive, or a  faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD  at a lower speed, to clean the CD/DVD drive lens (cleaning kits are  often available from electronics suppliers), to check whether the hard  disk is old and in need of replacement, or to move the system to a  cooler environment.

i have only one RAM so i can't remove it also my RAM and hard disks are working properly.:(:(

---

### Post by BC59 on 2011-12-12
Do you have Windows installed to the computer? You could check the hard drive for faults. If not try to boot with the Ubuntu CD and choose try and not install. Then from Disk Utility--your hard drive--Smart Data--Run self check.
Post the results.

---

### Post by chetancx on 2011-12-12
> **BC59 said:**
> Do you have Windows installed to the computer? You could check the hard drive for faults. If not try to boot with the Ubuntu CD and choose try and not install. Then from Disk Utility--your hard drive--Smart Data--Run self check.
Post the results.
i used short self check from ubuntu (try from usb) it showed 1 bad sector
what to do now??  i have attached the screenshot.

---

### Post by BC59 on 2011-12-12
The best way is to format the drive. From the same CD boot and try. Then choose the application GParted. From there choose to format the drive, better to ext4 file system. Then from the icon on the desktop, choose to install Ubuntu.
The problem is that your HDD has bad sectors and this means, you can use it a little more, but don't trust it, because sometime in the future you could loose data.

---

