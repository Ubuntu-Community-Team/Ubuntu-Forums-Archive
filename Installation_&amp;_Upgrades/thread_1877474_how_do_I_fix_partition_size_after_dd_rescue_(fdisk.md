---
title: "how do I fix partition size after dd_rescue? (fdisk/gparted discrepancy)"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by buntuyu on 2011-11-08
After gparted failed to copy a partition I ultimately resorted to dd_rescue, with "dd_rescue -v /dev/sda3 /dev/sdb6"

I had to first create a new, empty "/dev/sdb6" in order to ddrescue the (original) /dev/sda3 "into" /dev/sdb6 of a size larger than the original. (My first attempt failed, with dd_rescue running out of space on /dev/sdb6 -- "no space left on the device").

dd_rescue seems to have completed the task (overcoming input/output errors). However, now I have a discrepancy. 

fdisk is showing the copy (/dev/sdb6) to be 250GB (the larger, "container" size I set for the receiving partition), but gparted is showing the same partition to be 238GB (the size of the original -- /dev/sda3).  I ran the gparted "check" command on the new, copied partition, hoping gparted would detect the discrepancy. It reported having checked and "grown" it (last listed task), but the discrepancy was not fixed.  fdisk is still reporting 250GB.

I am afraid to work with the partition table further, for fear of losing data.

---

### Post by oldfred on 2011-11-09
dd is intended to copy from exact size to exact size.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

If sda6 is 250GB what is the issue? 

Post these
The sfdisk output from the text file above.

sudo blkid

sudo parted /dev/sda unit s print

---

### Post by buntuyu on 2011-11-18
> **oldfred said:**
> dd is intended to copy from exact size to exact size.



Not "dd".  "dd_rescue".  [http://www.gnu.org/s/ddrescue/ddrescue.html](http://www.gnu.org/s/ddrescue/ddrescue.html)

My hard drive has bad sectors - both gparted and (standard) dd fail, with "Input/output error"s.  That's why I'm using dd_rescue (or "ddrescue").

Since my post, I booted up the cloned partition (with its size discrepancy), and it seems to work fine. 

But I'm still not sure what happens if I add a subsequent  (/dev/sda7) partition beginning at the lesser, 238GB boundary... would something attempt to keep writing to /dev/sda6 to the greater, 250GB boundary (clobbering data on the new /dev/sda7) ??

---

### Post by tartalo on 2011-11-18
This?
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

