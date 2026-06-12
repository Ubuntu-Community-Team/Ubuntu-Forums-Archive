---
title: "Firebird 2.1 and FreeAdhocUDF"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by faustobm on 2009-11-27
Hi,

After install ubuntu 9.10 and firebird 2.1 I had problems to use freeadhocUDF.
I found solution in firebird BUG TRACK.

1 - Install Firebird

sudo apt-get install firebird2.1-super
sudo dpkg-reconfigure firebird2.1-super

2 - Download and install FreeAdhocUDF

3 - Copy libib_util.so to /usr/lib
cp /usr/lib/firebird/2.1/lib/libib_util.so /usr/lib.

---

