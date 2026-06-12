---
title: "Problem installing from Samsung SH-S183 SATA DVD RW drive"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by JMMorris on 2007-06-17
When I try to install from a live cd in a Samsung SH-S183 drive I get the following messages at the prompt:
    (initramfs) [xxx.yyyyyy] ata5.00 failed to set xfermode (err_mask=0x4)
or
    (initramfs [xxx.yyyyyy] ata6.00 failed to set xfermode (err_mask=0x4)
The motherboard is an Intel D975XBX2. Any help would be appreciated.

---

### Post by LeighT on 2007-06-23
Yes I had similar problems installing from both a live CD and the alternate CD using a SATA LG DVD -RW, as I thought the problem is that the OS doesn't recognise the SATA CD-ROM. 
So I installed a IDE CD-ROM and Ubuntu ran OK and I was able to install Ubuntu from the live CD.
Ubuntu is now installed and it recognizes both the SATA CD-ROM. and IDE CD-ROM.
So it looks like the installer doesn't recognizes SATA CD-ROMs
So as a quick and dirty work around just install a IDE CD-ROM and boot from it.

---

### Post by stadt on 2007-06-23
I had too troubles to install Ubuntu from an SATA DVD (LG 30N) on an Intel P965 based Motherboard. 
Solution was to disable AHCI in Bios and revert to IDE. After installation AHCI can be enabeled again (absolutely necessary if you have a installed Windows with enabeled AHCI drivers, otherwise it won't boot) .

---

