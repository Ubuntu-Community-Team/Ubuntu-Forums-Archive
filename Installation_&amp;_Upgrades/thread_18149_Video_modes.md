---
title: "Video modes?"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by Fluff on 2005-03-04
Hi!
Im new to linux!
I forgot to add more video modes in the installation so i now have 1024*768.

How do I add video modes?

//Fluff

---

### Post by p!=f on 2005-03-04
Warty:
```

sudo gedit /etc/X11/XF86Config-4

```
Hoary:
```

sudo gedit /etc/X11/xorg.conf

```
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34 [GeForce FX5200]"
        Monitor         "AOC HT731"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```
Look at the line "Modes".

---

