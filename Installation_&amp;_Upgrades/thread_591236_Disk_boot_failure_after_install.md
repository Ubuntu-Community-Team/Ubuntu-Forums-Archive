---
title: "Disk boot failure after install"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by GodsDead on 2007-10-25
hey there i see many posts around the forums to do with this subject but i cant sort it out!
Got given a system that had a blown PSU, so i got a new one and got the system working, used my live ubuntu CD - 6.06, that works, the system is working fine, install went fine, it just wnt bloody boot from the hdd with the os!?
so heres the specs of the PC and i have included a photo of the screen.
2.4 Ghz processor
Tiny 10gb HDD :S (don't have another one spare)
256mb ram
gerforce gfx card

never used ubuntu proeprly before, please help me get it sorted, so i can enjoy it!!


oh and im new to the forums hi all!:guitar:

---

### Post by wolfen69 on 2007-10-25
did you check the BIOS settings?

---

### Post by GodsDead on 2007-10-25
> **wolfen69 said:**
> did you check the BIOS settings?

yea i have, changed the boot priority's around, from booting from cd to HDD-0 so its like this
1 - HDD-0 (tried 1)
2 - CD
3 - USB

:S

---

### Post by GodsDead on 2007-10-25
I GOT IT WORKING!
i put in nan old 18gb i found as a slave.. second HDD and it all worked 0_o any idea why?

Also, its full of crap, and i cant acccess it in ubuntu at all.. its l reconised any everything.. how would i wipe it and use it as a secondary HDD? 
once i have done this im going to need to be able to "share" this drive throughout my home network, iv heard of a programme called samba?
Would that do it?

---

### Post by Kuptis on 2007-10-25
I'm having the same problem and my screen looks very similar to the one godsdead posted.  I've tried everything I can think of such as installing several times and using Knoppix (don't have Windows and don't want it [can't afford it]) to look at what's on the disk.  Under Knoppix I can mount it and view the files/directories and use gparted to view the partitions.  Everything looks OK but I get the same message.

I have a Biostar GF7050V-M7 motherboard with 2GB RAM.  The HDD is IDE with 61GB (can't afford a SATA drive yet).  I'm using the server version of Ubuntu (Feisty Fawn).  CPU is Intel Dual-Core E2140 Allendale 1.6GHz.

Anything else y'all need to know to help me out?

BTW... I also tried using a floppy boot disk with SMB (or is it SBM?) and it doesn't work that way either.

The HDD is from an e-machine.

**[COLOR="Red"]My problem has been resolved.[/COLOR]**

---

