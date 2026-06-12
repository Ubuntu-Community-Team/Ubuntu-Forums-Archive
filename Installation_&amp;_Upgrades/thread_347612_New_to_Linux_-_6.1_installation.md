---
title: "New to Linux - 6.1 installation"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by vodkasoda on 2007-01-27
Hi all,

As in the title, which should say 6.10 (DOH !!!) I am brand new to Linux. I am experienced with Windows and Mainframes (though not Unix, unfortunately). 
Ubuntu was recommended to me by a friend and I have tried to do an install earlier today, but cancelled it before completing it, leading to this post ...

I have created a 20Gb partition, formatted as Fat32. I did this after googling last week & it seemed the best option ... firstly, am I correct or is NTFS a better option ?

Secondly, when I run the Install, I get to step 6 and it insinuates that I need different partitions on different disks (I currently have a WinXP machine with 4 HDs, partitioned for numerous reasons) ... is this right or can I just point everything at this same 20Gb partition ?!?!

Any help appreciated ...

Gaz

---

### Post by bward1 on 2007-01-27
For your linux install you really wanna have either ext3 or reiserfs for your root partition.  It is also advisable to create a small, seperate, /boot/ partion that is ext2.  In windows you may know about the page file which is basically like hard drive ram, in linux this is known as swap space and it too needs to be it's own partion.  Linux can read and write to FAT32 you really dont want to put your linux install there, just files that you want both windows and linux to be able to use.  I suspect that this is your problem, but others with more experience may be able to provide more insight.  Good luck, and have fun learning linux!

---

### Post by vodkasoda on 2007-01-27
> **bward1 said:**
> For your linux install you really wanna have either ext3 or reiserfs for your root partition.  It is also advisable to create a small, seperate, /boot/ partion that is ext2.  In windows you may know about the page file which is basically like hard drive ram, in linux this is known as swap space and it too needs to be it's own partion.  Linux can read and write to FAT32 you really dont want to put your linux install there, just files that you want both windows and linux to be able to use.  I suspect that this is your problem, but others with more experience may be able to provide more insight.  Good luck, and have fun learning linux!

Thanks for getting back to me ... can I point the whole installation into this 20Gb partition & allow the installation to do the re-formatting it asks to do ?!?!? I'm obviously a bit wary of it re-formatting anything outside of this partition as I have movies, pictures, MP3s, Windows & programs out there ... and the way that Linux reports the partitions back to me is totally alien !!!

---

### Post by az on 2007-01-27
Just boot the installer and pick manula partitioning when you reach that step.  Delete the partition you made for Ubuntu.   That will just make FREE SPACE.  Go backwards in the install process and you will be offered to use that free space to install ubuntu.  Pick that and the installer will do all the partitioning for you.  It will create a root and a swap partition for you.

You only need those two partitions.

---

### Post by vodkasoda on 2007-01-27
[-o< > **azz said:**
> Just boot the installer and pick manula partitioning when you reach that step.  Delete the partition you made for Ubuntu.   That will just make FREE SPACE.  Go backwards in the install process and you will be offered to use that free space to install ubuntu.  Pick that and the installer will do all the partitioning for you.  It will create a root and a swap partition for you.

You only need those two partitions.

Sounds good, I'll give it a go ... but I'm scared [-o< !!!!!!!!!

LOL ... I'm more scared of the wife, really !!!

Gaz

---

### Post by az on 2007-01-27
> **vodkasoda said:**
> [-o< 

Sounds good, I'll give it a go ... but I'm scared [-o< !!!!!!!!!

LOL ... I'm more scared of the wife, really !!!

Gaz

My wife only uses Ubuntu.

And anyway, the partitionner will balk before it does something risky.  Nevertheless, back up your important data....

---

