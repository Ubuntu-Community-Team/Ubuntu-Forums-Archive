---
title: "Cannot install Lubuntu (or any other ubuntu based os), graphical issues."
date: 2015-07-06
forum: Installation &amp; Upgrades
---

### Post by spogghi on 2015-07-06
Good morning everybody. I'm here because I can't install Lubuntu and any other ubuntu derivatives on my pc , in dual boot with windows 7.

  
[LIST]
[*]Version of Lubuntu interested: lubuntu-15.04-desktop-amd64 
[*]PC specs: 
**CPU**: AMD FX-4100 (Zambezi 32nm Technology)
**Motherboard**: Gigabyte Technology Co., Ltd. GA-990XA-UD3 (Socket M2)
**Storage**: 149GB Seagate ST3160815AS (SATA)
**RAM**: 8,00GB Dual-Channel DDR3 @ 671MHz (9-9-9-24)
**Graphics**: Monitor: Acer P225HQ (1920x1080@60Hz)
**Graphic Card**: 4096MB ATI AMD Radeon HD 6570 (Sapphire/PCPartner) [connected to the monitor via DVI]
**Audio**: Dispositivo High Definition Audio (ID hardware: HDAUDIO\FUNC_01&VEN_1002&DEV_AA01&SUBSYS_00AA0100&REV_1002) 
[/LIST]
  
Today I've tryed to install Lubuntu, but after I choose the language  (italian), it came up with a strange graphical issue.
A few seconds I can see the loading screen of lubuntu, blue background with the icon and 5 circles loading, 1920x1080p resolution, then it disappears.
I can only see my  mouse moving but the rest is a bunch of big colored squared and pixels  floating around:[http://i.imgur.com/N9nNhHL.jpg](http://i.imgur.com/N9nNhHL.jpg)

I searched a bit but I really don't know how to do. Is my graphic card  supported? (I think yes basing on some wikis found on google [http://wiki.ubuntu-it.org/Hardware/Video/Ati/Radeon](http://wiki.ubuntu-it.org/Hardware/Video/Ati/Radeon))

Any help is appreciated :)
Thank you very much.

---

### Post by Bucky Ball on 2015-07-06
Welcome. Boot from the install media. When you see the purple screen with the icon at the bottom, hit any key. You should get to a screen with 'Try Lubuntu' 'Install Lubuntu' etc.

Hit the F6 key. From the options, choose 'nomodeset'. Proceed. Any luck?

---

### Post by grahammechanical on 2015-07-06
This link will show you some images. Work your way down to the section called Changing the CDs default boot options and look closely at subsection 6 - F6 other options. You are looking for that menu and you need to select nomodeset and then press Enter. follow that by pressing Esc to get back to the screen where you can run Try Ubuntu.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by spogghi on 2015-07-06
Thank you, it works. However (quite obviously) graphics are not in full resolution 1920x1080.

---

