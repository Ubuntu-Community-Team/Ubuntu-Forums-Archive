---
title: "Errno 30] Read only filesystem"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by anadeem.ch on 2011-03-11
I am installing Ubuntu 9.04 Desktop on my system. using entire disk. my disk is new one. first time i installed ubuntu on it successfully, used it and installed new kernel and some upgrades. all were successful.but on installing some drivers, its files system corrupted. so I had the need to re-install the OS again.
NOW , when i am installing the OS , it gives error "(Errno 30] Read only filesystem" explaining that either CD/DVD is corrupt or HDD is corrupt. temperature of the environment may be high. I changed the system , ehanged the environment, moved to some cool place, changed CD drive and CD (after making new one from ISO), changed the HDD but all useless, error is there,  while installation is in progress my sda1 is mount on /target. when i see fstab, here in the line of /dev/sda1 ,error=remount-ro is observed.
sometime installation gives error no 5 sometimes it gives error no 30 but both the errors convey almost same message explaining that either HDD is corrupt or CD . As i have explained that I changed every thing including HDD and CD but the error is same. please help me to get rid of this error
A.Nadeem

---

### Post by Hippytaff on 2011-03-11
Did you use a different iso with the new CD? the iso might be corrupt. Try [Md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by anadeem.ch on 2011-03-11
yes I used different iso's. after checking its hash. few days ago when i was installing from previous iso, it installed successfully. but now from this iso too, the process is unsuccessful. and I cannot do it successfully from newly downloaded iso.

---

### Post by Hippytaff on 2011-03-11
Have you tried a different distro? not that it should make any difference, but it's worth trying just as a process of elimination.
 
Have you tried booting from liveCD and reformattingthe HDD (Providing you have nothing you want to save)

---

### Post by ajgreeny on 2011-03-11
9.04 is not supported any more.  Why did you choose that version?  I would suggest 10.04 which is a LTS version with 3 years support on desktop.

---

### Post by Hippytaff on 2011-03-11
> I am installing Ubuntu 9.04 Desktop on my system
 
You know I completely didn't read that.
 
+1 try 10.04

---

