---
title: "SATA, Noapic &amp; Ubuntu"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by drew boardman on 2008-03-05
Dear All

I have a new laptop thats needs Vista replacing with Ubuntu. I have two concerns/problems.

1. When I install a live cd, be it Mandriva, SUSE, Ubuntu it freezes.

I have asked somebody and they mentioned pressing F6 at the startup and typing in noapic or nolapic (whatever that it is?). When I press F6 there is already text in there. What is the the correct way of writing it in? Do I overwrite the text already there?

2. Did think to just wipe the hard drive with GParted and start the install from blank. GParted installs but won't see the HDD, its SATA. Is this the problem with the distros above, they have not installed the SATA drivers to see the HDD to install in the first place. How do I find out what SATA HDD I have to find the correct dirivers that work with Linux?

Thanks for your help.

---

### Post by prshah on 2008-03-06
Both problems are related.

Some laptops (esp. some Compaq models) have SATA set to "Native" or "Legacy" mode in the BIOS options. 

If you can find such a BIOS option (SATA Support, SATA Legacy Handling, SATA compatibility mode, etc), try changing to the next availible option to check if it works.

You dont particularly need to install any SATA "drivers". use the command 'dmesg | grep -i "attached scsi disk"' to find out if your HDD is recognised or not; if it is, you will get a three letter code for your HDD (typically sda) at about the beginning of the line.

Cheers,
PRShah

Cheers,
PRShah

---

### Post by drew boardman on 2008-03-09
Thanks for the reply

I think the problem is ACPI.  I get the following error message, does it mean anything to anybody?

"ACPI Exception (processor_core-0781) AE_NOT_FOUND Processor device is not present.
Marking TSC unstable due to: possible TSC halt in C2"

Thanks

Drew

---

