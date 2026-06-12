---
title: "How to set multiple Logical hard drives during Installation [Advanced Partitions]"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by TobiasRipper on 2010-12-31
Hi, I'm Dima... I'm a new user, just transfered from Windows 7 to Ubuntu 10.10 and I'm already lost.

Right now I have NOTHING installed on my ubuntu OS so I'm ready to reinstall it as many times as needed until I will get this thing right...

What I need to do is, during the installation, I want to create several logical drives from my single physical drive inside of a laptop. So what I want it to set up the partitions like this:

1) C:/ for OS
2) D:/ for Programs
3) E:/ for Files

Even though it is a Laptop, it HAS to be 3 separate logical drives so that all the files wouldn't mix up with programs and OS files... I believe that I kinda understand the basics of setting partitions during the installation... root "/" for the OS, Home "/home" for the files and swap "/swap" as a backup for RAM.

Well... this is as far as I could go... I don't know what settings to pick in the partition creating window during the installation in order to create logical drives. I 100% don't know what I'm doing because this is my very first day with linux.

umm... also I don't want to go ahead and try to fix it within the os because at this point it will be MUCH MUCH easier for me to do this from the beginning.

Thanks for the help...

---

### Post by garvinrick4 on 2010-12-31
# You are allowed 4 Primary partitions per HDD.
And extended drive counts as 1 Primary partition.
# Any partition inside of an Extended partition is a logical partition.
As many logicals as you want.
# In the linux install:
```
 
sudo apt-get install gparted

```
Or in live cd (already has gparted installed)
Gparted is the partitioning tool: Make your partitions there. Google gparted get the manual
and should be ok, not real hard to understand. You already know / is a file system, what a 
swap is and what a /home is.
Linux is ext4 and Windows is NTFS format.
Now when you install use manual install and put each / , /home in the partition you have made for it.
Put grub2 (boot manager software) in sda if the first drive. In sdb if second drive in sdc if third and so on and on. 
If your internal drive will be sda
# From now on instead of C; drive D:drive,  F: drive it will be sda1, sda2, sda3 just named different in linux.

---

### Post by TobiasRipper on 2010-12-31
Hi, Thank you for such a quck reply. And I really really appreciate the afford of narrowing the answer down to pin point but I still can't quite get some points.

So you're saying that it is best to create logical drives using gparted? So then while installing the fresh OS I should use the function of "Format the whole drive and install the OS" just like the majority of the installation tutorials tell me?

Very very sorry for my misunderstanding of the concept.. my fault...

Even though I have some understanding of what the root, home and swap are for... it's as far as it goes... 
maybe, if it's not too much to ask, could you just write a step by step guide just for the OS installation part, and I'll try to figure out a way of creating partitions in gparted later on. Again I really really appreciate all of your afford, it's just me who's not yet used to the system and it's concepts.... usually windows did most of the job and I just had to observe the blinking lights :)

so.. if it's not too much to ask... a simple tutorial starting from the point where you are given a choice to either parallel install the os OR use the whole drive with a fresh new installation OR to do the advance partition. until the next installation step. Just the features that I need to pick from the drop down menus. just as an example... I'm trying to find a tutorial that would explain things this way: [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

Thank you very very much. Happy new year by the way...

---

### Post by garvinrick4 on 2010-12-31
There is a user in these forums that has written a graphical installation guide for ubiquity
installer for 10.10. I will bump this up to front for you and see if someone has it, I will look
for it and post when I find it, I am on a new 11.04 install and do not have all my bookmarks here.

---

### Post by TobiasRipper on 2010-12-31
Ah, thank you very much for all the afford!!!

---

### Post by TobiasRipper on 2010-12-31
Actaully I read a few tutorials in installing 10.10 but all of them just explain to set:
root with about 6 to 15 gb for the os
swap to be wtise as much as your ram
and home for all the files and settings. (btw isn't /home made for OS settings and preferences in case of OS reinstalatio to preserve the settings?)

Well the LIve CD seems to be taking for ever to boot so maybe I could do all the partitions during te instalation... - Most of the tutorials tell me to boot the Live CD and do all the partitioning in there through gparted. Maybe I could do it this way:

During the instalation set the:
root to be 15gb
swap 6gb (3gb ram)
and home to be... 30gb. (for settings and user preferences)

and leave the rest of the space unallocated. Then when the os is installed, I'd create additional logic drives. The problem is that I don't know HOW to set the drives... there is so many functions and drop down menues for creating partitions, I just don't know the purposes of those functions.

---

### Post by TobiasRipper on 2010-12-31
Ok I apologize for all the hassle. I figured things out.

I called my friend who is a hot shot linux user. The problem was that I got used to the practice that when you create logic drives from a physical drive, windows displays those logic drives as separate drives in "My Computer" and I thought that Linux would do the same thing but the guy told me that Linux will only display drives separately when they are Physicaly two different drives... virtually the logic drive will be displayed as folder inside of it's physical drive inside "My Computer" of linux. 

:lolflag:

---

