---
title: "How to install Smart card support for Evolution"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by Luk__ on 2010-10-16
I configure Smard cart opensc by this configuration manual
[http://www.opensc-project.org/opensc/wiki/EvolutionSteps](http://www.opensc-project.org/opensc/wiki/EvolutionSteps)
but Evolution not view my smart card.

---

### Post by Luk__ on 2010-10-17
Resolve problem need to add in /home/rosen/.pki/nssdb/pkcs11.txt

library=/usr/lib/onepin-opensc-pkcs11.so
name=OpenSC

---

