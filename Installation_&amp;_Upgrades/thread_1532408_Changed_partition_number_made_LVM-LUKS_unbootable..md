---
title: "Changed partition number made LVM-LUKS unbootable. Please help."
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by f1r3br4nd on 2010-07-16
Hi, everyone. I recently set up a Windows machine to dual-boot with Ubuntu (LVM and LUKS) using the 10.04 alternate install CD. I then deleted a partition which changed all the other partition numbers. Now I am no longer being prompted for a password and the encrypted volumes are not being mounted.

Here is how the partitions were originally:

--------primary partitions---------
hd0,1: Dell recovery tools, primary
hd0,2: Windows, primary
--------logical partitions---------
hd0,7: /boot
(16G of free space)
hd0,8: an encrypted partition containing an LVM group that in turn contains volumes for root, home, and swap
(some more free space)
hd0,6: empty fat32 partition
hd0,5: NTFS partition containing a backup image of the Windows partition

Here is how they are now:

--------primary partitions---------
hd0,1: Dell recovery tools, primary
hd0,2: Windows, primary
--------logical partitions---------
hd0,6: /boot
(16G of free space)
hd0,7: an encrypted partition containing an LVM group that in turn contains volumes for root, home, and swap
(some more free space)
hd0,5: NTFS partition containing a backup image of the Windows partition

I tried going into console mode in GRUB and manually changing the partition numbers assigned to root. It boots into (hd0,6) but never asks for the password for hd0,7 and never maps it.

I also tried the instructions [here]("http://ubuntuforums.org/showthread.php?t=1205372") and [here]("http://ubuntuforums.org/showthread.php?t=611165") but in both cases only the two primary partitions, the boot partition, and the NTFS partition are showing up (as sda1, sda2, sda3, and sda5). I cannot do 'cryptsetup luksOpen' because there is no physical device to run that command on! 

I've never modified the LUKS/LVM partition itself and GRUB and various partition manager tools still see it, so I know it's still there, just being ignored by Ubuntu CDs (both live and alternative) while from GRUB I cannot decrypt it.

* What controls the number that GRUB assigns to a partition? Is there some way for me to force that number to change?

* I can get the kernel in the /boot partition to start, it just doesn't see the LUKS/LVM partition. Is there something I should change in the /boot partition so make it start doing so again?

* I expect to occasionally add, remove, and resize partitions in the free space in the future. Is there anything I should do to prevent a repeat of this problem the next time?

Thanks.

---

