---
title: "Can only use GNOME FAILSAFE after upgrade to 7.10"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by solaria on 2007-10-23
Can't login to:  GNOME, KDE, or Xfce  after the upgrade to 7.10.

It will accept the username/password, show the desktop background (not wallpaper) for about 30 seconds, then change back to the login screen.

GNOME Failsafe seems to work fine, but it looks like some options are missing because of the 'failsafe'.

Using the legacy Nvidia 96xx drivers.  Display looks good, dual monitors and all...

So how do I track down the problem?

---

### Post by haggus on 2007-10-24
I have the same problem and I have an alternate install cd but I can't get the cdromupgrade command to work in gnome filsafe any help would be appreciated thanks.

edit I found a way to fix my installation open a terminal in gnome failsafe and type :

sudo dpkg --configure -a

It tokk about fifteen minutes for it fix almost everything except:

Errors were encountered while processing:
 wesnoth-all
 wesnoth
 wesnoth-editor
 acpid
 libqt3-mt-dev
 ubuntu-desktop
 acpi-support
 powermanagement-interface

---

### Post by solaria on 2007-11-08
No, that didn't do it.  Also tried the reconfigure all... took a lot longer, but also didn't do anything.

Probably should mention that the video card is a Nvidia Quadro NVS, using the legacy ("9639") drivers.  Evidently there's some problem with XGL??

What finaly got it working (well, mostly working) is:

```
touch ~/.config/xserver-xgl/disable
```

"Working" in that KDE and XFCE are OK... GNOME however still isn't right.

I can login to the GNOME desktop alright:  wallpaper, icons, taskbar, etc...
The problem is that when I open an application, the window is stuck in the top-left of the screen with no way to move it; no windowbar.

...and the Logout Button doesn't work.  Well, it eventually will work, but takes about 5 minutes and lots of clicks for the logout screen to show.


Close... no cigars yet.

---

