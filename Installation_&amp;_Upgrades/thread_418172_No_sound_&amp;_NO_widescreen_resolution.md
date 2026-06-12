---
title: "No sound &amp; NO widescreen resolution?"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by firingstone on 2007-04-22
I have just install Ubuntu 7.04 into My new computer with a samsung widescreen LCD monitor 940bw and a motherboard of intel 945gm, then I met two problems
1. no sound at all 
2. no widesceen resolution, I need a resolution of 1440*900, but it did not give me the choice.
anybody happened to have met the same problems?  Is there a way to fix it ?
thanks in advance .

---

### Post by ntetreau on 2007-04-22
As for the widescreen, install 915resolution, then go into your /etc/X11/xorg.conf file 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bak
sudo gedit /etc/X11/xorg.conf

go to the Screen section and change:

    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection

for     SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection

reboot, if you have a problem copy back the backup file

---

### Post by firingstone on 2007-04-22
Thank you, ntetreau I will try it now.

---

### Post by firingstone on 2007-04-22
NO... that did not work.
BTW,  [PHP]915resolution -l[/PHP] gives me this
[PHP]Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel[/PHP]

---

### Post by ntetreau on 2007-04-22
Okay, sorry, I haven't configured an intel in a while.  Try:

sudo 915resolution 5c 1440 900 32

Then, sudo 915resolution -l, mode 5c should now be with 1440x900 32 bits 

Keep the changed xorg.conf with your new resolution, restart, that should work!

---

