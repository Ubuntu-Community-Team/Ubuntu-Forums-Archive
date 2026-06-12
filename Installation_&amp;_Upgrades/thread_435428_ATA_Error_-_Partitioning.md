---
title: "ATA Error - Partitioning"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by haargerman on 2007-05-06
Hey all - I'm really hoping someone can help me out here.

So I'm attempting to instal Ubuntu 7.04 on my Dell E1505. I have to use the text installer because I have an ATI X1400 video card.

So I got to the partitioning part - and now I'm confused as hell.

Here is what I have right now:

#1 primary  49.3MB  K  Fat16  /media/sda1 --- Dont know what this is.
#2 primary  70.0GB  K  ntfs  /media/sda2    ---- This is where Windows is installed - I don't want to touch this partition.
#3 primary   10.0GB  K ntfs /media/sda3 -- I formatted a partition to get this..
           unusable  13.3GB     unusable      -- What is going on here? I can't do anything with this, I would like to use this for Ubuntu.
#4 primary 5.1GB    K  fat32 /media/sda3

So right now I cannot boot into windows and ubuntu is not installed.

I need to fix this so I can either;
a) boot into windows and install linux later or;
b) install linux and be able to DUAL-BOOT

Someone please help?
Thanks
~ Aaron

---

### Post by haargerman on 2007-05-06
Is there a way I can just set #2 primary as a bootable flag, save changes, and abort the install and I'll be able to boot into Windows?

Can anyone help me to try and boot into Windows? I need a computer for tomorrow. 

I can't get past the Dell Logo ..it give me an ATA Error and goes no further, or brings me to the Ubuntu Install screen.

---

### Post by haargerman on 2007-05-07
...If I select the Guided option to "Use the largest continous free space", do I have to worry about information being lost?

---

