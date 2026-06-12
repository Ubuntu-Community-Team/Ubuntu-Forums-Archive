---
title: "copying data to other partition pre installation"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by JPMaximilian on 2006-11-27
What I'd like to do is resize my current 60 gig harddrive to two ~30 gig partitions, then copy over my files from the 6.06 partition I'm currently running to the second partition and then do a clean install of 6.10 on the origional partition.  I've resized the partitions using Gnome Partition Editor, but I'm unable to then mount that parition so that I can copy the files over.  

I get the following error in nautilus:

Unable to mount the selected volume
details:
error: device /dev/hda3 is not removable

error: could not execute pmount

Can anyone offer some assistance?  Thanks.

---

### Post by aysiu on 2006-11-27
I don't think you need to mount it if you use, for example, *dd* to copy the partition: ```
sudo dd if=/dev/hda1 of=/dev/hda3
``` You can also [use PartImage to copy the partition over](http://www.psychocats.net/ubuntu/partimage).

---

### Post by drphilngood on 2006-11-27
You can also do it all from within the Alternative Installation CD.

---

