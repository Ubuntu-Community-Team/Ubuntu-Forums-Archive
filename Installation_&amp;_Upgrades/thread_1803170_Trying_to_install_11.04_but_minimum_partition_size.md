---
title: "Trying to install 11.04 but minimum partition size is 49.6 GB of my disk drive?"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by skaldicpoet9 on 2011-07-12
Hello there, I just downloaded Ubuntu 11.04 today and tried installing it to my computer, however, according to the installer the minimum amount that I can resize the partition is 49.6 GB (of a 160gb HDD, with an existing Windows 7 partition). I don't need that much space though and was wondering if there were a way to lower the minimum partition size? The last version of Ubuntu I installed (10.10) allowed me to set my partition at 15GB no problem. What gives? I don't want to allocate that much space to Ubuntu and don't see why the minimum would be set that high. Is there any workaround to this?

---

### Post by mikewhatever on 2011-07-13
Perhaps it has something to do with your partition layout?
The minimum size for the root partition is now about 5GB, which is far less then what you get.

---

### Post by Quackers on 2011-07-13
Is this in Windows Disk Management screen?
Are you sure that's not the maximum shrinkage, rather than the minimum? You should be able to change the numbers yourself if you are reducing it.

---

### Post by Mark Phelps on 2011-07-13
Following up on what Quackers said -- are you sure you're not reading the minimum SIZE of the resulting partition? Win7 calculates how much it will allow you to shrink the OS and shows you the final SIZE of the partition.

You can enter any shrinkage amount LESS than the maximim allowed.  You don't have to shrink it that far if you don't want.

OH, and after you do the shrink, reboot into Win7 a couple of times to let the filesystem do any adjustments and settle down before you install Ubuntu.

And, if you have an optical drive, use the Backup feature of Win7 to create and burn an Win7 Repair CD.  This will come in handy later, should you need to repair the boot loader for Win7.

---

