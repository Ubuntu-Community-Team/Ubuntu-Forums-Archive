---
title: "ATI radeon 7500 series with ubuntu 9.10"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by unkelmarkmark on 2010-02-06
So far everyone thats tried to help has mentioned modifying xorg.conf

On this installation, there is no xorg.conf file.

Anyone with video troubleshooting experience with ubuntu 9.10 ?

I cannot even get 800x600 16 colors displayed correctly

---

### Post by ajgreeny on 2010-02-06
If there is no xorg.conf simply make one with the command ```
gksudo gedit /etc/X11/xorg.conf 
```and the try filling it with your own version of this which is my xorg.conf for my ati 9200SE card, using the open source ati driver.  I have not copied all the comments at the top of my file as they do nothing. If this file exists, it is read and used by the system.

Use your own figures for resolution wanted and refresh rates and see how it goes.

> Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by Mark Phelps on 2010-02-08
Sorry if I'm telling you something you already know ... but ... don't fall for the temptation to download and force the installation of any ATI drivers.  There are none for Ubuntu 9.10 that will work with your card, and forcing such an installation will only hose up your display so that all you will see is a black screen with a blinking cursor.

---

