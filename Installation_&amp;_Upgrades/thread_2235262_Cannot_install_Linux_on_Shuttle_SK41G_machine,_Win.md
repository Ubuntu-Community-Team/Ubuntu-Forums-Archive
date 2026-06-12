---
title: "Cannot install Linux on Shuttle SK41G machine, Windows XP works, not syncing"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by Richard_Fleming on 2014-07-19
chipset: km266 vt2835

I have tried to install Lubuntu (two different CD-ROMs, one IDE and one USB), Peppermint (two different CD-ROMs, one IDE and one USB), and Crunchbang (USB flash drive). 

None of them will install. Lubuntu gets to the screen where I can select Install but then the word Lubuntu appears with a progress indicator but the installer gets no further. Instead it gives me a kernel panic:

kernel panic - not syncing: attempting to kill init! exitcode=0x00007f00

cpu: 0 PID: 1 Comm: init not tainted 3.13.0-24-generic #46-Ubuntu
hardware name: VIA Technologies, Inc. KM266-8235/Fx41, BIOS 6.00 PG 12/08/2003
00000000 0000000 ee091f1c c164b873 c192fe00 ee091f3c c16469ac c1826f5c
c1aa5c80 ee091f28 c192fe00 c0086c40 ee058000 ee091f8c c105911f c1827280
00007f00 00000004 b772bf08  00000001 00000020 00000000 00000000 ed4a2c88
call trace:
[<c164b873>] dump_stack+0x41/0x52

and so on (I didn't copy down everything)


------

I am a Linux beginner. The only thing I can think of that may be causing these problems, other than that the chipset isn't supported (which doesn't seem to be the case) is that the onboard NIC is causing the trouble since it is defective (replaced with a PCI NIC). I tried bypassing the ProSavage onboard video by installing an AGP Radeon 2400 Pro but that didn't fix the problem.

---

### Post by Richard_Fleming on 2014-07-20
I tried making an Xubuntu USB drive and booting from it and got this:

[IMG]http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png[/IMG]

---

### Post by Richard_Fleming on 2014-07-20
Unbelievably, Xubuntu installed and seems to be working with no problems so far. I tried Lubuntu, Peppermint, Crunchbang, and even GhostBSD 3.5.

---

