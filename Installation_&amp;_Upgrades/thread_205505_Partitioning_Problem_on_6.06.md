---
title: "Partitioning Problem on 6.06"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by digi421 on 2006-06-28
I have an AMD Athlon64x2 currently running Windows XP. I have 4 S-ATA hard drives, 3 of which are in a fake BIOS-Raid pack. The 4th disk is my boot and system disk.
On this 4th disk, there is currently 1 partition, taking up half of the disk space.
On this partition is the Windows system
The remaining space (120GB) I wanted to use for the ubuntu install.
So I booted from the DVD and started the installer once the GUI had booted.
I choose the disk to which I want to install (/dev/sda4) and create 2 primary partitions (112GB for / as ext3 and 8GB for swap as linux-swap).
Then the installer does the partition changes but after I click install I get the error message that there was no root filesystem. I double checked that the 112GB partition was mounting as / (or at least it's designated to do so) and the small partition as linux-swap.
I don't want to touch the raid-pack since it's a fake BIOS raid0 and contains too much valuable data to lose through experimenting. I just want this one disk (/dev/sda4) to be available under linux. Oh and of course I want to be able to choose which OS to boot.
Did I miss something when creating the partitions? Should I create an extended partition and then in this extended partition create 2 logical partitions containing / and swap?

---

