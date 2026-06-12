---
title: "Ubuntu Hardy 8.04 usb install (swap error)"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by willum1 on 2008-10-18
Hello all,

I am trying to install 8.04 onto a 16GB usb pen drive, i go through the normal install process, enter workstation and timezone parts.

I get to the partition options and select the usb drive and in the advanced section set the boot loader to the usb drive aswell.

The install appears to start, and partitions seem to begin, the ext3 partition gets to about 5% and then i get this error.

"The attempt to mount a file system with type swap in SCSI7 (0,0,0), partition #5 (sdc) at none failed.

You may resume partitioning from the partitioning menu"

I currently have ubuntu installed on an internal hard disk fine, and on another usb pen drive in persistent mode, but wanted a full install on a usb drive.

Can anyone help me with this?

Ps. on this drive i have managed to run a persistent mode install aswell.

---

### Post by a35077 on 2008-11-01
I have the same problem. Both automatic and manual configuration go wrong. I think it is related to the USB stick but it is not an error (i have several sticks that hold the same problem). Some other sticks work fine. 

What I also noticed is that I can format the stick (and make it booteable) in FAT32 but I can't format it NTFS. 
Low level format goes well. No errors while using it in FAT32.

Any clue's??

---

