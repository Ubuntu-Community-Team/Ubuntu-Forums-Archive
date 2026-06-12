---
title: "Polling for Preferred Desktop HDD Parm Values"
date: 2008-07-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-07-17
So I started a bug on my dissatisfaction with Ubuntu defaults on a desktop install to having no HDD spin down value. Especially for users with multiple HDDs, they would have all their drivers spinning all the time with this default. Bug is at:

[https://bugs.launchpad.net/ubuntu/+bug/243821](https://bugs.launchpad.net/ubuntu/+bug/243821)

However, there's also the bug about HDD spinups occuring too often and that creating a wear situation all of its own. Bug is at:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

So this begs the question is it better to:

1. Never spin down
2. Spin down always after a sensible period of time
3. Spin down selected drives only (say data drives) after a sensible period of time

---

### Post by Gina on 2008-07-18
My first thoughts were for no. 3 but then I thought "that would need setting - adding extra complication and bloat"  also if you go off and leave the computer on it seems unreasonable to leave any drives running continuously causing heat and unnecessary wear on drives and fans (and it's not "green").  However, it's essential to make sure drives are not spun up unnecessarily as well as choosing a sufficiently long time after use before spinning down, to avoid wear from that cause.

So I'm voting for no. 2 with reservations.

---

### Post by MALEADt on 2008-07-18
There wouldn't have to be much complication involved. Just an extra tab in the "Energy preferences" dialog, and for every drive a slider from 30s to 60m. As the users for whom we want to keep things simple, mostly have only one drive, this wouldn't complicate stuff too much.

However, a sensible default value (5m) without having to customize would be nice too, Gina makes a good point there.

---

### Post by tcommbee on 2008-07-18
Having an option for spindown time might lead to many people setting a value that's actually _worse_ than the default (from a power saving/ disk life time pov). An option for never spinning down might be reasonable, but not used very often either imho (therefore maybe in gconf).

---

### Post by olskar on 2008-07-18
> **tcommbee said:**
> Having an option for spindown time might lead to many people setting a value that's actually _worse_ than the default (from a power saving/ disk life time pov). An option for never spinning down might be reasonable, but not used very often either imho (therefore maybe in gconf).

Perhaps have a little text that recommends a default value and tells you what the effects would be if you are setting the values to high/low?

---

