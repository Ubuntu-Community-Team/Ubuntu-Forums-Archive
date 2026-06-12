---
title: "grub doesn't run after clearing CMOS"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by bernardfrancois on 2005-09-30
Hi,

I thought I had a hard disk problem, so I cleared the CMOS on my motherboard using the propriate jumper. Afterwards, it turned out that the problem came from two IDE devices being set as master.
Due to the clearing of the CMOS (I think), grub doesn't start any more and my computer boots to windows.

I have read the thread [http://www.ubuntuforums.org/showthread.php?t=64711](http://www.ubuntuforums.org/showthread.php?t=64711) , and I tried the solution in that thread (booting the ubuntu cd in rescue mode and running grub-install /dev/hda).
When I do that, I get a message 'The file /boot/grub/stage1 not read correctly.'

Can anyone help me to make the grub bootloader run again?

Thanks in advance,

Bernard

---

### Post by bernardfrancois on 2005-09-30
I also tried to make a grub bootdisk, as described here: [https://wiki.ubuntu.com/HowToMakeAGRUBBootFloppy?highlight=%28grub%29](https://wiki.ubuntu.com/HowToMakeAGRUBBootFloppy?highlight=%28grub%29)

After formatting the floppy with the ext2 filesystem, I'm unable to mount it. I get a message 'mount: /dev/fd0 has wrong device number or fs type msdos not supported' (allthough I succeeded in formatting it using mke2fs /dev/fd0).

Anyway, I'm tired of this, I will re-install ubuntu now. if anyone knows the solution to the above mentioned problems; I'm still interested, and prolly other people too...

---

### Post by az on 2005-09-30
You probably changes your drive settings and grub could no longer find stage 1.5.

Grub errors are usually bios-related, and not linux-related.  You have to make sure that if you make a change in bios, that the grub configurations (mappings) are changed and that bios can actually read the disks where grub is (LBA setting)

---

### Post by bernardfrancois on 2005-10-01
By clearing the CMOS, I set the BIOS to the factory defaults. However, I never changed a lot of stuff in the BIOS, so I don't know if the reset changed alot. Did the installation of grub change something in BIOS, which got canceled when I cleared the CMOS?

Is it possible that the MBR (master boot record) got cleared/overridden when resetting the CMOS?

---

### Post by mcduck on 2005-10-01
Propably you just have to set your hard disk mode to 'large' or 'LBA' in bios.

Clearing CMOS doesn't affect disk itself in any way, so it could'n have done anything to your MBR.

---

### Post by bernardfrancois on 2005-10-01
It's too late now, I already re-installed ubuntu. Maybe someone else still having a similar problem could try this in the future and post his/her comments here.
The motherboard I experienced the problem with was an AOpen AK77-8XN.

---

