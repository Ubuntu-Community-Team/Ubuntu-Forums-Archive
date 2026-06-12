---
title: "DualBoot: XP+Ubuntu error using Live CD"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Justin_C on 2007-12-30
I have a 500GB hard drive with windows xp pro on a 120GB partition.  I also have a FAT32 partition and a partition set aside to install ubuntu.  I was able to successfully burn the ubuntu cd and it works fine in windows.  However, when I restart the computer with the CD in it is able to boot to the CD and i am able to work around in that initial menu.  When I select the first option (Start or Install ubuntu) I get a series of errors, exception emask, etc.  I'm not sure where to go from here.  My computer specs are as follows:

Intel Duo Core 2 Quad Q6600 @ 2.40GHz
2 x 1.00 GB RAM
Leadtek 8800GT 512MB gfx card
The optical drive and hard drive are both sata and there is a sata controller on the motherboard.  

Any help is appreciated!

---

### Post by Justin_C on 2007-12-30
Update:

Used the alternative cd.  Was able to sucessfully create a root partition and swap partition.  Restarted.  Successfully got into GRUB boot loader.  Was able to select ubuntu.  Got to ubuntu start logo.  Locked up, went to a command line type thing and punched out a bunch of errors similar to what i was getting before.  Will post more specifics in a bit.

---

### Post by Partyboi2 on 2007-12-30
You couldtry with out the splash screen loading.
When you get to the grub menu highlight the ubuntu kernel and press "e" to edit, then highlight the kernel and press "e" then at the end of the kernel line you will see "Splash" put "no" infront of it so it will say nosplash.

---

### Post by Justin_C on 2007-12-31
Tried booting without the splash screen.  Said it was "loading".  Received the exception Emask error again about a dozen or so lines down.  What exactly does that mean?

---

