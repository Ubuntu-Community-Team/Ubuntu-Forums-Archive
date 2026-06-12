---
title: "dual boot system keeps restarting after booting windows xp"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Divermarv on 2007-09-05
I've just installed ubuntu 7.04 to dual boot with windows xp on my work desktop. I booted into ubuntu just fine, and then restarted and booted into windows xp just fine. But this morning, I thought I'd restart and boot into ubuntu for awhile, but my system just keeps rebooting. It appears that it restarts just after GRUB loads.

I did not get any indication that windows changed my MBR. Now as I don't have anything meaningful in ubuntu just yet, I'm reinstalling from the boot cd, but I'd sure like to get this dual boot thing working well. I'm really excited about trying out ubuntu! There may be a convert here!

---

### Post by wonk-o-matic on 2007-09-05
That's a tough one, since you (apparently) are getting nothing on the screen to indicate the problem.  

You may have bumped into a hardware problem, but it seems more likely to be a GRUB issue.  When I've had those, just booting from a CD and mounting the hard drive, then adding a blank line to the bottom of the /boot/menu.lst file has got me going.  

It's voodoo, shouldn't matter, but every once in a while a GRUB update will give me strange behavior.

---

### Post by Divermarv on 2007-09-05
Ok, I'm a complete newbie to this. I did what you said, but the file is readonly, and I'm not sure how to unprotect it. Besides, there was already a blank line at the end of it. Would I be better suited by trying to find a GRUB forum?

---

### Post by merlinus on 2007-09-05
A few ideas:

Check BIOS to see that nothing is set up to automatically boot xp.

You can edit /boot/grub/menu.lst by entering this in a terminal, after mounting ubuntu after booting with the live cd:

```

gksudo gedit /boot/grub/menu.lst

```

Post that file, and also results of:

```

sudo fdisk -l

```

-merlin

---

### Post by Divermarv on 2007-09-06
Just an FYI, I booted up into ubuntu to try this, and I got an error. I will do this again, and post the error, but unfortunately work got in the way. I'll get back to this as soon as possible.

Thanks

---

### Post by downset on 2008-05-20
hi merlinus,

i hope you could help me with my problem. my xp keeps on restarting.:( i'll post your instruction what you've said above this thread.

menu.lst
> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=18b2b70e-f282-413d-be39-520727386829 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=18b2b70e-f282-413d-be39-520727386829 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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

sudo fdisk -l
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        5100    20482875    f  W95 Ext'd (LBA)
/dev/sda3            5101       19457   115322602+   7  HPFS/NTFS
/dev/sda5            2551        3455     7269381    b  W95 FAT32
/dev/sda6            3456        5025    12610993+  83  Linux
/dev/sda7            5026        5100      602406   82  Linux swap / Solaris


the sda1 (with *) is my xp partition disk

thanks in advance. :)

---

### Post by downset on 2008-05-20
up for this thread.

---

### Post by nagao88 on 2008-05-23
a similar thing happened to me - at first, it was only occasionally when my computer would die when starting up, then this morning, i needed about 5 tries to start it! 

(it's exactly at the same point - after the grub screen.)

---

