---
title: "Old laptop Lubuntu installation bug screen"
date: 2016-08-08
forum: Installation &amp; Upgrades
---

### Post by imasck on 2016-08-08
Hey guys! 

Im trying to install Lubuntu 16.04.1 LTS in my old laptop. But when I start the installation process or I chose "Try Linux without installing" I got this problem: 

[ATTACH=CONFIG]270625[/ATTACH]

Those are the laptop specs: 

Model: Acer ASPIRE 5520
Processor: AMD Athlon 64 x2 Dual-Core processor TK-57 (1.9 GHz, 2 x 256 KB L2 cache)
Graphics: Up to 895MB NVIDIA GeForce 7000M TurboCache
RAM: 2GB DDR2
Display: 15.4" WXGA Acer CrystalBrite LCD (8ms/220-nit)
Storage: 160GB HDD


Im trying to install it with a USB ISO image made with Rufus. I forgot mention, the USB works without problem in other laptops.

---

### Post by mörgæs on 2016-08-08
Hi, welcome to the fora.

Did you get the offer to install closed-source drivers during installation?

---

### Post by imasck on 2016-08-08
Yes I got the offer, but I dont check it because my laptop wasnt connected to internet. I will try again the installation and tell you the result. By the way, thanks for the welcome.

---

### Post by imasck on 2016-08-08
I have tried again installing with the "Third Software" option and I got the same result. Also I dont recieve the offer about closed-source

---

### Post by imasck on 2016-08-08
GOT IT! Just had to edit some lines in GRUB. 

Those ones:

```
[COLOR=#000000][FONT=&amp]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
#GRUB_GFXMODE=640x480[/FONT][/COLOR]
```


For those:

```
[COLOR=#000000][FONT=&amp]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=TV-1:d nomodeset"

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]GRUB_GFXMODE=1280x800[/FONT][/COLOR]
```


After that, just update my GRUB and REBOOT.

---

### Post by ajgreeny on 2016-08-08
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

