---
title: "CD Won't Boot"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by gregscharrer on 2008-06-07
I have an Acer Aspire 5100 laptop. I burned an image of 8.04 on a CD using Infrarecorder and did the checksum. I successfully booted my desktop PC at work with the CD, but my laptop won't boot from it. I went into the BIOS and made the CD first on the boot list. My boot list from the BIOS is below.
1. USB CDROM
2. IDE 0
3. IDE 1
4. SATA
5. PCI BEV RealTek Boot Agent
6. USB HDD
7. USB FDD
8. USB Key

I enabled the boot menu so I could see the boot order prior to booting. It showed me this list.
2. IDE 0
3. IDE 1
5. PCI BEV RealTek Boot Agent

I also tried booting from the CD using my Windows XP backup. That didn't work either.

I'd like to have both Windows and Ubuntu on my laptop. Any ideas on how to get Ubuntu installed? Thanks

Greg

---

### Post by Partyboi2 on 2008-06-07
A work around you could try is [[COLOR=Blue]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/") which does not require a cd.

---

### Post by gregscharrer on 2008-06-07
Thanks. I read the info at the link, and it looks like just what I need. I downloaded it and ran it, though it cancelled the install because I want it to go to my D: drive and it only gave me the option of putting on C:, which looks like it would mess us Windows. I want a dual boot system. Any thoughts on that?

---

### Post by avtolle on 2008-06-07
Looking at the site, and the screenshots there, it looks like you could install to the D: drive if you select it there at the bottom under "custom". Don't know for sure if this is true, haven't tried it. I may have misunderstood you, and you did the d/l to D:, but the installer wants to install on C:; if this is what you are saying, someone else may be able to help you given my ignorance of how unetbootin works.

If, once it is downloaded, it acts like the CD, you should be able to select which drive upon which to install. Again, my lack of knowledge is showing, and I'll yield to those more knowledgeable.

---

### Post by gregscharrer on 2008-06-08
Thanks for the help. I took the easy way out and bought an 8Gb USB drive. I installed Ubuntu there and it booted right up. I appreciate the help. It says me hours of frustration.

---

