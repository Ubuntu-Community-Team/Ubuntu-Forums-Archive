---
title: "GRUB Error 15: File not found"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Zarathu on 2008-01-28
Originally, I had one hard drive with Windows on a partition, Linux on another, Linux swap on the third, and another NTFS partition for Windows programs on the fourth.  They were in that order.

I used an app in Windows to remove both Linux partitions and drag my fourth one (the programs) over to sit right next to the OS's partition.  It was done successfully, and I mounted both drives under LiveCD to make sure all files were intact.

Naturally, I knew I was going to get an error 22 with GRUB upon booting, so I was going to use an Ubuntu LiveCD to reinstall GRUB.

```
ubuntu@ubuntu~# sudo grub
Probing devices to guess BIOS drives. This may take a long time.

grub> find /boot/grub/stage1

Error 15: File not found

grub>
```

lolwat????!11

Using an Ubuntu 7.10 CD, by the way.

I'm going to try using XP's "FIXMBR" in the recovery console.

[edit] FIXMBR worked. :)

---

### Post by lcdial on 2008-02-02
I had the same problem.  I determined that  Grub was pointing to the wrong Ubuntu partition.  So, from the grub loader, I edited the command to point it to the right partition.   Once I pointed to the right partition (in my case, hd0,1), all was well.   After booting, I was able to edit the grub boot menu and all was well.

---

