---
title: "Dual Boot"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by mwiebelhaus on 2007-04-28
I am wondering if i can dual boot with ubuntu 6.02 LTS while xp media center edition is on the computer (Laptop Dell E1505) in nfts format so can i ?

Computer Info

XP Media Center Edition C drive formated in nfts file system
1 Gigabyte of memory
Intel Pro Wireless
Intel Centrino Duo

---

### Post by palmerthegeek on 2007-04-28
mwiebelhaus,

Yes, you need to complete a couple of tasks before hand.

I suggest following this HowTO: 
[https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo](https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo)

Good luck and Happy Ubuntuing!

---

### Post by mwiebelhaus on 2007-04-28
would it just be easier to  reinstall windows xp and make two drives instead of one c drive cause i dont want to screw around with all of that.

---

### Post by bulldog on 2007-04-28
If you feel like it,just do so :) 
You need 10GB of free space to install ubuntu,but more is better.

You can ,as an alternative,download the gparted live cd ,[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) burn it to a cd and boot from it.
Resize your windows partition and create two partitions for ubuntu.
Make a swap 1GB and format it as swap
Make ext3 partition for the /   [root] partition.
Apply your changes an when done,exit the gparted cd.

Fire up the ubuntu install cd and hit the install button. [on the desktop]
Follow the steps till you get to the partitioner and choose manual partition.
Mount the swap as swap and the ext3 partition as /
Format them both [swap as swap and / as ext3] set the bootflag to yes for the / partiton and apply these settings.
The install should be smooth from here.

---

### Post by mwiebelhaus on 2007-04-28
i guess i will just do that cause im kinda knew to dual booting and i want to resize them to my likings = ):popcorn:

---

### Post by mwiebelhaus on 2007-04-28
when i start the computer it gives me the choice of Media Center then Media Center but when i choose the second media center its says something root cannot find hal.ddl us it because there is a unformated d drive that is RAW ?

---

### Post by bulldog on 2007-04-29
> **mwiebelhaus said:**
> when i start the computer it gives me the choice of Media Center then Media Center but when i choose the second media center its says something root cannot find hal.ddl us it because there is a unformated d drive that is RAW ?

Why do you need to choose Media Center twice?
Did you resize the hdd without errors?

Can you start a live cd session and post the output of```
sudo fdisk -l
``` it's a lower case L.

---

