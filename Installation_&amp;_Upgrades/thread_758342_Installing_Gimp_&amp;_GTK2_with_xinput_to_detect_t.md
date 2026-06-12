---
title: "Installing Gimp &amp; GTK2 with xinput to detect tablet"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by andrevanzuydam on 2008-04-17
**Scenario:**
If I run X windows with desktop effects enabled then the standard package of GIMP is not detecting my tablet.  The solution is to install GTK2+ with xinput=yes as part of the .configure command then recompile GIMP to use the new GTK2+ library.

This is what I have done so far:

[LIST=1]
[*]I downloaded GTK2+ latest version and did a default ./configure --with-xinput=yes
After make install I ran ldconfig to update the compiler libraries to the latest versions.
[*]I downloaded the latest GIMP, got all the dev dependencies to compile it and did a ./configure to a GIMP folder on my home path.[/LIST]

Gimp works fine but still doesn't detect my tablet in "effects" mode in X.  My conclusion is that GIMP didn't compile with the xinput GTK or GIMP is not loading the correct GTK version.

**Question:**
How do I check which libraries GIMP is using or how do I make it use the newly compiled GTK library with the xinput support.

---

### Post by andrevanzuydam on 2008-04-21
I've removed the xserver-xgl from my UBUNTU installation, downloaded the latest graphics drivers, as I have an ATI card.

I wanted to run compiz but it kept on saying that my graphics card was blacklisted.  This was easy to remove in the /usr/bin/compiz file.  Adding the following lines to my xorg.conf file helped make the enabling of effects without running xserver-xgl

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

Section "DRI"
   Mode   0666
EndSection

Section "ServerFlags"
        Option  "AIGLX" "on"
EndSection

I really hope this helps someone as I have the desktop effects working and my tablet operating properly.

---

