---
title: "Copying system to new hard disk?"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by neqqu on 2007-12-10
Hello,

I have a new hard drive. I want to get rid of my old hard drive. I have well working Gibbons system in old hard drive.

There is some threads, howto use gparted. Ok, I made similiar ext3 and swap partitions to my new hard disk with gparted, what next?
Which command I use to copy whole filesystem to new hard drive?

And then that grub thing... I am newbie, so for example this thread didn't help me much: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Could someone tell me exactly what to to with grub, how I copy it to the new disk.

Give me some commands :)

Thanks.

---

### Post by mikewhatever on 2007-12-10
You'll either have to use the above mentioned thread for grub, which also gives the required commands, or super grub cd.

---

### Post by tact on 2007-12-10
Is your new HDD totally empty and you have no problem wiping it and starting again?   If so then why not use the "dd" command and let that make a complete copy of your existing HDD onto the new HDD (i.e. clone the old drive).

you need to be very careful with the dd command as if you get the input and output parameters wrong you will overwrite the wrong drive.

Lets say for example that your existing drive is installed and in your system is /dev/sda

Lets say for example that your new drive, when connected to the system, comes up as /dev/sdb

then the command below will copy /dev/sda to /dev/sdb
```
sudo dd if=/dev/sda of=/dev/sdb
```
("if" means input file and "of" means output file)

dd takes a long time as it copies disk sector by sector and gives no indication of progress.  I cloned a 120GB drive recently and it took about 6hrs!   Once it is done though the new drive is a total clone of the old drive.  remove the old one, replace it with the new one and it will boot perfectly.  No problem even with grub.

I gotta stress again:
You would need to know for sure that /dev/sda is your old drive and /dev/sdb is the new drive as getting this wrong will be disasterous!  If you want to know more, or are not sure, then need to ask further..... dont be afraid to ask.

---

### Post by neqqu on 2007-12-10
Ok, does that dd commad erase that old disk? Or will it just copy whole disk sector by sector. My old disk is 320GB and the new one is 500GB. Will this be a problem?

---

