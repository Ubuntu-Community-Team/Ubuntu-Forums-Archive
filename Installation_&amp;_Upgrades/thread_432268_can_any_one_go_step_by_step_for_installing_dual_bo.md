---
title: "can any one go step by step for installing dual boot?"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by willh on 2007-05-03
I wana dual boot xp and ubuntu will anyone help?

---

### Post by willh on 2007-05-03
btw im on the live cd if that helps

---

### Post by finalzero on 2007-05-03
Fairly straight forward but you will need to select the right option when you the screen asking you to configure your hard disk drive partitions.

If you have Windows XP installed on one drive and its using all of the space (including any free space) then you may be able to choose the option to auto-resize your partition and use any free space for linux - you will have the option to configure how much fee space to leave for Windows XP.

The other option is to manually edit the partition table however this really depends on how brave you feel and your knowledge of partition management.  The screen is not too difficult to navigate through however it can be a little daunting at first.

When you choose the manual option you will see a list of partitions the installer has found, if you only have the one Windows XP partition then you will see only that listed as a NTFS partition and then any free space after that.  However if your Windows XP is using the whole drive then you will have to resize the partition so I advise you to follow the step above i.e. to auto-resize the partition and let the installer do the work for you.

However if you have a second spare hard drive or free unused space then you can setup partitions here.  First take a note of the amount of free space available on the drive, it will show you in the list as unused and then the size in Gigabytes (GB).  Now you need to workout how much space to give each partition, for the simplest setup I recommend two partitions, one for the Ubuntu system and one for the swap space (all linux installs must have some swap space).

If you have 1GB of main memory or above then assign 1.5 to 2.5GB of space for your swap space, assign the rest to your Ubuntu install.  You will see a button at the top to allow you add new partition, click on this to display the add partition box.

You only need to complete two steps here, set the size of the partition, this should the maximum free space available minus the swap space e.g.:

20GB - 2GB = 18GB
so you would assign 18GB to this new partition

Next choose the file system as Ext3 and then hit ok to create this new partition, you should now see it listed below your Windows Partition.

Click add again, you will see that the box has already set the size to the remaining available space. Set the file system to linux-swap and then hit ok to create it.

Thats your two partitions setup, now you can continue. You may receive a message asking you to assign a mount point to the partition. Edit the first partition you created, you should be able to assign a mount point, choose the  /   symbol which tells Ubuntu to install th whole system into this one partition (easiest setup).  Now hit continue to carry on with the install.

The partition manager will format the drives and then start installing Ubuntu, when its complete you will be asked to reboot.  When your system boots up you will see the Grub OS menu, this menu will have some entries, one will be Linux and the last one should be your Windows XP partition.

Now you can dual boot.

---

### Post by kdarkentity on 2007-05-03
hey whats up man? i have a dual boot system set up to boot from xp and ubuntu edgy 6.10...which version do you want to install?...How large is your hard drive?...and how is your hard drive currently partitioned?

---

### Post by wearekosh on 2007-05-05
FYI
here is a cool video on dual booting
[http://video.google.com/videoplay?do...90811311898236](http://video.google.com/videoplay?do...90811311898236)

It worked for me but i did not do it exactly as they did it

I made a full backup of my XP drive and instead of installing XP as they do in the video i pulled the windows cd out before it started the xp install and then dumped my backup onto the drive.

And my reward was a dual boot Ubuntu and (my original) XP

hope this helps:guitar:

---

### Post by zvacet on 2007-05-06
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

