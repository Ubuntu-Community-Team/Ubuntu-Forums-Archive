---
title: "attempting to try ubuntu - won't install (locks during install process)"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by superchode on 2005-11-07
it fails almost immediately in the install.... the last two lines it shows are: 

'ACPI: Looking for DSDT in initrd... not found!'

and then just 

'   not found!' 

and it stalls.

this is on a MSI K7D motherboard with a single 1600+ MP chip in it. i wasn't sure about the hardware beforehand so i ran it through 5 passes of memtest86 without issue.

could someone let me know what the lines it locks up on are referring to and what direction i should be looking in to try and find a fix?

---

### Post by varunus on 2005-11-07
First, make sure the problem isn't with the CD itself...the Ubuntu ISO can be picky about being burned.  You can use the "md5sum" tool to make sure your ISO is correct; there's instructions on the forums here somewhere.

Assuming the problem is not CD-related, you could also try booting the install CD with the noacpi option.  (Hit F1, F2, or F3 at the boot prompt, it'll show you how...i think you just type "linux noacpi" and hit enter).  However, you shouldn't have to do this...this disables power management, which seems to be where your error is occuring.  Make sure your CD is ok.

If the noacpi gives you a successful install, you can configure power management in your system later once its booted into Ubuntu.

---

### Post by superchode on 2005-11-07
great, thanks. i'll try that tonight.

---

