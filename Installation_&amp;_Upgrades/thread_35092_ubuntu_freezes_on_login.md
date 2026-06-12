---
title: "ubuntu freezes on login"
date: 2005-05-17
forum: Installation &amp; Upgrades
---

### Post by shady on 2005-05-17
Hi all,

after a fresh ubuntu (Hedgehog 5.04 [AMD64]) installation ubuntu freezes when I try to login or press on the "languages"/"session" options on logon screen.

I've tried to run dpkg-reconfigure xserver-xorg (with mostly defualt values) and got the same problem. 

any assistance would be greatly appreciated.

----- 
Athlon64 3000+ 
1GB DDR400 
Giga-byte x600pro 128MB

---

### Post by alastair on 2005-05-17
What graphics card?
And what driver in the /etc/X11/xorg.conf file?

Does it freeze if you replace the driver with "vesa"?

---

### Post by shady on 2005-05-17
FINALLY !! 

thanks alastair I'm writing this from ubuntu ... changed to vesa and everything's good

my card is Gigabyte Radeon x600 pro , and xorg  was set to ATI.

what now ? should I stay with vesa ? is there any thing else to check ? 

-----------------
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X600 (RV370)"
        Driver          "ati"
        BusID           "PCI:5:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-50
        VertRefresh     43-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon X600 (RV370)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
----------------

---

### Post by alastair on 2005-05-17
If you're not a gamer (like me), or into 3D apps, then you can take your time figuring it out. There's a chance that the card you have is too new, or not as supported with the open-source "ati" driver. Your best bet is to do some research and see if others have problems. I don't keep up.

Xorg has a list archived here :

[http://freedesktop.org/pipermail/xorg/](http://freedesktop.org/pipermail/xorg/)

A lot of ATI (mainly proprietary) issues are discussed here (on the Linux forum) :

[http://www.rage3d.com](http://www.rage3d.com)

If you cannot get the "ati" driver to work (not sure what relation this is to the "radeon" driver - renamed?) - then you could try the proprietary driver "fglrx". But ... be warned that ATI have a very poor record for support and configuration on Linux. They are painful.

---

