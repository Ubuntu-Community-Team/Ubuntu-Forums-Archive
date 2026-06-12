---
title: "Transition from IDE Slave to SATA"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by eriqjaffe on 2008-07-12
I have recently come into possession of an 80gb SATA hard drive that I'd like to move my Ubuntu install onto.

ATM, I dual-boot with Windows, and Ubuntu is installed on the 40gb drive in the ATA slave position (here's the relevant text from my menu.list):

```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a1f1702d-5349-4457-b116-7e7fd57e8916 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a1f1702d-5349-4457-b116-7e7fd57e8916 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I'm not concerned with how to copy the partitions, I know I can use gparted, or clonezilla, or dd for that.  I just want to clarify - once I've transferred the data, all I'll need to do is edit the root & kernel lines in menu.list to reflect the new drive & UUID?  Am I thinking of this correctly?

---

### Post by logos34 on 2008-07-12
If you clone/image the partitions over, it copies everything, INCLUDING the uuids.  You won't even need to reinstall grub if you leave the arrangement as is.  The kernel lines in menu,lst, as well as the entries in /etc/fstab, do not need editing.  Just make sure to disconnect the old drive before you reboot.  Then format it before you hook it back up.  As long as the sata is in second position, and root is the first partition on the disk, 'root (hd1,0)' should work

---

