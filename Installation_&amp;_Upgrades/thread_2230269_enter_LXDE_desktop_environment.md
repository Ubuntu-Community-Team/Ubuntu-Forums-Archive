---
title: "enter LXDE desktop environment"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by nathanb2 on 2014-06-18
I was given responsibility for maintaining a Ubuntu intranet server and I know very little about Ubuntu and find command line challenging. Therefore, I installed the LXDE desktop environment via command sudo apt-get install lubuntu-desktop and rebooted the server. However, I don't know how to enter the desktop environment. A search online didn't seem to give much help. Can someone help out an Ubuntu-challenged person?

I am running Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-64-generic x86_64)

Thank you.

---

### Post by steeldriver on 2014-06-18
If you didn't install a display manager, then you should be able to start the desktop after logging in at the CLI using

```

startlxde

```

FWIW I personally would have installed lxde-core instead of the full lubuntu-desktop

EDIT: actually I'm surprised lubuntu-desktop didn't install lightdm and make the system boot straight to a GUI login greeter

---

### Post by nathanb2 on 2014-06-18
Thanks for the tips... Yes, I probably should have installed the core but I don't know any better at this point.
When entering startlxde, I get the following : 
Gtk-WARNING **: cannot open display:

X11 Forwarding is enabled.

Suggestions?

---

### Post by steeldriver on 2014-06-18
Are you trying to start an LXDE session over ssh by any chance?

---

### Post by nathanb2 on 2014-06-19
Yes, I'm accessing it with putty.exe via SSH. It's a virtual server on VMWare VSphere.

---

### Post by nathanb2 on 2014-06-19
Ah, when I open it via vSphere it goes directly to the desktop, cool. Thanks so much!

---

