---
title: "Help with installation of Swap partition"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by Alexh830 on 2007-07-06
I have been trying to install the ubuntu on a my new hard 120Gb drive for hours. My problem is that when I get to the prepare partitions I create one larger partition (assign it " use as: ext3" form the drop down menu) and one smaller partition (assign it "use as: Swap" from the drop down menu). When I  click froward I always get the alert "You have not selected any partition for use as a swap space...". What am I doing wrong?
Thanks

---

### Post by dabl on 2007-07-06
OK, since you've already sunk hours into this project, spend 15 minutes more and make a GParted Live CD. Download the image here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Boot the GParted live CD, and make your partitions with that. If you are not dual booting with Windows, then here is a recommended partition plan:

/ = 10GB  (set the "boot" flag on this one)
/{swap} = 1GB
/home = all the rest of it

You won't actually assign the mount points with GParted -- just make 3 partitions of these sizes, and set the boot flag on the 10GB partition.  You don't need to format the partitions with GParted.

Then mount your Ubuntu Feisty _Alternate Install_ CD, and use "guided installation" to select the mount points for each partition, and format and install.  Guaranteed to work!  :popcorn:

---

### Post by Alexh830 on 2007-07-06
Thank you, it worked. I'll admit I was a little scared to take the jump into linux but with a forum like this and user that are quick to lend a hand. I am ready to go in head first. Thanks

---

### Post by dabl on 2007-07-06
Glad you got through it!

:guitar:

---

