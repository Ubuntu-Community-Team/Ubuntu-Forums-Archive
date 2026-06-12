---
title: "[SOLVED] how to delete swap partition without screwing up grub"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by josephellengar on 2008-11-08
I recently figured out that my swap partition didn't work so I started using a swap file.  Now I want to get rid of it (the partition).  I deleted it with gparted and put the extra space into my ubuntu install, but then my grub got messed up.  I fixed it by putting back the partition and doing some other stuff, but now if I try to get rid of the swap partition I alway get a grub error 17.  Any suggestions?  Thanks in advance.

---

### Post by cariboo on 2008-11-08
Did you run update-grub after removing the partition?

Jim

---

### Post by josephellengar on 2008-11-08
> **cariboo907 said:**
> Did you run update-grub after removing the partition?

Jim

No.  lol  Is it that simple?  What does that do?

---

### Post by caljohnsmith on 2008-11-08
It might be that your Ubuntu partition number changed after you deleted the swap partition, so please post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there if you want.

---

### Post by josephellengar on 2008-11-08
Device Boot      Start         End      Blocks   Id  System
/dev/sda1       127202670   234436544    53616937+   5  Extended
/dev/sda2   *          63   127202669    63601303+   7  HPFS/NTFS
/dev/sda5       127202733   232508744    52653006   83  Linux
/dev/sda6       232508808   234436544      963868+  82  Linux swap / Solaris

and:

(I had to change the root for ubuntu and for the splashimage manually to hd0,4.  I guess that I'm going to have to change the root for recovery and memtest as well?)

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c260499c-b40a-48da-a8be-e88ae8b67d9c ro splash vga=normal  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c260499c-b40a-48da-a8be-e88ae8b67d9c ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-11-08
I was just thinking, have you made sure you don't have /dev/sda6 being mounted in your /etc/fstab any more? Make sure of that, and then I would go ahead and delete your swap partition again, and resize Ubuntu to use that space. If Ubuntu still is sda5, you should be just fine as far as booting goes. If Ubuntu changes partition numbers, then you will have to reinstall Grub to the MBR (Master Boot Record), and also change your menu.lst. Not too big of a deal. Let me know how it goes, and I can give you specific help with Grub if your partition number changes. :)

---

### Post by josephellengar on 2008-11-08
Thanks!  It worked this time.  I've tested all of my boot options and they all work.  Wow, this is the fastest I've ever been able to close a thread.

---

### Post by caljohnsmith on 2008-11-08
That's great it turned out to be so simple. Cheers and have fun with Ubuntu. :)

---

