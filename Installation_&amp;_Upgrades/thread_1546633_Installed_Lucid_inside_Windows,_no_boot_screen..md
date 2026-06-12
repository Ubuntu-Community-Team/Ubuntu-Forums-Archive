---
title: "Installed Lucid inside Windows, no boot screen."
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by Meganehmbee on 2010-08-05
I recently installed Lucid Lynx inside my Windows XP using Wubi. When I restart I don't have a boot screen giving me the option to boot into either or, it just boots directly into XP.

How do I fix this so I can boot into Lucid?

---

### Post by bcbc on 2010-08-05
> **Meganehmbee said:**
> I recently installed Lucid Lynx inside my Windows XP using Wubi. When I restart I don't have a boot screen giving me the option to boot into either or, it just boots directly into XP.

How do I fix this so I can boot into Lucid?

There's supposed to be an entry added to c:\boot.ini when you install. The actual install (ubuntu installed to the virtual disk) requires it, so likely you've just downloaded the cd image and created the virtual disk i.e. no bootable ubuntu. So you will have to reinstall.

To see what might have gone wrong, open windows explorer, enter %temp% on the address bar, find and open the wubi log file and look for any errors or post the contents here (within [CODE[SIZE="1"] [/SIZE]][/CODE] tags).

---

