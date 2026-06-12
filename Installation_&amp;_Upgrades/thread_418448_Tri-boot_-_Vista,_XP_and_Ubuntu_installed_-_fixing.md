---
title: "Tri-boot - Vista, XP and Ubuntu installed - fixing GRUB?"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by JamesWx on 2007-04-22
Hi everyone

I've read through (and tried!) many forum threads, doc pages and blog posts and nothing seemed to be going right. I formatted the drive and set up partitions as so;

Vista - 50GB - NTFS
XP - 15GB - NFTS
Share - 10GB - FAT32
Extended partition with Ubuntu and Swap

```

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6629    53247411    7  HPFS/NTFS
/dev/sda2            6630        8541    15358140    7  HPFS/NTFS
/dev/sda3            8542        9816    10241437+   b  W95 FAT32
/dev/sda4            9817       11978    17366265    5  Extended
/dev/sda5            9817       11723    15317946   83  Linux
/dev/sda6           11724       11978     2048256   82  Linux swap / Solaris

```

I did Ubuntu first which booted nicely and works. I then installed XP to the D: drive, which boots nicely. I then installed Vista to C:, which also works and gives the option to get back into Windows XP at boot.

However, I can't boot Ubuntu. Seeing as partitions and settings are perfect on all OS' now, I wonder what's the best way to boot (Grub or Windows Boot Manager)?

I'd really appreciate any thoughts on the best way to get it back?

Unfortunately I had to install 7.04 in text mode, and can only live CD on 6.06. It sounds like installing Ubuntu might pick up the Windows boot thing and make it available in Grub which would be perfect - but I don't want to lose anything?

Many thanks everyone! 

James

---

### Post by eyelessfade on 2007-04-22
the problem is that windows is not nice. It see grub and overwrite it. You need to boot into your ubuntu using a live cd dapper should work or any other live cd. and reinstall grub. It should fix your problem.

how is a bit more complicated.

when you have booted into linux do a.

mount /dev/sda5 /mnt/test
chroot /mnt/test /bin/bash

you are now in your linux enviroment, and can reinstall grub. apt-get install --reinstall grub

hope it works

---

### Post by JamesWx on 2007-04-22
Hi - thanks very much for the quick reply.

I inserted the 6.06 CD and followed that through, and it all seems to work fine. When I reboot though it still goes to the Windows Boot Manager.

Is there anything else I need to change to make it use Grub instead of Windows Boot Manager?

Many thanks again - can't wait to start using Ubuntu again.

---

### Post by mlind on 2007-04-22
Do the steps eyelessfade said (chrooting to your existing install using livecd)
But instead of reinstalling grub package, do this
```

grub-install /dev/sda

```
This will install grub back into boot sector of /dev/sda.

To play safe, then invoke
```

grub-update

```

---

### Post by JamesWx on 2007-04-22
Thanks very much - that cured it. 

Thanks for all your help - now just to add Windows to the menu.

---

### Post by eyelessfade on 2007-04-22
didn't grub do it for you?

for only one windows it should be:

title           Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by mlind on 2007-04-22
My windows is on a separate hdd. Use the entry eyelessfade provided, it should work. Just add it after AUTOMAGIC KERNEL LIST entries.
This is what Ubuntu installer generated in my /boot/grub/menu.lst for some time ago.

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

---

### Post by grossaffe on 2008-02-21
I plan on installing Ubuntu on a computer that is currently dual-booting vista and xp.  last i read (which was a while ago) there were problems with grub tri-booting these three together because Vista Boot Pro didn't work with it or something.  so basically, if i were to install Gutsy Gibbon right now, would it have any problems setting up the boot-loader to work with all my OSes, or would it work straight from the installation CD?

---

