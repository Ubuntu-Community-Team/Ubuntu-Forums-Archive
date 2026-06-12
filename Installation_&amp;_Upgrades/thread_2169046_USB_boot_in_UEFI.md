---
title: "USB boot in UEFI"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by renato3 on 2013-08-20
Hi, I've read this tutorial:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And I've followed all instructions, but I don't get how I'm supposed to boot my USB pendrive. Ubuntu 13.04 is already in it, I created this bootable pendrive with Unetbootin. But when I restart my computer, the pendrive doesn't boot and my Windows 8 is loaded. I'm trying to install Ubuntu in dual boot with Win8 and I want to preserve my current UEFI boot partition. Could someone help me, please?

---

### Post by sudodus on 2013-08-20
64-bit versions work only in 64-bit computers. 32-bit  versions work in 32-bit and 64-bit computer with BIOS, but not with  UEFI. If you want to boot in UEFI mode and install your Ubuntu flavour  alongside Windows, you should use for example the **ubuntu-13.04-desktop-amd64.iso** directly.

That is a good wiki page (that you refer to).

Have you checked that the downloaded file is OK (with md5sum)?

You can clone the iso file with ***dd*** and make it work with UEFI (if you have problems with the Unetbootin method).

See the [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by sudodus on 2013-08-20
Or is the problem that your computer is not even trying to boot from the USB drive?

You need to press a button to let you select boot device, or you need to change the boot order in the BIOS menu.

You can usually see which button to press on the very first screen shown at boot.

But to get more specific help, please specify your computer: Brand name, model, cpu, ram, graphics card. And try also Boot-Repair and run the ***boot-info script*** [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)[URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by renato3 on 2013-08-21
Everything was ok with the ISO image and I downloaded the 64 bit version, but the USB image wasn't being booted. I solved by pressing F12 and specifying to boot from pendrive. Thanks for your help.

---

