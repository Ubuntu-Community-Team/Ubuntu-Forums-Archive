---
title: "RAID1 issues"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by phroggelator on 2010-06-06
I have a freshly installed Lucid (on new disks). The disks are partitioned identically (naturally) and the installer works correctly. The problem is that when I try to boot off the newly installed disks, the RAID1 assembly fails. Instead of /dev/md0 through /dev/md5 being composed of /dev/sda1 and dev/sdb1 and so on, it joins the entire /dev/sda and /dev/sdb as /dev/md5 and tries to setup /dev/md0 through md4 as partitions of this /dev/md5 (ie md5p1 through md5p6 - it tries for md5p7, but runs out of space). Naturally as this is not how the device were built by the installer, the boot fails at this point.

I can use mdadm to remove the dodgy devices and then assemble the arrays using the --scan option and it gets it correct. Also if I boot off the rescue CD, this also gets it correct and the system boots as expected.

My question is this: What is different between booting the rescue CD (the same CD I installed from) and booting off the disk? Surely the kernel on the CD is the same as the one installed by the installer? Something must be different though to cause the raid module to mis-assemble the raid devices (it's definitely the module as you can see it go wrong on the console). I tried setting "raid=noautodetect" on the kernel command line, but it seems to ignore this.

Any thoughts about whats going wrong here?

---

### Post by phroggelator on 2010-06-24
Just to add a bit to this. I've tried the same thing with a new motherboard (I managed to brick the old one with a BIOS flash), but the problem remains the same. I'm now wondering if perhaps there is some sort of issue inside udev perhaps.

The other thing that occurs to me is to wonder if for some reason it needs  /boot to be on it's own partition. Is this still a requirement in Ubuntu? It's not for Fedora core and hasn't been for some years so I can't see why it would still apply to Ubuntu.

Anything from the crowd mind?

---

### Post by phroggelator on 2010-06-28
Solved! Well for me at any rate. It seems that the tools surrounding the MD stuff in Ubuntu are less than perfect and there are several threads here and there across many years that indicate this. There appear to be two main things people are saying that might fix the issue. Unfortunately they didn't for me but the solution is still related. All changes are in the mdadm.conf.

First is setting HOMEHOST in mdadm.conf. Apparently the hostname is used in setting the UUID, which is fine, except that while the system is still running from inside the initramfs, the hostname is not set and thus it doesn't recognize the UUID's as something it should auto-assemble. I set it HOMEHOST to "" as was recommended and reassembled the initramfs, but this did not result in a clean reboot.

Second is changing the auto option on the CREATE line in the mdadm.conf to "md" rather than "yes". Again after rebuilding the initramfs and rebooting there was no impact.

However at this point I reviewed the content of /proc/partitions (as used by the initramfs) and noticed that /dev/sda came up first. Given that the default DEVICE setting in the mdadm.conf tells it to scan /proc/partitions and assemble stuff based on what it finds there and /dev/sda is listed first and the borked result was that it assembled /dev/sda and/dev/sdb into a MD device with subpartitions....

I reset the DEVICE line to have the value "/dev/sda? /dev/sdb?" and it then booted normally. Whether or not the earlier two changes are required I'm unsure as I left the earlier two changes in place.

Important note! Apparently there was a bug whereby it didn't matter if you selected "boot degraded arrays" as an option, it always halted the boot no matter what. I did discover a few weeks a go that in fact one of the updates after the basic install reverses this and no mtter if you told it NOT to boot a degraded array it always did. This leads directly to it (in my case because of the borked array build discussed above) running fsck on the incorrectly assembled arrays, which directly destroyed that particular install....

---

