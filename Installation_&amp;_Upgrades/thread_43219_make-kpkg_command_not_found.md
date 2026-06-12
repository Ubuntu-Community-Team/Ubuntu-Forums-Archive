---
title: "make-kpkg: command not found"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by tseliot on 2005-06-21
Hi guys, I'm trying to compile a new kernel but here's what I get when I prompt:

sudo make-kpkg clean

make-kpkg: command not found

What's wrong?

(I'm following this HOWTO [http://www.ubuntuforums.org/showthread.php?t=43065&highlight=kernel+2.6.12](http://www.ubuntuforums.org/showthread.php?t=43065&highlight=kernel+2.6.12)

---

### Post by Xian on 2005-06-21
In Debian the "make kpkg" command is made available through the 'kernel-package' package, which is available in Synaptic. Check to see if this is also listed in Ubuntu.

---

### Post by tseliot on 2005-06-21
Thanks, this works!

---

