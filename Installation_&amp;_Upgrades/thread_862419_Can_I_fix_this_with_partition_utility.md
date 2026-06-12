---
title: "Can I fix this with partition utility?"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by user7464j on 2008-07-17
Hi all,

I got impatient and cluttered up my drive....I'll spare you the gory details, it was late. 

Anyway, I would like to clean up the GRUB by removing Ubuntu 6.10 and make better use of the disk space. The Ubuntu 6.10 was an incomplete install that I interrupted. I typed what I could remember from the GRUB:

Ubuntu 8.04.1, Kernel 2.6.24-19-generic
Ubuntu 8.04.1, Kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+
Other operating systems:
Microsoft Windows XP Home Edition
Ubuntu 6.10 (6.10) (on /dev/sda3)

I used Synaptic to search for 'linux-image' any was planning to delete everything but 2.6.24-19 but 'install' was the only option available.

Ultimately I would like to have both OS's with a single shared storage (3 partitions??? More? less?) or whatever configuration that makes the most sense. Any recommendations (and step by step guides) would be greatly appreciated.

Oh.... Dell Inspiron 1000, 100GB HD, 512 RAM.

---

### Post by mikewhatever on 2008-07-17
> Anyway, I would like to clean up the GRUB by removing Ubuntu 6.10 and make better use of the disk space. The Ubuntu 6.10 was an incomplete install that I interrupted.

Delete the partition it's installed on, either sda7 or sda3.

> I used Synaptic to search for 'linux-image' any was planning to delete everything but 2.6.24-19 but 'install' was the only option available.

That's Hardy's kernel. Don't remove it unless you want to remove Hardy too.

---

### Post by jimv on 2008-07-17
BACKUP ANYTHING YOU DON'T WANT TO *POSSIBLY* LOSE BEFORE DOING THIS!!!

OK, get a Gparted boot disk from: [http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-live-0.3.7-7.iso](http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-live-0.3.7-7.iso)

Burn that to a CD and boot up from it.  It will bring you to a Gparted window like the one you posted.

Then you can delete the 6.06 partition, and move/resize the other partitions as desired.  ALSO, you can delete one of those SWAP partitions.  You only need one.

---

### Post by user7464j on 2008-07-21
Well I managed to do something wrong. I downloaded and burned the Gparted disk, rebooted, deleted 6.10 (/dev/sda3), deleted the extra swap file, resized the remaining swap file to take up the space from the deleted one and tried to exit but the utility froze. I rebooted to this:

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17

What did I do? What should I do?

---

### Post by upchucky on 2008-07-21
error 17 is the error that indicates it cant find stage 2, stage 2 is the /boot/grub/menu.lst that needs to be edited to tell grub what drives to boot.

i just did a post yesterday explaining how to fix this, search my name and look for other posts as well so u understand exactly how to fix it.

it is a very simple fix if you understand what you are doing.

---

### Post by user7464j on 2008-07-21
Well I'm currently digging around.... I found a post directing someone else to a Sper Grub Disk. I burned SGD and put it in the drive. It is able to boot XP but not Ubuntu 8.01.1. When I try to use SGD to boot Linux directly it shows:

root (hd0,6)
 Error 17 Cannot mount selected partition

Does the '6' represent the swap file that I deleted? Linux was installed on 7. I'll keep digging...

---

### Post by CarlosNYB on 2008-07-21
Removing the boot loader will clear the error, yes.

But now you need to put in another boot loader so your computer also sees linux.

---

### Post by user7464j on 2008-07-21
I removed /dev/sda3 which had Ubuntu 6.10. I left /dev/sda7 alone which has Ubuntu 8.1.01.

---

### Post by logos34 on 2008-07-21
> **user7464j said:**
> It is able to boot XP but not Ubuntu 8.01.1. When I try to use SGD to boot Linux directly it shows:

root (hd0,6)
 Error 17 Cannot mount selected partition

Does the '6' represent the swap file that I deleted? Linux was installed on 7.

(hd0,6) = sda7

Maybe run a filesystem check on root form the ubuntu live cd:

sudo fsck /dev/sda7

If you aborted gparted, the partition table may be partially messed up (partially because you are able to boot windows).  Try to straighten it out with **testdisk.  **(it's in the repos)

---

### Post by user7464j on 2008-07-21
I was just about to delete the partitions and start over.

Anyway I received the following on the terminal:

fsck 1.40.8 (13-Mar-2008 )
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda7

I initially had two swap files (attachment in OP). I deleted the bottom one and expanded the top one since I have 1024RAM.

---

### Post by logos34 on 2008-07-21
> **user7464j said:**
> I was just about to delete the partitions and start over.

Anyway I received the following on the terminal:

fsck 1.40.8 (13-Mar-2008 )
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda7

I initially had two swap files (attachment in OP). I deleted the bottom one and expanded the top one since I have 1024RAM.


The root partition number may have changed when you deleted one of the swaps.

Check gparted again or sudo fdisk -l

---

### Post by upchucky on 2008-07-21
```
sudo fdisk -l
``` will tell you the partitions, and if hd0,6 looks like it has 8.01 then,


since it found root at hd0,6

then do ```
sudo grub
```

then ```
find /boot/grub/stage1
```

it should tell you that root is hd0,6
if this is true,
then do ```
setup (hd0,6)
```   the brackets are part of the code

it has shown that root is the mbr bootloader stage1, and the setup tells grub to make a new stage2, stage 2 is the /boot/grub/menu.lst that should get 8.01 running, and if windows will not boot then you need to search for the chainloader info to get it booting

---

