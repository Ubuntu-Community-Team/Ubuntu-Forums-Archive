---
title: "xorg.conf appears to be empty???"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by ccaazz on 2007-03-23
hello, i own an ati x600 video card, and have already found that it won't boot properly unless i change the drivers - (from ati to vesa).  

To do this i have to press: ctrl+alt+f1, once the xserver error appears, to enter the terminal.

From there on, i enter in: sudo nano etc/X11/xorg.conf

this should open the xorg.conf file, but when the file loads in nano, i see nothing at all?

does anyone know what the problem is here?

thanks!

---

### Post by ffxr on 2007-03-23
typo: your missing an /

```
 sudo nano /etc/X11/xorg.conf 
```

you ca browse to the directory and file manually as well using cd's and dir's

---

### Post by ccaazz on 2007-03-24
that appears to have fixed it! 

thanks!:)

---

