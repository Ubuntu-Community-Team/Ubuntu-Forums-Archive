---
title: "i Series access for Linux IBM 5250 natty"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by kaleem.sa on 2011-04-29
Hi,

My installation of IBM5250 was successful in Natty but i am unable to start the emulator.

below is the error i am getting.


Ibm5250
5250: [ INFORMATIONAL ]: Build Date: March 2008 (1.6).
5250: [ DEBUG ]: RegistryInfo::WhichKeyboard(): Could not open file /etc/X11/XF86Config or /etc/X11/xorg.conf.
5250: [ ERROR ]: 

    ***** There are no fixed or scalable fonts unavailable            *****
    ***** Session not starting. Please verify that the 75 and 100 DPI *****
    ***** fixed fonts are installed..                                 *****
    ***** The xlsfonts -fn "*-*-medium-r-normal--*-*-*-*-m-*" command *****
    ***** will list the available fonts.                              *****

Segmentation fault

Any body Please help me with this

Thanks,
KALEEM.
I installed all the dependencies like (libmotif3,libstdc++5,Ms fonts,)

---

### Post by n8bounds on 2011-05-09
I'm having the same problem. Working on it now.

---

### Post by n8bounds on 2011-05-10
> **kaleem.sa said:**
> Hi,

My installation of IBM5250 was successful in Natty but i am unable to start the emulator.

below is the error i am getting.


Ibm5250
5250: [ INFORMATIONAL ]: Build Date: March 2008 (1.6).
5250: [ DEBUG ]: RegistryInfo::WhichKeyboard(): Could not open file /etc/X11/XF86Config or /etc/X11/xorg.conf.
5250: [ ERROR ]: 

    ***** There are no fixed or scalable fonts unavailable            *****
    ***** Session not starting. Please verify that the 75 and 100 DPI *****
    ***** fixed fonts are installed..                                 *****
    ***** The xlsfonts -fn "*-*-medium-r-normal--*-*-*-*-m-*" command *****
    ***** will list the available fonts.                              *****

Segmentation fault

Any body Please help me with this

Thanks,
KALEEM.
I installed all the dependencies like (libmotif3,libstdc++5,Ms fonts,)

Got it. Basically, just install xfonts-100dpi xfonts-75dpi and reboot.

[http://n8.thruhere.net/blog/?p=1122]("http://n8.thruhere.net/blog/?p=1122")

---

