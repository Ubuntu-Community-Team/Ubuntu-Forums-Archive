---
title: "/home in fat32?"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by nosiad2 on 2005-06-23
Hi, i have two 10 gig hard drives and i was just wondering if it is possible to use 1 hardrive as a 'systems' hard drive, where i would partition it so that it is shared by winxp and ubuntu. Then i would have the other hard drive in fat32 to use for my /home in ubuntu. since it is fat32, i would be able to see mu music in windows..

is this posible?

---

### Post by bunced on 2005-06-23
[QUOTE=nosiad2]Hi, i have two 10 gig hard drives and i was just wondering if it is possible to use 1 hardrive as a 'systems' hard drive, where i would partition it so that it is shared by winxp and ubuntu. Then i would have the other hard drive in fat32 to use for my /home in ubuntu. since it is fat32, i would be able to see mu music in windows..

is this posible?[/QUOTE]
 You can, but I don't suggest this is the best way. I suggest you have the FAT32 dive mounted at a point such as /home/username/Documents - that way, you don't have all the problems with Ubuntu clogging up the drive with configuration files. To have it like this, at the terminal do:

sudo nano /etc/fstab

then at the bottom enter the line 

/dev/hda?              /home/username/Documents             fat32           auto,user,rw           0 0

where /dev/hda? is your hard drive partition and /home/username is your home directory

Regards,
David

---

### Post by mingus on 2005-06-23
I believe this is possible, but may not be advisable.  FAT32 is not a journaled filesystem.  While home is primarily for user data files, program executables and scripts are also sometimes placed in this directory.  Consider leaving /home on HDD1, creating a FAT32 partition on HDD2 for your music which you mount to a directory you create like /MyMusic, and then placing a symlink from that directory in /home.  Then whenver you open Ubuntu /home, you will see /MyMusic as if it is in /home, when it actually is on the other drive.

---

### Post by Lunde on 2005-06-23
[QUOTE=nosiad2]Hi, i have two 10 gig hard drives and i was just wondering if it is possible to use 1 hardrive as a 'systems' hard drive, where i would partition it so that it is shared by winxp and ubuntu. Then i would have the other hard drive in fat32 to use for my /home in ubuntu. since it is fat32, i would be able to see mu music in windows..

is this posible?[/QUOTE]
home as fat32, probably not the best solution. Why don't you just mount a "My documents" under /home/user_name/Documents, this way you can store and view files form boh systems and you don't have all the hidden files and directories viewable in windows.

EDIT: 3 answeres at the same time, your're lucky

---

### Post by nosiad2 on 2005-06-23
hey thanks bunced....i am going to do just that....can i do it using the partition app that comes with the setup instead of installin and then using the terminal?

---

### Post by mingus on 2005-06-23
bunced and lunde's solution is better than mine . . .

---

