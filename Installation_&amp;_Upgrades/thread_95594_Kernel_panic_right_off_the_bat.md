---
title: "Kernel panic right off the bat"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by chriszuma on 2005-11-26
When I boot from the CD to try to install the AMD64 version, right after I hit enter on the boot prompt, it gives me this error: <0>kernel panic - not syncing: Aiee, killing interrupt handler!

I'm running on an Athlon 64 3500+ in my Shuttle ST20G5. Anyone have any idea what's going on here?

---

### Post by taurus on 2005-11-26
It could be that there is something wrong with your CD!  Before you burned it to a CD, did you run checksum on the iso image first?  Also, try to burn it at a slower speed, 4X maybe...

---

### Post by varcsscotty on 2005-11-30
just to add to this...I also have AMD64 version....got a Kernel Panic when trying to bootup.  It worked before. but now can't get it to work. running and AMD64 Athlon 3000+.

*I thinks it's trying to tell me to do my hw...heehee*

---

### Post by ALK13 on 2005-12-14
it's a problem with acpi... to solve it, boot with acpi=off and noapic.

"Boot : linux acpi=off noapic"

ALK13

---

### Post by jeremym on 2005-12-14
i also am getting a kernel panic when trying to install. I posted something this morning about it with a screenshot attached. Do you think this is the resolution to my problem as well?

---

