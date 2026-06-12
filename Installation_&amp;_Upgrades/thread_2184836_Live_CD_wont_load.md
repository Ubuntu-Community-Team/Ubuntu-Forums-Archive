---
title: "Live CD wont load"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2013-10-30
HP laptop runs great on 32bit OS (12.04 Precise) turns out to have 64bit CPU, but wont boot with 64bit version (12.10) of Ubuntu live CD. Should I download and burn a newer 64bit version (13.10)?

I checked the 64bit 12.10 version CD on another 64bit PC and it boots OK, so nothing wrong with CD. Ran 'uname -p' on a terminal and returned "i686" but 'uname -i' returned "386". So is it a 32bit CPU with 64bit capabilities?

---

### Post by fantab on 2013-10-31
It can't be. The CPU is either 32bit or 64bit. However 64bit CPU is backward compatible, which means you can install a 32bit OS on 64bit machine BUT not the other way round.

Run this command in your HP and post its output:
```
grep --color=always -iw lm /proc/cpuinfo
```

[https://help.ubuntu.com/community/32bit_and_64bit#How_to_Check](https://help.ubuntu.com/community/32bit_and_64bit#How_to_Check)

---

### Post by mayagrafix on 2013-10-31
Thanks for the great grep command. Very interesting. It returns a positive flag for 64 bit cpu, but after more research, the main board turns out to be only 32 bit capable (Wistron 30B2 mobo with intel Intel i945GM Northbridge chipset).

Ya learn something new everyday.

---

### Post by fantab on 2013-11-01
Intel 945 Graphics does not have the best of support in Linux. Search the forum and WWW for more info.

---

