---
title: "Hide Live USB partition from Linux, Windows etc."
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by choben on 2010-05-18
I want to set up my USB memory stick(s) (4gb) so that I have a partition (3gb?) for personal data storage and another hidden (1gb?) for booting/installing Ubuntu live from the 'stick' on friends' and colleagues' computers.

I have a number of queries:

[INDENT]1) If I flag the boot partition 'hidden' in Gparted, it does what I want in Ubuntu but not in Windows; in Windows you can see the hidden partition, 'Wubi', and not the storage one. Does it simply depend on the physical position of the partitions on the memory stick?[/INDENT]
[INDENT]2) I am using Unetbootin and Gparted (both GUIs). Should I prepare the live boot partition before or after partitioning the memory stick?[/INDENT]
[INDENT]3) How much memory should I allow for the live boot partition?[/INDENT]
[INDENT]4) Is there anyone who has asked similar questions or tried to achieve the same results before? Please let me know if I'm doing it all wrong.[/INDENT]
;-)
Cheers

---

### Post by Mike_tn on 2010-11-15
No answers? This is from May! I came looking and you answered mine ha ha, you said flag it in Gparted to hide the boot partition from Ubuntu. Thanks~
As to the rest, I can try to answer briefly off the top of my head...well not off the top, I studied and returned:
> **choben said:**
> 1) If I flag the boot partition 'hidden' in Gparted, it does what I want in Ubuntu but not in Windows; in Windows you can see the hidden partition, 'Wubi', and not the storage one. Does it simply depend on the physical position of the partitions on the memory stick?

Windows only sees the first partition on a USB. Make your data partition the first partition and put it on the right side in Gparted. That means it will be called in Gparted, once done, as sdb1 or sdc1 whatever it happens to be. You see data that way. Whichever side you partition and format first will be called sd_1. (Where _ is a letter that varies) So plan to make that partition first and make it your data partition.

You can hide it all from Windows by not giving it a drive letter through its Computer Management tool. You won't see either one. Maybe Windows sees nothing already and you want it to see your USB, then check to be sure it has a drive letter, if not then give it one with that same tool.

> **choben said:**
> 2) I am using Unetbootin and Gparted (both GUIs). Should I prepare the live boot partition before or after partitioning the memory stick?

I like to partition first then install. No need to risk anything that way. Resizing something with data in it has to be more risky though maybe small risk.

> **choben said:**
> 3) How much memory should I allow for the live boot partition?

As to how much room for boot up. My hunch is to leave a little space in the boot partition. Some tutorials leave it no extra space but I also heard it runs better with some space, 1GB for the install part. I usually leave some breathing room rather than none at all, that seems good if you can afford it. If you make a persistent casper version with the Ubuntu Startup Disk Creator then you would want a much bigger install partition side and maybe a bigger USB overall.

> **choben said:**
> 4) Is there anyone who has asked similar questions or tried to achieve the same results before? Please let me know if I'm doing it all wrong.

I wanted to copy the way the Mandriva Seed sets up theirs but didn't DOH! Now I have to redo it. That tool puts a tiny empty partition as sdc1 or sdb1 etc (first partition) on the right side as you see it in Gparted. The installation side, sd_2, is on the left. You have to resize the sd_1 empty side to fill out your USB with storage space after it finishes. The boot side is pretty tight, only room for the compressed install, not much breathing room. It runs good though. It doesn't have a slider in the GUI to set anything up much in advance. It has a GUI but simple like UNetbootin's. Also Gparted has no idea what file system Mandriva is using on the installation partition of the USB, very interesting.  They flag the Boot side as "Boot" and "Hidden". They flag the Data side as "LBA". I'm installing Ubuntu that way as I type but with a casper partition.

---

### Post by Mike_tn on 2010-11-22
Graphical example of what I came up with to partition a USB. I tried to make my image appear large in the body of the text but could not make it work. Tried several ways.  You  can click the attached thumbnail to make it bigger.

---

### Post by choben on 2010-11-25
Thanks Mike. It has been a while since I posted this and I believe I was successful in making both partitions behave how I wanted them to. If I want to remember how to do it again, I'll know where to look!
:popcorn:

---

