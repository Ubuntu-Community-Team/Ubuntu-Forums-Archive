---
title: "Dual screen fails... After update?"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by WardLoockx on 2008-01-30
Hello,

I'm using Kubuntu and yesterday I had some updates concerning KDE itself.. Dual screens always worked for me but when I booted this morning only one screen is working... 

I use Xranr for dual screen support 

```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2960 x 1200
VGA disconnected (normal left inverted right)
LVDS connected (normal left inverted right)
   1680x1050      60.0 +
   1280x800       60.0
   1280x768       60.0
   1024x768       60.0
   800x600        60.3
   640x480        59.9
TMDS-1 connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9
   1152x864       74.8
   1024x768       75.1     60.0
   800x600        75.0     60.3
   640x480        75.0     60.0
   720x400        70.1
TV disconnected (normal left inverted right)

```

I always use the following command (in autostart in kde folder), but when I do it manually it fails to and no error 

```

xrandr --output LVDS --left-of TMDS-1

```


The TMDS-1 is the working screen.

Somebody with the same problem? 

Thanks

---

