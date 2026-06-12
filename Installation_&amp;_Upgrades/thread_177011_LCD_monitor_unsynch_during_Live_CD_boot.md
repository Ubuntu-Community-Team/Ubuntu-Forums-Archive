---
title: "LCD monitor unsynch during Live CD boot"
date: 2006-05-15
forum: Installation &amp; Upgrades
---

### Post by nodyad on 2006-05-15
Starting the 5.10 live CD on Via EPIA M10000 board, AOC LM-700 monitor, the procedure gets through the initial device detection slew of messages, then the display becomes unsynched on a screen that appears to be blue and white.  The AOC display cannot resynch on the signal, so I am effectively stuck at that point. I also tried a TV as monitor (changed the EPIA BIOS to TV only) but got the same behavior at that point. Suggestions on what to twiddle to get past that hangup?

I also get this same behavior with the installation CD.  In the Linux world, would it be okay to use a different monitor that works for installation, then switch back to the AOC after installation and any file mods to enable the AOC LM-700?

---

### Post by nodyad on 2006-05-15
Taking a hint from some other postings, I got a bit further using boot: live vga=771 (a setting for laptops--I have no idea why that works or what is magic about the value). This was able to synch the monitor properly, but I was unable to get past loading the preinstalled session.  Prior to this, the lan detection failed to find the Epia M10000's 10/100 adapter, but would this affect the preinstalled session part of the boot sequence?

---

### Post by Macperson on 2006-05-27
Same here. Unable to get past  the 'preinstalled session' hang-up.
Tried the MD5 checksum etc. No luck.
This seems to be a common problem, has anybody actually managed
to find a solution that would apply to all of us?

Shame.... I would like to experience Ubuntu prior to using it as my
main os.

Macperson (a frustrated Macperson!)
~~~~~~~~~~~~~~~~~~~~
WindowsXP Home Ed - Desktop pc.

---

