---
title: "Ubuntu won't boot up after upgrading"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by h_howee on 2008-05-04
I just upgraded to hardy last night (at least I think it did). I just left it on overnight after it got to the downloading part. My brother restarted the computer this morning but he says he doesn't know if it finished upgrading or not, he says he just closed it.
The upgrade must have stopped wherever the first modal dialog box appeared. The desktop won't load now, I can see the mouse when it boots but the rest of the screen is black. How can i fix this?

---

### Post by h_howee on 2008-05-04
other possibly relevant info:

/media/disk/var/log/gdm/:0.log
([https://answers.launchpad.net/ubuntu/+question/13690](https://answers.launchpad.net/ubuntu/+question/13690))
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux howard-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May  4 10:48:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

```

I'm going to try [http://ubuntuforums.org/showthread.php?t=609439](http://ubuntuforums.org/showthread.php?t=609439)

---

### Post by h_howee on 2008-05-04
I logged on with failsafe terminal and executed
sudo pkill -HUP nautilus
nautilus &
gnome-panel

The desktop and panels show up but it's set to an ugly theme, it tells me it can't initialize HAL, I can't connect to the internet, I can't open the update manager, and much more... Is there any way to backup all installed softwares and make a fresh hardy installation, then recopy all softwares back? Or is there a simple way to fix all of this?

---

### Post by Pumalite on 2008-05-04
A clean install is your best bet. You can save your files with your Ubuntu Live CD.

---

### Post by h_howee on 2008-05-04
Which files am I supposed to copy if i want to save a copy of all installed softwares with the menu shortcuts and all the panels?

---

### Post by Pumalite on 2008-05-04
That's a tall order. You could use AptOnCD, but that doesn't address what you want completely. In my case, I save photos and movies and do everything again. Much cleaner, much faster.

---

