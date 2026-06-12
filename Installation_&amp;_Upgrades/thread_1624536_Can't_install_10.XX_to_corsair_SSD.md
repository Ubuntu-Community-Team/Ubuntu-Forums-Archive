---
title: "Can't install 10.XX to corsair SSD"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by Robert Pallister on 2010-11-17
Hey, I will start this like everyone else seems to do. I am new to linux.

I am trying create a dual boot of Ubuntu and Windows 7 on my new 60 gig Corsair SSD drive. Windows 7 installs without a problem but when I try to install Ubuntu Desktop 10.10 it will not detect my SSD drive during the installer or when I start Ubuntu off the CD/USB. So I downloaded 10.04 and it will see the SSD drive but once it start copying files it gives me this error: " [Errno 30] Read-only file system: '/target/bin'." I have tried may different downloads of 10.10 and 10.04 along with many different burned disks burned at the slowest speeds. I have tried it many times off different flash drives with different downloaded isos.

I did MD5 test my iso and it was fine, I burned the disk at 8x using OSX 10.6 disk utility, and checked the CD before pressing install and came back with no errors.

I ran a check on my RAM and it passed with no errors.

I tired the alternate ubuntu 10.4.1 installer, hangs when installing the base system at 17% when extracting libacl1... Then I get the error "The debootstrap program exited with an error (return value 1). Check /var/log/syslog or see virtual console 4 for the details." This CD was burned at 8x, MD5 is okay, and CD had no errors.

Windows 7 was able to see my SSD and fully install to it.

My system is a custom built and here are it's specs
AsRock mobo (I had an ASUS but it fried so instead of buying a good mobo I got a temp till I can upgrade)
AMD 5200+ AM2
2 gigs Corsair XMS ram DDR2
BFG Nvidia 8800 GTS 6XX of memory (I cannot remember off the top of my head)
ASUS sata DVD burner
Corsair Force Series 60GB SSD
Thermaltake Toughpower XT 775W

---

### Post by Robert Pallister on 2010-11-18
Alright, I was able to get Ubuntu 9.04 to install so I am just doing the Distribution Upgrades.

---

