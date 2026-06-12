---
title: "Need help with setup ubuntu 7.10 problem with screen"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by moonscape on 2008-02-20
After starting installation after some time coming damage scren like if i put 1024x768 grafic mode in windows (monitor is old can be used with 800x600 and 60Hz only) I have tried to start  instalation in VGA-mode but problem is commig again. What can i do with  this trouble? Please help me:confused:

---

### Post by bwhite82 on 2008-02-20
Edit the file:

/etc/X11/xorg.conf

Under the section "screen" change the resolution to 800x600, get rid of the rest of the resolutions. Make sure under section "device" that the driver is "vesa". Save. Enjoy.

---

### Post by wpshooter on 2008-02-20
> **moonscape said:**
> After starting installation after some time coming damage scren like if i put 1024x768 grafic mode in windows (monitor is old can be used with 800x600 and 60Hz only) I have tried to start  instalation in VGA-mode but problem is commig again. What can i do with  this trouble? Please help me:confused:

If you are just now doing the installation of Ubuntu try hitting either the F4 or maybe F6 key at the initial Ubuntu boot screen menu and it should give you a choice of screen resoltions to install.

---

