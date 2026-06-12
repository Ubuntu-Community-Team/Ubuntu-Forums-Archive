---
title: "Windows Won't Boot After Fresh Ubuntu Install"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by Tsen on 2007-05-10
Alright.  I've searched around, and I've found a few threads with similar problems, but the solutions suggested there aren't working for me, and I don't think the problem source is the same.

I'd been dual-booting windows for a few weeks, but eventually I needed to resize my Windows partition to make space for some extra music I needed to move off of my external hard drive.  So I booted up with the Feisty alternate install disk, deleted my Ubuntu partition, resized the Windows partition, and created a new (smaller) partition that I installed Ubuntu onto.

Partway through the installer, it popped up a notification saying it had detected Windows XP (correctly), and said that if it was the only other OS on there, it would be safe to write GRUB to the MBR.  This was as I expected (I almost always install GRUB to the MBR), so I continued.

However, when I attempted to boot into Windows afterwards, I can select the Windows XP entry in the GRUB loader, but it gets stuck at a black screen with the text  "Starting up..." and won't go further.  

I suspect it has something to do with Vista--I installed it a while back, but I'd done two fresh format and installs of XP after.  The reason I still suspect it is because before resizing Windows this time, the entry in GRUB was "Windows Vista/Longhorn Loader" or somesuch like that.  So did Vista install a bootloader to the MBR that XP had still been using?  I really have no idea.

Anyway, I've tried reinstalling GRUB from a LiveCD, but it doesn't fix the problem.  I did a fixmbr from the XP install disk, but that doesn't work either.  Anybody know how to fix this?

Here's my relevant /boot/grub/menu.lst:

```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3fe39f9d-4b67-422c-a252-c21affb113d0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3fe39f9d-4b67-422c-a252-c21affb113d0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
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

---

### Post by Zelutos on 2007-05-10
Have you tried doing a clean install on that partition since you resized it? Everytime you resize a partition on a hard disk there is always the risk that data can be corrupted which could be causing you to have an error with windows itself rather than your MBR.

---

### Post by Tsen on 2007-05-10
Urgh...I hope not.  There's a lot of stuff on that partition I still need...
Well, time to break out the external hard drive again.

---

