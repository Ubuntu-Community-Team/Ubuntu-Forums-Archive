---
title: "wubi doesn't work; booting from CD won't work."
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by Instrument on 2008-06-19
I tried all of the bootparameters I know, and each time I would get this:

init: rcS main process (5846) killed by SEGV signal
init: unable to execute "/bin/sh" for rc-default: no such file or whatnot found
init:rc-default main process (7131) terminated with status 255


I've been trying for a week now to install ubuntu, how can I work around this?

---

### Post by Instrument on 2008-06-19
bump

---

### Post by cod3rbro on 2008-06-19
If you want to install Ubuntu from cd, your RAM at least should 256 mb

---

### Post by orenk on 2008-06-20
I'm trying to install ubuntu 8.04 from CD (Normal, and OEM Modes)
same thing happens to me... Cant install it.

init: rcS main process (5138) killed by SEGV signal
init: unable to execute "/bin/sh" for rc-default: no such file or whatnot found
init:rc-default main process (6277) terminated with status 255

_H.W. Spec:_
1Gb Ram
80Gb H.D.D
2000MHz Pentium 4
Chipset 865GM-L asrock (Motherboard)

Ubuntu 7.10 works like a charm...

---

### Post by Instrument on 2008-06-24
> **cod3rbro said:**
> If you want to install Ubuntu from cd, your RAM at least should 256 mb

I have 1gb...

---

### Post by nnebular22 on 2008-07-12
same issue here....:confused:

---

### Post by grandroyal on 2008-07-12
I had the same problem, when I did a dual boot install on Vista 

I found that I was using a DVD instead of a CD.
So, I Downloaded the correct wubi and live cd .iso, put them on a CD and had no problems.

---

