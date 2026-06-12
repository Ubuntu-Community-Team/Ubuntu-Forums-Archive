---
title: "beta 8.10 3d macbook?"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by elementxyz on 2008-10-11
Hi,

tried the intrepid beta 8.10. It runs good.I even can connect to my wireless network out of the box! But the 3d effects don't work :( It run with 7.10 and 8.04. It's the macbook 2.1 with intel gma 950 i think.

---

### Post by elementxyz on 2008-10-17
i found out was my problem was. The 3d effects won't turn on because i had second 22 display on my macbook. And the intel driver supports no dri for virtual resolution higher then 2048.

The trick is to put the macbook display in the configuration tool under the other display. So that the two displays not come over 2048.

---

