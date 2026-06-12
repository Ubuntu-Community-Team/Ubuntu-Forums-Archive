---
title: "No longer able to boot from LiveUSB after dual-boot install + other boot issues"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by oogabubchub on 2013-08-23
Background information:
Alienware M17x-R1
2x 500gb HDD in RAID 0
New partition table:
[LIST=1]
[*]~100mb ext2 /boot
[*]~677gb ntfs Windows 7
[*]~315gb ext4 /
[*]~8gb swap
[/LIST]

I've had a dual-boot working on this machine for a few years already. I wanted to do a clean install of my Ubuntu partition with 13.04 and in doing so I chose to shrink the Windows 7 partition from ~900gb to ~677gb. After install, my Windows Boot Manager still said Ubuntu 12.04 and would then drop me into grub command line. When I tried boot-repair, I'd get a grub menu which would then drop to a BusyBox shell saying "Gave up waiting for root device." I believe this was originally caused by selecting a partition for boot instead of my RAID name (/dev/mapper/nvidia_XXX).

My latest effort has been to delete the partitions listed as 1, 3, and 4 and reinstall from LiveUSB, choosing /dev/mapper/nvidia_XXX as my boot loader location. Now, when I try to boot without the LiveUSB in, I just get a blinking white cursor and no boot menus whatsoever. When I try to boot with the LiveUSB in, I get a grub menu which seems to attempt to boot to /dev/mapper/nvidia_XXX4 for my Ubuntu partition. Unfortunately, the only thing in /dev/mapper is /control.

I'm lost now....did grub install on my LiveUSB unintentionally? How do I fix this?

---

