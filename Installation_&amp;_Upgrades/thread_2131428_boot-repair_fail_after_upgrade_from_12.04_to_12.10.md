---
title: "boot-repair fail after upgrade from 12.04 to 12.10"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by hazmat74 on 2013-04-01
Hello,
I have instability issues after recent upgrades (I don't know which ones might be responsible) in 12.04. I've checked my memory with memtest86+, scanned the hard disk, and checked for other possible hardware issues with lm-sensors. Nothing has come up. The failures seem to be related to graphics, but I'm not sure how. Compiz was crashing frequently, so I ran Ubuntu 2D hoping for some stability. That helped in the sense that X didn't fail completely. When the computer crashes some programs may still be up and running like firefox, but it isn't possible to do anything else at all. I don't think this is a hardware issue, because memtest86+ ran all night without any difficulty. When Ubuntu is running, the OS crashes somewhere just over 50 minutes with regularity, whether or not I'm logged into the Ubuntu desktop. Updating the kernel from 3.2 to 3.5 did not help. Neither did a fresh install of Ubuntu 12.04 from the live cd.
So the last thing I'm trying now is to install Ubuntu 12.10 fresh in place of 12.04, and hope that this can solve the problem. I've done this, but now it won't boot up at all. I've looked at the message boards and tried boot-repair, twice now, which did not work for me. [http://paste.ubuntu.com/5668730](http://paste.ubuntu.com/5668730)
I first selected /boot (/dev/sdb1) for installation of grub, and then /home (/dev/sda). I have also tried booting from grub-rescue prompt as described [http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash](http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash) but I can't get past the "ls" stage: every command I type returns either "error: bad filename" or "error: file not found".
I have an intel core i7 with 24G ram and an Nvidia GT200 GeForce GTX260 gfx card. If upgrading doesn't work the next step I am contemplating is to replace the graphics card, although I don't have any strong basis to believe that this is the problem.
Thanks for any help you can provide.

---

### Post by oldfred on 2013-04-01
I do not think Boot-Repair installs drivers for btrfs or xfs. You may be able to install those drivers and it will see partitions. But Boot-Repair will only really help if you cannot boot.

Have you installed the nVidia drivers?
And with 12.10 you have to install headers first.
 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)


BTRFS, not ready for prime time
 [http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
EXT4 Still Leads Over Btrfs File-System On Linux 3.8
[http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1)

Some i-series systems needed extra boot parameters.

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off and nomodeset
pci=nomsi  or  ACPI=Off
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w

Are you running Optimus? or dual video?

---

### Post by hazmat74 on 2013-04-01
I did install the Nvidia drivers when I was still using 12.04, and it did not lead to increased stability. I haven't even gotten there with 12.10, because I can't boot up. Based on your reply it seems I have two options, 1) format the /boot and root and /var partitions and change the fs type to something else (perhaps ext4?), followed by reinstall of Ubuntu 12.10 or 2) revert everything to 12.04 and perhaps troubleshoot Nvidia some more. Do either of these options sound reasonable? I simply chose the partitions and fs-types to mirror the existing system which has been very stable up to now.

---

### Post by oldfred on 2013-04-01
If you just want to experiment and have 25GB to play with, just do a full install to a new partition. All my installs are in 25GB partitions and I have data in separate data partitions.

---

### Post by hazmat74 on 2013-04-02
This instability was caused by two problems.

1) The root, /boot, and /var partitions were installed on a SSD which was failing.
2) The controller SATA port on the motherboard is probably also defective.

This morning after a reboot, the Bios was not detecting the presence of the SSD anymore. I booted into live CD, which was able to run continuously for greater than 3 hr. In this state, the SSD was still not detected. After moving the SSD cable over to the one remaining SATA port on the MB, I was able to see the drive again from the boot menu. I rebooted into liveCD, ran boot-repair advanced options to purge grub and reinstall grub on the SSD. I was then able to reboot into Ubuntu from the fixed SSD /boot partition, but the instability problem persisted.

Two potential mechanisms:
1) mysql tables, /var and /log are all on SSD drive
2) other users were using the SSD / for intensive data storage

Solution:
I am replacing the SSD with a spinning disk drive, where the newly-reinstalled Ubuntu will reside.

---

