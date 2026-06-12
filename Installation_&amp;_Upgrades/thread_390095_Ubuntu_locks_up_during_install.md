---
title: "Ubuntu locks up during install"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by archer75 on 2007-03-21
I have tried both Ubuntu 6.10 and Ultimate Ubuntu 1.3

System Specs:

Intel Core 2 Duo e6600
Motherboard: DFI Infinity 975x
Video card: Radeon x1900xtx
Soundblaster X-Fi(using onboard realtek for linux)
Optical: NEC 3520
Optical: NEC 3550

Hard Drives:
Belkin Raid controller card 2x250gb Seagate
Highpoint Raid controller card 2x160gb Seagate
4 onboard intel SATA2 ports:
150gb WD raptor
74gb WD raptor
2x500gb Seagate
Ubuntu detects all drives except those on the highpoint card which is unusual as it's the one that has linux drivers. The belkin that is detected as no linux drivers that i'm aware of.

Windows is on the 150gb drive and i'm installing ubuntu on the 74gb drive.

The problem is during install it locks up at various points and the system has to be rebooted. 

The first time it locked up at 16%, second time at 22% then 23%, followed by 39% with another lockup at 45%. 
It doesn't matter which install disk I use, it still locks up during install at various locations.
I have tested with and without the highpoint card in. No difference. 

Any ideas?

---

### Post by wpshooter on 2007-03-21
Did you check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by archer75 on 2007-03-21
> **wpshooter said:**
> Did you check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

yes.

And I tried booting with safe graphics mode. No difference.

---

### Post by wpshooter on 2007-03-21
Are you trying the 64 bit versions or the 32 bit version ?

---

### Post by archer75 on 2007-03-21
> **wpshooter said:**
> Are you trying the 64 bit versions or the 32 bit version ?

32bit

---

### Post by wpshooter on 2007-03-21
Try the ALTERNATE (text based) install CD.

---

