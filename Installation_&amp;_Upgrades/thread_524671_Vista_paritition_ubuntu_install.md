---
title: "Vista paritition ubuntu install"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by auroramae on 2007-08-13
I had ubuntu and XP peacefully coexisting on my old computer.
I have a  new system and I can't seem to obtain the same bliss.

I've read the related threads as they came up and also searched online and  I am just dense.

I reserved a new  partition of 24g in Windows Vista Home premium

I can boot from the ubuntu CD and when I choose to install I get to the part where it is asking me for my user info and it seems like the next  step will be to overwrite the parititoin.

I panic and back out worrying that Windows will be toast.

I have gone into the administration area and the partitions  show as disks but no info is available for either disk so I can't tell which is which.

I also cannot see much info about most of the hardware on the system " unknown."

How do I determine the empty parition and get ubuntu to install there. 

I am a complete noob so please be kind if this a really stupid question.

The computer is a toshiba with AMD turion x64 duo core
I am trying to install 
Ubuntu Version 6.06 LTS 64 bit 

Should I use 7.04 instead?

Any advice would be greatly appreciated.

---

### Post by logos34 on 2007-08-13
Unless you really need the support option of dapper, I'd recommend you go with Fesity 7.04.  I'll likely do a better job recognizing your hardware.

But on the dapper cd you could try fdisk for paritition info:

sudo fdisk -l  (lowercase L)

or Gparted (menu bar>system>sdmin>Gnome partition editor)

the latter should give you a better pciture of your disk setup

---

### Post by auroramae on 2007-08-14
Thank you.  I will try the Fdisk in Dapper to determine which partition is which.

I downloaded Feisty and could not load it.  
Page after page of errors regarding the  HD among other things came up. Then it reported errors regarding  Xscreen and asked if I wanted to configure it and upon affirmation, it  pretty much said "you can't do anything about this -  give up!" LOL 

I'll muddle through.

---

### Post by mrhirsh on 2007-08-14
I have the exact same processor  - and I am having a similar problem.

First, don't try 7.07:  It won't work at all, you will not be able to install it.  I tried, got an error message about my graphics driver, spent a day trying to find one (and couldn't).

I then installed 6.06 and got further in the installation process though.

Vista has a utility that will allow you to shrink the hard drive and thus partition it, giving the unallocated space it's own letter.  My install was going fine until the "step 5 of 6" where it seems to be looking for drive space and/or set up a partition.  But it is just in an endless loop.  The machine doesn't lock up (I can cancel) but it doesn't complete the install.

Sorry I don't have a complete answer, but don't waste your time on 7.07

---

### Post by merlinus on 2007-08-14
You might try gparted live cd to set up the partitions:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by auroramae on 2007-08-15
In 6.06 I chickin out before the endless loop because I could see in the system are that my vista partitons aren't showing the size.

> You might try gparted live cd to set up the partitions:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

Thanks will try it

---

