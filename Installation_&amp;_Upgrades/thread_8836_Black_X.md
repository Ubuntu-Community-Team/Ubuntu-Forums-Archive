---
title: "Black X"
date: 2004-12-21
forum: Installation &amp; Upgrades
---

### Post by Dan on 2004-12-21
Have installed successfully onto my IBM T22, everything works, except that the black X that appears on startup never goes away, it doesn't follow the mouse just sits there in the middle of the screen. How can I make it go away?

---

### Post by Dan on 2004-12-21
OK fixed it, a case of RTFM 


this is how

This is caused by problems with hardware acceleration of the cursor. You can work around this problem by editing /etc/X11/XF86Config-4 and adding the following line:
Option "HWCursor" "false"

or

Option "SWCursor" "true"

to the Device section of the file.

Note that the option is specific for each video card driver.

To be sure to enter the proper information check the man page for your driver.

Examples:

man radeon
for ati cards or
man nv
for nvidia cards.

The result section should look like:

Section "Device"
Identifier "nVidia Corporation NV25 [Geforce4 Ti 4600] 0"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "HWCursor" "false"
EndSection

---

