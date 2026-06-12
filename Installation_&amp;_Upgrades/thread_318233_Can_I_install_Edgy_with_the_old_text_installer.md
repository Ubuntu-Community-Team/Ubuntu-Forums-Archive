---
title: "Can I install Edgy with the old text installer?"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by alieas on 2006-12-13
Can someone please tell me how to launch the old debian style text based installer with Edgy?

There doesn't seem to be any LVM support in the GUI-Install.

I've been using Breezy on this box for some time and really want to upgrade!!


Thank you

---

### Post by xabbott on 2006-12-13
Did you get the live cd or alternate?

---

### Post by maxamillion on 2006-12-13
If you would like to upgrade, you can do so via aptitude or apt-get with the dist-upgrade command after editing your sources.list to edgy. There are alternate methods, but most rely on update-manager which is currently having bug problems.

But if you want to do a fresh install with the text based debian-style installer then you will need an "alternate" installation cd instead of "desktop" (live/gui).

/me

---

