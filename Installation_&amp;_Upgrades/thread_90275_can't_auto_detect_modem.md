---
title: "can't auto detect modem"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by tatt2d26 on 2005-11-14
i finally got 5.04 to work on this machine but now i cant use my modem...it's on com 3 tried settin it manually and auto detect..no luck....any ideas?

---

### Post by Lambert on 2005-11-14
Did you try the wiki?

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=modem&titlesearch=Titles]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=modem&titlesearch=Titles")

---

### Post by Kapre on 2005-11-14
[QUOTE=tatt2d26]i finally got 5.04 to work on this machine but now i cant use my modem...it's on com 3 tried settin it manually and auto detect..no luck....any ideas?[/QUOTE]

Is your modem an internal one? Most of the internal modems are not detected by Linux (as there is no driver made for them in linux). Check the Hoary guide (that's on my signature below) and look for the modem utility to scan what type of modem you have.

K

---

### Post by az on 2005-11-14
[QUOTE=Kapre]Is your modem an internal one? Most of the internal modems are not detected by Linux (as there is no driver made for them in linux). Check the Hoary guide (that's on my signature below) and look for the modem utility to scan what type of modem you have.

K[/QUOTE]
Lucent, Intel, Agere, some others have linux drivers.  they are just not on your cd.

If it is an internal hardware modem, then it may be configured by alsa as /dev/ttyS14.  Try that, since it still may not autodetect it as such.

---

