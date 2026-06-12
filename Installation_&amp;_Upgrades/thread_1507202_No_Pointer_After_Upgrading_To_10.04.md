---
title: "No Pointer After Upgrading To 10.04"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by SteveDee on 2010-06-11
I've just upgraded a Compaq D510 from 9.10 to 10.04.

During upgrade I got a message:-
```

Missing Resources.
The NetworkManager Applet could not find some required resources.
It cannot continue.

```
However it did continue, and the system seems to work OK except the mouse pointer is invisible.

I can use <ctrl> to highlight where it is, and I can click on menus and run apps.

If I VNC in from another machine I can see the mouse pointer on the remote screen.

With at least one Theme/Icon/Pointer configuration combination I can get the pointer to appear after boot, but only by launching either Firefox or Gimp.

Your suggestions ladies & gentlemen please.

____________________________
Booting from 2.6.31-20 instead of 2.6.32-22 solves my problem.

---

### Post by azurehi on 2010-06-11
I had the same issue after either Upgrading to 10.04 or doing a fresh install.  After installation, I installed the Nvidia driver (96 in my case) and the pointer again became Visible.  Interestingly enough, I installed the first beta release of 10.10 and the pointer was there from the start.
NOTE:  After updating 10.10, the pointer had disappeared and I to install Nvidia 96 form Hardware Drivers.

NOW, I cannot get to desktop :confused:

---

