---
title: "TRIPLE: XP, VISTA (already loaded) now UBUNTU 7.10"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by dvsj on 2007-11-22
Hello all, I am just a beginner with Ubuntu.. I would like to install Ubuntu 7.10 in a triple boot where XP and VISTA is already installed on a partitioned hdrive. 

1) XP Sp2 (250 GIG)
2) Vista (200 GIG)

3) EXT3 - (30 GIG)
4) LINUX SWAP - (1 GIG)

when I installed UBUNTU 7.10 and reboot I get the Windows boot screen but did not show the option for Ubuntu...PLUS. I lost my access to boot on VISTA - I've read some of the threads in here but it didn't apply to the problem I have. What is the most simplified way to fix my issue?

---

### Post by Pumalite on 2007-11-22
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://partedmagic.com/](http://partedmagic.com/)
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by dvsj on 2007-11-24
Pumalite, thanks for the infos...I will read up on it and will try...

---

### Post by Pumalite on 2007-11-24
You are welcome. Good luck. You cannot fail. You have everything you need to win.

---

### Post by dvsj on 2007-11-25
Pumalite, I installed UBUNTU according to the instructions...my reserved EXT3 and SWAP was setup and but when I booted my machine UBUNTU is not part of the boot menu...anything I missed? This is a Triple boot... I have XP, VISTA, and want to run UBUNTU to run on a 2 gig SWAP w/ 30 gig on EXT3....

---

### Post by Pumalite on 2007-11-25
Get Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Boot from it and at the Terminal, post:
sudo fdisk -lu
cat /boot/grub/menu.lst (from the partition that contains 'boot')

---

### Post by dvsj on 2007-11-26
Pumalite, when I display my partitions it shows the 'boot' on windows xp...is that where I run the commands?

---

### Post by Pumalite on 2007-11-26
No. You have to look for a linux   partition and find the folder 'boot'.

---

