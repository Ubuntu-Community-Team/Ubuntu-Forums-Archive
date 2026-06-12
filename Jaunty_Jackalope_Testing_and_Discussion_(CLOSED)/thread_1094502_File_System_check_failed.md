---
title: "File System check failed"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by irv on 2009-03-12
I know what I did wrong, but I am not sure how to fix it?
During the install of Alpha 5, I set the partitions for my /home on a separate drive. ( I have two hard drives sda and sdb.) on sda1 I have the OS booting, and sda2 as swap. On sdb I am mounting /home. When I boot the system it come up to this:
> Please repair the file System Manually.
CONTROL-D will terminate this shell and resume boot.
bash: no job control in this shell.
what I did wrong was to set the /home /dev/sdb1: size wrong.
When I look in the log file: var/log/fsck/checkfs
It looks like this:

 > Log of fsck -C3 -R -A -a 
Thu Mar 12 10:30:51 2009

fsck 1.41.4 (27-Jan-2009)

/dev/sdb1: The filesystem size (according to the superblock) is 9765617 blocks
 
The physical size of the device is 9763495 blocks
Either the superblock or 
the partition table is likely to be corrupt!


/dev/sdb1: 
UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

fsck died with exit status 4

Thu Mar 12 10:30:51 2009
----------------

If I use gparted and go in and change the size of hdb1, will I screwup my /home mount, or even mess up my MBR so I can't even boot?
I am not sure what to fix at this point?
Any help would be greatly accepted. 
Thanks
Irv

---

### Post by irv on 2009-03-13
Seeing I didn't get any help on this one, I just dump it all and started over from scratch. But seeing I am not up on using KDE (I use Gnome) I just loaded 8.04 version. I will just wait until the next version comes out. 
So just let this thread die.
By the way I tried to fix it using gparted and resizing the partition but it still kept coming up with the same error. By loading 8.04 it set the size right, and I am up and running.

---

