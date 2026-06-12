---
title: "intrepid - hp nx9420 / ati mobility radeon X1600 driver"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aljosa on 2008-10-06
i'm using intrepid on hp nx9420 which has ati mobility radeon X1600 driver and currently i'm using open-source drivers since there are no ati/amd drivers that support xorg in intrepid.

i have no xv support and i can watch movies only using gl2 output, anybody knows when ati will release driver that will work with intrepid or if opensource drivers in intrepid will have better video output soon?

---

### Post by krazyd on 2008-10-06
Hi, try adding```
Option    "AccelMethod"    "exa"
```to the Device section of your xorg.conf

---

