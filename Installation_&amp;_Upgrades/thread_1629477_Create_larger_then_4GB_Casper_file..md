---
title: "Create larger then 4GB Casper file."
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by Eraknelo on 2010-11-23
Hello,

I have recently been experimenting with installing Ubuntu 10.10 on a USB/Flash drive, and have finally stumbled on the "Universal USB Installer", using a so-called "Casper" file for persistence.
Now I wanted to make the Casper file bigger, and found this article: [http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

I was reading it, and got confused at this part:
"This tutorial assumes that you have already created a bootable USB Flash Drive that contains Ubuntu or an Ubuntu based Live Distro like Xubuntu, Kubuntu, Linux Mint, Crunchbang, etc.  You should delete any existing casper-rw file from the drive to free up  all available space before proceeding.
1. Restart your Computer, booting from an Ubuntu Live CD" 
Do they mean that you have to make 1 flash drive that was created with the Universal USB Installer, and has a Casper file on it, AND you have a Live CD from which you operate?

If so, could I use one flash drive that acts like a Live CD (without the Casper file), and create another flash drive that DOES have the Casper file, and then boot from the one without, and follow the instructions? (Sorry for the complex sentence, didn't know how other to put it...)

Any help would be appreciated :-)

-René

---

### Post by garvinrick4 on 2010-11-23
I believe it said to boot off of live cd then insert usb with 4 gig of casper and resize your larger flash drive to that 4 gig in gparted after unmounting in gparted (cannot work on mounted drive) and then rest of instructions. Good luck partner.

---

### Post by Eraknelo on 2010-11-23
> **garvinrick4 said:**
> I believe it said to boot off of live cd then insert usb with 4 gig of casper and resize your larger flash drive to that 4 gig in gparted after unmounting in gparted (cannot work on mounted drive) and then rest of instructions. Good luck partner.
Thank you very much for your reply.
What exactly do you mean with "your larger flash drive"? It seems as if you&#341;e talking about 2 flash drives at this point ;-)

-René

---

### Post by garvinrick4 on 2010-11-23
From what I understand you are trying to make a larger than 4 gig of persistence drive.
You can make a 4 gig with startup disk creator in ubuntu so I just figured it was an 8 or 16 gig flash drive you were trying to use. Just one flash drive, making a 4 gig casper and then
making that larger with your website you gave.

---

### Post by Eraknelo on 2010-11-23
> **garvinrick4 said:**
> From what I understand you are trying to make a larger than 4 gig of persistence drive.
You can make a 4 gig with startup disk creator in ubuntu so I just figured it was an 8 or 16 gig flash drive you were trying to use. Just one flash drive, making a 4 gig casper and then
making that larger with your website you gave.
Ah! I see now. Thank you for your help! You have brought me great joy at 2:13 AM. Bless you :D

-René

---

### Post by C.S.Cameron on 2010-11-23
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
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.

---

### Post by Eraknelo on 2010-11-24
> **C.S.Cameron said:**
> Casper-rw files are FAT32 which limits them to 4GB.
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
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
Thank you so much! This is a lot easier then stated in that article :)

I'll try and get this to work then. I'll mark solved for now ;)

-René

---

### Post by Dingo_aus on 2011-11-17
Thanks for that, it really helped me out.

---

