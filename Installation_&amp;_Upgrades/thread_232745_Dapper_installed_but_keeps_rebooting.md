---
title: "Dapper installed but keeps rebooting"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by Bubba Ho-Tep on 2006-08-09
My Dapper installation is failing to boot - it continually reboots itself. 

I'm trying to install on a HP Pavilion t620a.

I had exactly the same problem when installing Breezy [here](http://www.ubuntuforums.org/showthread.php?t=140981)

That was solved by doing "live acpi=off noapic nolapic"

But didn't work for the Dapper install. 

I was using Knoppix and it had the same issue  - using "acpi=off noapic pci=bios' got it to boot.

So I thought I was really clever when I got the live CD to boot using that line. I did the Dapper install (as a clean install) blah blah all seemed fine until I came to reboot.

Kept rebooting. Bugger.
Ok I thought I'll add the "live acpi=off noapic pci=bios" line in the grub menu thingo when it comes up. Did that, no joy.

Ummm I'm out of ideas and I really want to take a chainsaw/axe/whatever to the computer.

Anyone have any ideas to stop me sawing my computer in half?

BH-T

---

### Post by bigken on 2006-08-09
go into the bios and see what is set to boot ie keyboard ect and dissable
them 1 at a time and see if this fixes it for you :(

---

