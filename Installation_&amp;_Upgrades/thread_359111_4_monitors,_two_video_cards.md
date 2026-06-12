---
title: "4 monitors, two video cards"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by pajamarama on 2007-02-11
I'm currently running XP with three 19" LG LCD monitors and one Sony 19" Multiscan CRT. I use the onboard ATI Radeon Xpress 1150 for two monitors and a PCI-E Radeon X800 for the other two.

Everything works great in XP so I'm certain that the hardware is functioning properly.

When I boot from the Ubuntu 6.10 live CD, I everything looks kinda crappy when booting as if it's not displaying as many colours as it should be as well as only displaying on two of my four monitors. Near the end of the boot process  all monitors go blank, I get the startup sound, and that's about it.

If I go into my BIOS and disable my PCI-E video card, I get the bootup graphics on the other two monitors (looking better). When booted, the monitors are in mirror mode, and I see no way to set it to landscape.

I would like to be able to have all four monitors working so I can set up a dual boot.

---

### Post by RandomJoe on 2007-02-11
I don't think you are going to be able to do that from the boot CD.  You will have to edit /etc/X11/xorg.conf to suit your particular installation and then restart X, which is a lot easier once installed.

I run a triple-head setup (with an unused fourth output) and yes, when you first install and get things going it'll only come up on one screen.  (Or mirrored on two, depending on the card.)  Once you get the base system running, you can reconfigure X.  Just exactly what you have to do will depend on your cards and I have no experience with ATI.  However, primarily you need to get the correct driver running (whether that be the default one, or the binary ATI one), get the PCI IDs for your video cards, then configure the screens.

The following is the relevant portion of my xorg.conf file for my nVidia cards:
```
Section "Device"
        Identifier      "card1fp1"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "card1fp2"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Device"
        Identifier      "card2fp1"
        Driver          "nvidia"
        BusID           "PCI:8:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "card2fp2"
        Driver          "nvidia"
        BusID           "PCI:8:0:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "center"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "right"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "left"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "spare"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "centerScreen"
        Device          "card1fp1"
        Option          "UseDisplayDevice" "DFP"
        Monitor         "center"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "rightScreen"
        Device          "card2fp1"
#       Option          "UseDisplayDevice" "CRT"
        Monitor         "right"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "leftScreen"
        Device          "card2fp2"
#       Option          "UseDisplayDevice" "CRT"
        Monitor         "left"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "spareScreen"
        Device          "card1fp2"
        Monitor         "spare"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Multi-Screen"
        Screen          0 "centerScreen" 0 0
        Screen          1 "rightScreen" rightof "centerScreen"
        Screen          2 "leftScreen" leftof "centerScreen"
#       Screen          3 "spareScreen" leftof "leftScreen"
        Option          "Xinerama" "true"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

```
You can get the PCI IDs by using 'lspci' and looking for the lines that mention video.  Mine are:
```
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0392 (rev a1)
0000:08:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0392 (rev a1)

```
Take the last three sets of numbers for your BusID, so one is 1:0:0 and the other 8:0:0.  Someone else I helped found that theirs had a hex digit but the xorg.conf file evidently needs decimal.  It didn't work when he used 0:f:0, but did with 0:15:0.

I seem to remember reading that some dual-head ATI cards will show two PCI IDs, one for each output, but that Linux only uses the first one.

---

### Post by veloce on 2007-02-11
dual head under ubuntu is not easy. i agree, trying to do it with a live CD would be a nightmare.

However, for ati cards there is a proprietary something called mergeFB for doing the dual head thing.  This is thought to be easier than xinerama which us plebs with other video cards have to deal with.

mergeFB has been referred to elsewhere in this forum.

---

### Post by newpants2003 on 2007-06-21
> **RandomJoe said:**
> I don't think you are going to be able to do that from the boot CD.  You will have to edit /etc/X11/xorg.conf to suit your particular installation and then restart X, which is a lot easier once installed.

I run a triple-head setup (with an unused fourth output) and yes, when you first install and get things going it'll only come up on one screen.  (Or mirrored on two, depending on the card.)  Once you get the base system running, you can reconfigure X.  Just exactly what you have to do will depend on your cards and I have no experience with ATI.  However, primarily you need to get the correct driver running (whether that be the default one, or the binary ATI one), get the PCI IDs for your video cards, then configure the screens.

The following is the relevant portion of my xorg.conf file for my nVidia cards:
```
Section "Device"
        Identifier      "card1fp1"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "card1fp2"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Device"
        Identifier      "card2fp1"
        Driver          "nvidia"
        BusID           "PCI:8:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "card2fp2"
        Driver          "nvidia"
        BusID           "PCI:8:0:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "center"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "right"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "left"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "spare"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "centerScreen"
        Device          "card1fp1"
        Option          "UseDisplayDevice" "DFP"
        Monitor         "center"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "rightScreen"
        Device          "card2fp1"
#       Option          "UseDisplayDevice" "CRT"
        Monitor         "right"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "leftScreen"
        Device          "card2fp2"
#       Option          "UseDisplayDevice" "CRT"
        Monitor         "left"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "spareScreen"
        Device          "card1fp2"
        Monitor         "spare"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Multi-Screen"
        Screen          0 "centerScreen" 0 0
        Screen          1 "rightScreen" rightof "centerScreen"
        Screen          2 "leftScreen" leftof "centerScreen"
#       Screen          3 "spareScreen" leftof "leftScreen"
        Option          "Xinerama" "true"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

```
You can get the PCI IDs by using 'lspci' and looking for the lines that mention video.  Mine are:
```
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0392 (rev a1)
0000:08:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0392 (rev a1)

```
Take the last three sets of numbers for your BusID, so one is 1:0:0 and the other 8:0:0.  Someone else I helped found that theirs had a hex digit but the xorg.conf file evidently needs decimal.  It didn't work when he used 0:f:0, but did with 0:15:0.

I seem to remember reading that some dual-head ATI cards will show two PCI IDs, one for each output, but that Linux only uses the first one.

what kind hardware are you using? you dont need twinview mode for triple?

---

