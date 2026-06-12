---
title: "how to install Kubuntu to a different drive"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by chrisrodgers on 2011-07-31
Hi!  I have a PC that has several disk drives in it.  One disk has Windows 7.  Two disks are RAIDed (1) together for all of my digital media, etc.  The RAID controller is built into the MB and comes up in the boot before the point to choose to change bios settings.  Anther disk has UbuntuStudio installed on it.  The other disks are just storage.

I want to install Kubuntu on the same disk that has UbuntuStudio on it and add Kubuntu to the existing grub menu.  The disk is 1TB and currently looks like this (created this way by the UbuntuStudio install):
/dev/sdb1 - ext4 - .91TB, 19GB used
/dev/sdb2 - extended - 3GB, 3GB used
   /dev/sdb5 - swap - 3GB, -

When I go to install Kubuntu from a thumb drive, It offers me to use SCSI6.  That looks like 1 of the two disks in my RAID 1 array.  That is obviously NOT a good choice.  The window with the partitioning choice makes it look like a drop-down, but the SCSI6 disk is the only choice in the drop-down list.

Will I not be able to use the Guided repartition option?  I suppose I could shut down, unplug all other drives, then boot from the thumb drive... then it will have only 1 disk to choose from.  But if I want to reinstall, or if I want to install yet another flavor (maybe Xbuntu to see what it would look like if I want to put it on the kids' pcs), I don't want to always resort to juggling hardware.

If I go the Manual route in the install, it shows me all of the disks.  I see which one I want it on.  How do you suggest I repartition?  Since they (UbuntuStudio and Kubuntu) will not be running at the same time, can I reuse the Swap that already exists (sdb5)?  Or do I need a separate swap area?  To make the area for Kubuntu, do I shrink sdb1 and create an addtional partition as ext4 to hold kubuntu?  

Ideally, I would like it to finally look like this:
  UbuntuStudio - 200GB
  Kubuntu - 200GB
  Swap - 3GB (exists)
  (+ an additional swap if I can't reuse swap spaces)
  Remaining disk space as WORK (+550 GB)

Suggestions?

---

