---
title: "Trying to get Ubuntu to install where I want it too."
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by Arukas on 2008-07-12
I have 200 gigs of unparition space on a hard drive and Ubuntu does not want to install there.  How can I make Ubuntu install there with a guided approach?  I do not know how to manually install what I want it too.

---

### Post by confused57 on 2008-07-13
> **Arukas said:**
> I have 200 gigs of unparition space on a hard drive and Ubuntu does not want to install there.  How can I make Ubuntu install there with a guided approach?  I do not know how to manually install what I want it too.
You can use an installed Ubuntu or the live cd, open a terminal and post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

Here's an excellent guide for partitioning basics:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Arukas on 2008-07-13
That does work.  Ubuntu wants to still install on my second drive.  Its doesn't want to install where I want it too.  And fdisking it doesn't help.

---

### Post by confused57 on 2008-07-13
> **Arukas said:**
> That does work.  Ubuntu wants to still install on my second drive.  Its doesn't want to install where I want it too.  And fdisking it doesn't help.
Did the output of the command I gave you earlier show the unpartitioned space?  If it does, you may be able to install Ubuntu using the manual partitioning option, which is relatively easy.

---

### Post by nline on 2008-07-13
I can't get it to recognize my EIDE WD120 Gb drive.  It recognizes the two 320Gb SATA drives and install there, but still does not recognize the EIDE drive.

---

