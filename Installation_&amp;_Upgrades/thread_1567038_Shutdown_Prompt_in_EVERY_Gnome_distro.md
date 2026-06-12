---
title: "Shutdown Prompt in EVERY Gnome distro"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by lordylordy on 2010-09-03
Hi

Can anyone help?  I raised another question on the forum that was linked to Ubuntu 10.4 but that just petered out.

Every single Gnome based distro I have tried on a desktop machine has immediately popped up with the Log Out, Shut Down etc prompt as soon as the desktop loads.  I doesn't happen with any KDE based distro!!

I have tried resetting the CMOS/BIOS etc and it's not the Power Pack, tried two!

Anyone else had this or something similar.

The machine is a Fujitsu Siemens Desktop with 3GB RAM, decent graphics etc...

I've tried KDE distros and don't like them as much and really want to get back to a Gnome environment.

---

### Post by Tipo on 2010-09-03
It sounds like you've got something broken in your GNOME configuration files.

This will reset your gnome configuration to the default, but try moving the following folders to something like .foldername.backup:

[LIST]
[*]~/.gnome
[*]~/.gnome2
[*]~/.gconf
[/LIST]

Where '~' is your home folder.

---

