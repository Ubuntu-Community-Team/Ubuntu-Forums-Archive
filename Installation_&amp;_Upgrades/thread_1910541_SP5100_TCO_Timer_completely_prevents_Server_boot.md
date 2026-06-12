---
title: "SP5100 TCO Timer completely prevents Server boot"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by LeaffyLeif on 2012-01-17
Hi all, I'm Leif!

I've recently made the decision to migrate my Server from Windows Server 2008 R2 to Ubuntu Server 11.10 (both 64-bit). A short hand list of specs:

CPU: AMD Athlon II x2 7550 @ 2.5GHz
GPU: ATI Radeon HD5450 (512MB GDDR3)
RAM: 4GB DDR2 800MHz
System HD: 40GB Seagate
Storage HD: 2TB Samsung F4
WLAN 1: Atheros card (works fine)
WLAN 2: Edimax card (not detected, but whatever)

It spends about 8 seconds booting into "Ubuntu, with Linux 3.0.0.24 Kernel" before hitting "SP5100 TCO Timer: mmio address 0xfec000f0 in use". It halts there, and nothing happens.

I've gone into the recovery kernel, tried blacklisting SP5100_tco however it says it isn't found. I've also tried apt-get remove'ing the graphics driver (as I'm aware the SP5100 is linked to my GPU) but apt-get claims that the it can't access its source list or something - whatever happens it won't run.

Can anyone shed any kind of light on this? I never expected this to be smooth, but I certainly didn't anticipate a system breaking error ...

Anywho, thanks in advance..

[edit] Kernel version is in fact 3.0.0.12-Server. My bad. SP5100_tco apparently doesn't exist, and neither does the xorg.conf, so my guess is it's directly related to something completely different...

---

### Post by LeaffyLeif on 2012-01-17
Update:

Tried a Ubuntu desktop 11.10 LiveCD, got to the boot menu, selected language and "Try Ubuntu without Installing". Hit Enter, few seconds later (after some standard issue underscore flashing) I get some lovely purple and green graphical distortion. Definitely GPU related.

Update 2:

Downloading the verbose installer...

Update 3:

Trying a 32-bit verbose...

Update 4:

32-bit no longer displays SP5100 error, but hangs at "k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled"

Gah :(

---

