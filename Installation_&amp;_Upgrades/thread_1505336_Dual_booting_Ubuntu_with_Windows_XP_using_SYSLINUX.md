---
title: "Dual booting Ubuntu with Windows XP using SYSLINUX"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by mrt_doulaty on 2010-06-09
I've a 100 MB FAT32 partition which is the first primary (and active)  partition of my hard disk.
I've installed SYSLINUX to that drive.
I've  another primary partition which I installed Windows XP to it.
I've installed Ubuntu 10.04 LTS.

I want  to have a boot menu using SYSLINUX to choose between Ubuntu and Windows XP.
I used chain.c32 and menu.c32. I can boot Ubuntu, but I can not boot my Windows XP.

My  syslinux.conf file entry for Windows XP is as below:

LABEL WinXP
COM32 chain.c32
APPEND hd0 2 ntldr=ntldr

But this does not work, failing with  "Failed to load the boot file" error.

What is wrong?

---

### Post by wilee-nilee on 2010-06-09
You might want to read this wiki.
[Wikipedia](http://en.wikipedia.org/wiki/SYSLINUX)

---

### Post by mrt_doulaty on 2010-06-09
Nothing there helps!

I've already tried too many things...

---

### Post by wilee-nilee on 2010-06-09
The first paragraph.
> SYSLINUX 

SYSLINUX is not normally used for booting full Linux installations since Linux is not normally installed on FAT filesystems. Instead, it is often used for boot or rescue floppy discs, Live USBs, or other lightweight boot systems. 

Does this make sense, maybe there is some custom way of doing this but you have XP and Lucid installed, if you just used grub you would have a working system.

To be honest I'm going to turn off the auto reply email, this is a waste of time.

---

### Post by mrt_doulaty on 2010-06-09
> **wilee-nilee said:**
> The first paragraph.
[quote]SYSLINUX 

SYSLINUX is not normally used for booting full Linux installations since Linux is not normally installed on FAT filesystems. Instead, it is often used for boot or rescue floppy discs, Live USBs, or other lightweight boot systems. 

Does this make sense, maybe there is some custom way of doing this but you have XP and Lucid installed, if you just used grub you would have a working system.I'm using a modified version of SYSLINUX, it checks something before the boot process begins. So I've to use SYSLINUX...

---

### Post by mrt_doulaty on 2010-06-14
I've just updated my VMWare WorkStation, the simple boot chaining is now working as desired...

---

