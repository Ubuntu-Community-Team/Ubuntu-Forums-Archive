---
title: "Kubuntu 6.06.1 i386 kernel panic"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by regtek on 2008-02-17
Good day,

so i just made a clean copy of Kubuntu 6.06.1 and it seems to be working fine while i start the installation from my laptop but while i insert the cd in my desktop and begin the installation process i get a 
->**..MP-BIOS bug: 8254 timer not connected to IO-APIC.**
->**Kernel panic - not syncing: IO-APIC + timer doesn't work! boot with apc=debug and send report. then try booting with 'noapic' option.**
my current MB is **680i SLI Chipset** if this is a BIOS related issue.

Thank you.

EDIT :: forgot to mention when i do boot from "noapic" option my system seems to freeze after loading all drivers and such at the loading screen.

---

### Post by borsten on 2008-02-17
you copied the system from another pc?
remember to update the root=/dev/whatever in your menu.lst.
in emergency use a live-cd/dvd and boot with root=/dev/whatever to boot your system, then maybe build another kernel

---

### Post by regtek on 2008-02-17
Thank you for replying,

no i didn't its a live cd what i meant was the cd was not defective since i used it on my laptop and it ran just find but on my desktop it ran into an error. i am just gonna assume that my motherboard is incompatible with that version of the O/S.  

so far i did the following workarounds: 
-> boot option "noapic nolapic" -> failure. 
-> disable IO-APIC from BIOS settings. -> failure.

although 7.10 works just fine. but i guess i find the older version a bit more stable. (i will learn to deal with it if there is no solution)

---

