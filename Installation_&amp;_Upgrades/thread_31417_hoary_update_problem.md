---
title: "hoary update problem"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by masther on 2005-05-03
Hi all,
I have just passed to the hoary of Ubuntu.
In the Warty, the X server works with XFree86 and my Dell LCD worked properly in its native 1280*1024 60Hz mode. Since i used the Hoary, the server used were the new xorg and it doesn't let me the 1280*1024 60 Hz choice. it obliges me to use this resolution in 75 Hz. All my trying to change it in the /etc/X11/xorg.conf or with xorgxfg doesn't change anything.

I use a Dell Dimension with a LCD : 

Section "Monitor"
        Identifier   "DELL E173FP"
 ### Uncomment if you don't want to default to DDC:
        HorizSync    31.0 - 80.0
        VertRefresh  56.0 - 75.0
        Option      "DPMS"
EndSection

a intel graphic card

Section "Device"
        Identifier  "Intel Corporation 82865G Integrated Graphics Device"
        Driver      "i810"
        BusID       "PCI:0:2:0"
EndSection

and this mode

        SubSection "Display"
                Depth     24
                Modes    "1280x1024"
        EndSubSection

but in the gdm : system >> preference >> screen resolution

the refresh rate only propose 75 Hz !!!

thank you in advance

---

### Post by pepejeria on 2005-05-03
I just had the same problem, i changed the 
 VertRefresh 56.0 - 75.0
to 

 VertRefresh 56 - 60

and now i have 60 hz refresh rate. Dont know if its the correct way to solve it but i have 60 hz now

---

### Post by masther on 2005-05-04
thanks for your
help but i put  VertRefresh 56 - 60 and it doesn't work, i can only access to 75Hz
i try also VertRefresh 60 and the xorg-server doesn't want to know !!!

any idea ?

---

