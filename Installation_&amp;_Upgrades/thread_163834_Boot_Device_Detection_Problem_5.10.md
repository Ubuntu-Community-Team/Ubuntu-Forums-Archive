---
title: "Boot Device Detection Problem 5.10"
date: 2006-04-21
forum: Installation &amp; Upgrades
---

### Post by dblegend on 2006-04-21
Hello,

I recently installed Breezy 5.10 on my compaq 2175US laptop.  The laptop doesn't have a working CD drive, so I used a USB external drive to do the install.  Now, when I boot without the drive plugged in, I spend roughly three minutes in what seems to be some sort of infinite hardware detection loop, looking at the following screen:

Booting 'Ubuntu, kernel 2.6.12-10-k7 '
root (hd0,0)
    Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.7.12-10-k7 root=/dev/hda1 ro quiet splash
    [Linux-bzImage, setup=0x1c00, size0x134400]
initrd /boot/initrd.img-2.7.12-10-k7
    [linux-initrd @0x1b97f000, 0x560d87 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
Loading, please wait...

If I plug in the drive, the boot process begins immediately, otherwise, eventually the laptop gives up on the detection and starts the boot process.  Does anyone have any idea what I can do to fix whatever is causing this problem?  So far the only action I've taken is commenting the drive information out of the fstab, but that didn't help.  Thanks in advance.

Dave

---

