---
title: "Dual boot on pc having 3 partition"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by psvyas on 2007-03-29
I have 3 partition - 1 primary partition (FAT32) on which windows xp is present and 2 logical partition(one is FAT32 and other is NTFS) for storing files,pictures,etc.
I want to dual boot windows with ubuntu.
Do I need to delete 2 logical partition to create ext3 and linux-swap.
Please help.I am not sure about partitioning.

---

### Post by jms1989 on 2007-03-29
Well, you will need to make some space to install Ubuntu, 20Gb might be a good size for it. or you can install another hard drive and install Ubuntu on it. Set the new hard drive to master by setting the jumpers.

The ubuntu installer will install a new grub window that will have WinXP on it, this way you can dual-boot with Windows and Ubuntu.

On a side note; commercial computers are not fast enough to run multiple OSes at once. You can do it with emulators but you won't get the same performance.

-- jms1989

---

### Post by psvyas on 2007-04-09
Hi ,

I had partitioned my harddisk using sysrescuecd.It has gparted 0.3.4.I was not able to partition using ubuntu 6.06 lts live cd.It has gparted 0.1 old version.It did not allow me to partition swap and fat32 in the extended partion.
When I tried installing ubuntu using ubuntu 6.06 lts live cd, I was not able to manually edit partion.The system just just seems dead.I have 40 GB harddisk and 256 MB RAM.
So I chose first option ,i.e installer will make the ext3 and swap automatically.Everything went right.
Now the problem is ,while installing grub it did not ask me to install it on MBR or on partition.I think it got installed on MBR which I did not like.
When I reboot the system,GRUB loader is displayed and I am able to boot into windows and ubuntu which every OS I select.

1)How can I use NTloader to boot windows xp as well as ubuntu.
2) If I uninstall ubuntu I think I won't be able to boot to my windows xp as GRUB will also get uninstalled.

Please guide me how can I use NTloader to boot windows and ubuntu without messing up with my windows xp.

Prashant

---

