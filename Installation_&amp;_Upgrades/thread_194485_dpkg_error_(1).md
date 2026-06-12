---
title: "dpkg error (1)"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by spaulson on 2006-06-11
Tried to upgrade from Breezy to 6.06.  Everything went fine until  I go the following message.

Errors were encountered while processing:
/var/cache/apt/archives/ia32-libs_1.4/ubuntu19-amd64.deb
sub-process /usr/bin/dpkg returns and error code (1)

I then got the alternate CD and went into recovery mode.  Got a shell and did and apt-get dist-upgrade -f to try and upgrade from the CD.  This resulted in the same message.

Anyone else run into this ?
Any sugestions ?

Thanx

---

### Post by sinkxdie on 2006-06-11
Wait that was the error message?
That doesn't give any details on the problem.

---

### Post by spaulson on 2006-06-11
Found this message burried in all the output

dpkg-divert: rename involves overwriting `/usr/bin/ldd' with different file `/usr/bin/ldd/amd64', not allowed

I set permmisions to 777 on ldd, but this had no effect.

---

### Post by spaulson on 2006-06-12
Solved this problem by renaming /usr/bin/ldd to /usr/bin/ldd.bak

This allowed the upgrade to continue.  System working now

---

