---
title: "Why would the AGP Aperture affect Karmic but not Jaunty?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-05
In a 2.94 Ghz Celeron with the ATI/AMD Radeon 2600XT AGP8X card (This card is still supported by ATI), Mfg. is: "ati2mag_RV630,PCI\VEN_1002&DEV_9586"

To boot into live CD or installed, the BIOS setting of "AGP Aperture" must be set at 256 or greater.

Any ideas - is this a bug that needs to be reported?

---

### Post by emarkay on 2009-10-05
And why would a 512 Meg card NEED a bigger aperture?  Is Karmic calling for ALL 512 megs of VRAM for the boot screen???


Here's a good technical description of this:
[http://forums.techpowerup.com/showthread.php?t=2](http://forums.techpowerup.com/showthread.php?t=2)
and
[http://www.adriansrojakpot.com/Speed_Demonz/New_BIOS_Guide/AGP_Aperture_Size.htm](http://www.adriansrojakpot.com/Speed_Demonz/New_BIOS_Guide/AGP_Aperture_Size.htm)

---

### Post by emarkay on 2009-10-06
Bug report filed:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd/+bug/444824](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd/+bug/444824)

---

