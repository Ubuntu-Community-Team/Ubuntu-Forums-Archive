---
title: "Grub finds Gentoo installation on second HD, but doesn't give that option on startup"
date: 2014-05-03
forum: Installation &amp; Upgrades
---

### Post by teacherjeff2 on 2014-05-03
I just performed a clean install of 14.04 to a desktop with three hard drives installed. The first HD is a working installation of Gentoo. The second is a single partition where I keep my multimedia files. The third is where I installed Ubuntu. When (from the new Ubuntu installation) I run update grub, it "finds" my Gentoo installation:

```
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Gentoo Base System release 2.2 on /dev/sdb4
done
```

But when I boot the system (choosing the disk where Ubuntu is installed as Boot device), I don't get the Gentoo installation as an option. (I can still boot Gentoo by choosing that disk for the boot device.)

Any ideas what I'm doing wrong, or failing to understand?

---

