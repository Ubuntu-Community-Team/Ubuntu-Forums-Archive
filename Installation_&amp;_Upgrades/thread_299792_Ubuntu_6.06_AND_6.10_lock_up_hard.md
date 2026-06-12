---
title: "Ubuntu 6.06 AND 6.10 lock up hard"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2006-11-14
Ok, so, I got tired of M$ on the laptop, and all my servers run ubuntu already, so, ubuntu desktop was a logical choice for me to install. I needed a dualboot setup, and I managed to repartition my 40Gb drive into 2 20Gb partitions.

I then first tried to install 6.10 EFT from a downloaded CD. It brought up the initial splash screen, I then selected the first option in the menu, and got all the usual messages, then the screen went blank, and the system locked up hard. So, I rebooted.

This time I pressed f6 and deleted the "quiet" from the boot line, and booted again. The last two messages before it locked up again were:

> ACPI: looking for DSDT... Not found.
ACPI: setting ELCR to 0200 (from 0e28)

At this point, it locked up hard, and I was forced to do a hard reboot.

So, I repeated all the above steps, and added: "acpi=no noapic nolapic" to the boot line, and booted. Again it stalled at exactly the same point, after outputting exactly the same messages. Hmmm... Okay... 

I repeated the above, only this time erased the entire bootline, and entered "live vga=771 noapic nolapic"

The results were the same.

I tried again, this time with "live vga=771 acpi=no noapic nolapic"

Again, same results.

OOkay... so 6.10EFT ain't gonna boot.

So I tried with a 6.06LTS disk.

Guess what..

**Exactly the same thing happened!!**

So, I'm stumped. Does anyone have any suggestions?

---

### Post by ReaderRat on 2006-11-14
You might post your computer specs...RAM, video card,etc....

---

### Post by Milambar on 2006-11-14
Ok, I found the solution, I was gestalting (read ranting) at a fellow sysadmin who has more experience than me.. He said "Wait, acpi=no? Don't you mean acpi=off?"

So I tried with acpi=off, and the machine booted without any problems at all. Im writing this from a lovely new Ubuntu Dapper-Drake installation :)

Strange how its always the little things that catch you out.

I just need to tweak it now, so it will let me close the lid of the laptop without halting everything, as when at home, I hook it to a nice big 19" CRT monitor (I know, I know... CRT iew..), and like to close the lid so the cat can't walk over the keyboard.

Does anyone know how to do this?

---

