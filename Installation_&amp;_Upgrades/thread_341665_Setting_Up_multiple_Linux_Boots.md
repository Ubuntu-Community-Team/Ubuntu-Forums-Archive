---
title: "Setting Up multiple Linux Boots"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by arthurbarnhouse on 2007-01-18
I need to have Mandriva Linux installed for some work I'm doing for various classes, but I want to have Ubuntu Installed on my laptop as well.  I redid the partition table giving each installation a swap file, and setting both of them as primary, but when I start the computer it only gives me the option to Boot into mandriva.  Does anyone know what I need to be doing?

---

### Post by confused57 on 2007-01-19
What you might want to do is install Ubuntu's grub to the mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Ubuntu should recognize Mandriva(which I assume uses grub, not lilo) and automatically add an entry to boot Mandriva...just in case it doesn't, you might want to write down the exact entries in Mandriva's grub and you can manually add an entry to Ubuntu's grub.

You can use the same swap partition for both OS, but separate swaps work also.

---

### Post by Wim Sturkenboom on 2007-01-19
No answer to the question, but swap partitions can be shared between different distros.

---

### Post by SectionThree on 2007-01-19
> **Wim Sturkenboom said:**
> No answer to the question, but swap partitions can be shared between different distros.
This might, for some irrational reason, be the answer to the question. If not, try a different bootloader.

---

