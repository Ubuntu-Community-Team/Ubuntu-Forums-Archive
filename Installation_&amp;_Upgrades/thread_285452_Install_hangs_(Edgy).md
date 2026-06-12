---
title: "Install hangs (Edgy)"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by skep on 2006-10-26
Ubuntu Linux Version: 6.10 (Edgy)

My Computer:
- CPU: AMD Athlon-XP 1800
- Videocard: nvidia GeForce 4200-Ti
- Soundcard: TerraTec 128i PCI
- CD-/DVD-Drive: LG GSA-4163B (DVD/CD-Burner)

Problem: The installation of 6.10 hangs.

I downloaded the ubuntu-6.10-desktop-i386.iso, checked the md5sum and burned the iso to a cd.
After booting the bootscreen appears, I choose the correct language and "click" on "Installation" (the 1st point in the menue). After that the progress-bar appears and then nothing, nada...from this point on nothings happens anymore. Ctrl+Alt+Fx doesn't bring me to any console or boot-log, so I have no idea why it hangs..

I tried to start the install in the safe graphics mode (2nd menue-point) and I tried different boot-parameter like "nosplash" and "live pci=noacpi"...all with the same (bad) result.

Anyone have an idea?

---

### Post by boz on 2006-10-26
Did you happen to select the option to check disk for errors before trying to install?  I've had a couple of bad install disks before.

---

### Post by skep on 2006-10-26
> **boz said:**
> Did you happen to select the option to check disk for errors before trying to install?  I've had a couple of bad install disks before.Yeah..but the same thing happens..progress bar appears and nothing happens..it doesn't even come to the point where it checks the CD for errors..

---

### Post by Cambrant on 2006-10-26
I have the same problem. I'm starting to believe the CD is an inferior medium for installing operating systems with, since the same thing has happened on several computers and several different OS:s during the past few months.

The installation usually stops by a blinking underscore in the top left corner of the screen. No X, no anything. By selecting the safe graphics mode i was able to get it to arrive at the gnome desktop, but then it crashed when i tried to run firefox. Overall it seems to happen at totally random places in the boot process.

My computer is totally fine with Edgy otherwise (I'm writing this from the same computer running Edgy) but I want to perform a clean install. I am willing to try different things if anyone has any suggestions.

Edit: I'll try the alternative cd now in case that works out better.

---

### Post by skep on 2006-10-26
hmm..tried without "quiet splash" boot-parameters and the install hangs at some ACPI stuff..the latest boot/install-log entry shows something like:
ACPI - Thermal Zone blabla...

nothing changed to that with "pci=noacpi" parameter..

---

### Post by skep on 2006-10-27
Disabling ACPI in the Bios "solved" all the problems..hmm..

---

