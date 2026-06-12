---
title: "usb-creator: Creating a persistence file larger than 4 GB"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kenny_Strawn on 2010-02-21
In the USB Creator, how do I create a persistence file larger than 4 GB? I have a 500 GB hard drive, and want the rest of the space not taken by the ISO file extractions and bootloader to be taken up by casper-rw.

Yes, I want to be able to use the external HDD to be able to boot and be able to save everything the drive can hold.

---

### Post by cariboo on 2010-02-21
Why not just do a regular install and put grub2 on the mbr of the usb drive, then set usb as the first boot option in the bios. I just setup Lucid the same way, and can still boot my Karmic install when the Usb drive is disconnected.

---

### Post by garvinrick4 on 2010-02-22
There is not any way to make a Fat32 formatted flash drive using USB creator larger than
4 gig. Any larger and you must use ext3 or ext4 and have a /boot and a / and make a system
that it was intended for. 4 gig can make a nice little system but not using your /home for media. Excellent for an alternative Live CD and a whole lot faster.
 It seems in do time some company will come up with a way to have more than 4 gig persistence in a flash drive as the price of them keeps coming down and the sizes get larger and larger.

Sorry just realized it was a hard drive you were discussing I just assumed flash. Refer to cariboo907.

---

### Post by Kenny_Strawn on 2010-02-22
It is not a flash drive I am trying to use. It is an external 500 GB SimpleTech hard drive (Hitachi HDS721050CLA362) that attaches to the computer via a USB port. This is what I need help on.

---

### Post by cariboo on 2010-02-22
The usb boot cd creator, formats the flashdrive as fat32, it will do the same thing to your external drive. You won't gain anything from using that tool.

---

### Post by jocko on 2010-02-22
> **Kenny_Strawn said:**
> It is not a flash drive I am trying to use. It is an external 500 GB SimpleTech hard drive (Hitachi HDS721050CLA362) that attaches to the computer via a USB port. This is what I need help on.
Then just boot from a live cd, start the installer and, like in a normal installation, make sure you set up partitions and install to the correct drive and also that you install grub to the mbr of the same drive...

---

### Post by psyke83 on 2010-02-22
> **Kenny_Strawn said:**
> It is not a flash drive I am trying to use. It is an external 500 GB SimpleTech hard drive (Hitachi HDS721050CLA362) that attaches to the computer via a USB port. This is what I need help on.

Forget about the USB Creator tool, it's not designed to be used the way you want to use it. Linux (and therefore Ubuntu) can use a drive connected via a USB enclosure the same way as a regular IDE or SATA drive, as long as your BIOS is new enough to boot from USB. My Ubuntu installation is running off of a USB drive right now.

The only caveat during normal installation is that at the last step, you may want to click the "Advanced" button and change the location to install the GRUB bootloader from /dev/sda (your internal drive) to /dev/sdb (should be your USB drive, providing that only have one internal drive).

---

### Post by C.S.Cameron on 2010-02-22
For persistence larger than 4 GB using U-C you can make a casper-rw partition or casper-rw and home-rw partitions.

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar).
Create a 1.5 GB ext3 partition to the right of this, label it "casper-rw".
Create a partition in the remaining space and labeled it "home-rw" (optional).
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select minimum Stored in reserved extra space, (128 MB).
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk and delete the casper-rw file.
Shutdown, remove CD, reboot.
changes will be persistent.

---

### Post by Ibidem on 2010-02-23
What filesystem is the drive?
[4 gigs is max file size for FAT32]("http://en.wikipedia.org/wiki/FAT32#FAT32"), so that makes a difference.
If you've got that much space, I would suggest a full install.

---

