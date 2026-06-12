---
title: "[SOLVED] Upgraded from Feisty to Gutsy but still running Feisty kernel"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by davidkahn on 2007-11-06
The computer was running Ubuntu Feisty  7.04 AMD 64-bit version and we updated it by clicking on the "Upgrade" button in the Update Manager.  All seemed to go well, and the System Monitor now says that it is running  Gutsy.  However,  "uname  -a"  returns:

Linux CERTIBY1 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux

and "2.6.20-16-generic" is the Feisty kernel.

Yet,  "sudo do-release-upgrade" says that no new release is available.

The problem with this is that it is impossible to install/upgrade VMware  Workstation because the version of gcc is newer than the kernel.

Can you force an upgrade to the Gutsy kernel?  Any suggestions?

Thanks.

David

---

### Post by birdbrain on 2007-11-06
Have you rebooted?

---

### Post by davidkahn on 2007-11-07
Yes, I have rebooted.

Here's the odd thing, which I discovered after posting my question.  The GRUB boot screen lists only the 2.6.20-16 and 2.6.20-15 kernels as being available for booting, with 2.60.20-16 as the first (and presumably default) entry.  Yet  /boot/grub/menu.lst  lists the the correct kernel (2.6.22-14) as the first menu entry see below).  Could there be a configuration parameter somewhere the overrides  /boot/grub/menu.lst as GRUB's default configuration file?

Thanks,

David

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by davidkahn on 2007-11-08
The ultimate solution to this was to download and run Super GRUB  ([http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)). Super GRUB showed that the Gutsy kernel was on hd1 rather than hd0. So changing "root (hd0,0)" to "root (hd1,0)" allowed /boot/vmlinuz-2.6.20-16-generic to boot.

The only thing left to understand is how it is possible that the new kernel is on a different disk, as the two hard drives in this PC are in a Linux software RAID array (versus having a hardware RAID controller), and one would therefore expect that their contents would be identical.

---

### Post by luh3417 on 2007-11-10
Hi, I have the same problem. Can you tell me what file on which disk and partition you edited changing "root (hd0,0)" to "root (hd1,0)"

Thanks

---

### Post by davidkahn on 2007-11-12
The file you want to edit is /boot/grub/menu.lst.  Towards the end of it you will see two sections:

[INDENT]title        Ubuntu 7.10, kernel 2.6.22-14-generic
[COLOR=Red]root        (hd0,0)[/COLOR]
kernel        /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
[COLOR=Red]root        (hd0,0)[/COLOR]
kernel        /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro single
initrd        /boot/initrd.img-2.6.22-14-generic
[/INDENT]Change the two red text entries to "root        ([COLOR=Red]hd1[/COLOR],0)" and GRUB should boot the Gutsy kernel.  Frankly, I consider this a hack, as the next time your kernel upgrades, it will re-run the program update-grub, which will change this entry back to hard drive 0 (hd0).  I plan to report a bug with the software RAID that allows the kernel to be written  to one of the mirrored disks.

While you are editing menu.lst, you might want to consider setting the entry "fallback" to 2, which means that if the default entry (0, which means the first entry in the GRUB list) doesn't boot,  to attempt the third entry, which should be the the prior version of the kernel.

Regards,

David

---

### Post by doobydave on 2008-02-18
Hi.

I have same problem only on my laptop (with a single hard drive). The gutsy kernel doesn't appear on boot yet features in menu.lst

What should i do?


end of menu.lst :-

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c9a4cc8a-ec55-494d-add4-c6987a7d9dce ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c9a4cc8a-ec55-494d-add4-c6987a7d9dce ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c9a4cc8a-ec55-494d-add4-c6987a7d9dce ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c9a4cc8a-ec55-494d-add4-c6987a7d9dce ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
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

---

### Post by davidkahn on 2008-02-25
Try running:

   sudo update-grub

Then check that the Gutsy kernel is still listed in  /boot/grub/menu.lst

If it is, that implies that you have all the kernel files.  Then you will need to need to reinstall grub:

   sudo grub-install YourHardDiskDevice

The device is probably hd0, or if you know that it's something like /dev/sda1 you can use that.  After you do this try rebooting.

Good luck.

---

### Post by doobydave on 2008-02-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193098](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193098) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks.

I've posted a bug report on this as it became apparent that grub was still using the menu.lst from my ubuntu studio install (pre feisty>gutsy upgrade)

As a workaround, i have just pasted the new kernel entries in menu.lst (feisty>gutsy upgraded) into the menu.lst on the ubuntustudio partition.

---

