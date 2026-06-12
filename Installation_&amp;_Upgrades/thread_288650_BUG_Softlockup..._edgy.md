---
title: "BUG Softlockup... edgy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by jf18 on 2006-10-30
Hi!

as soon as available I installed UBUNTU Edgy 6.10 on my Dell Inspiron 6400 (2Gb mem).
Everything went pretty smooth appart for a relatively slow boot... (slower than 6.06)
After a few days I hit the following snag at boot:
the process completely hangs, I rebooted two or three times and then tried  the recovery boot, which showed that the problem is when configuring the network interfaces:

Bug Soft Lockup detected on cpu#0 

(fwiw, the 6400 has a centrino duo chip).
Almost desperate, I followed some suggestion found on the web: several consecutive boots more!! I cannot believe it! When I try to escape the infamous alt-ctrl-del windows attitude.... this is what I get to!?
Appartently after 5 more trials it worked. BUT my wireless card does no longer show up in the networking configuration window... (for the moment I can live without it but I find this pretty frustrating!!!).
Any clue?
Thanks in advance,
JF

---

### Post by finite9 on 2006-12-04
might be the same bug as is registered on lauchpad (search for "BUG: soft lockup detected on CPU#0!")


I have this problem too :( has to do with wireless device not being activated during boot: Edgy cannot handle that situation.

Forced to reinstall Dapper until issues is fixed.

---

