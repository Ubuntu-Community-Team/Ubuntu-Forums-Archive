---
title: "Ubuntu IA64 hangs after loading ramdisk from cd"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by nickenzi on 2011-04-04
Hello, 
I'm trying to install Ubuntu IA64 onto an IBM eServer x455.  I've tried 10.04, 9.10, and 8.04.1 but they all hang after they load the ramdisk from the CD.  Is there something I can do to give them a kick in the right direction?  I tried 6.06.1 which begins to boot but results in a kernel panic during the boot process.  Is there an IA64 version of Feisty or Gutsy available that I can try?  I searched the web and the various Ubuntu archives, but no dice.  Any help would be greatly appreciated.
-Nick

---

### Post by sanderj on 2011-04-04
I know nothing about Itanium, but in general with boot problems, I would change the CD boot options and turn off boot options. 

Specifically: I would turn off ACPI (via ESC then F6 in the boot screen?), and check if the system boots. If not, turn off ACPI and more options, and try again.

PS: I'm sure not an Itanium system has ACPI (as it has no BIOS, right?). Anyway: turn off options ;-)

HTH

---

### Post by nickenzi on 2011-04-04
Well, I can't turn off ACPI since there isn't an option in the EFI configuration utility, and I just try to boot Ubunto from the CD with the default option ELILO gives me.

---

