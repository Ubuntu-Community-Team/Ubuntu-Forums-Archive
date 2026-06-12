---
title: "Unable to boot Ubuntu 6.06"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by Ocelsolid on 2007-09-27
I Have windows xp home edition, and got  ubuntu live cd , when i insert the disck then  start loading and  chose START OR INSTALL UBUNTU then this message came up:

 [36.419381] ..MP - BIOS bug: 8254 Timer not connected to IO - APIC [36.419381]  Kernel panic - not syncing:IO - APIC  + Timer doen't work! Boot with apic = debug and send a report then try booting with the 'noapac' option [36.419381].

I hope someone can solve my problem !:(

thankyou for taking your time to read this :)

---

### Post by Ocelsolid on 2007-09-27
Unable to boot ubuntu 6.06

---

### Post by ddrichardson on 2007-09-27
Do as the error message says, when the menu comes up, hit F6 and add the following to the end of the kernel line:```
noapic
```Many systems have problematic or non-standard APIC implementations.

Incidentaly this is not the forum to post this in - it's purely for feedback regarding the forum itself.

---

