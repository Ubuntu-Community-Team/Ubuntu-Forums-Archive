---
title: "after the installation"
date: 2004-11-04
forum: Installation &amp; Upgrades
---

### Post by bluefuse on 2004-11-04
I installed ubuntu with no issues, except for one small thing, i have a black X in the middle of my moitor, how do I get rid of thia problem?
\

---

### Post by az on 2004-11-04
Read the faq:
[http://www.ubuntulinux.org/support/documentation/faq/hwcursor](http://www.ubuntulinux.org/support/documentation/faq/hwcursor)


I have a black "X" in the middle of my screen, in addition to the normal mouse cursor.
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

This FAQ applies to: Any version 
Created by Matt Zimmerman 
Last modified 2004-11-03 08:41 AM

---

