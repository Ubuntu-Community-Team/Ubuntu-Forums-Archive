---
title: "[SOLVED] Installation Help: Ubuntu Installer Dies on My Hardware"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by svet-am on 2007-12-19
Since this is mostly about hardware compatibility, I'll list my specs first:

AMD Athlon FX-62 @ Stock (cooled by Zalman 9700)
Gigabyte GA-M59SLI-S5 (nVidia 590 SLI)
4x1GB Mushkin DDR2
eVGA 8800GTX SuperClocked
500GB 7200 WD Caviar SATA
Audigy2 ZS with LiveDrive
Plextor SATA DVD-RW
Sony PATA DVD-ROM

This hardware can install and run Fedora Core 8 just fine.  However, whenever I try either the x32 or the x64 installer CDs, I get the dreaded "kernel alive" message and then the installer hangs.  I've tried booting with various permutations of the ACPI and APIC bootloader options with no help.  The CDs I'm using are not ISO-burned, but rather officially pressed discs straight from Canonical.

I'm a newb on these boards because I've piddled with Ubuntu on my laptop off and on for a while.  However, I've been runing Linux (mostly CentOS or Fedora or SuSE) since about 2000.

Any guidance on what I need to do to make this work would be appreciated.

---

### Post by PmDematagoda on 2007-12-19
I would suggest that you give the Alternate CD a try, it can be downloaded from [here]("http://www.ubuntu.com/getubuntu"), just check the checkbox near the end of the page to download it.

The Alternate CD is the text-based installer for Ubuntu and is used in situations where the normal Live CD does not work.

---

### Post by wpshooter on 2007-12-19
Even though the CD is straight from Canonical, did you run the CD integrity check function that is found on the initial Ubuntu boot screen menu ?

---

### Post by svet-am on 2007-12-19
found an answer buried in a different thread.  thanks for the replies, though.  turns out I need to disable to boot splash as that appears to be what's killing it.

---

