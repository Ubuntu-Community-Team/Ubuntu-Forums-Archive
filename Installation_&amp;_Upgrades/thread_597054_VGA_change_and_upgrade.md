---
title: "VGA change and upgrade"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by robytex on 2007-10-30
Hi,
I use 7.10 and all works fine.
But my VGA (on the motherboard) is not so good and I would like to upgrade my
pc with a new nVidia card.
It's possible to do this change without reinstall Ubuntu?
I know how to do this upgrade in Windows, but I'm a newby with Linux.
Someone can help me with a sort of step by step guide?
TIA

Robytex

---

### Post by confused57 on 2007-10-30
I just did the same thing a few months ago...was using SiS onboard graphics and installed a VGA Nvidia graphics card.  What I did was change the video driver in xorg.conf to "vesa" before installing the graphics card.  Some bios may require you to manually disable the onboard graphics, I was lucky that my bios automatically disabled it.

To change your driver to "vesa", open a terminal(Applications---Accessories---Terminal):
```
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
gksudo gedit xorg.conf
```

Change the video driver to "vesa", with quotes, then quit & save.

Install your video card & it should boot up using "vesa", then you can install specific drivers for the card.

---

### Post by robytex on 2007-11-06
thank you, it seems easy...I'll try

---

