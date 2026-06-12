---
title: "Dual-boot 32-bit with 64-bit Ubuntu 10.04: the 32-bit won't boot"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by jarmo3 on 2011-07-18
I recently decided to try Ubuntu 64-bit, and, after finding that I could not test it using Virtualbox, I successfully ran it from a Live CD. I next installed it alongside my Ubuntu 10.04.2 32-bit install, with both OS's utilizing separate \ and \home partitions (but not the same \ and \home, I created additional partitions for the new install). The two installs do utilize the same \swap and \boot, but I did not format the \boot during the 64-bit install.

Here is my problem: I can no longer boot the 32-bit install. I can still access that partitions and the data, but the grub bootloader screen takes me to the 64-bit install even when I select the partition which gparted confirms to hold the 32-bit install. I have been unable to correct this using either update-grub or startupmanager.

Since the 64-bit install is running smoothly, I am not terribly troubled by this situation, but I would like to do a more extensive side-by-side comparison before I stick with 64-bit over 32-bit.

Any suggestions?

---

### Post by miklcct on 2011-07-20
Can you please post the partition layout (sudo fdisk -l /dev/sd?) and /boot/grub/grub.cfg ? Actually, sharing /boot is not a good idea because the kernels will overwrite each other. I suggest you not using a separate /boot, boot into the Ubuntus and reinstall all the linux-* packages.

---

### Post by jarmo3 on 2011-07-20
Here is the result of sudo fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad35d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      487424   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              61         304     1952768   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3             305        8838    68542465    5  Extended
/dev/sda5             305        1277     7811072   83  Linux
/dev/sda6            1277        4316    24413184   83  Linux
/dev/sda7            4317        6041    13856031   83  Linux
/dev/sda8            6042        7014     7811072   83  Linux
/dev/sda9            7014        8838    14647296   83  Linux

```

And the grub.cfg is attached.

miklcct: I don't understand what you mean by > I suggest you not using a separate /boot, Are you suggesting that I create a new \boot partition for the 64-bit install? If so, I don't see how that will allow me to boot into the 32-bit install (the one that I currently cannot access) in order to reinstall the linux-* packages.

---

### Post by oldfred on 2011-07-20
Do not create /boot partition at all. Only very old desktops with 137GB boot limit and servers or server type configurations with RAID or LVM may need a separate /boot. Some new or unusual root partition formats that are not support well may also need a /boot.

The /boot has the grub & kernel files, so the 64 bit probably overwrote the 32bit versions.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by giannilmbd on 2011-12-30
Hi
Did you solve your problem?
I'm trying to have dual boot with both Ubuntu 32 and 64. But I cannot make grub work on the 32 version (it complains that the kernel should have been installed first)

---

