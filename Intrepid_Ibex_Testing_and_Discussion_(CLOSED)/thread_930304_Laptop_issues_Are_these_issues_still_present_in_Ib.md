---
title: "Laptop issues: Are these issues still present in Ibex?"
date: 2008-09-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by denzilla on 2008-09-25
I've read here about some problems with Ubuntu placing undo wear on laptop HDDs in regards to load cycles and also some things about laptops running hotter when using Ubuntu vs. Windows. Have these issues been addressed with Ibex? I'm installing Alpha 6 on an Inspiron E1505 Laptop to play around with now.

---

### Post by zombiepig on 2008-09-25
I think the load cycle issue has been fixed, a few days ago there was an update to acpi:

"ac.d/90-hdparm.sh, battery.d/90-hdparm.sh, resume.d/90-hdparm.sh,
    start.d/90-hdparm.sh: Set hdparm power management to 254 for all hard
    drives.  Ignore errors while detecting of APM is supported.  Set
    hdparm -B 128 while on battery in 90-hdparm.sh. Head parking is useful
    on the road for shock protection. Still set hdparm -B 254 while on AC.
    (Closes: #448673, #452489, #453478, #458787, #481685)"

Since that update, I haven't seen anything worrying in my cycle counts (I did previously to that update, and had to manually make those changes in hardy)

---

### Post by denzilla on 2008-09-25
Thats good news! Now, anyone notice increased heat running ibex vs windows?

---

### Post by FuturePilot on 2008-09-25
According to [this]("https://wiki.ubuntu.com/PowerManagement#How%20to%20get%20disks%20idleing%20correctly%20(without%20excessive%20load%20cycling)") wiki page, a lot of the load cycle issues have been fixed in Intrepid.

---

