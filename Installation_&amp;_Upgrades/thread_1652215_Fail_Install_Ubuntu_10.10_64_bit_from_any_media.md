---
title: "Fail Install Ubuntu 10.10 64 bit from any media"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by varooneh on 2010-12-24
Hi all , i downloaded ubuntu 10.10 64 bit from ubuntu.com web site and write it on cd for install it on my laptop when i want install ubuntu i get error in installation during . this error :

> 
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a  faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD  at a lower speed, to clean the CD/DVD drive lens (cleaning kits are  often available from electronics suppliers), to check whether the hard  disk is old and in need of replacement, or to move the system to a  cooler environment.                      
when get this error i create bootable usb flash with Universal USB Installer and boot my laptop from flash but when i want install from flash i get this error again , i tried very very tried for this error , i write more cd and test it but i've this problem again , please help me :cry: .

my laptop Informaion :
dell studio 1558
cpu : intel core i7
ram : 4gig ddr33 1333
hard: 500 gig 7200 rpm

---

### Post by dino99 on 2010-12-24
when burning, always do it the slowest possible


depend on your hardware sometimes you need to add either: noacpi, nomodeset ( F6 if i remember) when booting

---

### Post by varooneh on 2010-12-24
> **dino99 said:**
> when burning, always do it the slowest possible


depend on your hardware sometimes you need to add either: noacpi, nomodeset ( F6 if i remember) when booting


i write ubuntu iso with 10x and 8x speed but i h've this problem :(

---

### Post by varooneh on 2010-12-25
Help me!

---

### Post by Quackers on 2010-12-25
Have you checked the MD5SUM of the downloaded iso to make sure the download is good?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

