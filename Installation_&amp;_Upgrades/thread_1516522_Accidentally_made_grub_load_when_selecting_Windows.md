---
title: "Accidentally made grub load when selecting Windows 7 at boot"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by Zalastax on 2010-06-23
When updating to latest ubuntu version I accidentally picked to install grub on dev/sda1 (Windows 7 partition)
Now when I select Windows 7 in boot menu, another grub boot menu appears and if I select Windows 7 there it happens again, and again and so on.

What can I do to delete the grub that prevent Windows from booting?
Can I make grub boot without the need of the Windows boot?
I can look in the Windows partition and everything seems right and I can't find any grub files, but still the problem is there.

---

### Post by darkod on 2010-06-23
Use this procedure to remove grub2 from /dev/sda1:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, that's partition #1 on disk /dev/sda.

---

### Post by Zalastax on 2010-06-24
Thanks!
It worked like a charm.

---

