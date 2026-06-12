---
title: "macrium system restore failed"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by _Diego_ on 2014-02-12
Hi,
I've done a system image with Macrium Reflect Free v5 (updated) on a dual boot system with Mint Petra 64 bit and Seven x64 Ultimate installed on the same device (obviouslly different partitions :P). My configuration has an initial hidden recovery primary partition, a primary boot partition (ext3) of 500 mb, a primary ntfs partition for windows 7 and an extended logical partition on which I've put a ntfs data partition, an ext4 partition for linux Mint and a final swap area. The system configured in this way has no problems.
I 've done the system image only for the boot, the seven and the mint partitions.
When I try to restore it on a second machine (which is exactly as the original one, ie same manifacturer, same model, same devices on it, et cetera...) using either Linux Rescue CD (mounted with unetbootin on a USB Device) or Win PE Rescue CD (mounted with unetbootin on another USB flash Device) the process ends normally but when i reboot the system it fails even to show grub menu.

On the Macrium WIN PE Rescue CD there is an option to resolve boot problems (there isn't a similar one on the macrium linux rescue cd). If I run this option it detects only Seven OS (as it is a windows enviroment) and tries to restore MBR and so on, but the problem isn't solved. This way, running a live USB GParted shows the partitions correctly.

If I run a live session of Linux Mint Petra on a USB Flash Device, after having done a Linux restore GParted shows my entire HDD device as unallocated, but I can enter in all the partitions that are correctly been restored by Macriu,m. I can see all the files restored and even open and modify them.

I've also tried to use Boot-Repair with the common restore options from the live session. It replaces the Grub  in the Boot partition and afetr rebooting I can see the grub menu (I can see only Linux OS and no windows), BUT IF I MAKE THE CHOICE TO BOOT PETRA IT DOESN'T LOAD.

This is the report created by Boot-Repair.
[http://paste.ubuntu.com/6919496/](http://paste.ubuntu.com/6919496/)




Please someone help me!

---

### Post by fantab on 2014-02-12
This not Ubuntu related.

> Windows not detected by os-prober on sda2.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

You seem to have left over GPT data on the HDD. Remove it and hopfully your system will boot again.
Use [Fixparts]("http://www.rodsbooks.com/fixparts/"). to resolve the partition issue.

---

### Post by _Diego_ on 2014-02-12
thanks fantab, you can mark the post as solved :)

---

