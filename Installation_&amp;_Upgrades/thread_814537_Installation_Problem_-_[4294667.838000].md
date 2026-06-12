---
title: "Installation Problem - [4294667.838000]"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by Crothall on 2008-05-31
I'm trying to install from the LiveCD boot disc.
It's an 'official' version and not a written disc.
When I run it, I get the main menu, but when I choose 'Instal' I ultimately get a black screen with this message;

[B]Uncompressing Linux… Ok, booting the kernel.
[4294667.838000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[4294667.838000] Kernel panic – not syncing: IO-APIC + timer doesn’t work!  Boot with apic=debug and send a report.  Then try booting with the ‘noapic’ option [4294667.838000].[/B]


I know my way around a computer, but this is all waaay over my head.  What is this saying?  What do I need to do?  The computer I'm trying to run the disc on is an HP that is only a year old this month!  It came pre-installed with Vista.

Thanks guys!

---

### Post by Rocket2DMn on 2008-05-31
At the menu, try pressing F6 and adding this to the end of the kernel line:
```
acpi=off noapic
```

---

### Post by Crothall on 2008-05-31
Well bugger me that seems to have worked.
Ha!
It's installed and now rebooting from the hard drive!
eeeeeeeee!
I can't wait!

*rubs hands together*

Thanks mate!

---

