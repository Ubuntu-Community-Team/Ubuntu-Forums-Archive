---
title: "K3b: /usr/bin/wodim: A write error occured.on ubuntu11.04"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-06-13
Sorry it is not kubuntu, but ubuntu 11.04.

/usr/bin/wodim: Please properly read the error message above.
write track data: error after 151672832 bytes
Writing  time:   34.976s
Average write speed  82.9x.
Min drive buffer fill was 100%
Fixating...
Fixating time:    0.001s
/usr/bin/wodim: fifo had 2580 puts and 2390 gets.
/usr/bin/wodim: fifo was 0 times empty and 1205 times full, min fill was 94%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -data -tsize=1953312s -

---

