---
title: "ASUS AH 3650 : (ATI) half of the memory accessible"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zika on 2009-03-17
in my log I found:```
[    0.789720] (II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
[    0.789730] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
```should I do something?

my /etc/X11/xorg.conf, now, is totally bare:```
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

are there any tweaks I could use now, with current state of xserver-xorg-video-ati?

---

### Post by taavikko on 2009-03-17
Check out the two man pages;

```
man ati
man radeon
```

the latter gives "VideoRam" which you could try...
I have no experience with ATI cards so...

---

