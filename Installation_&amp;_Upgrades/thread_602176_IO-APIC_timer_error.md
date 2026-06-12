---
title: "IO-APIC timer error"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Taters on 2007-11-04
Wikipedia was nice enough to enlighten me on what IO APIC stands for (Advanced Programmable Interrupt Controllers) but how do I turn it off?

When I run the Gutsy Gibbon ISO file, It does not encounter any errors until I try using the desktop. (it freezes at the splash screen after the login screen)

Basically, if you could answer these questions in their order of importance, that'd be dandy:

How would I turn of IO APIC?

How could I configure IO APIC to work?


Oh, and I nearly forgot to add: I am running on a HP Pavilion a1200y with a Intel Celeron D processor, a ATI Radeon Xpress 2000 card, and finally it was designed for XP :(

I will give additional information if requested.

Thanks.

(Finally, Feisty displays a Timer is not connected warning, but it boots fine)

---

### Post by dcstar on 2007-11-04
> **Taters said:**
> Wikipedia was nice enough to enlighten me on what IO APIC stands for (Advanced Programmable Interrupt Controllers) but how do I turn it off?

When I run the Gutsy Gibbon ISO file, It does not encounter any errors until I try using the desktop. (it freezes at the splash screen after the login screen)

Basically, if you could answer these questions in their order of importance, that'd be dandy:

How would I turn of IO APIC?

How could I configure IO APIC to work?


Oh, and I nearly forgot to add: I am running on a HP Pavilion a1200y with a Intel Celeron D processor, a ATI Radeon Xpress 2000 card, and finally it was designed for XP :(

I will give additional information if requested.

Thanks.

(Finally, Feisty displays a Timer is not connected warning, but it boots fine)

Add **noapic** to the end of your Grub bootstring.

---

### Post by Taters on 2007-11-04
Um... How? I"m sorry, I only have a very basic understanding of the command line, so the "bootstring" is foreign to me....


Or should I just use Google?


Er.... I went to grub, pressed "c" for command line and entered

<grub> debug = apic
Entering debug
<grub> noapic
Error 27 Unknown command


Now it ignores my cd tray!

How can I undo that?

---

