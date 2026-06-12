---
title: "wont boot after fresh install"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by dmallion on 2013-02-07
So I did a fresh install of Debian 7 wheezy i386. It worked fine but when I selected Debian in grub it boots to this error.

---

### Post by PowerBarry43 on 2013-02-07
Hi

That my friend is a kernel panic! normally this is pretty bad news and can point to hardware incompatibility. If possible I'd try 64 bit or if you can boot into a live cd and chroot in you could have a go at installing a later kernel which can sometimes get you out of kernel panics.

Hope this helps and good luck!

Barry

---

### Post by dmallion on 2013-02-07
This is a really old computer. It is not 64bit. It wouldn't even boot most 32bit live CDs that weren't i386. When I chroot do I need to install special kernel?

---

