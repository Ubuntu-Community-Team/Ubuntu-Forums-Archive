---
title: "Something wrong with k7 kernel. (Or my hands?)"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by fresco on 2005-08-10
Hey

Nearly I installed k7 kernel via synaptic. Installaton went fine, so I rebooted to look at it. First steps of booting went fine, but after that i got blue (don't mix it with Windows' :) ) screen with the message that my X server could not start. In the error message I found something like "No displays found" or "No active displays found", I can't remember well. So.... What is wrong? Here is my xorg.conf:



Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "SAMTRON"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "SAMTRON"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by tom-ubuntu on 2005-08-10
I think, nvidia driver does not need, or even work, if DRI is enabled.

---

### Post by 8FootSativa on 2005-08-10
[QUOTE=joeuser]I think, nvidia driver does not need, or even work, if DRI is enabled.[/QUOTE]

I've been having a lot of problems lately that I haven't before...like after getting the driver up and running I get a command line after bootup. This has made me reinstall about 6 times. This has never happened before, is the DRI issue a possible culprit?

---

### Post by xodeus on 2005-08-10
If you update your kernel, than you have to update our nvidia driver.
Change your default nvidia in this section to nv with your fav text editor:
```
Section "Device"
Identifier "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection
```
Then try to start your X engine. 
If your familiar with using console linux an lynx or links then just go to [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver) and follow the steps to update your nvidia driver.

---

### Post by fresco on 2005-08-10
regular i386 kernel does not have problems with X and works well....  :-k

---

### Post by tom-ubuntu on 2005-08-10
I am using the k7 kernel with my nvidia card aswell without any problem. It is important, that you install first your kernel, and then the nivida driver. Because this is loaded as kernel module. So if you switched your kernel, the you have to make sure that you also have the correct kernel-module loaded, otherwise it will not work. Link to ubuntuguide has been posted before.

And yes, the DRI in the xorg.conf can cause problems aswell. As far as I know, the nvidia driver brings its one DRI module.

---

### Post by theToolman on 2005-08-28
I think the difference is the the k7 kernel doesnt work with the *binary* nvidia driver, only the nv driver.  See [http://www.ubuntuforums.org/showthread.php?p=321813#post321813](http://www.ubuntuforums.org/showthread.php?p=321813#post321813)

---

### Post by angkor on 2005-08-28
[QUOTE=theToolman]I think the difference is the the k7 kernel doesnt work with the *binary* nvidia driver, only the nv driver.  See [http://www.ubuntuforums.org/showthread.php?p=321813#post321813](http://www.ubuntuforums.org/showthread.php?p=321813#post321813)[/QUOTE]

It does work with the Nvidia driver:

```
uname -r
2.6.10-5-k7
```

 ```
 glxinfo | grep direct
direct rendering: Yes
``` 

As stated before, install the Nvidia driver all over again after installing the new kernel, if that doesn't work directly just try and reconfigure the x-server.

---

