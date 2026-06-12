---
title: "White Screen"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by raulcigil on 2006-08-17
To install my Ubuntu linux on laptop i make this steps:

1) Run Live CD Default Settings, and the screen of laptop turn on white color and the system hangs.

2) I try it again but i change resolution for 800x600x32 and runs de Safe GRaphics Mode. It loads ok , and i make the install (six simple steps).

3) Then i reboot and when i go to run my new SO, the screen goes to white screen and the system hangs.

4) I try it dkpg-reconfigure xserver-xorg (in recovery mode) many  times  an try with many drivers as "sis", "Vesa", "vga" and others.
My graphics it's a SIS630.

That I can do?
Thanks for all.

P.D. Excuse my poor english, i'm spanish.

---

### Post by taurus on 2006-08-17
It should be lower case v as in vesa, NOT Vesa...

---

### Post by raulcigil on 2006-08-17
i used dkpg-reconfigure xserver-xorg text interface for configure it.

i type it erroneously in the thread.

thanks taurus.

---

### Post by taurus on 2006-08-17
Look in your /etc/X11/xorg.conf to make sure it is actually used vesa...

```
more /etc/X11/xorg.conf
```

---

