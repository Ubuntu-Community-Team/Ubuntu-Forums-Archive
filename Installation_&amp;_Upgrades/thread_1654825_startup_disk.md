---
title: "startup disk"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2010-12-28
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Burn your CD or create a USB drive:
choose usb + ubuntu -> click show me how

Image 4 - Stored in extra reserve space...

This option is greyed out for my usb stick (1 partition, 8gb fat 32)?

---

### Post by wilee-nilee on 2010-12-28
So you have loaded and clicked on all areas like the image correct?

Not sure why it's greyed out this is a working program when used correctly, but anything can happen.

---

### Post by peterfernandes238 on 2010-12-28
This option is greyed out for my usb stick (1 partition, 8gb fat 32)?
-----------
Peter Fernandes

---

### Post by Mark Phelps on 2010-12-29
Just tried this for Ubuntu 10.10 desktop using a 4GB flash drive, already formatted with FAT 32 -- and it worked just fine.

---

### Post by C.S.Cameron on 2010-12-29
You can make persistent partitions, sizes optional:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

