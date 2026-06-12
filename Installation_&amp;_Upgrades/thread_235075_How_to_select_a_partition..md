---
title: "How to select a partition."
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by linuxnoobie on 2006-08-12
I hope someone can help me.  I don't know what I'm doing.

I have partition magic 8.0 on my computer running windows XP.  From PM8, I selected the option "partition for new OS".  After that I selected 70GB of drive C: to partition.  PM then asked me what OS i was gonna install on it.  I chose linux, and then it asked me to partition a swap (dunno what that is) of 500MB. So I did.  The whole partition process seemd to go without any problems.  After loading the boot disk I chose to install.  Right here is where I get confused.  It goes through detect disks and other hardware flawlessly but then I get to a section titled !!Partition Disks with 3 options.

1. Erase Entire Disk: IDE 1 Master
2. Erase Endire Disk And Use LVM:
3. Manually Edit Partition Table.

So I chose #3 since I wan't to install it on one partition without wiping out winblows.  After choosing that option, it shows my hard drive and its partitions as follows:

#4 primary 526.4 MB F swap swap
#2 primary 4.7 GB K fat32 /media/hda2
#1 primary 173.3 GB B KNTFS /media/hda1
#3 primary 71.5 GB K ext2 /media/hda3
-Undo Changed to Partitions
-Finish Partitioning and Write Changes to Disk

OK I know #4 is my swap, even though I don't know what a swap is, and #1 is the first partition of drive C: with windows installed.  My computer came partitioned with a backup of windows on the second partition which would be #2 (i guess its a gateway thing).  #3 is obviously the part I want to install linux on but dont know how to select that option.  Whenever I hit ENTER on that partition I get this information:

USE AS: Ext2 file system
Format the partition: no, keep existing data
Mount Point: /media/hda3
Mount Options: defaults
Bootable Flag: off

I guess my problem is that I don't actuall know how to choose to install ubuntu to that specific partition let alone install it at all.  I just don't want to make any mistakes and ruin something.  Please help.

---

### Post by meng on 2006-08-12
You want the following:
Use as: Ext2 (or ext3 if you want journalling, or some other FS if you know what you're doing)
Mount point: / (that's all, just /)
Mount options: defaults
Bootable flag: off
(you'll want the bootloader to be in the MBR)

---

### Post by bruenig on 2006-08-12
There is a nice tutorial on google video for this, just skip ahead to the ubuntu installation.
[Here is the link.](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+dual+boot)

---

### Post by confused57 on 2006-08-12
Here's an excellent guide for installing with the Desktop CD:
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

Might want to read over this guide, mainly for installing with the alternate cd, but there's some great information on the site:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by linuxnoobie on 2006-08-12
Thanks.

I'm gonna try to get this working.  Hopefully I'll be right back.

---

### Post by linuxnoobie on 2006-08-12
Thanks guys.

I guess i was just a little too paranoid.  Everything installed correctly.  But I still got 1 more problem.  I don't remember setting up a username and it's asking me for a username and a password.  I do remember them asking me for a password though.  So maybe I accidently skipped to quick over the username part.  Do you know what the default username is.  I tried ubuntu. Oh I just remember that it said its case sensitive.  I'm gonna go try Ubuntu and see if that works.  If you know, please lemme know.

---

### Post by linuxnoobie on 2006-08-12
nope.  i tried Ubuntu and UBUNTU as usernames and got nothing.

---

### Post by confused57 on 2006-08-12
> **linuxnoobie said:**
> nope.  i tried Ubuntu and UBUNTU as usernames and got nothing.

If you entered your name when you were installing, that's probably your username(or just your first name?)

---

### Post by meng on 2006-08-12
Yes, if you entered your first and last names during install, then your first name (all lower case) will be the username.

---

### Post by linuxnoobie on 2006-08-12
Didn't work.

I don't even remember it asking me for a username or even a name at all.  I do remember it asking me for a host name which is ubuntu and I tried that also.  All caps no caps and first letter capped.  Is there somehow a way to get around this.

---

