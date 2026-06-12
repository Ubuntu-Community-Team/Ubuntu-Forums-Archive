---
title: "The drive appears confused."
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by elpresidente on 2006-06-29
Just purchased some parts to build a new PC for the wife with intention of moving her to Linux (which she agreed to). I am, however, getting a "The drive appears confused" error. 

Parts I am using:

Asus P5LD2-VM motherboard
Pentium D 2.66
Seagate 160Gb SATA drive
NEC DVD burner
Sony DVD-rom

I am also using the amd64 (em2t?)  iso.

Any suggestions?

---

### Post by taurus on 2006-06-29
Is Pentium D a 64bit???

---

### Post by elpresidente on 2006-06-29
[QUOTE=taurus]Is Pentium D a 64bit???[/QUOTE]

Pentium D Processor 805 2.66 Ghz - supports EM64T - 64 bit.

I was able to get it installed (used Xubuntu 6.06 - 64 bit) with the acpi=ht option. Problem I have now is that it hangs when GDM is killed, via ctrl-alt-bs, logout, restart, or sudo killall gdm. Any suggestions about that would be great.

---

### Post by Tantawi on 2006-06-30
I had the same problem, and fixed it by disabiling the SATA controller! but it still stucks at "Loading Hardware Drivers" :(

- Intel Pentium 4 2.80E GHz @ 3.06 GHz.
- MSI Neo2-P Platinum Edition. (Intel i865PE).
- 1 GB Elixir PC3200 DDR400 Dual-Channel @ DDR438.
- PNY GeForce 6600GT 128 MB AGP8x @ 530 Mhz / 1 GHz.
- 160 GB WD Caviar SE SATA + 2x80 GB WD Caviar PATA.
- NEC ND-3540 16x DVD-RW.
- Lite-On 16x DVD-ROM.
- 19" ViewSonic VA912 DVI-D LCD.

---

