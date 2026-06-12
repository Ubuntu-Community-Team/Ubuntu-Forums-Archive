---
title: "Accelerated Graphics Driver stopped working after upgrade"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by NichtDu on 2007-10-30
Hi

After upgrading from 7.04 to 7.10 my desktop responds extremly slowly.

I remember when I first setup 7.04 it took me ages to get the graphics driver working - and in the end it worked but i didnt knew exactly what was the changeto make it working - but i didnt mind since i was happy everything worked. Additional problem with my Graphics Card was that with the fglrxdriver the cards fan was always running on max speed due to a known bug (R480)

So now we upgraded to 7.10 and we are back to the same Problem

Lets start with some core infos:

$ lspci  | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)]
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)] (Secondary)

$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

$ glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32

$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

Relevant xorg.conf parts:

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
        Load            "dbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)]"
        Driver          "ati"
        Busid           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
#       Option          "AGPMode"       "4"
#       Option          "AGPFastWrite"  "true"
#       Option          "DisableGLXRootClipping"        "true"
#       Option          "AddARGBGLXVisuals"     "true"
#       Option          "AllowGLXWithComposite" "true"
#       Option          "EnablePageFlip"        "true"
EndSection
Section "DRI"
        Mode    0666
EndSection
Section "Extensions"
        Option          "Composite"     "Enable"
#       Option          "Composite"     "0"
EndSection

I remember that i set some symbolic links in the /usr/lib folder to get it working but now cant find the relevant document again where that was explained.

Most guides nowadays tell me using the fglrx driver - which doesnt help as well and additionally still has the fan problem even though acceleration still doesnt work - and that the open source driver wont work for me due the output part about direct rendering - but i got it to work on 7.04 so i doubt that this card wont work in general im just missing something - maybe someone can give me a hint.

---

### Post by dacap06 on 2007-10-30
Upgrading from the Fawn to Gutsy would not necessitate a change in your X11 configuration file. Use your regular backup of your Feisty configuration (e.g. made as root in a shell, set to the root directory by issuing the command:  tar cvfz etc.tgz  etc), restore the tar file to the /tmp directory then copy /tmp/etc/X11/xorg.conf over /etc/X11/xorg.conf and restart the X server.

If you didn't make a backup of your configuration (shame on you!), then you might try installing the xdebconfigurator package and running it on the command line.  Don't forget to back up /etc/X11/xorg.conf first.  If you end up hammering it into something completely unworkable, at least that way you could easily restore the old configuration.

---

