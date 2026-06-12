---
title: "Is it possible to mis-detect Vista when installing Grub?"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by Smithernz on 2010-07-06
Hi, I'm not really sure if this is the right place for this, but it seems the best-suited. I recently installed Ubuntu Studio on my PC, dual-booting it with Vista. Once the installation had finished, and I had rebooted, Grub showed the two Vista options:

Windows Vista (loader)
Windows Recovery Environment (loader)

When I load up "Windows Vista (loader)" it opens my Acer eRecovery Management, but when I load "Windows Recovery Environment (loader)" it opens what looks like a normal version of Vista. Is it possible that on installation, Grub accidentally swapped the two around, or have I probably mucked up my computer?

Also, if this wasn't the place to post this problem, where would have been better?

Thanks!

---

### Post by darkod on 2010-07-06
Yes, it's mis-detection. Grub2 only detects the boot files and tries to "guess" which OS it is. But depending how the boot files were created, it can guess wrong. :)

I don't think you did anything wrong.

---

### Post by Smithernz on 2010-07-06
Oh good, that's a real relief. Thanks very much!

---

