---
title: "Live USB reboot problem"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by lsemmens on 2011-12-10
I'm running a Persistent Live USB version of Oneiric (11.10) on a Toshiba ( Sattelite L500 series) Laptop. There is no HDD installed at the moment so my only choice is Live CD (no persistence) or USB key. I've been away from Linux since Karmic, as I found that Windoze 7 was far superior to its previous incarnations. 11.10 is superior in many ways, but I am having trouble finding my way around, no biggie.

A niggling problem, and not worth spending too much time on, is that should I need to perform a system restart, my laptop seems to forget that there is anything plugged into the USB slot and tries to boot from optical drive followed by network boot ROM, neither, of which, are valid boot devices. A cold boot (power refresh) always has the desired effect, but what could be (I'm guessing) "ejecting" the device on any of the the USB ports?

P.S. New HDD will be installed after Christmas (I stole the existing one for a repair job) and then this question will be redundant.

---

### Post by dabl on 2011-12-10
You need to go into your "Setup" or BIOS configuration menus, and find the boot sequence settings, and the USB settings.  You want it set to be able to boot from USB, and then in the sequence you want the USB removable device to be first/top in the sequence list.

---

### Post by lsemmens on 2011-12-10
> **dabl said:**
> You need to go into your "Setup" or BIOS configuration menus, and find the boot sequence settings, and the USB settings.  You want it set to be able to boot from USB, and then in the sequence you want the USB removable device to be first/top in the sequence list.
Thanks for that, but, BIOS is already set to boot from the USB device first, otherwise I'd never be able to cold boot it. The problem only occurs after a warm boot where something tells BIOS to ignore the device plugged into the USB port and look for other bootable devices, none of which are available. As I said, it's nuisance value and not a major obstacle. I have discovered another, more pressing, problem re: wireless connectivity which will be the subject of another thread if I can not find a suitable solution by searching here and elsewhere.

---

### Post by lsemmens on 2011-12-18
Just as an update, for some reason, this problem is resolved. I have not installed or changed anything so I cannot offer any possible idea.

---

