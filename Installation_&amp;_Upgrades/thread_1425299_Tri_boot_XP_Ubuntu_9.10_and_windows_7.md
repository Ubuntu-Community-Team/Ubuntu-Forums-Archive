---
title: "Tri boot XP Ubuntu 9.10 and windows 7"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by shahzadah on 2010-03-08
HI, Im using windows xp and ubuntu 9.10 installed on my pc. I had installed xp first and then i did intalled ubuntu 9.10. both I use to select from the grub menu in start and working fine.. Now... I want to Install Windows 7 alongwith XP and Ubuntu 9.10. i just want that in grub menu i have three options to select. xp, ubuntu and 7... so i can enjoy three of it. and i also want to install windows 7 without disturbing windows xp and ubuntu... please help me with this regard.

---

### Post by johnson.d on 2010-03-09
You can look into a similar thread which may be of help:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Mark Phelps on 2010-03-09
> **shahzadah said:**
> ... Now... I want to Install Windows 7 alongwith XP and Ubuntu 9.10. i just want that in grub menu i have three options to select. xp, ubuntu and 7... so i can enjoy three of it.
Doesn't work that way.  When you install Win7, MS Windows will detect that you already have XP and will (1) install the boot loader files into the XP partition, and (2) create menu entries for Win7 and "Earlier version of Windows" (XP).  When you then boot using GRUB, you will only have two choices -- Ubuntu and Windows.  You will not be able to bypass the MS Windows OS selection menu.

>  and i also want to install windows 7 without disturbing windows xp and ubuntu...

Also ... doesn't work that way.  Win7 will install the boot loader files to the XP partition, so in that way, it will "disturb XP".

Also, since it will replace the MBR in the process, you will have to reinstall GRUB to be able to boot back into Ubuntu.  So, in this way, it will "disturb Ubuntu".

---

### Post by shahzadah on 2010-03-10
its okay if its only "disturb" the grub of ubuntu and mbr of windows xp. not the files or any other settings or etc... but.... as you told 'Mark phelps' that it will have two options after installing windows 7 over windows xp and ubuntu 9.10. 

1. windows
2. ubuntu

Some thing like that ? ? ? rite ?

and when i will select windows i will further have two options

1. windows 7
2. windows xp

is that rite ? ? ?

so i can run any operating system as i like selected in start like this ? ? ? and is it problem free ? ? any one have tried installing windows 7 over windows xp and ubuntu 9.10 ? ?

if its ok then it is fine.... please tell me that should i go for installing windows 7 over windows xp and ubuntu.. if its problem free and don't crash my PC..

---

### Post by Mark Phelps on 2010-03-10
> **shahzadah said:**
> its okay if its only "disturb" the grub of ubuntu and mbr of windows xp. not the files or any other settings or etc... but.... as you told 'Mark phelps' that it will have two options after installing windows 7 over windows xp and ubuntu 9.10. 

1. windows
2. ubuntu

Some thing like that ? ? ? rite ?

The actual GRUB menu will have additional choices, including one for each kernel configured in Ubuntu, but you will only have ONE MS Windows choice.  GRUB is not able to provide individual choices for different MS Windows installs when they have their boot loader files in the same partition.
> 
and when i will select windows i will further have two options

1. windows 7
2. windows xp

is that rite ? ? ?
Actually, it will probably say something like "Earlier version of Microsoft Windows" instead of "Windows XP" -- why it can't simply list XP is a mystery.

> so i can run any operating system as i like selected in start like this ? ? ? and is it problem free ? ? 
It will launch the OS you select.  What happens after that has nothing to do with GRUB.

> any one have tried installing windows 7 over windows xp and ubuntu 9.10 ? ?
Your terms are unclear ...

If by "over" you mean replacing XP with Win7, you will then no longer have access to XP because MS does not support actually upgrading to Win7 "in-place", meaning, it will REPLACE XP with Win7.

If you mean "adding" Win7 to an existing installation and leaving XP intact, that will require creating a new NTFS partition for Win7 (or creating unallocated space in which to create that partition) and will result in the menu scheme mentioned above.  IT will not disturb your XP install (other than Win7 boot loader files being added), will leave those files intact, and will still allow you to boot into XP.

> if its problem free and don't crash my PC..
No one can tell you that... MS provides a utility you can download from their site and run on your XP install to determine POSSIBLE conflicts in Win7.  And, while Win7 does allow the use of SOME XP-era drivers, and will run SOME XP-written applications just fine, the actual results are on a one-by-one basis.

Although there's no LiveCD mode for Win7, you can "borrow" a Win7 DVD from a friend, install it on your machine -- and if you do NOT enter a product key, you will have 30 days to use it before it requires activation.  That's really the ONLY way to determine how well it will work on a particular machine.

---

