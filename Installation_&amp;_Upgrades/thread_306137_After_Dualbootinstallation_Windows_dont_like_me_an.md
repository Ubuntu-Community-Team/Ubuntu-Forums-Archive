---
title: "After Dualbootinstallation: Windows dont like me anymore..."
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by jo.angel on 2006-11-24
Hi all! I have just installed a dualbootsystem (windows xp prof, Ubuntu 6.06). Something is wriong with it...Grub seems to have installed nicely and offers me to boot windows xp. However, if i try to boot, Windows says something like: UUh sorry, I cant boot, This might be because of some software or hardware changes...It then offers me to try the alst functioning configuration, but all I get is a reboot... to my Grub menue

Thats what I have done:
First thing, I masd a partition (hda1 for windows, hda2 for ubuntu). The#n I made a Windows XP install. After that the Ubuntu install, wherby the installer used my hda2 to place my root directory in hda3 and my swap iun hda5. 

Check out my **fdisk**:
> fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1946    15631213+   c  W95 FAT32 (LBA)
/dev/hda2            1947        4742    22458870   83  Linux
/dev/hda3            4743        4865      987997+   5  Extended
/dev/hda5            4743        4865      987966   82  Linux swap / Solaris

And here a short excerpt from my  /**boot/grub/menu.lst:**
> title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

Any idea where the problem could be? Your help is greatly appreciated,
Cheers,

Jo

---

