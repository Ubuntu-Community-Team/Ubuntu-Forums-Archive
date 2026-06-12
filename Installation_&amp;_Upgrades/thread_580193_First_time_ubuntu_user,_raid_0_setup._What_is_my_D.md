---
title: "First time ubuntu user, raid 0 setup. What is my Dualboot Solution, XP+Ubuntu?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Masc0t on 2007-10-18
I am brand new to Linux and am currently on Live session.
I have 2x 320gb SATA II drives in Raid 0.

[IMG]http://i23.tinypic.com/2jacg9h.png[/IMG]
[IMG]http://i22.tinypic.com/10mu0b6.png[/IMG]

I choose manual because I obviously want to keep WinXP Pro.
From what I've read ubuntu doesn't use RAID properly.
Any help for me what to do next?

These are Seagate Barracuda 7200.10 drives.

**Update:**

I've also read something about ATI users and ubuntu. Just wanted to throw it out that I have an ATI X800 GT. Will I run into any problems?

---

### Post by mattpker on 2007-10-18
In order for this to work you need to install ubuntu before winxp. Here is a guide: 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Masc0t on 2007-10-18
> If Windows isn't already installed, install it first. If you leave space for Ubuntu at this step you don't have to resize your NTFS partition later.


Hmmm?

---

### Post by Masc0t on 2007-10-18
That guide doesn't appear to be for RAID 0

---

### Post by Masc0t on 2007-10-18
bump. 

I'm using the FakeRaid how to guide
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)


I'm sort of stuck at this step
[http://gentoo-wiki.com/HARDWARE_Dell_Precision_690#Repartition_RAID0_Storage_Array](http://gentoo-wiki.com/HARDWARE_Dell_Precision_690#Repartition_RAID0_Storage_Array)

Please help

---

### Post by pjman on 2007-10-18
FakeRAID is not fun to setup. It took me a couple of days but I finally got mine going. Here is the thread that helped me enormously:

Successful and "easy" install DUALBOOT FeistyFawn/XP with nvdia raid0 stripeset
[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

After following those instructions I ran into one problem, configuring GRUB. Here's my thread I created asking for help. Turns out it was a simple fix (boot flag needs to be set..:oops:).

[SOLVED] Dual-Boot setup using dmraid/fakeRAID - Having grub problems
[http://ubuntuforums.org/showthread.php?t=531754](http://ubuntuforums.org/showthread.php?t=531754)

I hope this helps you.

---

### Post by pjman on 2007-10-18
Also, after you get this setup, make sure you make a backup of your /boot/grub/menu.lst file. When there are kernel updates this file will not be updated correctly. At leasts that's what I've seen :(. You you will need to restore your menu.lst file and manually change the version number of the kernel in the file to the updated version. Very odd - I wish fakeraid was better supported. Someday I suppose.

---

