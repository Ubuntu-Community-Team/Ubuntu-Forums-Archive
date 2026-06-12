---
title: "Installing on USB not working.  3 times."
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by joehoward on 2010-12-14
After I accidentally broke my first successful install of 10.10 netbook edition on a flash drive, I have been COMPLETELY unsuccessful in trying to put it back on my flash drive.

I have a 4GB PNY flash drive that I have been able to boot from in the past
I want Ubuntu 10.10 installed on it so i can use my own customized OS on school netbooks

and i've tried 4 times to get something to boot up, each unsuccessful because it can't seem to read the Casper file.

Nothing I use seems to be able to create a working Casper-RW file

I've tried using the Universal USB installer from pendrivelinux.com as suggested by the Ubuntu download page.  It can't seem to figure out how to create a working persistance file
I've tried using the USB startup disk creator from a Ubuntu 9.10 boot disk.  That keeps stopping and saying there is some sort of error.

I've had a problem with the casper file [before]("http://ubuntuforums.org/showthread.php?t=1641643"), and someone mentioned I should use an ext3 instead.
Can somebody *please* help?  I am stumped.

---

### Post by C.S.Cameron on 2010-12-14
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

### Post by joehoward on 2010-12-15
Those directions worked perfectly, I am happily using a partitioned Flash Drive.

I think there was a problem with the disk image I originally downloaded, because when i got a new one, I didn't get the error.

Thank You very much C.S.Cameron, you have saved me much frustration:D

---

### Post by C.S.Cameron on 2010-12-16
Thank you for letting us know that it worked for you.

---

