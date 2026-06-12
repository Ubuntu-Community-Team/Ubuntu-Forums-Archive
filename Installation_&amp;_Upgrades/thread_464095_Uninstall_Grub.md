---
title: "Uninstall Grub?"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by paraplier on 2007-06-04
I have uninstalled 7.04  from within a Vista dual boot but Grub lurks and hangs at startup. I managed to overwrite Grub with a different boot selector software but still need to remove Grub. Any ideas, suggestions, search terms are greatly appreciated.

TIA,
paraplier

---

### Post by nereid on 2007-06-04
Linux is completly gone from your system? Then, if Vista still has the format command, a simple

```

format /mbr

```

should do the trick, but please read the format documentation first. I don't know if anything changed from Win 2k or XP to Vista.

---

### Post by paraplier on 2007-06-04
Thanks. Makes perfect sense.

Paraplier

---

### Post by Frederick J. Harris on 2007-06-04
I don't believe...

format /mbr

exists.  There is a...

fdisk /mbr

...which isn't documented by MS, but is oftentimes used, I think.  However, I don't believe it will work on anything but a FAT16 (maybe FAT32???) disk.

---

### Post by louieb on 2007-06-05
> **paraplier said:**
> ... managed to overwrite Grub with a different boot selector software ... 
Does it boot straight to VISA now? If so GRUB is gone.

---

