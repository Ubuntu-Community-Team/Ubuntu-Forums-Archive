---
title: "RAID-0 is CRITICAL"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by herveb on 2010-05-09
Hi,

I just finished painfully the installation of Ubuntu 10.04 LTS on my laptop, and i just noticed a RAID-0 is CRITICAL while booting.

What is this?

FYI, I have two Hard drives, and it took us some time to figure out why the computer doesn't want to boot at all - there was empty bit without partition at the beginning of the drive.

[http://ubuntuforums.org/showthread.php?t=1471679]("http://ubuntuforums.org/showthread.php?t=1471679")

appart from that, it boots ok - well, used to, I've just tried to upgrade my nvidia driver, now i have only access to very basic graphics :mad:

---

### Post by herveb on 2010-05-10
any ideas anyone regarding this "Raid-0 is critical" message?

---

### Post by ronparent on 2010-05-10
Looking over your prior thread, this popped out at me on your 1st post:

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

That is the ususal output when you are dealing with a raid0 array. Just casually perusing the rest of the thread, if a raid0 existed when you started, it doesn't now! That is probably all the message signifies. That said, you have two drives now to do with whatever you will. However, apparently the raid0 signature still exists in the meta data section of one or both of the two drives. Since you are not now using the raid it would probably be better to erase the raid meta data. To find it, in a terminal type **sudo dmraid -ay**. This will reveal any remaining meta data and on which disk it resides. To erase write **sudo dmraid -E** to erase any remaining meta date.

You are lucky to have installed if raid meta data remained on anydrive, but, I can see from that prior thread that a lot was going on. With the meta data gone you should be fine.

---

### Post by herveb on 2010-05-11
this is strange...

```
boisson@boisson-laptop:~$ sudo dmraid -ay
no raid disks
boisson@boisson-laptop:~$ sudo dmraid -E
ERROR: option missing/invalid option combination with -E

```

---

### Post by ronparent on 2010-05-11
"no raid disks" tels you all you need to know, No further action needed.

---

### Post by herveb on 2010-05-11
found out what the problem was, thanks to one of the clue you pointed at

> **ronparent said:**
>  However, apparently the raid0 signature still exists in the meta data section of one or both of the two drives. Since you are not now using the raid it would probably be better to erase the raid meta data. 

I then rebooted with the liveCD, open GParted, and there it was: an unused 1MB part at the beginning of sdb - the second Hard drive. I expanded sdb to fill the whole of the disk, the error message is now gone
:guitar:

---

