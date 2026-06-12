---
title: "Installation Failure - Attempting to Dual boot with Windows 7"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by TruthDose on 2010-11-16
Hi, I have been trying to install ubuntu 10.10 and older versions alike in every way that I can on my Toshiba Satellite c655d. I have burned numerous discs from several mirrors and even tried using WuBi.

Everything seems to be fine but I am getting this screen any time I try to do anything with ubuntu -  

[http://img339.imageshack.us/img339/3356/20101116161033.jpg](http://img339.imageshack.us/img339/3356/20101116161033.jpg)

---

### Post by TruthDose on 2010-11-16
Partition - [http://img691.imageshack.us/img691/3278/capturedlr.png](http://img691.imageshack.us/img691/3278/capturedlr.png)

---

### Post by TruthDose on 2010-11-17
:bump:

---

### Post by wilee-nilee on 2010-11-17
Ubuntu will not install to any other then a ext type partition, generally ext4 is used. Your screen shot of text means nothing. Wubi is different though.

If you want a dual boot shrink the W7 partition=C with the W7 partitioner, leaving a open space for Ubuntu, and use the install in free space option if it is on the install Ubuntu cd. Make sure after shrinking W7 reboot it before installing Ubuntu to make sure it is okay

So you have 3 primary partitions already, but the good news is that Ubuntu is usually installed inside a extended partition which allows a unlimited amount of other partitions inside that you can fit. Generally though Windows will not boot from a extended, although I have seen people do it.

Ask more questions if needed, and make sure you are burning the ISO image not as a data burn and check the Md5sum of the ISO and or the cd.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Verbeck on 2010-11-17
could you check the md5sum of the iso you downloaded

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)
and compare it to 
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

see if it matches

---

