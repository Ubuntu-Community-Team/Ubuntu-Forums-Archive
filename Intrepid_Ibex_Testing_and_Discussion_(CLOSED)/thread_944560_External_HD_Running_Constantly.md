---
title: "External HD Running Constantly"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philliptweedie on 2008-10-11
Have a Seagate FreeAgent Desktop 500Gb.

Before in Hardy it would essentially turn off after a period of inactivity, and only come back alive when I tried to access it.

Since updating to Intrepid it's on and spinning constantly. Does anyone else have the same problem with this brand or any other external HD. Also, how could I go about filing a useful bug report?

Cheers,

Phil

---

### Post by psyke83 on 2008-10-11
> **philliptweedie said:**
> Have a Seagate FreeAgent Desktop 500Gb.

Before in Hardy it would essentially turn off after a period of inactivity, and only come back alive when I tried to access it.

Since updating to Intrepid it's on and spinning constantly. Does anyone else have the same problem with this brand or any other external HD. Also, how could I go about filing a useful bug report?

Cheers,

Phil

It may be due to the recent changes to the default spindown time for drives (to avoid drive wear particularly with laptops).

Try:
```
$ sudo hdparm -B 128 /dev/sdX
```

Replace X with the proper device letter allocated to your external drive.

---

