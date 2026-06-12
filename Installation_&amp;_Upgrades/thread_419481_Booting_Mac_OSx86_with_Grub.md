---
title: "Booting Mac OSx86 with Grub"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by topnotchvariable on 2007-04-23
I'm triple booting my laptop XP/Ubuntu/OSx86

All work fine but my boot loader isn't working they way i want it. I'm trying to use grub to boot but for some reason it does not like OSx

this is the section of my menu.lst file that is giving me trouble:

title XP
root (hd0,0)
chainloader +1
boot

title OSx86
root (hd0,3)
makeactive *******************<I believe this is the problem>
chainloader +1
boot


XP boots fine and Ubuntu boots fine but whenever I place the makeactive statement in the boot loader it Hijacks my MBR and defaults to that specific partition, in my case OSx. But without that statement selecting OSx86 simply defaults back to the grub menu.

Now I could use chain0 but would prefer GRUB if possible due to my inexperience with OSx86 let alone OS X altogether. What I want is to have the grub menu load up I select my OS and no further actions needed until I need to login to whatever OS I booted, I've found with Chain0 I need to tell it to load startup options then I can select my OS. Well like I said I would like to use GRUB because it is more stable then chain0 (because of the nature of OSx86) but if all else fails looks like chain0 would have to be the option

can anyone help me?

I've also thought about the chainloader /chain0 option but have no idea where to place the chain0 file on the ubuntu partition, and I have tried chainloader force+1 option (same out come as chainloader +1)

p.s I'm using Windows XP Pro, Ubuntu 6.10 and JaS OSx86 10.4.7 on an IBM Thinkpad R60 (intel centrino duo, 1gb ram, 80gb Toshiba SATA HD, Radeon Mobility x1600 PCIE) I believe that is all the relevant info about my system.

---

### Post by mikawber on 2008-01-15
Did you get this to work? I'm having the same exact problem

---

### Post by topnotchvariable on 2008-02-12
Do not try booting OSX 86 with grub it will now work, but it works perfectly if you use either chain0 and make OSX your boot partition or you use the XP bootloader

---

