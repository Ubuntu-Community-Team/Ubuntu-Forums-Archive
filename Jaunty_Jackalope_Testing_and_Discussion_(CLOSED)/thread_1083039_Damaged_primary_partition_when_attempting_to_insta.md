---
title: "Damaged primary partition when attempting to install Jaunty?"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by demothen on 2009-02-28
I recently attempted to install Jaunty to a new partition on my 320g internal drive.  The Jaunty install seems to work fine, however I can no longer load my Intrepid system.  I've gotten a message saying:


/dev/sda1: UNExpected inconsistency: run FSCK manually.
 (i.e., without -a or -p options) 
fsck died with exit status 4

an automatic file system check (fsck) of the root filesystem failed. a manual fsck must be performed, then the system restarted.  the fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
the root filesystem is currently mounted in read-only mode. a  maintenance shell will now be started. after performing system maintenance, press control-d to terminate the maitenance shell and restart the system. 
bash: no job control in this shell.

Before this, there is also a comment similar to / the same as this:
GParted 0.4.3

Libparted 1.8.8
Check and repair file system (ext3) on /dev/sda1  00:00:00    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 508810679
size: 508810617 (242.62 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:00    ( ERROR )
     	
e2fsck -f -y -v /dev/sda1
     	
The filesystem size (according to the superblock) is 76626025 blocks
The physical size of the device is 63601327 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes

e2fsck 1.41.4 (27-Jan-2009)

========================================
which I got when i tried to use gparted to check/repair the primary partition.

I have backups of all my essential data, but I would prefer not to have to rebuild the entire system naturally.  I picked up an external 320g hdd today, and reformatted it to ext2 in Jaunty, however I can not seem to write to it. (I am attempting to copy from the primary partition - which i can mount in Jaunty, to the external hdd)  Just trying to do a file browser copy, but I can not seem to write to the new external drive at all.  I can also not write to the external drive using my intrepid netbook.

Any assistance would be greatly appreciated.

-edit
Should mention, when I installed Jaunty, it seemed to hang for an abnormal period of time during the formatting, during which I clicked the next button at least once.  I don't know that this is a problem, just thought it might be useful information. I did not have any sort of progress bar during this phase, so I was concerned that I might have frozen up.

---

