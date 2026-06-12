---
title: "gedit segfaulting when opening files"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kingborel on 2009-07-23
> Jul 23 17:46:44 borrell-laptop kernel: [ 1880.256377] <6>gedit[5666]: segfault at aaaaaaae ip 005785c2 sp bfbce2b8 error 4 in libglib-2.0.so.0.2104.0[542000+c3000]


Anyone else getting this? It's happening when I try to open some plain text files. It was happening 2 days ago but I didn't have time to investigate. 

I'm about to file a bug on it

EDIT:

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/403378](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/403378)

---

### Post by taavikko on 2009-07-23
Commented.

Not visible here, in any way.
Is your system up-to-date (main-server) local mirrors may be out of sync several days.
Was this a clean install or an upgrade from jaunty.

---

### Post by kingborel on 2009-07-23
Yeah I already apport-collected on the bug. It's a clean install from a few weeks ago, after the Alpha 2 build. All up-to-date, so I'm thinking I'll just wait a bit and hope it sorts itself out.

---

### Post by terry_gardener on 2009-07-29
i am also getting this problem i have used apport to report bug. 

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/406481]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/406481")

---

### Post by MaX on 2009-07-29
> **terry_gardener said:**
> i am also getting this problem i have used apport to report bug. 

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/406481]("Bug Report 406481")

Yeah it happens for me to. But if you open gedit and then drag/drop a file on it it will stay open.

---

### Post by BCurtisWX on 2009-07-29
The bug is already reported.

[https://bugs.launchpad.net/bugs/401934](https://bugs.launchpad.net/bugs/401934)

---

