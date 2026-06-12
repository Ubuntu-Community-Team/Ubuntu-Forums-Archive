---
title: "Video Issue With Intel D201GLY2 motherboard"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by thevenerablez on 2008-07-31
Hi,

I'm trying to run Ubuntu 8.04 on my Intel D201GLY2 (Mini-ITX)-based system. I have a widescreen monitor and would like to use 1680 x 1050 resolution. When I select this option in the Screen Resolution preferences, the monitor switches resolution, and I get nasty vertical banding spaced about 1 centimeter apart, with grainy pixels separating each band.

I looked into this and believe I need a third-party SiS964 driver. Does anyone know what this problem is? I would greatly appreciate any help you could give.

Thanks,
Zach

---

### Post by mishathegoat on 2008-08-31
[Bump] I'm having similar issues

---

### Post by mishathegoat on 2009-07-08
Even after a year I still have this problem...

[Bump]

---

### Post by Lovecraftian Horror on 2009-08-29
[bump]

Me three. I know this is really old, but I've had this board for about a year and a half with the issue. I'm pretty sure it's to do with the refresh rate. 

Have either of you experimented with the official Intel drivers?

---

### Post by Lovecraftian Horror on 2009-08-29
Go to the terminal, cd to your root directory.
```
sudo mousepad etc/x11/xorg.conf
```
Replace mousepad with editor of choice. 
My output:
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```
By simply adding 
```
Driver "vesa"
```
to the device section, I got rid of the vertical lines. Unfortunately, I'm now stuck with 1280x, 1024x, and 800x resolution. I have a 1440x900 monitor, so I'm playing with xorg.conf some more.

---

### Post by mishathegoat on 2010-02-28
Thank you lovecratian but it doesn't look like a xorg.conf file exists anymore on 9.10..

Anyone have any suggestions? This issue has been bugging me for 2 years now and I still haven't found a sucessful solution that will work on my desktop

---

