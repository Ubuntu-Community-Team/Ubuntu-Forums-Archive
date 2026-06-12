---
title: "no obtion to install windows 7 alongside ubuntu"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by proggy on 2011-10-31
Hello,
I booted Ubuntu 11.10 cd tonight so i could install it on a laptop with Windows 7 ,
when  the installer opens it doesnt give me the choice of installing it alongside Windows but only gives me the choice of wiping widows or create partions which i`m not really comfy with and would`ve prefered seeing my windows partion in graphical mode and just moving the bar like previous installs.
i`ve seen screeshots of the installation process of ubntu 11.10 and it included the option of installing ubuntu alongside windows.
Anyone know why this option was not inculded in my copy?

---

### Post by Script Warlock on 2011-10-31
if you have no ubuntu installed i think it only displays 2 options. manual partitioning or that "something else" option also has a gui to guide you install ubuntu.

---

### Post by Quackers on 2011-10-31
How many primary partitions already exist on your hard drive?
Is there any unallocated space on the drive (outside of any partitions)?

---

### Post by proggy on 2011-10-31
It only has one primary partition and most likely a hidden second partition with a windows (recovery,reinstall).
I`m curious of where you are going with your questioning.

---

### Post by raja.genupula on 2011-10-31
Hi man 
      Honestly I dont know the answer for your issue.But i wanna give my suggestion to you that install the Ubuntu in its own partition . Better to choose manual and create a own partition for it.

---

### Post by Mark Phelps on 2011-10-31
> **proggy said:**
> It only has one primary partition and most likely a hidden second partition with a windows (recovery,reinstall).
I`m curious of where you are going with your questioning.

It's common for OEMs to install the maximum of four primary partitions onto a PC preloaded with Win7.  This makes the installing of Ubuntu, or any other OS, into a primary partition impossible -- without first removing one of the existing primary partitions.

IF you can get into Win7, then open Disk Management and look at the "drives" (what MS Windows calls Partitions) on your hard drive and count them.  If there are already four, that's the maximum allowed -- and the Ubuntu installer knows this and will NOT offer you the option to create more partitions.

---

