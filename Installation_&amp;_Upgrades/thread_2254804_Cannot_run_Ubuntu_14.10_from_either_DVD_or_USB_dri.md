---
title: "Cannot run Ubuntu 14.10 from either DVD or USB drive"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by rranger2 on 2014-11-30
I've run into an odd problem with launching Ubuntu 14.10. For some reason, it launches just fine from a DVD on one of my PCs (a six-year-old Dell Inspiron 518), but I can't get it to run on either a new Dell Inspiron 3000 desktop or on a Foxconn mini-PC (using either a DVD or thumb drive). 

To further add to the oddness, when I try to launch Ubuntu from either of the PCs with the issues, it gives a completely different start menu on the two machines, followed by a blinking cursor, and culminating with a blank screen. Can anyone tell what might be going on? This is pretty weird.

---

### Post by flaymond on 2014-11-30
Blinking and black screen? You might not 'burn' the .iso file in the proper way. Try UnetBootin (well working) to 'burn' it to your USB. So far, do you format your usb to FAT32 before you burn the iso file? You need to format it to FAT32. If you use CD, please check the CD if the CD broken or something. I don't use CD because the chance to success is lower than USB.

---

### Post by rranger2 on 2014-11-30
So, I took your advice, re-formatting the USB drive and then using the Pendrivelinux utility (I was doing all of this from Windows 8.1, and that's the Ubuntu recommended tool) to reformat and create a bootable USB drive. It had exactly the same results as my earlier efforts. In fact, I'm typing this from Ubuntu on the Dell Inspiron 518 that is the only machine on which this works.

I'd really like to get this working on my new Dell machine, so if anyone has insight into what is going on, I'd appreciate it. It launches the boot screen with the install options, then goes to black with no further activity.

---

### Post by sudodus on 2014-11-30
> **rranger2 said:**
> I've run into an odd problem with launching Ubuntu 14.10. For some reason, it launches just fine from a DVD on one of my PCs (a six-year-old Dell Inspiron 518), but I can't get it to run on either a new Dell Inspiron 3000 desktop or on a Foxconn mini-PC (using either a DVD or thumb drive). 

To further add to the oddness, when I try to launch Ubuntu from either of the PCs with the issues, it gives a completely different start menu on the two machines, followed by a blinking cursor, and culminating with a blank screen. Can anyone tell what might be going on? This is pretty weird.

A six-year-old PC is probably running in BIOS mode (not UEFI). I guess the new Dell Inspiron 3000 desktop runs in UEFI mode. I don't know enough about the Foxconn computer. The difference between them might be that the Foxconn runs in BIOS mode, which makes the start menu look differently, because the start-up processes are different (syslinux with BIOS, grub2 with UEFI).

The problems might depend of the graphics chips or wifi chips. Please describe the specifications of the computers as detailed as possible, at least

- Brand name and model (also for the Foxconn)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Please tell us also which version and flavour of Ubuntu that you are testing (Standard Ubuntu 14.04.1 LTS, 64-bits or something else).

This information would help us give relevant advice.

-o-

You can start browsing the following links (and links from them)

[booting with UEFI]("https://help.ubuntu.com/community/UEFI")
[UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295")[URL="http://ubuntuforums.org/showthread.php?t=2230389"]

Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it[/URL]

---

### Post by mörgæs on 2014-11-30
Have you tried booting with the **nomodeset** boot option?

---

