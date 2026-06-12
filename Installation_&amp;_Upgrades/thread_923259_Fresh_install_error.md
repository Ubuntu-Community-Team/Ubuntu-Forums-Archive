---
title: "Fresh install error"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by Adamrl018 on 2008-09-18
Hey guys, I'm a new user to Linux my friend told me to try it out since i was having so many issues with windows...

anyway I'm tring to install it i burnt the iso to a cd at 8x and i popped in my computer and it asks me to choose a language and every thing starts to load but then i get these messages:

[  57.225067]..MP-BIOS bug: 8254 timer not connected to IO-APIC
[  57.404000] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option

I have no idea what this means.
Help please? :]

---

### Post by Partyboi2 on 2008-09-18
At the main menu when you boot the ubuntu live cd press F6 and at the end add ```
noapic
``` then press enter and see if this works.

Or try and disable IO-APIC in your bios if you are able to

---

### Post by Adamrl018 on 2008-09-18
woooooooooooo thanks! you rock! :D

---

