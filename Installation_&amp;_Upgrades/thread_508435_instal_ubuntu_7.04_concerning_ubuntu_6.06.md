---
title: "instal ubuntu 7.04 concerning ubuntu 6.06"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by Jannes. on 2007-07-24
hlo

first of all i will say that im working on 2 partititions (ubuntu 6.06+windows XP)
I downloaded ubuntu 7.04 and burned him to a cd...
Now i start ubuntu with the cd and i will install it BUT i have to solve 7 questions and at the fourth they ask me how will you install ubuntu,1 automatic (full hard disk) 2 hand made 
I choose Handmade cause i wont install it on my full hard disk and then i have a screen with my partititions 

device                      type   mount point        format?       size           used
/dev/sda
[INDENT]
/dev/sda1                 ntfs  /media/sda1                           73396MB   50600MB
/dev/sda2                 ext3 /media/sda2                           45600MB   6800MB
/dev/sda3                 swap                                               1028MB     0MB
[/INDENT]
when i select the second one and press next it give me a fault:
"No basic file system has been defined. Please repair this from the disk classification menu"
I dont know what to do :confused:

PLZ help me in eng or dutch

---

### Post by manndani on 2007-07-24
I think when I installed mine, I had the ext3 as "/" and then I had a "swap".
I also had "/home" but that's optional.

---

### Post by dabl on 2007-07-24
Yes, your root partition "/" is missing from this picture.  As a minimum, you should have "/" and "swap".  It's better to have "/home" on a separate partition as well, if you value your data a lot.  Here's guidance on partition planning:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

:)

---

### Post by LeCagot on 2007-07-24
I am a novice user and I believe I am having the exact same problem as the original poster.  I have a four partition model with Windoze at the root and Dapper in the last partition (the two middle partitions are FAT32 data areas visible by both OSes).  When I installed the previous Ubuntu version it installed everything including the boot-up selector, not a glitch.  I'd assumed that root was somewhere on the Linux partition (never had to go look for it).  Is there a graceful way to install over a previous Ubuntu installation or do we have to reformat the partition to give the installer a clean slate?

---

