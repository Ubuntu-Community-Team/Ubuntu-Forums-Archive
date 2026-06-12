---
title: "ATI video problem in Ubuntu 10.4 LTS"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by DMcCunney on 2010-05-19
I just upgraded from Ubuntu 9.10 to 10.4.  The target box is a Fujitsu Lifebook p2110 circa 2002, with an 876mhz Crusoe processor, 256MB of RAM, and a 40GB UDMA4 HD, multibooting Win2K Pro, Ubuntu, Puppy Linux, and FreeDOS 1.0.  The Lifebook has an ATI Rage Mobility M! video controller with 8MB onboard video RAM.  Ubuntu was installed from the MinimalCD, and uses Xfce4 as the default window manager.

The upgrade went smoothly save for Video.  The native resolution of the screen on the Lifebook is 1280x768 in 16 bit color.  Windows and Puppy both support it.  Ubuntu 9.10 did.  Ubuntu 10.4 thinks the best possible is 1024x768.

I haven't found an Xorg.conf file.  Does anyone know where the X configuration data is stored, and what I need to fiddle to get 1280x768 back?

Thanks in advance.
______
**Dennis**

---

