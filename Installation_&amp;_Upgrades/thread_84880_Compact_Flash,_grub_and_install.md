---
title: "Compact Flash, grub and install"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by ExemplarUbuntu on 2005-11-01
I have returned to the problem of trying to get a VIA mini-itx board to
boot Ubuntu from a Compact Flash card in an IDE adapter.

When I left this, I had run grub on the CF card but wasn't able to get it to boot.
Now when I try this.. I get the error:

>grub

grub>  root (hd0,0)
Filesystem type unknown, partition type 0x6

I believe it thinks the partition is FAT
I tried using mke2fs and fdisk to change the partition to Linux type but
the error remains.

The card work perfectly and is recognised at being ext2. I have also tried
another identical card.

How do I convince grub that this card has an ext2 partition ?

Peter

---

### Post by wossname on 2006-04-26
Booting from a PCMCIA card (or adapter) is not trivial, read:
[http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-4.html#ss4.4](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-4.html#ss4.4)

I qoth:
"Having the root filesystem on a PCMCIA device is tricky because the Linux PCMCIA system is not designed to be linked into the kernel. Its core components, the loadable kernel modules and the user mode cardmgr daemon, depend on an already running system. The kernel's ``initrd'' facility works around this requirement by allowing Linux to boot using a temporary ram disk as a minimal root image, load drivers, and then re-mount a different root filesystem. The temporary root can configure PCMCIA devices and then re-mount a PCMCIA device as root."

---

