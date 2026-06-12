---
title: "Installed UNR 10.04 will not boot"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by cdforehand on 2010-05-24
I intalled UNR 10.04 onto my netbook with windows and it booted up fine. So I decided to completely erase the windows drive and use UNR solely. I installed it and hit the restart and it'll shut down, then come up with a the eMachines logo then it goes to a black screen with a flashing cursor. That will flash two or three times, then stop for a few seconds, then it starts all over again. It won't go any further, if I want to do anything I have to shut it down and boot from my LiveUSB.

Here are the specs for my netbook:

[INDENT]eMachines eM250

VGA BIOS Version: Intel V1585
System Bios Version: V1.25

CPU Type: Inter Atom n270 @ 1.60Ghz

Ram: 1Gb

Hard Drive: 160Gb[/INDENT]

I would appreciate any help. Thanks!

---

### Post by darkod on 2010-05-24
I think grub2 is looking at the wrong place now because of the previous install.

Use these instructions for 9.10 and beyond, to reinstall grub2 on the MBR of the disk from live mode:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

