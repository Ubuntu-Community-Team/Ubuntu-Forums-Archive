---
title: "[SOLVED] grub does not initialize; ubuntu non-bootable"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by jorik42 on 2008-08-15
Morning;

ive been working to get my operating systems configured to my satisfaction on my new box.  ive been working towards a dual boot system with vista and ubuntu 8.04.  installing vista, though slow, goes without a hitch.  Furthermore, installing Ubuntu also goes flawlessly.  So, you may be wondering what the problem is; the problem is that grub flat out does not work.  The files are all there (as ascertained by looking at the files via a live cd).  but grub simply does not get run on boot.  The bootup process simply defaults to vista.  does anyone have any ideas, as this doesnt make any sense to me...

jorik

---

### Post by Pumalite on 2008-08-15
When usin Vista, you have to allocate space for Ubuntu with the Vista partitioner first. Otherwise, Vista will not let you run anything in that machine.

---

### Post by jorik42 on 2008-08-15
not true; ive set up multiple other machines with similar setups to the one i desire (vista + ubuntu) using gparted to do the partitioning.  not had any problems with those machines.

---

### Post by jorik42 on 2008-08-15
or are you trying to say that the vista partition needs to control the whole disk as of the time of vista installation, then after that i would go in and, using the vista partitioner or gparted, create the partitions for ubuntu, and then install it?  

and if so, why does it have to be done that way?


jorik

---

### Post by logos34 on 2008-08-15
> **jorik42 said:**
> not true; ive set up multiple other machines with similar setups to the one i desire (vista + ubuntu) using gparted to do the partitioning.  not had any problems with those machines.

good for you, but plenty of people in these forums have had trouble, and the recommended way is to use vista's own disk utility.  It's mentioned in the ubuntu user docs:
[https://help.ubuntu.com/community/WindowsDualBoot#Resizing%20partitions%20with%20Windows%20Vista](https://help.ubuntu.com/community/WindowsDualBoot#Resizing%20partitions%20with%20Windows%20Vista)

---

### Post by jorik42 on 2008-08-15
ok, so, just to make sure i covered all my bases, i wiped the partitions from my drive, re-installed vista, created a second partition for ubuntu using the vista disk management tools, then restarted and installed ubuntu to the prepared partition.  restarting after that gives me the following error:

BOOTMGR is missing
Press Ctrl+Alt+Del to restart

So it seems that something has once again been screwed up somewhere.  As a side observation, if i set the bios to boot from a differenct hard disk (one with no OS), grub shows up and gives an error (error 22..).  This tells me that grub is on the disk, and working, but something with vista is somehow screwing it up...


jorik

---

### Post by logos34 on 2008-08-15
> **jorik42 said:**
> ok, so, just to make sure i covered all my bases, i wiped the partitions from my drive, re-installed vista, created a second partition for ubuntu using the vista disk management tools, then restarted and installed ubuntu to the prepared partition.  restarting after that gives me the following error:

BOOTMGR is missing
Press Ctrl+Alt+Del to restart

So it seems that something has once again been screwed up somewhere.  As a side observation, **if i set the bios to boot from a differenct hard disk (one with no OS),** grub shows up and gives an error (error 22..).  This tells me that grub is on the disk, and working, but something with vista is somehow screwing it up...


oh, so you have more than one disk--should have said so before...post your fdisk output (run from live cd)

sudo fdisk -l

---

### Post by jorik42 on 2008-08-16
didnt think that it mattered before; i disconnected all the drives but the drive i wanted the OS's on, and it worked.  It seems that the bootsectors (or grub at least..) were being installed on a different disk.  

ill mark this as solved once i find the correct button..


jorik42

---

