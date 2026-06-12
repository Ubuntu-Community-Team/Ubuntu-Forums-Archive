---
title: "OS Problems"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by MattyG on 2008-04-14
Ok, I installed Ubuntu and it works fine. But I got a new 80GB HDD that I put Ubuntu on. But the 250GB HDD I origanally installed it on will not let me put Vista back on. When I installed ubuntu I told it to use whole disk, so I am assuming that the hdd dosent have the windows sys files and boot sec files. Well any way can someone tell me why it is doing this and how to fix it please.

---

### Post by jbulcher on 2008-04-15
> But the 250GB HDD I origanally installed it on will not let me put Vista back on.
How are you going about this, and what are the problems are you running into? When you are re-installing Vista, are you formatting the hard drive? Vista uses a different file system than Linux, so formatting is usually necessary.

---

### Post by dstew on 2008-04-15
> When I installed ubuntu I told it to use whole diskThis option erases the entire disk before installing Ubuntu, so the Windows system was removed. You will have to re-install the whole Windows system from scratch. If you desperately need some files from the erased Windows system, you would have to try partition recovery tools like TestDisk.

---

### Post by martrn on 2008-04-15
if you are trying to expand your vista partition to include the full hardisk you will need a repartitioning tool to repartition you hard-disk.  If you have two hard disks and one with ubuntu on, you could boot ubuntu and type:

sudo gparted

and you will be able to graphically reclaim the partitions on your harddrive.  If you wish to change the partitions while running windows I would recommend looking for a simular programm like partition magic or something the tools for windows partitioning don't cut the buiscit.   I reccomend changeing only one partition at a time before commiting any changes and changeing your mind half way through partitioning will render you disk (or disks useless).

Ubuntu doen't usually change any system files, the only thing it usually does is install its own boot manager (Grub), and over-right the windows boot manager.  I have no idear how the windows boot manager words but grub is operable through command line you can type 

pico  /boot/grub/menu.lst

to find out how grub current boots your system:
To boot windows on a fisrt partition on a second drive you would type the following

rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
unhide          (hd1,0)
chainloader     +1
 
Grub commands are very difficult to get right but it possiable to boot a windows system from grub if you have no other boot loader present.

---

