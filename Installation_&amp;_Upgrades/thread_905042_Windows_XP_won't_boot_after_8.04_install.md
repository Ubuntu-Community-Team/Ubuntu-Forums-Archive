---
title: "Windows XP won't boot after 8.04 install"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by keegs454 on 2008-08-29
I've looked at some other threads to see if this problem had already been addressed, but I didn't find any that were quite the same. I'll try and be as specific as possible.

Installed Windows XP (SP1 - it's an old disc) on my 320GB HD. To begin with, for some reason the installer wouldn't recognize more than 130GB of space. I installed Windows, and later resized it to 200GB with a GParted live CD, leaving the rest blank for my Ubuntu 8.04 install. Windows ran fine even after the resize, and it recognized the change in HD size.
Then I installed Ubuntu, and had it install on the "largest continuous free space" on the hard drive, which was the 120GB I left unformatted. The install went smoothly, and Ubuntu restarted just fine, but when I restarted in XP it began to load, but the Blue Screen of Death popped up with a random error message, and I had to restart. I don't get why this is happening, because I've installed a dual-boot in the same manner before with no problems. What's going on?

Here's the details:
**from menu.lst**
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cd4d7148-0b2d-4fdf-92d0-81f6c8f67da4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cd4d7148-0b2d-4fdf-92d0-81f6c8f67da4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
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

###################################################

Here's the results of typing fdisk -l:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       38913   107772052+   5  Extended
/dev/sda5           25497       38362   103346113+  83  Linux
/dev/sda6           38363       38913     4425876   82  Linux swap / Solaris


Any ideas what to do? I don't know why it's being difficult like this.
Note - if need be, I can reinstall one of both OS's, but if there's a fix that takes less time, that'd be appreciated.
Thanks for the help.

---

### Post by Herman on 2008-08-30
> but the Blue Screen of Death popped up with a random error messageWhat exactly was the error message, often error messages contain useful information and valuable clues as to what might be wrong.
Try a file system check first, boot your Windows XP installation CD and run CHKDSK /R.
It is recommended in the GParted documentation to always run CHKDSK after resizing an NTFS file system with GParted.
> Installed Windows XP (SP1 - it's an old disc) on my 320GB HD.if the file system check doesn't help, maybe try shrinking it back to a smaller size like less than 127 GB and see if that helps.
I read somewhere that Windows XP only supports file system sizes up to 127 GB prior to SP2. I'm not sure about that but it might be true. 
Then install SP2, then try resizing back to a larger size. See if it boots.

---

