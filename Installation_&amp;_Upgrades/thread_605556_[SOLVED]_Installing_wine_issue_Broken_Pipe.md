---
title: "[SOLVED] Installing wine issue: Broken Pipe"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by Albertahawk on 2007-11-07
Having an issue installing wine (I was downgrading, CS:S wont start).
Ive had this before but forget the command to fix it, it may have been purge.

dpkg-deb: subproces paste killed by signal (Broken Pipe)

[SOLVED]
Look closer at the terminal spouted error, ended up purging libwine:

apt-get remove --purge wine libwine

---

