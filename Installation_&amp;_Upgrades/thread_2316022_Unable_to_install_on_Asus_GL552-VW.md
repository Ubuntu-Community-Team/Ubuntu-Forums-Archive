---
title: "Unable to install on Asus GL552-VW"
date: 2016-03-04
forum: Installation &amp; Upgrades
---

### Post by samalex1014 on 2016-03-04
I've had Ubuntu installed on my last 4 computers, but it seems like each generation is making it more difficult.

Currently I've tried installing 15.1 and 14.0.4 LTS, and neither have worked.

I've focused more on 15.1 as it worked best on my desktop with Nvidia graphics, and my Asus has Nvidia GTX 960 M.  When I've tried booting to "Install Ubuntu", I get an ignoring BGRT error that I've read is just the startup graphic, plus a few errors such as Na caching mode page, and nouveau unknown opcode, at which point booting freezes.  I've attempted adding nomodeset to the start parameters at the Grub menu, but it gets another option or two through, and freezes again.

I'm booting from a USB and have Fast Mode and Secure Boot disabled, CSM enabled.

[Edit] I'm dual-booting with the Windows 10 that came with my computer.  I have 2 hard drives, one an HDD, the other an M.2 SSD with two partitions, which is where I want to install Ubuntu.  I haven't gotten to that point yet, but it's there in case it helps at all.

[Edit 2] When I choose either "Try Ubuntu without installing" or "Install Ubuntu", then I receive the following screen:

[     0.043200] Ignoring BGRT: invalid status 0 (expected 1)
[     3.978792] nouveau E[   VBIOS][0000:01:00.0] 0xf152[0]: unknown opcode 0x00
[     3.978813] nouveau E[  DEVINIT][0000:01:00.0] init failed, -22
[     3.978828] nouveau E[      DRM] failed to create 0x00000080, -22


When I press e at the Grub screen and add nomodeset so the params look like:

setparams 'Install Ubuntu' nomodeset

     set gfxpayload=keep
     linux     /casper/vmlinuz.efi   file=/cdrom/preseed/ubuntu.seed boot=casper only-u\biquity quiet splash ---
     initrd     /casper/initrd.lz

then I get stuck at the same screen that states:

[     0.043200] Ignoring BGRT: invalid status 0 (expected 1)
[     3.977836] nouveau E[  DEVINIT][0000:01:00.0] unknown indexed vga port 0x3744
[     3.977857] nouveau E[    VBIOS][0000:01:00.0] 0xb195[0]: script needs crtc
[     3.977874] nouveau E[    VBIOS][0000:01:00.0] 0xb195[0]: script needs OR!!
[     3.977903] nouveau E[    VBIOS][0000:01:00.0] 0xb195[0]: script needs OR link
[     3.977943] nouveau E[  DEVINIT][0000:01:00.0] unknown indexed vga port 0x3744
[     3.977960] nouveau E[    VBIOS][0000:01:00.0] 0xf152[0]: unknown opcode 0x88
[     3.977978] nouveau E[ DEVINIT][0000:01:00.0] init failed, -22
[     3.978010] nouveau E[      DRM] failed to create 0x00000080, -22
[     5.850971] sd 3:0:0:0: [sdc] No Caching mode page found
[     5.850990] sd 3:0:0:0: [sdc] Assuming drive cache: write through

---

