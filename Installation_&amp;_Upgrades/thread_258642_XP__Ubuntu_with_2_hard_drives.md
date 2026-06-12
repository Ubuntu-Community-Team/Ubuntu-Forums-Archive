---
title: "XP / Ubuntu with 2 hard drives"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by Anorak on 2006-09-16
I currently have Windows XP Pro on 1 IDE hard drive, and I bought a new SATA hard drive that I want both XP (NTFS) and Ubuntu (EXT3) to run off of, using the IDE drive as FAT32, for sharing files.  The question I have is, when I install XP Pro on the SATA drive first, will it mess up the existing IDE (that'll still have XP Pro), creating problems with the boot?

Or is there a way I can format the IDE and the SATA at the same time (through the XP installer?)?

---

### Post by donniep152 on 2006-09-16
my experience with this situation is it's always better to unplug your ide drive, install XP on to your sata drive, then install Ubuntu and use Ubuntu's grub loader.  Replug your ide in, set your sata up as master and your ide as secondary.  Then you should be able to boot into xp or ubuntu and still have access to your ide.  Try searching these forums for answers also as there is a wealth of info. here.

---

