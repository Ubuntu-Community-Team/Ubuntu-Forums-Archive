---
title: "Install into, and boot from Logical partitions"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Crossroads on 2008-05-15
[COLOR="RoyalBlue"]Can I install Ubuntu [7.10] into logical partitions and boot it from there?[/COLOR]

My current hard disk is as follows:
May 15 21:42:36 ubuntu kernel: [68.011695] hda: hda1 hda2 hda3 < hda5 hda6 >
with 3 primary partitions and 2 logical partitions, all for Windows use. I wish to keep Windows (sorry) and dual-boot Ubuntu.

I will use Acronis Disk Director to resize/move my existing partitions to free up sufficient disk space. 

If I use the Guided Install - use free space, I am hoping that the installer will create 2 more logical partitions, for / (root) and (swap), install Ubuntu into there and modify the MBR appropriately>

Or I could use the Manual Install and create three or four new logical partitions (/ (root), (swap), /home and one other perhaps), install Ubuntu into those partitions and modify the MBR.

Can someone confirm that this can be done?
Any reason why it would not work?
What problems might I encounter?

Thanks in advance for your advice.

---

### Post by oldos2er on 2008-05-15
Yes, Linux can boot from an extended logical partition. You could create the partitions before installing with this program:  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by mikewhatever on 2008-05-15
From what I saw in earlier versions, guided partitioning creates a primary partition for / and an extended one for swap. To be on the safe side, use manual partitioning. I can confirm Ubuntu installs and runs well on a logical partition, in fact, I seem to have a similar setup to that of yours. Good luck.

---

### Post by Crossroads on 2008-05-17
Thank you both, I'll give it a try later.

---

