---
title: "weird annoying GRUB problem"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by poo_22 on 2010-05-11
dear ubuntu forum, im trying to get my computer to dualboot gentoo and windows and i have a slight problem with grub (legacy) where i can still boot into windows, but i have to enter the command line in grub. grub does not see all three commands in my menu.lst!
when i press 'e' for edit it shows that under the windows 7 menu there is only root (hd0,1) and makeactive. its completely oblivious to the chainload +1 step.
i've tried putting the windows entry last, and all sorts of other things, but i can't get it to boot...
it should be noted that linux boots just fine.

here is my menu.lst:

```

default 1
timeout 5
#splashimage=(hd0,0)/boot/grub/splash.xpm.gz

#title Gentoo Linux 2.6.24-r5
#root (hd0,0)
#kernel /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 real_root=/dev/sda3
#initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

# vim:ft=conf:
title Windows 7
rootnoverify (hd0,1)
chanloader +1
makeactive
title Gentoo Linux 2.6.31-r10
        root (hd0,2)
        kernel /boot/kernel-gentoo-2.6.31-r10 root=/dev/sda5

```

here is my fdisk -l:

```

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15742   126447583+   5  Extended
/dev/sda2   *       15743       29663   111820432+   7  HPFS/NTFS
/dev/sda3           29664       29728      522112+  83  Linux
/dev/sda4           29729       30025     2385652+  82  Linux swap / Solaris
/dev/sda5               1        2550    20482812   83  Linux
/dev/sda6            2551       15742   105964708+  83  Linux

```

---

### Post by poo_22 on 2010-05-12
bump.

---

### Post by oldfred on 2010-05-12
Looks like a typo:
chanloader +1

Chainloader +1

---

