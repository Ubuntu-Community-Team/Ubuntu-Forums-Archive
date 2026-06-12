---
title: "No Login after 10.10 update"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by rjakiel on 2010-10-12
So far every thread on this topic is showing issues with nVidia cards.  I am using the embedded Intel chipset and still having the issue.  I updated from 10.04 to 10.10 and prior that I booted the LiveCD to make sure everything was working.  After the update completed successfully without errors the system rebooted and just stops at the splash screen.

I hit the "esc" key and it shows that the boot process has stopped at "Checking Battery State" yet this is a desktop.  I have tried passing the no acpi flags at boot to no success.  dpkg-reconfigure <package name> for gdm, xserver, gnome, ubuntu desktop, etc... no dice.  The only way to log in is ctrl+alt+F2 and then log in to through the console and then "startx" which brings me to my desktop.  GDM does not exist and is not running and cannot be started either even from the console.  So I ask ANYONE have any clue on how to resolve this?  Seeing that there are countless threads on this without a single resoultion.

Thanks in advance.

---

