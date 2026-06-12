---
title: "Flash Dive INstall Fails"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by BigYellowDog on 2010-12-14
I'm trying to install Ubuntu Server 10.10 from a flash drive and I keep getting the same failure message.  fs-secondary-module-2.6.35-22-generic can not be read.  I used Universal-USB-Installer on two different USB drives, one brand new.  I also downloaded the ISO twice.

---

### Post by cipherboy_loc on 2010-12-14
Check the MD5 sum. The sums are listed here ([https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)). Use a utility to hash the iso image, copy it, and run a find on the web page for that sum.


Cipherboy

---

### Post by BigYellowDog on 2010-12-15
Yes hashes match.  I'm able to copy the file off the flash drive also.

---

### Post by BigYellowDog on 2010-12-15
I downloaded server 10.04 LTS, but I kept getting "no common CD-ROM found"  It didn't seem to matter if I booted from a USB drive or a USB CD-ROM.  Then I found these [instructions]("http://www.revouser.com/forum/viewtopic.php?f=7&t=794") now which worked great.  Now I have Ubuntu server running :D

---

