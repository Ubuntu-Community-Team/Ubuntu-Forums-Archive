---
title: "hangs with strange condition"
date: 2006-04-09
forum: Installation &amp; Upgrades
---

### Post by bobex on 2006-04-09
AMD_64 3000+
NVidia GeForce 6600 GT
512GB RAM (dual-channel)
Abit AN8-Ultra
NForce4 Chipset
80GB SATA WDC
80GB SATA Seagate
120 ATA maxtor

I install the breezy on 120 Maxtir. Installation works fine, then several minutes after login maybe about 10-15 minutes
x hangs, mouse cant be operated just x screen without nothing I can do. I've tried so many way i know, i've installed 5 times and put the the instalation on different pastition but has no effect.
after i login i push "alt+ctrl+f1" to check and yes there is something wrong there that i cant found in the terminal in X. after 15 minutes maybe when i work on something in the sametime in "alt+ctrl+f1" screen there is error : 

[4333333.309928] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[4454545.343434] hda: dma_intr: status=0x51 { DriveReadySeekComplete Error }
[4252352.345435] ide: failed opcode was : unknown

it always show up with diferent number but same error, that's why my ubuntu suddenly hangs. can you help me please, i'm desperate. is there any effect with my other drive or what.i always restart after 20 minutes to avoid hang.
I have no problem like this in fedora core 4 and mandriva 2006.1

thanks

---

### Post by Kapre on 2006-04-09
Seems like there is an error on your HD. Do a scandisk or reformat the HD (as is shows some error on it).

K

---

