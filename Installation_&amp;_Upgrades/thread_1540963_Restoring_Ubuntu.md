---
title: "Restoring Ubuntu"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by ganeshmagal on 2010-07-28
Hi,

I backed my entire system (Ubuntu 10.04) using 'tar' and have a .tar file on my external HDD. I was wondering if I can restore this system on -
1) A brand new machine with Ubuntu 10.04 already installed
2) On a machine with Ubuntu 9.04
Because as far as I know when I untar the backup it will overwrite each and every folder in the system, so I should be able to do the 1st question, but I am not sure about the 2nd question.


Thank you

---

### Post by dabl on 2010-07-28
You _can_ do that (untar an entire OS onto another computer), but that doesn't mean that it's going to work correctly, or at all.  If the hardware is identical in _every respect_ (which it won't be -- the partition UUID for example is always different), then it could theoretically work, if you installed your Grub boot system the same.

It sounds like you are looking for something like clonezilla.  If you use clonezilla to make an image of a hard drive partition, and then you restore that image to an equal or larger sized partition on another computer, you will have a bit-for-bit true copy of the original.  Then you only need to work out the adjustments for any hardware differences, such as UUID numbers, and you will have the same software on a different hard drive.

---

### Post by ganeshmagal on 2010-07-28
I am looking for solutions using inbuilt utilities like - rsync, tar to have a regular backup of the machine and do a quick restore to a previous state when required.

---

### Post by ticket on 2010-07-28
Try using the dd command:

[http://ubuntuforums.org/showthread.php?t=1202926](http://ubuntuforums.org/showthread.php?t=1202926)

Despite the title, it is a success story.

---

