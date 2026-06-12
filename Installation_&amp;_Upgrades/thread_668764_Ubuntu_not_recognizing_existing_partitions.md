---
title: "Ubuntu not recognizing existing partitions"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by razorfrog on 2008-01-15
So, I've had Ubuntu on this computer before (Thinkpad x60), and trying to install it again, I'm now having issues...

Dualbooting with XP, the partitions are all set up:
120gb - XP install
30gb - ubuntu
1 gb - ubuntu swap
5gb - thinkpad restore

However, booting into Ubuntu on the live CD, the partitions are not seen as excising.. Even though the partitions automatically mount on the desktop. GParted gives a strange error seen below:

[IMG]http://img31.picoodle.com/img/img31/4/1/15/f_Screenshotm_29751b0.jpg[/IMG]

Any ideas how to make this work? 
Thanks!

---

### Post by yabbadabbadont on 2008-01-15
/dev/scd0 is the CDROM/DVD drive....  you can't parition it.

It appears to see /dev/sda fine though.

---

### Post by wolfen69 on 2008-01-15
see where the pull down menu is? (top right, /dev/sda 149.05 gb) go to that, and see what else is there.

---

### Post by razorfrog on 2008-01-15
Hey - it not being able to do anything with the CD drive sure makes sense.. Thanks.

The issue still stands though - Gparted sees the disk as unallocated space - which it definitely isn't..  (it even mounts the partitions, which really makes no sense)..

And there's nothing else in that dropdown menu on the top right..

---

### Post by wolfen69 on 2008-01-15
you must also open gparted as root.
```
sudo su
```
```
gparted
```
and unmount the drives you want to partition.
```
umount /dev/sdxx
```
substitute x with the appropriate letter/number

---

### Post by yabbadabbadont on 2008-01-15
You can't work on the partitions while they are mounted.  However, that doesn't explain why gparted sees the space as unallocated.  What is the output when you run "fdisk -l" in a terminal?  (use sudo if needed)

Edit: Too slow.  :D

---

### Post by razorfrog on 2008-01-15
So weird.. fdisk sees the partitions, no problem. Unmount them, no problem.. But Gparted and the installer still see the disk as unallocated space..

---

### Post by wolfen69 on 2008-01-15
i have had issues with gparted (in ubuntu) in the past. try the gparted live cd. [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by razorfrog on 2008-01-15
Well, I'm more concerned about the installer not seeing the partitions, not GParted... They just seem to share that problem. 

Any ideas on how to get Ubuntu on that partition that it can only-sorta see?

---

### Post by razorfrog on 2008-01-15
My most recent idea is that the disklabel created by norton partition magic is unreadable by Ubuntu perhaps? Could that be possible?

Edit: that seems likely, as GParted lists the disklabeltype as "unrecognized"

What now?

---

### Post by yabbadabbadont on 2008-01-15
You said that fdisk didn't have any trouble reading the partition table, correct?  If so, you might try opening the disk with fdisk and then rewriting the table without changing anything.  i.e.  fdisk /dev/sda then "w" to rewrite the current partition table, then quit.  [COLOR="Red"]ONLY do that if you have a FULL and COMPLETE BACKUP first.[/COLOR]  You would also most likely have to reboot the CD before the change would be visible to gparted.

---

### Post by razorfrog on 2008-01-15
Looks like I got things working by re-doing the partitions with Partition Magic. All very strange though. 

Thanks for all the help!

---

