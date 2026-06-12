---
title: "Making the perminent switch."
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by Ezprezo on 2009-12-24
Hello everyone. Well, I've installed this on my netbook and I've decided to stick with it. I was wondering how i'd go about deleting the windows XP partition I have on my computer and giving all of that space to linux without reinstalling linux. 

Any help would be appreciated and thank you in advance.

---

### Post by lyall on 2009-12-24
> **Ezprezo said:**
> Hello everyone. Well, I've installed this on my netbook and I've decided to stick with it. I was wondering how i'd go about deleting the windows XP partition I have on my computer and giving all of that space to linux without reinstalling linux. 

Any help would be appreciated and thank you in advance.


Hi Exprezo

First check and see if you have gparted install
look at System > Administrator > Gparted

if not there, then open Synaptic and search for "Gparted"
and install it.

or see the link 
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#GParted_Partition_Manager]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#GParted_Partition_Manager")

After you have installed go to System > Administrator > Gparted

If you would like to use windows in the future, I would make the windows partition smaller (resize).  Then just resize the Ubuntu partiton to full the space the you are not using now for Windows
You can always delete the Windows partition later if you want


To remove the Windows partition select it and delete it
then click on the big green Check mark to delete that partition
after the partition has been remove you should see unused disk space
right click on the partition and select resize/move and resize to balance of the drive.

But check where you swap partition is located, if it is at the end of the drive you should be okay, if not you should try to get it at end if you can, before you resize you partition

then resize you partition to full the hard drive for the Ubuntu partition

Or you can just re-install Ubuntu and select to install Ubuntu on the full drive


You you have any question about Gparted, open Gparted and check the Help
or ask the forums for more info

good luck and have fun learning

added = you might have a problem with Grub if you remove and increase the Ubuntu partition
this is something that needs to be checked if you done have a problem with grub

---

### Post by mocoloco on 2009-12-24
Just to add to what lyall said, if you plan to use the space for Ubuntu (and you probably do) you should boot from an Ubuntu disc or USB drive.  You won't be able to resize your Ubuntu partition while it's in use (mounted), so booting from an external media prevents that.
Then you just remove the Windows (NTFS) partition and resize your Ubuntu partition to fill it.

---

### Post by Ezprezo on 2009-12-24
Thank you very much for the help guys.

---

