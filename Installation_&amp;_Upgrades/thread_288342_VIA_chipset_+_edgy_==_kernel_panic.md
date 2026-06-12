---
title: "VIA chipset + edgy == kernel panic"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by youShotWhoInTheWhatNow on 2006-10-29
I have searched around and read quite a bit, but haven't found a solution.  I am running dapper currently, and just downloaded the edgy eft CD.  When I try to boot off the CD I get a kernel panic, very similar to what is posted here: [https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/66140]("https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/66140")

I have tried using "acpi=force" "pnpbios=off" "acpi=off" and various combinations of these (as suggested on this forum) but all to no avail.  I updated my bios, didn't help.  My bios doesn't have any acpi options that I can see. I have an MSI KT4 mobo with VIA chipset (seems like the common theme) and a Barton 2600+.

Any ideas or info would be greatly appreciated.

---

### Post by Skerit on 2006-11-01
I've got thesame problem with my MSI PM8M3-V Motherboard... I just can't understand how a kernel would go stable with such a huge bug in it! I've disabled every ACPI in my bios without any success...

However, enabling ACPI in the bios and then adding the following to the start-up command thing did help:

pnpbios=off acpi=force

---

