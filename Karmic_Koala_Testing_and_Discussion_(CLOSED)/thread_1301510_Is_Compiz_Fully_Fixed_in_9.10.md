---
title: "Is Compiz Fully Fixed in 9.10?"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FirstByté on 2009-10-26
I'm having GDM issues which I suspect is stemming from Compiz.

I'm online now using LiveCD.

On my Koala Karmic, I have compiz's extra effects enabled. I was trying to calibrate my battery a while ago, so I set my battery power management to suspend when battery is critically low and disabled all the rest features. Screensaver set to max (2hours). But I forgot to return the settings to normal after calibration.

Thus my system once shutdown after a critical battery low level. At bootup, I noticed some issues (errors flashed) about DRM during boot. But it went on smoothly till login screen. When I entered my login details it logs-in but turns ALL-WHITE but my mouse icon remained normal.

I tried reboot and it was fixed, so I never bothered. A while ago, I let my system to play some little B.Ball, getting back, the system was critically low on battery again.

I plugged it in, restarted my system, it logs-in as usually BUT to the same white screen: only the mouse was normal. In both occurrences, the sound was okay. I even tried the 3D cube effect of compiz, it works but only showing a WHITE CUBE...

Funny enough, as I shutdown my wallpaper appears. 

**This suggests to me that Compiz needs a fix or re-installation.** How can I disable compiz?


Here's my Xorg.0.log.old Errors
```
ubuntu@ubuntu:~$ cat /media/ce0ecab6-0a4d-482e-bc86-1653f0bca41f/var/log/Xorg.0.log.old | grep EE
	(WW) warning, (**[COLOR="Red"]EE[/COLOR]**) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(**[COLOR="Red"]EE[/COLOR]**) Failed to load module "i810" (module does not exist, 0)
(**[COLOR="Red"]EE[/COLOR]**) open /dev/fb0: No such file or directory
(**[COLOR="Red"]EE[/COLOR]**) intel(0): [drm] Failed to open DRM device for : No such file or directory
(**[COLOR="Red"]EE[/COLOR]**) intel(0): Failed to become DRM master.
(**[COLOR="Red"]EE[/COLOR]**) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(**[COLOR="Red"]EE[/COLOR]**) intel(0): /dev/agpgart is either not available, or no memory is available
(**[COLOR="Red"]EE[/COLOR]**) intel(0): Failed to initialize kernel memory manager
(**[COLOR="Red"]EE[/COLOR]**) intel(0): AGP GART support is either not available or cannot be used.
(**[COLOR="Red"]EE[/COLOR]**) intel(0): AGP GART support is either not available or cannot be used.
(**[COLOR="Red"]EE[/COLOR]**) intel(0): Couldn't allocate video memory

```

Any time I drop to Recovery Mode in the grub, the lines just scatter around. I appears like some sort of 'waterfall', thus I can't do any Xfix or whatsoever. 

```
ubuntu@ubuntu:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile **[COLOR="Red"]GM965/GL960[/COLOR]** Integrated Graphics Controller [8086:2a02] (rev 03)

```

```
ubuntu@ubuntu:~$ uname -ar
Linux ubuntu 2.6.31-11-generic #36-Ubuntu SMP Fri Sep 25 06:37:51 UTC 2009 i686 GNU/Linux

```

Sorry I don't know where to get the Compiz Log from.

Pls can someone help!

---

### Post by lovinglinux on 2009-10-26
Compiz is currently messing with KDE plasma panel and widgets. I can't move the widgets in the panel, unless I disable compiz.

To disable compiz run:

```
metacity --replace &
```

---

