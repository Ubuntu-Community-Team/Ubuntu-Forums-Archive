---
title: "How can I modify the keyboard layout in Karmic ?"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by scotty64 on 2010-01-14
I am using KDE on Karmic and I have the (old) problem that my German Apple Aluminium Keyboard is wrongly mapped.
How do I modify keyboard layouts in Ubuntu 9.10 Karmic ? There used to be a collection of files under /etc/X11/xkb, but there is only one called "base.xml" that I do not understand at all.
I do not want to use Xmodmap as I only want to modify this particular layout.

---

### Post by filipvanlaenen on 2010-01-17
I just found out that the files are moved to a new dir: /usr/share/X11/xkb/symbols

---

### Post by scotty64 on 2010-01-19
> **filipvanlaenen said:**
> I just found out that the files are moved to a new dir: /usr/share/X11/xkb/symbols
thanks a lot, that solved it.

---

