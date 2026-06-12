---
title: "How to remove 'ctrl alt +' to get to login prompt?"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by ntu on 2005-10-06
I have installed Ubuntu 5.04 and ended with a 'fuzzy yellowish screen'. Hit ctrl alt + a few times and got to login prompt. Logged in and eventually corrected the resolution.

Now, at every reboot, I still need to do the ctrl alt + 's to get to the login prompt. How to eliminate this?

Advice appreciared.

---

### Post by MrCheese on 2005-10-07
[QUOTE=ntu]I have installed Ubuntu 5.04 and ended with a 'fuzzy yellowish screen'. Hit ctrl alt + a few times and got to login prompt. Logged in and eventually corrected the resolution.

Now, at every reboot, I still need to do the ctrl alt + 's to get to the login prompt. How to eliminate this?

Advice appreciared.[/QUOTE]

You can either hand-hack /etc/X11/xorg.conf or run 

**sudo dpkg-reconfigure xserver-xorg** (see [http://ubuntuforums.org/archive/index.php/t-37157.html](http://ubuntuforums.org/archive/index.php/t-37157.html))

in a console. 

If hand-hacking just delete the unwanted higher-res settings (eg 1600x1200, 1400x960) which are listed in the Screens section. The default res at startup is the first entry.

---

### Post by ntu on 2005-10-07
Thanks MrCheese. If I hand-hack is it reasonably easy to get hacked resolutions back in the future if I need them?

---

### Post by duminas on 2005-10-07
[QUOTE=ntu]Thanks MrCheese. If I hand-hack is it reasonably easy to get hacked resolutions back in the future if I need them?[/QUOTE]
Have you looked at the xorg.conf file?
What he is referring to is something similar to this:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Monitor         "15 COLOR"
        DefaultDepth    24
        ...
        SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768" "800x600"
        EndSubSection
```
I snipped a lot of SubSections out, but this should still show you what he means.
See the "Modes" line in the SubSection? He is saying simply to remove unwanted resolutions. Hence, adding them back in via hand-hacking is as simple as typing "AxY" again where appropriate. :)

You might find *dpkg-reconfigure xserver-xorg* easier, though.

---

### Post by ntu on 2005-10-07
Thanks for your post Duminas.

I tried **sudo dpkg-reconfigure xserver-xorg **but did not know what to enter in the boxes that came up, so I tried 
**/etc/X11/xorg.conf  **and got permission denied. 

I am new to Linux and do not know how to get to my xorg.conf file to look at it. 

Will need to do some reading.

---

