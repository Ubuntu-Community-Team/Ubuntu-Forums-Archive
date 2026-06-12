---
title: "Help creating partitions for Ubuntu dual boot with Windows 7"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by Remember2Wipe on 2013-11-30
Hello there. Never dual booted before or partitioned my hard drive. 
I've just finished shrinking my C: drive and kind of guestimated how much space. If it's too big or small I could just change it. I have one guy saying 40GB minimum and another saying 5GB.

Anyways, do I just leave that space unallocated or what? I doubt I format it to NTFS or Fat32 because I'm not installing any Windows products on there. Is this correct?

Sorry about dumb thread. Just would prefer not to royally screw this up.

---

### Post by mikewhatever on 2013-11-30
Yep, just leave it like that, close GParted, and start the installer. Do not resize anything again, but look for the option to install in the unallocated space.

The official minimum is indeed 5GB, as the installer won't proceed with less space.

---

### Post by Mark Phelps on 2013-11-30
If it's not too late, BEFORE you install Ubuntu, do yourself a favor and use the Backup feature in Win7 to create a burn a Win7 Repair CD.  This will provide you the means to repair the Win7 boot loader -- should something go wrong during the dual-boot install.

---

### Post by Remember2Wipe on 2013-11-30
Already did it yesterday :cool:

Installing later tonight

---

### Post by fantab on 2013-11-30
You can give yourself more space... This depends on how you are going to use Ubuntu. If you will use it more than ther other OS then give your self more room, if you only want to try Ubuntu ocassionally then 35-40GB should be minimum. Ubuntu default install will be around 10Gb or less... in the remaining space you will be saving your data. Linux can read and write to NTFS Windows Partition, so you can share the NTFS Partition between the two OS....

Its better to give ubuntu more room than what you have allocated.

---

