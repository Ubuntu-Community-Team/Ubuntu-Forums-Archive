---
title: "Grub chainloading truecrypt bootloader?"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by quark_77 on 2008-03-25
Hi All,

I've been reading [Here]("http://ubuntuforums.org/showthread.php?t=689579") that it is possible to use the truecrypt bootloader to chainload grub if grub stage 1 is installed to the /boot partition  and the required partition e.g. hd(0,3) is marked bootable.

My question is: can it be done the other way around? Is is possible to chainload the truecrypt bootloader from grub?

Thanks in advance for any info you have,

Quark_77

---

### Post by dstew on 2008-03-25
My guess is that it should work, if truecrypt starts with a master boot record boot loader that can be loaded by a regular BIOS. Chainloading is basically the same thing as what the BIOS does, it just loads a sector into memory and jumps to it. The only issue might be how the boot sector is set up. Usually, the boot sector has a block address that loads the rest of the boot loader. That block address has to be correct. So, you might need to install truecrypt to a partition, instead of the master boot record, if truecrypt will let you do that.

---

### Post by quark_77 on 2008-03-27
Hi dstew,

Thanks for that -- I don't know if it does. I did a bit of reading up, if I can put it onto the bootsector for the c: drive as opposed to the MBR itself, it should chainload.

When my extra stick of RAM arrives I intend to do a bit of experimenting with VMware, XP (with truecrypt) and Ubuntu, to see if it does work. Also, I've got the TC sources and am getting hold of the DDK for windows to build truecrypt with. 

I'll post back here when I've got something to report.

If anyone has any further details I'd be grateful. Failing that, does anyone know any good disk analysis utilities so I can see what's going on? 

Thanks,

Quark_77

---

### Post by gearond on 2008-05-16
I am going to try to do it soon. I plan on writing TrueCrypt's MBR to a small logical partition containing only the MBR. I'll then try to chainload it.

---

