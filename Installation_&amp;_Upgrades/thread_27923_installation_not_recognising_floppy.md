---
title: "installation not recognising floppy"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by mdbarton on 2005-04-18
Hello, just started using Ubuntu - downloaded the Live CD at the weekend, tried it and liked it so installed Ubuntu this morning before going to work.  All worked well, with the exception that I wanted to install Grub to a floppy disk.  This is because I already have grub installed to load Gentoo and WinXP.  Unfortunatelly the installer did not recognise my floppy disk or drive - it didn't even read the drive (I tried fd0 or /dev/fd0 as per the onscreen instructions, also tried /dev/fda, etc).

So, took a deep breath, installed it to my existing boot partition (which overwrote my existing grub config) - fortunately I was able to retrieve an old copy of the config file and add the gentoo entry back on to the new config.

Question is, why did the installer not recognise my floppy drive?  Alternatively, it would have been good if the installer could have just added entries to the existing Grub configuration.

Cheers
Matt

---

### Post by nad on 2005-04-18
I have several issues with the installer. The first being the overwrite first hardrive being the default install option.

Isn't there an option to install grub to your / filesystem? Floppy handling is broken in the installer also?

I will take a look later.

Dan M

---

