---
title: "Live CD won't login (graphics problem?)"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by ed_r on 2008-10-19
I've got the Ubuntu 8.04 live CD (built 20080702.1).  I can boot from it; then I can select "Try Ubuntu without any change to your computer"; then I can see the login screen and allow the thing to start logging-in as the default "ubuntu" user; but then the login process fails:

[LIST]
[*]The screen turns orangey-biege and a mouse pointer (responsive) appears
[*]Then the screen turns black, but the cursor's still there and is still responsive
[*]Then the cursor becomes unresponsive and some grot appears in the top half inch or so of the screen
[*]Then the monitor goes into power save mode
[*]Then Ubuntu returns to the login screen
[/LIST]This whole sequences takes, oh I don't know, about 10 seconds.

I'm also getting the "8254 timer not connected to IO-APIC" message, but booting with "noapic" doesn't seem to help.  (I mean, it stops the IO-APIC message, but doesn't cure my login problem.)

**Help, please!**

    ~~~

FWIW, some information about my computer is enclosed below ...

[SIZE="1"]Monitor
-------
Philips 170S

Graphics card (according to MS Windows)
-------------
Chip type   = ATI Radeon Xpress 200 (0x5974)
Memory size = 64MB
Bios info   = BK-ATI VER008.045I.017.000
Location    = PCI bus 1, device 5, function 0

Main memory (according to MS Windows)
-----------
2.43GB RAM

Main CPU (according to MS Windows)
--------
Name      = AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
Device id = acpi\authenticamd_-_x86_family_15_model_43

Motherboard (according to F10 on boot)
-----------
Manufacturer = MSI
Id blurb     = RS482M A7191AMS V1.3B4 011306 13:46:40[/SIZE]

[COLOR="Red"]EDIT: oh, hang on, this is covered [elsewhere]("http://ubuntuforums.org/showthread.php?t=160304").  Maybe I'll post again if I get it working.[/COLOR]

---

