---
title: "Create larger than 4GB Casper file?"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by YouRik97 on 2012-09-01
> 
Originally Posted by C.S.Cameron [http://ubuntuforums.org/showthread.php?p=10155778#post10155778]("http://ubuntuforums.org/showthread.php?p=10155778#post10155778") 
Casper-rw files are FAT32 which limits them to 4GB.
If you want more than 4GB you can make a casper-rw partition and also home-rw partition. 
These partitions are only limited by the size of the drive.

Here is a step by step using usb-creator, universal should be similar. If you prefer UNetbootin let me know:


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
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.

actually i just signed up to ask this question ;)

do i have to boot from a live cd or can i edit that partition in windows?

---

### Post by oldos2er on 2012-09-01
Post moved to its own thread.

---

### Post by oldfred on 2012-09-01
Welcome to the forums.

Not many of those commands are unique to LiveCD. About the only thing you might be able to do is create the Fat32 partition. Windows cannot create Linux partitions.

---

### Post by C.S.Cameron on 2012-09-02
Windows can only see one partition, (the first), on a flash drive.
You need to boot a Ubuntu Live CD or Live USB or otherwise use a computer running Linux.
Windows also does not normally handle ext filesystems.

Do not try to format a flash drive with more than one partition with Windows, I have bricked two trying this.

---

