---
title: "Extremely slow xl2tpd with 2.6.31 since rc 3."
date: 2009-08-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Joe_Bishop on 2009-08-10
Previous 2.6.31 were too unstable - instant reboot under heavy IO (don't know if network or disk activity). Versions of 2.6.31 since rc3 become extremely slow with xl2tpd - I have 30Mbs connection through l2tp, but with these kernels I don't have more than 200 kilobyte per second, although with 2.6.30 and 2.6.31 rcN, N<3 I had about 3.7 megabyte per second. I didn't find out yet is it ethernet card driver (intel 82566DC) issue or kernel-xl2tpd interaction problem, so I've interested if someone has similar bug.

---

