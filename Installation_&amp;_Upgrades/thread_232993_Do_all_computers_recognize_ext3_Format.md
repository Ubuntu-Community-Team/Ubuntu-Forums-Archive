---
title: "Do all computers recognize ext3 Format????"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by joople on 2006-08-09
Hi all again.  Sorry for my threads no one seems to know how to fix DISK BOOT FAILURE... So I'm here now posting threads with different questions other than that to get to the bottom of this.  

I have a hard drive with 20gigs and I'm been trying to install UBUNTU on it for the past 5 days or so.  Trust me when I say everything is configured right.  I've done it all.  This hard drive had Windows XP on it at first so I tried to dual boot with UBUUNTU, but that didn't work GRUB would give an ERROR 25 message (which is a DISK READ FAILURE) So I fixed the MBR for Windows XP and accessed Windows.  So I decided to Wipe out Windows XP all together and just install UBUNTU. Everything installed perfectly.  But when I take out the CD and repoot as it says. nothing loads and I get a "DISK BOOT FAILURE..." So recap Windows Xp works, but UBUNTU doesn't.

So my only thought is... is it possible that certain computers, or Mobo's don't recognize ext3 Formats???

---

### Post by joople on 2006-08-09
Oh by the way I have the latest updates for my Award BIOS.

---

### Post by donkey42 on 2006-08-09
hi, ext3 is a partition format, that is not supported by XP, back to your problem, i think, you are trying to boot from CD (which is not possible, unless you have inserted a bootable CD inserted, enter the BIOS and verify the boot order is set to primary master HDD or HD0

---

### Post by joople on 2006-08-09
thanks donkey, but no that doesn't mean it's trying to boot from cd it means that it is not detecting the system on the hard drive I am pretty computer savvy and the boot order is fine believe me. Remember in my first post I verified already that the hard disk and everything is fine because I had windows XP on it before.

Unless you are trying to say that GRUB for what ever reason is telling the system to boot from CD,  but that is not the case because even wen I put the CD in and try to boot form first hard disk I still get the error DISK BOOT FAILURE...

Someone PLEASE tell me why UBuntu will not load.  SOMEone on the UBUNTU TEAM PLEASE you have to know what's up with this. Ubuntu will not will not will not load, Damn this is so frustrating !@#$ !@#$ !@#$ !@#$!!!!

---

