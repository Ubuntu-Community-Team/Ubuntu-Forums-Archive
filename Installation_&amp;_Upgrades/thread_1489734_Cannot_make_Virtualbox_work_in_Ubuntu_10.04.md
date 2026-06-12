---
title: "Cannot make Virtualbox work in Ubuntu 10.04"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by enverhoxha on 2010-05-21
I cannot make Virtualbox work in Ubuntu 10.04 (upgraded from Ubuntu 8.04). I tried both to install Virtualbox OSE from Package Manager and Virtualbox 3.2 downloaded from the Virtualbox site (32 bits version, as my OS). Installation is OK, but when I try to run it, I get an error message:
      Error in home/…/.virtualbox.xml (line3) — cannot handle settings version ‘1.2-linux’.
      Code: NS_ERROR_FAILURE (0×80004005).
      Got an idea?
Virtualbox would be good because it allows running some Windows applications or games. Wine seems useless, only a couple of applications run in Wine and practically no games. It keeps warning me about DirectX etc. I can't understand why Wine exists at all.

---

### Post by Jose Catre-Vandis on 2010-05-21
In version 3.18 that line is looking for 1.9 linux.

Try editing the Virtualbox.xml and changing 1.2 to 1.9 and see what happens.

You also may have some "leftovers" so if you uninistall do a search for anything virtualbox on your system before installing again

---

### Post by enverhoxha on 2010-05-23
The change in VirtualBox.xml worked. Thanks!

---

