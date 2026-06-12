---
title: "Installation/live-eval problem"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by Scynet on 2008-05-17
Hello.

I just added my laptop hard drive (SATA) to my desktop PC. I formatted the drive in Vista, it's now in NTFS format and Vista sees it just fine.

The problem is, I can't even boot to Ubuntu with either 7.04 or 8.04 live-eval CDs. I get this (the list of numbers seems to change):

(initramfs) [   103.34816] ata3.01: revalidation failed (errno=-5)
[   110.051796] ata1: irq_stat 0x000000040, connection status changed
[   110.051851] ata1: SErrpr: { DevExch }
[   138.506235] ata3.01: revalidation failed (errno=-5)
[   173.664612] ata3.01: revalidation failed (errno=-5)
[   174.168066] ata3.01: revalidation failed (errno=-5)
[   209.310264] ata3.01: revalidation failed (errno=-5)
...
...

what's the problem? Any fixes?

EDIT: ATA3 should be the new HDD.

---

