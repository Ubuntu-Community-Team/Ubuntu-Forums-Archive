---
title: "Installation problem with HP Laptop"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by rebshalom on 2008-02-29
I have the following config:
Product Name  tx1320us  
Product Number  GS865UA#ABA 
Microprocessor  2.0 GHz AMD Turion 64 X2 Dual-Core Mobile Technology TL-60 
Microprocessor Cache  512 KB + 512 KB L2 cache 
Memory  2048 MB DDR2 (2 Dimm) 
Memory Max  4096 MB 
Video Graphics  NVIDIA GeForce Go 6150 (UMA) 
Video Memory  Up to 559 MB 
Hard Drive  250 GB (5400 RPM) (SATA) 
Multimedia Drive  LightScribe Super Multi 8X DVD±R/RW with Double Layer Support 

Using a live CD from Ubuntu, a get a blank screen and hang after an inital screen of rapidly scrolled messages,
I have used the CD to install in VirtualBox on this machine and as a dual boot on another (older) laptop. 
HP still firmoly maintains that they will not support linux in any way shape or form, so please help

---

### Post by °Spitfire on 2008-02-29
Hm, i got Ubuntu 7.10 i386 running on a HP DV6610em without any Problem the only hard thing to configure was the Broadcom wifi chip.

Tell us what version you are trying to install?

---

### Post by rebshalom on 2008-02-29
I am trying to install 7.10. As I said it installed perfectly under VirtualBox on this machine and as a dual boot on an older XP machine. I think I saw a BIOS error flash before the Orange bar but it went too fast to read

---

### Post by dstew on 2008-02-29
If the Live CD does not run you basically have two choices:

1. Try kernel parameters. You can add them to the end of the kernel line after pressing F6 at the opening menu. Commonly tried parameters are vga=971 vesa=force acpi=off noapic nolapic irqpoll. My guess would be try vga=971 or vesa=force first, because most likely the problem is with the video display adapter not being happy with the Ubuntu live CD driver.

2. Use the Alternate Install CD to install Ubuntu. It installs the same Ubuntu desktop, but uses a text-based installer that is easier on your system. It is especially good for laptops. You get it from the same Download Ubuntu page, just check the box below the Start Download button. Note: even if you get Ubuntu installed, there is a good chance you will have to do some work to get the display working properly. Post again for more advice if you get that far.

---

### Post by rebshalom on 2008-03-01
:) Thank you it appear the vga and vesa options did the trick. Hallelujah I am free of VISTA

---

### Post by rebshalom on 2008-03-03
I spoke to soon. I cannot get to any USB ports or the ethernet port. As a result I cannot get to the internet to do any maintenance downloads. I assume all other ports are also inoperable. Any suggestions?

---

### Post by dstew on 2008-03-03
So, did you complete the installation? If so, check the Restricted Drivers Manager in your System --> Administration menu. Maybe there are restricted drivers you need to get that hardware going.

If you don't find anything there, post to the forum the output of **lspci** and we can start to work on your hardware.

---

### Post by rebshalom on 2008-03-10
I finally got a dual boot with vista. The basics are working but not the bells and whistles (fingerprint reader etc.) I can live with what's there and say good riddence to Vista.
Thanks to all who helped:KS:)

---

### Post by Denbert on 2008-03-20
> **°Spitfire said:**
> Hm, i got Ubuntu 7.10 i386 running on a HP DV6610em without any Problem the only hard thing to configure was the Broadcom wifi chip.

Tell us what version you are trying to install?

Hi Spitfire,

Could you please send information on how you configured the broadcom wifi?

I'm having a dv6565eo machine.

---

