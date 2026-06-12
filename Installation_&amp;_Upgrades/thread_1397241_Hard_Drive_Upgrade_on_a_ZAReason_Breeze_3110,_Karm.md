---
title: "Hard Drive Upgrade on a ZAReason Breeze 3110, Karmic Koala"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by ionFreeman on 2010-02-03
Hi! I'm about to embark on this project, and I'm looking for tips. I have an 80 GB hard drive with about 30 GB of data on it. I'd like to replace it with a 2 TB hard drive.

What's the best approach?

I'm thinking I can either image the current drive, boot to a DVD and restore that image to the new drive, or get an enclosure and copy the drive.

---

### Post by Syke on 2010-02-04
Put the new drive in the system, and put the old drive in a SATA/USB enclosure [1]. Use Clonezilla [2] to clone the drive from the old one to the new one. Then use GParted [3] to resize the partitions to expand the 80 gig partions to fill the 1000 gig drive.

[1] Around $25 cost at any number of retailers
[2] Ubuntu variant recommended: [http://clonezilla.org/download/sourceforge/](http://clonezilla.org/download/sourceforge/)
[3] [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by tgalati4 on 2010-02-04
Or more simply put in the second drive and do a simple copy:

sudo cp /dev/sda /dev/sdb

Swap drives and use gparted to recapture the extra space.

You might need to so some UUID fiddling to boot into the second drive since the UUID's of the drives will be different.

---

