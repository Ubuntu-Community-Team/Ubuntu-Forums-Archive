---
title: "Moving root and /home to new hard drive"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Mercury_Alpha on 2010-03-29
I purchased a new hard drive, and I would like to move Ubuntu 9.10's root and /home partitions to it. But all the guides I've seen for this process seem to refer to GRUB Legacy, while I'm using GRUB2. I've Googled some discussion threads, but what I've seen so far looks kind of ridiculously complicated.

I'm also dual-booting with Windows 7.

---

### Post by 2hot6ft2 on 2010-03-29
Everyone seems to like clonezilla.
[http://www.clonezilla.org/](http://www.clonezilla.org/)
That will take care of the cloning the partitions part.

If you're going to have ubuntu on a drive separate from win 7 then you will need to find out if the win 7 drive will be loading first in the BIOS. If it is then you'll need to reinstall grub 2 to it overwriting the grub 2 that's already there so it points to ubuntus new location, that's all. **Unless** there's something else that needs to be done for a separate /home partition that I don't know about.

You'll want to get rid of the original ubuntu partitions otherwise you may boot into them by mistake or by default not to mention making grub confusing as to which / and which /home you're using.

Either way you'll need to reinstall grub 2.

See the grub 2 guide in my sig. below but here's the basics

Using Ubuntu 9.10 livecd
Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:
```
sudo -i
```
To find out your partitions run
```
fdisk -l
```
Use that info for the following
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
You'll want to install grub to the drive that is first in the boot order in the BIOS
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process and once you're back in ubuntu run
```
sudo update-grub
```
It will automatically find your win 7 and add it to the grub list.

---

### Post by Mercury_Alpha on 2010-03-29
Thanks for the quick and informative reply. I should have also added that I plan to remove the old drive, which is currently listed as SDA and is an old PATA. The drive I want to move everything to is listed as SDC is a SATA drive. I already have another SATA drive previously installed and listed as SDB, so I'm using 2 of 2 SATA connectors on my motherboard, an ASUS P4P800SE.

So I imagine that after I've cloned to SDC, I should shut down the computer, remove the old drive, boot up the Clonzilla LiveCD, and follow those terminal instructions you listed? Or do I need to remove SDB to get my new drive recognized as SDA?

---

### Post by oldfred on 2010-03-29
It may depend on how you have them plugged  in. One my machine the three SATA drives seem to be based on the order plugged into the ports - i.e. port 1 is sda etc. I have seen where then the PATA drives get promoted to be in front of the SATA.  If your drives get renumbered any grub or fstab entries that use sda will have to be changed or go back and change port plugged into. If you clone drive UUIDs should be copied and be ok, but if you just copy they may change also. Just be ready to update grub and fstab afterwards.

---

