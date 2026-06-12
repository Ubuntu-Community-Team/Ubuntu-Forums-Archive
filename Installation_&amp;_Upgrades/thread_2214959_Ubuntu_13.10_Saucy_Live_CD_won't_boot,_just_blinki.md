---
title: "Ubuntu 13.10 Saucy Live CD won't boot, just blinking cursor on black screen"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by mike4ubuntu on 2014-04-03
Ubuntu 13.10 Live CD won't boot, just blinking cursor on black screen.  I've been able to use this same Live CD to install Saucy 13.10 on other systems, but not on a system with Gigabyte GA-970A-DS3P motherboard with AMD64 processor, with a Gigabyte (nvidia) GEFORCE GT640 graphics adapter.  Is there something in the BIOS that needs to be configured to make this work?  The BIOS IOMMU is disabled and the CD has the boot priority.  It's an Asus DVD drive.

---

### Post by Kris_Spencer on 2014-04-04
Hello! 

A quick search tells me that you have an EFI system. You may want to see if disabling Secure Boot will resolve the issue. Sometimes it gets in the way. You can do that in the BIOS settings.

---

### Post by mike4ubuntu on 2014-04-04
actually, as it turns out, I had to enable IOMMU.  It was disabled by default in the BIOS.  I had read previously that it should be disabled for Ubuntu to work, but that is evidently not the case.  At least, not for the Trusty 14.04 DAILY build on 2014-04-04.

---

### Post by Kris_Spencer on 2014-04-05
Oh good! Glad that you solved the problem. Don't forget to mark the thread as solved.

---

