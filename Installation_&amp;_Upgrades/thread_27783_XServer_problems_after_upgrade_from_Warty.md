---
title: "XServer problems after upgrade from Warty"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by Ceasama on 2005-04-17
Hi everyone, today I made the upgrade from Warty to Hoary using the 'sudo apt-get upgrade' and 'sudo apt-get dist-upgrade' commands.

At the end of the install, an error came up saying dpkg couldn't extract the new 'xlibmesa_gl' and the installing ubruptly ended.
Afterwards, I restarted, and went into ubuntu. The GDM screen was fine, and the login is alright, but when I try to log in normally, or by the Default System setting, it brings up an enquiry box with a light bulb in it and one letter: l.

Then it opens a terminal in the top left corner of the screen. Nothing else happens. No Panels or icons, nothing. The terminal is perfectly usable.

So I tried upgrading again. I noticed there were a few leftover packages that haden't been installed, so I used 'apt-get -f install'.
Once again, the error involving 'xlibmesa_gl' appeared, and it didn't make any other attempt to install other packages.
Upon using apt-get install xserver-xorg (Since when I try to reconfigure this, it says it isn't installed) the same packages come up as dependencies, but xlibmesa_gl NEVER INSTALLS.

I've tried doing it through Recovery, I've tried logging in on Failsafe GNOME, and that's the closest I've got to a desktop. I get a small amount of buttons, a trash can, and a huge error saying something about XServer.

I dunno what's going on, and I'm too noob to understand it. I'm trying to pick it up,-- But I didn't think upgrading from Warty would screw up the gui... I can't do much else than some basic commands in terminal.
Please Help!

---

### Post by Ceasama on 2005-04-17
Some more details about the error it shows in Failsafe GNOME...

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The XFree86 Project, Inc
40300001
You are using XFree 4.3.0.
There are known problems with complex XKB configurations.
Try using simpler configuration or taking more fresh version of XFree software.
If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>


EDIT: The results of 'xprop -root | grep XKB' were:
_XKB_RULES_NAMES(STRING) = "xfree86", "pc104", "us", "", ""

'gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd' was completely ignored by the terminal, even if used with sudo (I didn't even ask for a password).



DOUBLE EDIT: The reason for the premature upgrade exit is that dpkg is failing to process xlibmesa-gl for the reason:

"trying to overwrite '/usr/X11R6/lib/libGL.so.1.2' which is also in package fglrx-4-3-0"

I'm getting to sick of this! I want GNOME back...  :-(

---

