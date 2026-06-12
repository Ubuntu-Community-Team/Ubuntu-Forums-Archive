---
title: "partition trouble"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by prajul_maniath on 2009-11-16
i am running ubuntu 9.10.i have just one hard drive of 20 GB in which ubuntu is present.i want to dual boot it so i tried partitioning the primary drive but does not seem to be possible.can anyone tell me how i can proceed ?

---

### Post by TheHimself on 2009-11-16
You can't partition a drive which is mounted. You should boot the computer using the live CD and then use gparted to partition the drive. As I understand you have Ubuntu installed and you want to add a new OS. Right?

---

### Post by darkod on 2009-11-16
If you are doing it from within Ubuntu, it will not work because ubuntu is working from that drive. Boot the computer with ubuntu cd/usb stick and select the Try Ubuntu option. Then ubuntu is running from the cd/usb and you can use Gparted to change partitions on your hdd.

---

### Post by prajul_maniath on 2009-11-16
oh ok thanks......really helped a lot.....though i donno y i didnt figure out such the answer to such a noob question!!!!

---

### Post by prajul_maniath on 2009-11-17
hmmm this didnt work out.i tried to boot from the CD but the only option is install ubuntu.

---

### Post by oldfred on 2009-11-17
The usual download is the liveCD, you probably downloaded the text based installer.  You can download the liveCD or if you want a smaller download just download a gparted liveCD or parted magic liveCD as they are only about 100MB. I download them all as just in case. My older computer would not boot with some configurations but with others. I just checked, I also have supergrub, systemrecue & UBCD. 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by prajul_maniath on 2009-11-17
if i download this then i will not have a full live cd but then wat i need is  a  full live cd because i have to use the same live cd to reinstall grub after i install xp and want to dual boot linux and xp.so is there any way i can upgrade this text based installer(689 MB) to the live cd one(689 MB)???or is my only way to download the live cd version

---

### Post by dhavalbbhatt on 2009-11-17
> **prajul_maniath said:**
> if i download this then i will not have a full live cd but then wat i need is  a  full live cd because i have to use the same live cd to reinstall grub after i install xp and want to dual boot linux and xp.so is there any way i can upgrade this text based installer(689 MB) to the live cd one(689 MB)???or is my only way to download the live cd version

Your most recent post is a bit confusing - but if I am following you, then what you are asking is whether you can upgrade your text based installation CD to a live CD, or whether you have to download a new LiveCD - the answer to that question is, you will have to download a new liveCD, which is also called Desktop installation CD (it seems the one that you have right now is the "Alternate" installation CD, which is a text based installer and does not have a GUI, Desktop installation CD has a GUI). Once you have a Desktop installation CD, you should be able to use that to partition your disk as well as updage GRUB after you have loaded XP.

---

