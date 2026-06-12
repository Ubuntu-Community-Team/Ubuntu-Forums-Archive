---
title: "Installer crashed"
date: 2021-01-12
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2021-01-12
Hey all,

I am trying to install Ubuntu 20.04. It just stopped the installation and shows a message:

"We're sorry; the installer crashed. after you close this window we'll allow you to file a bug report using the integrated bug reporting tool.
This will gather information about your system and your installation process. The details will be sent to our bug tracker
and a developer will attend to the problem as soon as possible."

OK. So that's what it shows. When I started to install 20.04, I set it to erase all partitions and that's when the installer stopped and showed the message above. 

Does that mean I cannot start over to install 20.04? Can I drop back and use 20.04 as a live disk to find the problem? Or should I try to install 18.04 to see if I get the same error. Is getting a new hard drive a good option?

The system is older, with an AMD 9850 Phenom processor, 4 GB memory and a 650 GB HDD. I initially built the system, I installed Ubuntu 12.04. I later upgraded to version 14.04, and then up to 16.04. Everything worked well for a few years, but I decided to move up to version 20.04

When I started to install 20.04, I set it to erase all partitions and that's when the install stopped and showed the message above.

Any thoughts on how to fix this? Thanks.

---

### Post by ubfan1 on 2021-01-13
Did you hashcheck the downloaded ISO?  Media check used to be a choice on the live installer, to verify it.  Memory check also.  Then try running the live media in "try" mode, and partition the disk.

---

### Post by bcschmerker on 2021-01-20
**I've a Thread with a question related to this issue:**  "[[all_variants] Which bugs for CD installer crash attempting to install 3rd-party software?](https://ubuntuforums.org/showthread.php?t=2456855)"  I've a good CD for kubuntu 20.04.1-LTS Focal AMD64, as the disc self-check completed with no errors.

If your system is stable sans third-party drivers, re-attempt installation, leaving the "Install third-party drivers &c." box unchecked.  As of 20 January 2021 I'm awaiting a Reply on Bugs to track at Launchpad.

**Update:**  The installer misbehavior is being tracked as [Bug #1871268](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1871268).  As of 25 January 2021 several contributing factors are Fix Released, one In Progress; I consider the ISO itself as Fix Committed, Need Verification Focal / Groovy / Hirsute.

---

### Post by CelticWarrior on 2021-01-20
@bcschmerker

> [COLOR=#000000]I set it to erase all partitions and that's when the install stopped and showed the message above.[/COLOR]
is what's reported in the OP. Why do you think it has something to do with the third-party drivers, codecs, etc.?

---

### Post by bcschmerker on 2021-01-21
@[CelticWarrior](https://ubuntuforums.org/member.php?u=1826209)  **I'd traced it to an Installer misbehavior when third-party drivers are selected from the DVD**; the misbehavior is tracked as [Bug# 1871268](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1871268).  I got installed on open-source drivers and apt install'd the nVIDIA-390 packages after first reboot, but ran into a suspected Python 3 regression attempting to configure openlp after syntax-correcting the related *.py's.

@[Gnusboy](https://ubuntuforums.org/member.php?u=880166)  **My currently-down Hot Rod gPC has similar-generation hardware to your system,** with a GIGABYTE® GA-MA78GM-S2HP v2.0 (Advance Micro Devices® RS780G/SB700 chipset (integrated ATi® HD 3200 in northbridge), an AMD Athlon 64® 3500+ (Socket AM2; forced downgrade from an X2 5600+ that blew out its memory manager), and an ASUS® XONARESSENCESTX/A audio card on the ALSA snd-virtuoso driver), and no fewer than four SATA HDDs betwen two manufacturers plus one E-IDE DVD.  Knowing my way around the manual-partition section of installation, I normally re-use partitions, reserving the option to re-format them for upgrade filesystems.

---

### Post by CelticWarrior on 2021-01-21
[COLOR=#000000]@bcschmerker[/COLOR]

[COLOR=#000000]You're shoehorning your own issue in many places where it clearly doesn't fit. This is one of them because clearly the error happened before ANY actual installation. This is what I tried to hint about with the rhetorical question above. I'm sorry you didn't got the message. Not everything is suited for raising awareness for your specific issue that may or may not be related with what you think is the cause.[/COLOR]

---

