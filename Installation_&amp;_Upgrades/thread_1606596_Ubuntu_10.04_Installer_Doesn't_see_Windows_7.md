---
title: "Ubuntu 10.04 Installer Doesn't see Windows 7"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by ajlane17 on 2010-10-26
I've searched the forums, internet, etc... and I can't seem to find anything on this.

I installed Windows 7 using ~70% of my available hard drive space, the other 30% is unallocated. there are two partitions, the 100MB 'System' partition and the NTFS one with Windows 7.

On my first attempt to install Ubuntu:
The partitions didn't look right. It detected two NTFS partitions, the first one of 100MB, and a second NTFS partition using ~30% of my hard drive, and 70% (presumably Windows) as unallocated. I decided to go ahead and try to install it over the 30% NTFS partition thinking that maybe the installer just didn't recognize the free space right or something, but after that happened, Nothing loaded and my Windows partition was trashed.

I wiped the drive, and reinstalled Windows again with the 70/30 split.

On my second attempt to install Ubuntu:
On step 4 of the installation process (partitions) it doesn't detect my Windows 7 installation at all. Instead, it says the disk is 100% unallocated.

Does anyone know why the Ubuntu Installer is not detecting my Windows partition correctly? If so, how can I go about getting Ubuntu to see it and install itself along side Windows?

---

### Post by ajlane17 on 2010-10-28
Nevermind, I found out what the problem was. It looks like my GPT was corrupt. I deleted it and created a new one and that fixed the problem.

---

### Post by oldfred on 2010-10-28
I thought windows would not boot from gpt unless you convert it to a hybrid mbr/gpt. Ubuntu works with gpt, but you need a bios_grub partition.

Disadvantages of hybrid gpt/MBR
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)
Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
Converting:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. may destroy all data per srs5694
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

---

### Post by ajlane17 on 2010-10-29
Hey thanks for pointing out those articles. It looks like they're definitely related to the problems I'm having.

I removed the partition table from the drive and created a new MBR. I then installed windows, then resized the partition. I installed Ubuntu, and it created an extended partition with two logical drives (ext4, swap) and everything SEEMED good. 

When I restarted the computer, I got a grub error (no such disk). It said that the prefix and root were set to(hd0,msdos5) so I tried setting them to just (hd0,5) and that didn't work either. Neither way allowed me to see the partition. 

After loading the live CD i tried to 'fix' Grub, but nothing I tried seemed to allow me to see any partition on reboot.

I started again from scratch and attempted to set up a hybrid partition, but I must have done it incorrectly as gparted couldn't see the windows partition again.

I'll read those articles over and try to figure out how I can get this working and follow up with my efforts.

---

### Post by oldfred on 2010-10-29
The new format grub2 uses is either gpt1 or msdos1 so it knows the difference between the two styles of partitioning.

If you had gpt, left over data may be an issue.
Remove old gpt info/convert post#24 by srs5694 :
[http://ubuntuforums.org/showthread.php?t=1560383](http://ubuntuforums.org/showthread.php?t=1560383)

If not using windows I think gpt is better as you do not have the extended & logical partitions. I converted one small drive just to test it and with the bios_grub partition it just works. You can read gpt drives from windows if NTFS but cannot boot them. So if a drive is linux only and larger it may be better to use gpt.

---

### Post by ajlane17 on 2010-10-29
It seems like that guy in the post you linked was having the exact problem I am having, I'll give that tool a shot tonight and post my findings. I really appreciate your help with this!

---

### Post by srs5694 on 2010-10-29
> **oldfred said:**
> You can read gpt drives from windows if NTFS but cannot boot them.

One twist on this: If the computer uses Extensible Firmware Interface (EFI) 2.x firmware (aka Unified EFI, or UEFI) rather than a conventional Basic Input/Output System (BIOS), Windows *can* boot from GPT. In fact, IIRC, Windows *requires* GPT in that case, although I'm not 100% positive of that.

To date, most PCs use BIOS, not EFI. A few boards offer the option of either, though. It's also possible to use something called UEFI DUET to get UEFI working as an add-on product on BIOS-based computers; however, this is rather tricky to do. Still, with hard disk capacities rising, I wouldn't be surprised to see a disk manufacturer release something based on UEFI DUET to let ordinary Windows users actually use their new big disks....

---

### Post by DualCore555 on 2010-11-01
> **ajlane17 said:**
> Nevermind, I found out what the problem was. It looks like my GPT was corrupt. I deleted it and created a new one and that fixed the problem.

Can you please help me how to delete the GPT and create the new one? Im having exactly the same problem and i have no other ideas.

---

