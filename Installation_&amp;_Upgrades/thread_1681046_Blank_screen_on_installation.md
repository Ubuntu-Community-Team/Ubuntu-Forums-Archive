---
title: "Blank screen on installation"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by beastvold on 2011-02-03
I'm installing Edubuntu v. 10.10 from a burned DVD to a Fujitsu Lifebook (S Series, Product No: FPC04052AK).  BIOS comes up OK, and so does the initial installation screen where I choose the language then choose to install Edubuntu on my computer.  Once I choose the install option, the screen changes into mottled shades of grey and black and I can faintly see "Edubuntu" on a splash screen (only if I look really close).  Then the screen goes black (just no video, not "turned off" black).  I know the menus are still available and navigable because I can get through the first few screens from memory, and I can hear the CPU working with each selection.

It's not a problem with the DVD, as I have run complete and successful installations on three other similar laptops (all Fujitsu Lifebooks, but slightly different models [S Series, Product No: FPC04061AK]).

I would have thought that it is a problem with the graphics card (it is an older laptop), but I previously loaded Kubuntu fine without any graphics problems.

Does anyone have any ideas on how to resolve this?  Or, does anyone know how to run an non-graphical installation from a DVD? My hope is that if I can get it to install, it may come up fine from the HD.

BTW, I've already looked through the Edubuntu help file on troubleshooting blank screens ([https://wiki.edubuntu.org/X/Troubleshooting/BlankScreen](https://wiki.edubuntu.org/X/Troubleshooting/BlankScreen)), but this seems to apply only to situations post-install.

Thanks!

---

### Post by bmb80764 on 2011-02-05
The short answer is I do not believe this hardware is supported by 10.10.  My experience is based on trying to run/install ubuntu, not edubuntu, but I think the same problem applies.

From reading this [bug report (https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/362582)]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/362582") I infer that the driver that supports the video chip on this and other Fujitsu laptops is no longer shipped/supported by ubuntu.

The workaround for ubuntu *installation* is to use the "alternate" installation CD (is there an alternate CD for edubuntu?)  This allows installation in text mode, so that graphics are not reuqired.

If, however, you want to run a graphical desktop, the workaround is to install 8.04 (from the alternate CD), which is the last version supporting the old graphics driver.  After installation, you have to get to a command line (since the screen will be blank) using Ctrl-Alt-F1.  Edit the file /etc/X11/xorg.conf and find the section that says

```
Section "Device"
  Identifier "Configured Video Device"
EndSection
```

Add a line so it says

```
Section "Device"
  Identifier "Configured Video Device"
  driver     "i810"
EndSection
```

and restart.

The above worked for me with a Lifebook S6110 and Ubuntu 8.04.4

---

