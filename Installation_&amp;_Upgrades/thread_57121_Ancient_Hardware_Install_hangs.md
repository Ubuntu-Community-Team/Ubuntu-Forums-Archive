---
title: "Ancient Hardware: Install hangs?"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by EZ81 on 2005-08-15
Hello, im trying to install Ubuntu but it seems to hang early in the process.

-Pentium1@133MHz (actually a 120MHZ "Overdrive" processor sitting on a Pentium1/60MHz mainboard; slightly overclocked to 133MHz,  but this thing has been running stable for years, no problem there)
- 40M ram
- 20G HD
-Win98,  Suse 8.2, the latter was installed only because Wintendo alone did not recognize the size of the HD due to the ancient BIOS (1993...). I'm planning to leave Windows in place and replace Suse  with Ubuntu.


It did not boot from CD (Smart Boot Manager did not even see the drive, can't remember how Suse got on there...),  changing the CD drive to a newer one fixed this, it can boot from CD now using SBM.

Entered *server*  at the install prompt, Ubuntu complained about low memory, so Installation only works in english, no problem. Selected English language, german keyboard layout.
Next screen: *Detecting Hardware to find CD ROM* finished OK
*Scanning CD-ROM* and *Loading additional components* OK as well.

After this  the screen goes black with the cursor blinking in the bottom left corner. Text can be typed there, but it disappears after a few seconds, sometimes (once or twice a minute) the CD drive and/or the HD blinks.
This has been going on for 1.5h now (and it did the same thing earlier but i lost patience and rebooted after 20min the first time) ; does this look alright? Any hints?


Excuse the brain dump and thanks for reading this far,

;Matthias

---

### Post by nad on 2005-08-15
My guess is that the ubuntu kernel lacks support for your hardware. Possibly the processor, chipset?

Can you switch to another console to read messages?

---

### Post by EZ81 on 2005-08-15
nad,

in the meantime the PC rebooted itself without anything changed by the installation.

i can get another console via strg alt F2, no messages there, though.
'ps' shows various  processes that look right for a installation (at least to a KDE using mouse pusher  ;-)  ), deb-config, cd-rom retriever, kick seed, configure &%$§&, rescue.... and similar looking stuff. These change every time i run 'ps' and seem to repeat after a few seconds, hard to tell by just looking at that mess though...

EDIT: After a while tried ps again, it hung and wrote: 'out of memory, killed process 25000something' and a lot more things regarding memory and voila, reboot.

---

