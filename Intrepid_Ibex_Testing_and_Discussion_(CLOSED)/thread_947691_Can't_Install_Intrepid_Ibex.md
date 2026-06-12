---
title: "Can't Install Intrepid Ibex"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Maya-PSK on 2008-10-14
Hi to all , I'm trying to install Intrepid Ibex Beta from live cd , but when I'm configuring the partition table , the install process crash! 
Should I use alternate? 

Thanks

P.S: Sorry for my English :)

---

### Post by overdrank on 2008-10-14
Hi and welcome, intrepid is still in the testing stage 
Moved to  Intrepid Ibex Testing and Discussion :)

---

### Post by dabl on 2008-10-14
> **Maya-PSK said:**
> 

when I'm configuring the partition table , the install process crash! 



That's pretty clear English! 

Here's my recommended process -- it's guaranteed!  :)

1. Use a GParted Live CD to do your partitioning, before you try to install Linux.  Get the ISO [[COLOR="SeaGreen"]**here**[/COLOR]](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

-- Give *buntu 6GB, formatted ext3  (this allows some space for growth)

-- This is for the OS itself -- user data is in addition to this, if not on separate partition(s)

-- Notwithstanding rumors to the contrary, Linux still likes a swap space, whether it is "needed" or not -- at least 500MB -- and if you hope to suspend to RAM, then it needs to be at least as large as your installed memory

-- Doesn't matter whether you format the *buntu partitions or not, using GParted -- the *buntu installer offers formatting during installation

2. Then boot your *buntu Live or Alternate Install CD, and all you have to do is choose the partition(s) on which to install.

:)


p.s.  Burn those bootable CDs at 4X speed, and DAO mode, if you have it.  A defect on the installation CD might cause it to crash, too.

---

### Post by Maya-PSK on 2008-10-14
[quote="dabl"]That's pretty clear English! [/quote]

Thank You! :D

[quote="dabl"]
Here's my recommended process -- it's guaranteed!

1. Use a GParted Live CD to do your partitioning, before you try to install Linux. Get the ISO here

-- Give *buntu 6GB, formatted ext3 (this allows some space for growth)

-- This is for the OS itself -- user data is in addition to this, if not on separate partition(s)

-- Notwithstanding rumors to the contrary, Linux still likes a swap space, whether it is "needed" or not -- at least 500MB -- and if you hope to suspend to RAM, then it needs to be at least as large as your installed memory

-- Doesn't matter whether you format the *buntu partitions or not, using GParted -- the *buntu installer offers formatting during installation

2. Then boot your *buntu Live or Alternate Install CD, and all you have to do is choose the partition(s) on which to install.




p.s. Burn those bootable CDs at 4X speed, and DAO mode, if you have it. A defect on the installation CD might cause it to crash, too.
[/quote]

Well , thank you for your answer and your support. 
I think that using this guide I'll be an Intrepid Ibex user so early and maybe I'll left Hardy. :D

---

### Post by nanog on 2008-10-14
You should file a bug on the installer. 

When I have a problem with a beta install...I have been known to install stable and just upgrade. This is how I installed hardy on a couple of dell servers -- 6.06.2 -> 8.04. (known kernel bug.)

---

