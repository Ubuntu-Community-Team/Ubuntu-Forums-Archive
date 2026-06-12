---
title: "Screen resolution lost every reboot"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by jodoj80 on 2007-10-02
Hi. I've a crazy situation with my screen resolution. Every time I restart the computer Ubuntu lost the screen resolution configuration and use the 800x600 resolution. When this happen I can't change the resolution, because I just show the 800x600 in the droplist. 

I just can change the screen resolution when I disable the nvidia accelerator from "Restricted Devices" and reboot the computer. Them enable it again. But, if I reboot the computer the screen resolution takes the 800x600 configuration.

I've a nvidia geforce 7300 le. I try to install the driver from the offical nvidia website. But, nothing happen.

The screen resolution that I'm trying to keep is 1280x960. I don't care more higher than that, but I don't want it less than 1024x768. I'm a novice configuring and installing repositories, so I'll apprecite a details procedure to resolve this situation.

Regards,

---

### Post by haden9 on 2007-10-03
Can you please post your xorg.conf file?

Also what brand and how big is your monitor?

---

### Post by Dixon Bainbridge on 2007-10-03
You can remove the other resolutions from xorg.conf file so that your desired resolution is the only one showing.

in a terminal:

gksudo gedit /etc/X11/xorg.conf

then go down to the bit where there are monitor resolutions listed (monitor I think, might be devices) and then remove all the other listed resolutions (the ones inbetween " " marks). Add your desired one if its not there.

Save and restart X - hit control alt and backspace.

log back in.

---

### Post by wolfen69 on 2007-10-03
> **Dixon Bainbridge said:**
> You can remove the other resolutions from xorg.conf file so that your desired resolution is the only one showing.

in a terminal:

gksudo gedit /etc/X11/xorg.conf

then go down to the bit where there are monitor resolutions listed (monitor I think, might be devices) and then remove all the other listed resolutions (the ones inbetween " " marks). Add your desired one if its not there.

Save and restart X - hit control alt and backspace.

log back in.

you dont need to remove all resolutions. as you can see in my attatchment, all you need to do is add the resolution you need. i added  "1440x900" to the beginning of the 24 depth mode.

---

### Post by ruz322 on 2007-10-03
> **Dixon Bainbridge said:**
> You can remove the other resolutions from xorg.conf file so that your desired resolution is the only one showing.

in a terminal:

gksudo gedit /etc/X11/xorg.conf

then go down to the bit where there are monitor resolutions listed (monitor I think, might be devices) and then remove all the other listed resolutions (the ones inbetween " " marks). Add your desired one if its not there.

Save and restart X - hit control alt and backspace.

log back in.

You might want to be careful doing that. It could be an error with his video card or video driver. That means that by deleting those resolutions you might cause the x server not to work at all because then there would be no usable resolutions.

---

### Post by Dixon Bainbridge on 2007-10-03
Yeah good point ruz. I had a similar problem to the original poster and fixed it with the way I suggested. But you are right, should have advised a backup of the xorg.conf as well :)

---

### Post by ruz322 on 2007-10-03
Yea, If it is just losing the resolution for some strange reason, then your way will work fine. Just make sure he backs it up and that would probably work.

---

### Post by jodoj80 on 2007-10-04
Thanks everyone for your help. 

The xorg.conf file is complete empty. I don't know if this is right. To access this file I open the terminal and wrote ```
gksudo gedit /etc/X11/xorg.conf
``` Like Dixon Bainbridge said in his post. If someone knows what kind of configuration that the xong.conf file should have, please let me know.

Regards

---

### Post by Masterj15 on 2007-10-04
their is suppost to be away were you can redo your xorg.config file. (i don't know. I use to know but I'm just getting back into computers. sorry):(

---

### Post by dabl on 2007-10-04
Assuming a _Feisty_ or earlier version:

1. Follow this guidance to install the Envy script installer, and use Envy to install the Nvidia driver:

[http://kubuntuforums.net/forums/index.php?topic=3086232.0](http://kubuntuforums.net/forums/index.php?topic=3086232.0)

2. After Envy is done and the xserver is restarted and you are logged back in, then open a console and

```
sudo nvidia-settings
```

open the "X Server Configuration" tab, click "detect displays", then set your resolution and refresh (I just leave refresh on "Auto"), and then click the "Save to X Configuration File" button on the lower right, and click "merge" and "save" on the little window that pops up, and you will be done, and those will be your default settings. :)


If you're running Gutsy, post back because there is a minor additional tweak needed to run Envy.

---

### Post by Dixon Bainbridge on 2007-10-04
Dabl's way is probably the way to go.

---

### Post by jodoj80 on 2007-10-08
THANKS EVERYONE!!!! specially to **dabl** for your short guide about this issue. I got some error as you said, but I just follow all the steps.

I'm going to write other post with every step that I did to fix this issue. To help other user with the same problem like mine.

---

### Post by ShadowMKII on 2007-10-13
Thank you very much! I was having the same problem, and this guide helped me out a lot! The only thing I have to do now is figure out how to replace the X configuration file when I click "merge" and "save!!"

---

### Post by murraj2 on 2007-10-14
I seem to be having this same problem. I just upgraded to Gutsy and every time I restart x-server or restart the computer it sets my resolution to 1024x800.

---

### Post by jodoj80 on 2007-11-30
Well. Let tell you that after I upgrade to Gusty my screen resolution never keep the configuration.  Every time that I update the Gusty I've to reinstall the Envy (*first uninstall the NVIDIA driver and then install it again*). I've to do this every two days approximately.

This is how looks like my "xorg.conf" file after I made Gusty update.
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Oct  4 10:33:51 PDT 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

I hope you understand that it's not fair doing this procedure every time Ubuntu lunch an update.

---

