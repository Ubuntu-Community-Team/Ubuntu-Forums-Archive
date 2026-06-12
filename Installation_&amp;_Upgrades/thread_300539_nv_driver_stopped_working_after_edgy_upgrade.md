---
title: "nv driver stopped working after edgy upgrade"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by jabster on 2006-11-15
Hi.

I just upgraded from kubuntu dapper to edgy last night/this morning folling these directons: [http://kubuntu.org/announcements/6.10-release.php](http://kubuntu.org/announcements/6.10-release.php)

Upgrade seemed to go well...no errors...just some LC_ALL warnings during some program installations.

However, when I rebooted, X did not start. I get a no screens error found. This is with the "nv" driver. If I change the driver to "nvidia" X starts, but I only get 1024x768 resolution, whereas I get 1280x1024 with "nv" (side note: can someone explain that?).

Any ideas on what's going on here? I can understand "nvidia" not working...but "nv"?!?

If you need any additional info (xorg.conf or X-log) please let me know.

thanks,
john

---

### Post by jabster on 2006-11-15
Here's the relevant part of my X-log:
```
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(EE) Failed to load module "nv" (module requirement mismatch, 0)
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(EE) No drivers available.

Fatal server error:
no screens found
```

---

### Post by dblbogey on 2006-11-21
John, I'm having similar (I think) probs. Can you describe in detail how you changed the driver from 'nv' to 'nvidia'? Thanks, DOug

---

### Post by chartman59 on 2006-11-25
Had the same problem. Switching to nvidia worked for me... still trying to understand why, though. Here it how to do it: go to your command line, change to directory /etv/X11/, edit xorg-conf and search for the section with the graphics adapter (look for the string "nv") and replace "nv" by "nvidia", save the file and start up X again (using "sudo startx" for example.

---

