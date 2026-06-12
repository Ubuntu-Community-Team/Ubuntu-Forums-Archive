---
title: "Little bit more partitioning info?"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by God of the Meeps on 2012-07-29
Hey all,

I've had a decent amount of experience with partitioning my HD in preparation of Linux variants, but I've never had more than one Linux distro at any time.

I want to install Xubuntu and OpenSUSE, and I think that the most efficient way to do this would be to install Xubuntu and OpenSUSE on their own partitions, then have a separate /home partition (maybe a separate /boot for GRUB too?)

I've always just set the mount point of any linux distro to /, and I'm wondering if someone could give me a little more explanation on what changing the mount point does. Thanks in advance!

---

### Post by oldfred on 2012-07-30
I do not know OpenSuse, but each system will have its own / (root) partition. I now prefer to keep /home inside / so user settings are kept as part of system, but I move all data  and some of the normally hidden data folders into separate /mnt/data partition and link the folders back into /home. Not sure if that will work with OpenSuse as the UID & GIDs have to be the same for a data partition to work. Of course data in a NTFS partition has no UID or GID, sot that should work, if you also have Windows.

I would not make separate /boot. It just adds extra partitions and you cannot share /boot at all. 

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

You do have to decide which system's boot loader will be in the MBR and control booting. Does OpenSuse now use grub2 or still use grub legacy? Generally better to use grub2 to boot as it can find other installs and easily let you dual boot.

---

### Post by God of the Meeps on 2012-07-30
Ah, okay. Thanks for the help!

I don't want to install into the MBR, because I already have Mac OSX installed, and I'm afraid that doing so will make that partition unbootable. Would you still recommend against making a separate /boot partition?

Also, I'll probably be using Xubuntu's GRUB2 option, as OpenSUSE seems to still use GRUB.

---

### Post by oldfred on 2012-07-30
I do not know Macs, you can look in the Apple sub-forum for details.

---

### Post by God of the Meeps on 2012-07-31
Okay, thanks. Will do!

---

### Post by darkod on 2012-07-31
> **God of the Meeps said:**
> Ah, okay. Thanks for the help!

I don't want to install into the MBR, because I already have Mac OSX installed, and I'm afraid that doing so will make that partition unbootable. Would you still recommend against making a separate /boot partition?

Also, I'll probably be using Xubuntu's GRUB2 option, as OpenSUSE seems to still use GRUB.

I get the impression you are connecting having a /boot partition with the grub2 bootloader.

Separate /boot partition will only separate few basic boot files from the root partition, it will not install grub2 there by default.

You can keep your boot files on / (in other words without separate /boot) but tell grub2 to install onto the / partition. I guess you would need this to chainload grub2 from what ever bootloader is on the MBR booting the OSX. In general grub2 is not designed to be installed onto a partition but you don't have much choice. You would need to install the ubuntu and opensuse bootloaders on their root partitions, and then chainload from the main bootloader.

This is only in general. I don't know more details since I don't use OSX.

---

