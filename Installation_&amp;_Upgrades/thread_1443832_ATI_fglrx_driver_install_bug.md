---
title: "ATI fglrx driver install bug?"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by quadproc on 2010-03-31
I have come across what appears to be a bug while I was upgrading the fglrx driver on this system and I am looking for any information or insight regarding the problem.

Summary: I was running version 9 of fglrx satisfactorily under Ubuntu 9.04 and I decided that it was time to go to ATI's latest offering which is their version 10.3.  I have a slightly modified xorg.conf file (the primary mod being the specification of a BusID for the primary graphics card in this HD4870x2 system).  So I uninstalled the version 9 ATI driver using the uninstall script that came with the driver and I verified that the driver was no longer in use.  Then I installed the ATI version 10.3 driver manually using their ati-driver-installer-10-3-x86.x86_64.run file, rebooted, and tried some of the graphics effects such as wobbly windows and rotating cube.  These did not work, and I found that glxgears would immediately die for a segmentation fault.  So I started looking for the problem.

I found that the xorg.conf file generally had two entries for each section, and that those two entries were identical.  I commented out the redundant entries, rebooted, and found that things were working properly.  Here is an example of one section taken from the current xorg.conf file wherein I added #s to "remove" the offending entries:
> #Section "Screen"
#    Identifier "aticonfig-Screen[0]-0"
#    Device     "aticonfig-Device[0]-0"
#    Monitor    "aticonfig-Monitor[0]-0"
#    DefaultDepth     24
#    SubSection "Display"
#        Viewport   0 0
#        Depth     24
#    EndSubSection
#EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
It looks to me like there are two bugs involved here:

1. The ATI installation software incorrectly modified my xorg.conf file, and
2. The X server ungracefully fouled up when it found redundant input.

Does anyone know if my suspicions are correct?  Would it be worth reporting these bugs to either ATI support or to Launchpad or to both?  Thanks.

quadproc

---

