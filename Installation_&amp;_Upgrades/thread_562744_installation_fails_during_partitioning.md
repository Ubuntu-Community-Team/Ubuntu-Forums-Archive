---
title: "installation fails during partitioning"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by WEPrechaun on 2007-09-29
motherboard: MSI K8N Neo V2.0 H socket 754 ATX 
cpu: AMD Sempron 3400+
chipset: VIA
hd1: WDC WD300BB (master) resides in mobile rack
hd2: WDC WD800JB (slave)  resides in mobile rack
OS: Ubuntu 7.04 i386 live or alt
      Ubuntu 7.04 64bit AMD live or alt

problem: Installation seizes during hard drive partitioning. 

What must I do in order to successfully install Ubuntu? Should I be using the 32 or 64 bit version? 

Ubuntu was successfully installed on an older computer with a socket A mb, AMD Athlon T-bird cpu, exact same hd, & video card. Upon the live cd installation, a crash report appears then I see the error message, "a gnome panel has closed unexpectedly." The AMD64 alternate disc doesn't do anything after text installtion is selected. I also noticed that if I go into Places -> Computer, then I see 2 hard drives with almost equal capacities even though 1 hd is 30Gb & the other is 80Gb. Neither hd is mounted. Jumpers are correctly placed. Installation also failed while using 1 hd w/o a jumper so it's a single drive environment. 

Any assistance would be appreciated. Thank you.

---

### Post by overdrank on 2007-09-30
> **WEPrechaun said:**
> motherboard: MSI K8N Neo V2.0 H socket 754 ATX 
cpu: AMD Sempron 3400+
chipset: VIA
hd1: WDC WD300BB (master) resides in mobile rack
hd2: WDC WD800JB (slave)  resides in mobile rack
OS: Ubuntu 7.04 i386 live or alt
      Ubuntu 7.04 64bit AMD live or alt

problem: Installation seizes during hard drive partitioning. 

What must I do in order to successfully install Ubuntu? Should I be using the 32 or 64 bit version? 

Ubuntu was successfully installed on an older computer with a socket A mb, AMD Athlon T-bird cpu, exact same hd, & video card. Upon the live cd installation, a crash report appears then I see the error message, "a gnome panel has closed unexpectedly." The AMD64 alternate disc doesn't do anything after text installtion is selected. I also noticed that if I go into Places -> Computer, then I see 2 hard drives with almost equal capacities even though 1 hd is 30Gb & the other is 80Gb. Neither hd is mounted. Jumpers are correctly placed. Installation also failed while using 1 hd w/o a jumper so it's a single drive environment. 

Any assistance would be appreciated. Thank you.

HI and welcome, you may try these links, how did you burn the cd, as slow as possible
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And you may checksum the disc
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Good luck and hope this helps!

---

### Post by WEPrechaun on 2007-09-30
Ok, I'll try those suggestions. The iso was burned @ 4x speed with DVD Decrypter then again with Nero. 

Also, I was wondering if anyone could assist me with my initial questions:

1. If I'm using a 64bit cpu, then would it be better to install the 32 or 64bit version of Ubuntu?

2. I'm trying to install Ubuntu while using removable hd trays, Ubuntu 7 live cd sees 2 hard drives,  & doesn't report the correct sizes. How could I correct this? If it's not seeing the hard drives correctly then wouldn't that contribute towards the inability to partition the target hard drive & install?

Sorry to be a pain but I'm anxious to play with Ubuntu.

---

### Post by Pumalite on 2007-09-30
I prefer 32 bit, but there are other opinions in the forum. As for partitioning: 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
(the stand alone, burn to CD, boot from, program)

---

### Post by WEPrechaun on 2007-10-02
Out of curiosity, I returned the hd, video card, & dvd-rom drive to it's original computer.
Ubuntu 7 32bit version live cd installed fine, but Ubuntu doesn't boot from the hd at all.
Why do I suspect that my hd is at fault?

---

### Post by Pumalite on 2007-10-03
Did you check your hard drive?. What was it?.

---

### Post by WEPrechaun on 2007-10-03
The hard drive is a WD300BB. Since the hd is alone, I tried installing Ubuntu with the hd jumper removed and in the cable select position. I can format it, create/remove partitions, formatted the master boot record, hd is detected in CMOS, but it stops booting at the initial Ubuntu screen. May I also add that this hd is pretty old. Quiet as a mouse & never abused.

---

### Post by Pumalite on 2007-10-03
Ge a rescuecd and check your drive: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
[http://www.sysresccd.org/Online-Manual-EN](http://www.sysresccd.org/Online-Manual-EN)
(if you think that the problem lies with your drive)

---

