---
title: "Kubuntu Screen Resolution Issue"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Buelldozer on 2008-10-29
I am using a 6 year old Toshiba Satellite Pro 6000 laptop and something is being detected incorrectly.

I'm stuck with 800x600 (or lower) resolution and a choice of two refresh rates: Slow, and slideshow.

To make it worse I have 2" black border all the way around the screen, meaning I have about 10" of usuable display. This is very aggravating to work with.

I tried hand editing the xorg.conf file like I've done for previous releases but this time it's ignoring my manual entries. I cannot find anywhere inside KDE that will allow me to fiddle with the hardware itself.

I've seen some Gnome solutions bandied around but nothing for KDE, and specifically nothing that addresses what to do when the software thinks it's smarter than the user and ignores manual entries into xorg.conf. (BTW, why is this even possible. Manual entries into .conf files should have the force of LAW on a *nix system).

Does someone have an idea what to do here?

---

### Post by 4Orbs on 2008-10-29
My Kubuntu 8.10 resolution problem was fixed by adding the below code within the Screen section of xorg.conf. Change the resolutions to your preferred values, the first entry becomes the new default. You can add a second subsection if you want to define another depth value with different resolutions. By the way, I'm using the stock graphics driver because nvidia has not yet released the legacy drivers update. In my case, this brought the login page and all users accounts desktops to the proper resolution.

```

SubSection "Display"
Depth 24
Modes "1152x864" "1024x768" "800x600"
EndSubSection

```

---

### Post by Buelldozer on 2008-10-29
Thank you for the reply.

I made your suggested edit to the xorg.conf file and there was no result.

Here is my current xorg.conf

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
DefaultColorDepth 16
    SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Any more ideas?

---

### Post by dentaku65 on 2008-10-29
What is your video device?

---

### Post by Buelldozer on 2008-10-29
The official Toshiba specifications list it as a Trident CyberAladdin-T UMA.

---

