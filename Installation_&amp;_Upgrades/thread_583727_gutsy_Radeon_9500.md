---
title: "gutsy Radeon 9500"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by DwalerXIII on 2007-10-20
I waited for upgrading to Gutsy because of the problems with ATI drivers.
My PC is a AMD 2400+ with a radeon 9500 card.  Are there problems with this graphic card after installing Gutsy?? I read about problems with other cards but I think nobody mentioned the 9500.

Can I do the upgrade?

---

### Post by Pumalite on 2007-10-20
I'd stick with a working system for the time being. Read this:[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by mlind on 2007-10-20
I have ati 9550 and I'm using the radeon/ati (opensource) driver. No problems here.
FYI the proprietary fglrx driver has suspend/hibernate issues in Gutsy.

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)
[https://bugs.launchpad.net/bugs/132716](https://bugs.launchpad.net/bugs/132716)
[https://launchpad.net/bugs/121653](https://launchpad.net/bugs/121653)

---

### Post by joslinar on 2007-11-12
> **mlind said:**
> I have ati 9550 and I'm using the radeon/ati (opensource) driver. No problems here.
FYI the proprietary fglrx driver has suspend/hibernate issues in Gutsy.

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)
[https://bugs.launchpad.net/bugs/132716](https://bugs.launchpad.net/bugs/132716)
[https://launchpad.net/bugs/121653](https://launchpad.net/bugs/121653)

Have you been able to do "Visual Effects"? I have a 9550 with amd and I can't do composite.

---

### Post by mlind on 2007-11-13
> **joslinar said:**
> Have you been able to do "Visual Effects"? I have a 9550 with amd and I can't do composite.

yes, your gfx card's chipset is probably blacklisted by Ubuntu's compiz like mine, so you need to "whitelist" it first. When you try to enable the "Visual Effects" a message appears about blacklisting in ~/.xsession-errors

To ignore compiz blacklists
```

mkdir -p ~/.config/compiz
echo SKIP_CHECKS=yes > ~/.config/compiz/compiz-manager

```

(It's blacklisted for a reason, so you may run in to trouble.)

---

### Post by joslinar on 2007-11-14
Thanks for the info. I will try that and let you know.

---

### Post by joslinar on 2007-11-14
What i get is a message saying:

[SIZE="3"]The composite extension is not available.[/SIZE]

Here is the ~/.xsession-errors text


[FONT="Courier New"](process:5942): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5946): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/guatek:/tmp/.ICE-unix/5939
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: Initializing gnome-mount extension
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: 
** (nautilus:5999): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:5999): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:5999): WARNING **: Can not get _NET_WORKAREA

** (nautilus:5999): WARNING **: Can not determine workarea, guessing at layout
present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:6062): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:6062): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...

** (trackerd:6077): WARNING **: Tracker daemon is already running - exiting
/usr/bin/compiz.real (core) - Fatal: No composite extension
** Message: Not starting remote desktop server
evolution-alarm-notify-Message: Setting timeout for 5332 1195084800 1195079468
evolution-alarm-notify-Message:  Wed Nov 14 20:00:00 2007

evolution-alarm-notify-Message:  Wed Nov 14 18:31:08 2007

Window manager warning: Failed to read saved session file /home/jose/.metacity/sessions/default0.ms: Failed to open file '/home/jose/.metacity/sessions/default0.ms': No such file or directory

(gtk-window-decorator:6062): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:6062): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
No nvidia hardware available
[/FONT]

---

### Post by mlind on 2007-11-15
You need to have Composite extension and AIGLX enabled in your xserver instance.

Make sure you have something like this in your /etc/xorg.conf
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	**Option		"AIGLX"	"true"**
EndSection

Section "Extensions"
	**Option	"Composite" "Enable"**
	Option	"RENDER" "Enable"
	Option	"DAMAGE" "Enable"
EndSection

```
(and make sure you're using the opensource ati/redeon driver)

---

