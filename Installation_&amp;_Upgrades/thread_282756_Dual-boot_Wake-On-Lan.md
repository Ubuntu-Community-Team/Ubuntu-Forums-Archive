---
title: "Dual-boot Wake-On-Lan"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by PlastechFish on 2006-10-23
I have a computer set up in my appartment that I use for testing web sites/apps that I am developing that I would like to dual boot with XP and Kubuntu (XP for hardware support when I just want to record TV and stream Orb, and linux as the webhost when I need to test my PHP apps or just use a linux program I can't live without). 

I don't spend much time in my appartment, so I would like to be able to wake the computer on LAN to save power when I'm not using it, like at night.  The trouble is that I can't think of a way to select which OS to boot from a remote location.  Remote desktop and SSH are great, but they only work once the PC has booted. ](*,) 

Is this even a possible problem to solve?  Or, am I better off just virtualizing Kubuntu on XP with VMWare Server?  Any guidance would be appreciated.

TIA,
PF

---

### Post by PlastechFish on 2006-10-23
Nothin' huh?  Any idea who else to ask?

---

### Post by brundles on 2006-11-01
I don't think you'll be able to specify a boot OS via WOL in any way, but what you can do is tell GRUB (assuming that's your boot loader) which OS to use next time.

By default my PC boots to Ubuntu but on the rare occasion I do needs windows, using grub-set-default makes the next boot a Windows boot. You'll need to check what it saves back at the end of the menu.lst file though to make sure that Grub knows to boot Ubuntu on the following reboot.

---

### Post by PlastechFish on 2006-11-01
Thank you for your response.  I have done something similar: Acronis' boot loader has a setting to boot into a default OS after a certain amount of time has passed, and it can also be setup quite easily to load a different OS on the next boot.  It is easier than grub or lilo because my default OS is windows.

---

### Post by brundles on 2006-11-01
Glad you've got it sorted.

The other thought that had occured to me is that if you / partition is EXT2 or EXT3 (I think Ubuntu uses EXT3 by default but mine is ReiserFS as I overwrote a SuSE partition) you can edit the menu.lst file from Windows using something like EXT2IFS to get access.

Make sure you're using a Unix friendly editor though - I don't know what will happen if Grub is asked to deal with the additional LFs that Windows editors like so much.

---

