---
title: "Ubuntu Installation Stalls with black screen and cursor"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by Mark0114 on 2008-11-26
I am trying to install Ubuntu on my PC.  It has an old version of Windows and I'd like to completely replace with Ubuntu.

I downloaded the ISO file and burned to a CD.  The Ubuntu installation screen comes up and runs through its initial installation.  The screen goes blank and the Ubuntu cursor (X) is the only thing on the screen.  I can move the cursor with my mouse.
I cannot get any further in the installation. 
The PC only has a CD ROM and no DVD.  My other PC (which is newer) successfully installed Ubuntu using the same ISO file on DVD.

I also get this error before the installation tries to initialize:
ACPI: BIOS age (1999) fails cutoff (2000), acpi=force.......

Information on the older PC:
Processor Type: Pentium III, 500MHz
256MB Memory

Not sure what to do here.

---

### Post by cariboo on 2008-11-27
In addition to the apic option, you may want to try starting in safe graphics mode. To do this from the menu press F4 and select safe graphics mode.

JIm

---

### Post by Mark0114 on 2008-11-27
OK, I just tried the Safe Graphics mode and got the same thing.  The before the black screen with Ubuntu cursor came up, the screen had a bunch of horizontal lines almost as if it was trying to initialize but failed.

Also - A saw on another thread to try ctl + alt + Backspace.
When I do this, it seems to be checking some of the system settings.  I get a few errors such as:
"ImportError: /usr/lib/libpangoft2-1.0.so.0: cannot read file data: Input/Ouptut error"

"[239.937869] Buffer I/O error on device sr0, logical block 255993"

/usr/bin/system-tools-backends: error while loading shared libraries: /usr/lib/libprolkit-dbus.so.2: cannot read file data: Input/output error"

ouch!!!

---

