---
title: "created linux partition on usb drive,now cant delete them"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by allsystems on 2010-12-16
I followed a user isntructions on how to install ubuntu ontot a usb drive using a live cd,part of this installation required making some partitions in ubuntu. I now load this usb in windows and it only shows as 900mb,which was the size of one of the partitions. How do I delete the partitions so the usb is back to normal showing the true size. I have gone back into ubunto live cd and deleted the partitions there but no luck many thanks

---

### Post by ajgreeny on 2010-12-16
Assuming there is nothing on the usb drive you want to keep, you should run the live CD, and then use gparted to delete all the partitions on the flash drive and then finally format the whole drive as fat32, or ntfs if you prefer.  By default, just about all new usb flash drives you can buy are fat32, so that is what I would use.

---

### Post by allsystems on 2010-12-16
can you give me a step by step instruction please,also what is gparted?no theres nothing on the usb I want to keep,just want it all to be deleted back to normal

---

### Post by allsystems on 2010-12-16
quick update for anyone going through same problem. Download and burn the gparted live iso file. Load up and then you have the options to easily delete the partitions,the usb is back to normal.Many thanks

---

### Post by anthr6x on 2010-12-16
go to system->administration->disk utility with the usb connected to the PC and there you get the option to delete the partitions.

---

