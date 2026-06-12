---
title: "Raid1"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by Ane Lenstra on 2012-10-01
I want to setup RAID1 configuration but I already installed Ubuntu. How to setup this configuration now?

---

### Post by darkod on 2012-10-01
If you want to use software raid, this tutorial should help you:
[http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)

It's for 10.04 but the same would apply for later versions.

If you want to use fakeraid (bios raid), you can't transform from single disk into raid. You will have to copy any personal data, set up the raid which will destroy the current installation, and install again.

Note that for raid you need to use disks of identical size for best results.

---

### Post by Ane Lenstra on 2012-10-01
Thanks
 
I get to point 3. By using that command, I get the message that I don't have permissions to write on the disk. Used SUDO already, no result.
 
Also a message that DOS and Linux have other ways of reading a disk.
 
What should I do to avoid this?

---

### Post by darkod on 2012-10-01
If /dev/sdb is mounted, or if you are actually running your system on /dev/sdb, it would fail.

In that tutorial they are working under the assumption the system is on /dev/sda and the new disk is /dev/sdb. Make sure your case is the same. Also make sure you have not mounted /dev/sdb, any partition on it.

You can see mounted partitions (except swap) with:
df -h

PS. For step 3 you have other options too. They are trying to copy the partition table to avoid differences, but you can always simply create partitions on the new disk manually, just make sure the sizes are the same as the current disk, or the size is what you would like to use for the future raid.
Also, to change the partition type to 'fd', if needed, I find it much easier to use cfdisk and not fdisk.

---

### Post by darkod on 2012-10-01
When looking more carefully at the tutorial, it seems they are missing a very important step, copying the data. After creating the raid1 with only the new disk and mounting the raid devices, you need to copy the data from your current install so that when they reboot from the array, the system is there.

Otherwise if the array is empty there will be nothing to run.

---

