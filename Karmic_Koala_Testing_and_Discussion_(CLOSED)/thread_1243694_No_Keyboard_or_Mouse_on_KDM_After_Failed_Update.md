---
title: "No Keyboard or Mouse on KDM After Failed Update"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fifth on 2009-08-18
I've just updated tonight, first for a couple of days. While updating my system froze (while installing the new kernel) forcing a reboot. The reboot got me to KDM but I was not able to enter any input or switch VT's. A reboot into recovery enabled me to finish the upgrade but rebooting still fails at KDM.

Rebooting into recovery and running apt-get update gives the following error (roughly noted);
```

Failed to open connection to "system" message bus: Failed to connect to socket
/var/run/dbus/system_bus_socket
No such File or Directory

problem executing scripts APT::Post-Invoke-Success
usr/bin/dbus-send --system --dest=org.freedesktop.PackageKit
--type=method_call /org/freedesktop/PackageKit org.freedesktop.PackageKit.StatusHasChanged

string:'cache-update'

```

The upgrade appears to be complete, only package being held back is for mySql, all other updates have been installed.

Not sure how to proceed with this. First thought was just to wait for new updates, but if apt-get update is failing ... :(

---

### Post by fifth on 2009-08-19
Still getting the same error from 'apt-get update' but still managed to upgrade today.

Unfortunately nothing changed :( System is still borked. Any suggestions to get X working?

(Downloading Alpha4 as a last resort ..)

Although its nice having a working network plasma widget in Jaunty :) I do miss so many of the new features in KDE4.3

---

### Post by fifth on 2009-08-19
The apt-get error i receive in recovery/root is possibly (probably) not related to my problem with X dying on KDM;

[https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/388623](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/388623)

Copy of xorg log ...

```
I) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203
(EE) config/hal: couldn't initialise context: unknown error (null)
 ddxSigGiveUp: Closing log

```

KDM log ...

```
Build Date: 14 August 2009  06:43:50PM
xorg-server 2:1.6.3-1ubuntu2 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 19 17:31:28 2009
(==) Using config file: "/etc/X11/xorg.conf"
Setting master 
(EE) config/hal: couldn't initialise context: unknown error (null)
process 3512: Attempt to remove filter function 0xf4f600 user data 0x96c5420, but no such filter has been added
Dropping master 
 ddxSigGiveUp: Closing log
```

From dmesg ...

```
[   50.090316] hald[3363]: segfault at 1a3f1c6f ip 08058566 sp bfc8f4b0 error 4 in hald[8048000+5b000]
```

Problem seems to be hal?

---

### Post by edvar on 2009-09-30
It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!

---

