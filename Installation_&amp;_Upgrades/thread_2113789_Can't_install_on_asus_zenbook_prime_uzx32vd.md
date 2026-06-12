---
title: "Can't install on asus zenbook prime uzx32vd"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by Darngood on 2013-02-08
I have an ultrabok with 500GB hard drive and 32GB SSD. 

I have created a 100GB partition with windows 7 x64 on the HDD and i want to install a linux distro on the 32GB SSD.

This is how i try to install:
[LIST]
[*]I grabbed the 64-bit .iso of kubuntu(or other distros enumerated below)
[*]Created a live usb with lili usb creator or gtk-usb-creator
[*]Booted from usb
[*]Change booting option to include nomodeset acpi_oso=Linux
[*]Black screen
[/LIST]


I have tried various options added to the grub booting options including nomodeset, acpi_osi=Linux and other i have found on various forums but i still get black screen.

Basically, before the desktop should show up ( all the programs are shown with started network, touchpad etc), I end up with either:
[LIST]
[*]a completely **blank screen**
[*]a blank screen with a **NOT blinking** cursor on top left side of the screen
[/LIST]

I don't know what else to do now :(

Distros I have tried so far(all x64):
[LIST]
[*]Mint 14 cinammon
[*]Mint 14 mate
[*]Mint 14 xfce
[*]Mint 13 Cinammon
[*]Ubuntu 12.10
[*]LUbuntu 12.10
[*]KUbuntu 12.10
[/LIST]

Same problem on every distro... I'm just stuck now...

UPDATE:

I have managed to install Linux Mint 14 Cinammon x64, but it's a bit strange, and it doesn't fully work. Maybe by describing the steps some more experienced user can figure out what the problem is.

Steps:
[LIST]
[*] Boot
[*] Wait untill the sound of the logging screen to pop
[*] Press the fn + F1 key to get the laptop into the sleep state
[*] Start -> The login screen is displayed properly
[/LIST]

Any ideas what's going on?

Note:

To install I did this:
[LIST]
[*] Boot from USB
[*] Edit grub boot menu and add acpi=off
[*] Wait for system to load
[*] Close the laptop lid -> wait untill the laptop sleeps
[*] Open laptop lid -> the desktop is shown properly
[/LIST]

---

### Post by Darngood on 2013-03-03
Edit: Now it doesn't work anymore. Black screen whatever i do...

---

### Post by oldfred on 2013-03-03
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Is this also an Optimus system? With on board Intel video and nVidia chip?
      
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

---

