---
title: "LiveUSB persistence error"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by nightcracker on 2011-06-01
I have a USB with two partitions, one FAT32 with Ubuntu 10.04 on it, and one ext4 partition labelled casper-rw. According to the docs this should do to create a persistence installation, but I still get the "can't find persistence medium" error when booting.

Did I do something wrong or is this a bug?

I installed with unetbootin on the FAT32 partition and created the partitions using GParted.

---

### Post by C.S.Cameron on 2011-06-01
You probably need to edit your text.cfg file as follows:

Select disk / syslinux / text.cfg and add "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true **persistent** file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --


It may be simpler to select 128 MB extra space when making the drive with Startup Disk Creator and then delete the casper-rw file.

---

### Post by nightcracker on 2011-06-02
I did this already. What I exactly did was this:

- Create install with 128MB persistence on FAT32 partition.
- Remove casper-rw file from FAT partition.
- Resize FAT32 partition and create ext4 partition labeled casper-rw.
- Edit txt.cfg, copying live label, edit label to persistent, add persistent option to boot line and edit default to persistent.

---

### Post by C.S.Cameron on 2011-06-02
If you installed with "extra space" and then deleted casper-rw, you do not need to edit text.cfg

I previously wrote up both methods:

1)Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted the casper-rw file.
Shutdown, removed CD, rebooted.
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.


2) Boot Live CD.
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
Select disk / syslinux / text.cfg and add "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

