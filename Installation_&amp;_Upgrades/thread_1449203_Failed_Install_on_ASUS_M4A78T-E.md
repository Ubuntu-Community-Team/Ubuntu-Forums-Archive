---
title: "Failed Install on ASUS M4A78T-E"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by wactuary on 2010-04-07
Trying to put a fresh install on a new box.  Can't get it to install on either 9.10 or 10.04b1 cds.  Both hang with the same errors:

ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]

and

shpchp 0000:00:01.0: Cannot reserve MMIO region.

From what I could tell, others have this same motherboard working, but nothing I seem to do gets me past this point.  I've played with BIOS settings, tried to disable ACPI.  Tried running the install with the no acpi switches.  Nothing seems to make a difference.  I've upgraded the Mobo BIOS to version 3204, released 3/15/10.

Any help would be appreciated, I've been at it all day and gotten no where!

---

### Post by wactuary on 2010-04-08
Update:  I downloaded the Alternate CD and was able to complete the install using that CD.  Unfortunately, once the installation was complete and I ejected the CD, it failed to reboot.  Same 2 errors, just now at timestamp 2.89, instead of around 200 seconds in.

---

### Post by wactuary on 2010-04-09
Update 2:

It seems there is a bit of misdirection going on.  The hang and the error codes appear to be unrelated.  I had a PCI wireless card, D-Link DWA-542.  Once removed, the system booted as expected.  I was able to log in, connect to the internet using the wired connection and upgrade all packages.  Reviewing the DMESG, both errors still show up, so they were not my reason for the hang during boot.

Unfortunately, if I put the card back in, I still get a hung boot.  And since it's a total hang, I have no logs or other useful information regarding what went wrong in the process.

So now I need to get this card working, but at least I'm focused on the real issue.  Any thoughts on this new information?

---

### Post by wactuary on 2010-04-09
I'm closing this thread and opening a new one over at the Wireless section, as it turns out to be an issue with that specific card.

(Of course still no understanding of the original errors, but they don't seem to be mission critical.)

---

### Post by wactuary on 2010-04-10
I guess I'm having trouble letting this die...

Anyway, problem fully solved now.  On Lucid, installed the linux-backports-wireless-generic package.  Reinstalled card.  All OK.

I'm sure it's a bug that the system would crash on boot-up if that package wasn't there, but with no error message, I'm not sure how to report the bug in launchpad.  Happy to do it if someone provides some guidance.  But for anyone searching on the D-Link DWA-542 Wireless N card...  Works perfectly once the missing package is installed.  Crashes miserably without it.

G'night.

---

