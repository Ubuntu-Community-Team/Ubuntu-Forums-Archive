---
title: "Recompiling to 686"
date: 2005-01-02
forum: Installation &amp; Upgrades
---

### Post by giorgosc61 on 2005-01-02
Hello!

I have installed in ubuntu the linux-686 kernel. Is there a way to recompile gnome, firefox or even openoffice using the latest source code to get in that way the latest version and have this kind of software optimized for 686?

Thank you in advance

---

### Post by utanja on 2005-01-02
i would be interested in this answer as well......... :?:  :?:  :?:

---

### Post by sah on 2005-01-02
Why not just uninstall them, grab the source code tarballs, and do the make dance manually? man gcc for the right cflags to use for your arch.

---

### Post by randy on 2005-01-02
You'll have to rebuild the packages from the source packages after setting the cflags correctly.  If your looking for optimized packages (and some extra headaches for not much gain) you might be better off going with Gentoo, because you build everything from source and can specify cflags at build time.

---

