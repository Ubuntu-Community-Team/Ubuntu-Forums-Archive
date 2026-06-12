---
title: "Rearrange partitions before Breezy install."
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by aum11 on 2005-11-09
I wish to rearrange partitions before installing Breezy.  Due to unaccessible space on the harddrive, I need to relocate the current hoary Ubuntu partition so as to get contiguous space behind XP for more linux partitions....or can I simply move the Linux partition?

Very confusing....

Am I best to get a live linux containing qparted such as system rescue, or is there there a simpler way?

Thanks.

---

### Post by yesplease on 2005-11-10
See [http://www.ubuntuforums.org/showthread.php?t=88194](http://www.ubuntuforums.org/showthread.php?t=88194)

LIke Remmelas, I think it saves time when you just reinstall. However, if you decide to move your partitions, perhaps you can note the complete procedure because this question is asked often. 

With an install disk you also have the option to make new partitions and move data to them. (You cannot use gparted on mounted partitions, so that is where the live CD is usefull.)

---

### Post by aum11 on 2005-11-10
Thanks YESPLEASE.


Can I do rearrangement of the partitions when I load the install ISO, or do I need to get a live iso to rearrange before the install?

---

### Post by yesplease on 2005-11-10
You do not use the iso, but have to burn the install iso as an image.

With the install cd you can do a 'fake' install. This means that install will stop when the install disk sees that ubuntu is already installed. You follow the normal install procedure and maake your changes with the option 'manual partition'. Install breaks off but your partitions are changed. 

Read this whole thread: [http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652) . Be sure to leave your files on the partition, do not format them.

I still think it will save time when you just reinstall, but I wish you succes with this experiment.

You may be able to do this in rescue mode, but I can not help with that.

---

