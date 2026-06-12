---
title: "Western Digital My Book USB Drive problems"
date: 2008-12-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MaX on 2008-12-08
Since I bought it (Hardy) I've had problems in Ubuntu/Linux with my Western Digital My Book external USB Hard drive.


When I shut down the computer the external disk doesn't shut down. It still draws power from the USB on the computer.
When I do a sleep or hibernate, it shuts down correctly though.
So what is Ubuntu doing differently when just shutting down. Why doesn't it tell external drives to power down then?

I still have this problem in Jaunty...

---

### Post by zekopeko on 2008-12-08
i think that's normal. if the computer isn't pluged from the outlet it will draw power for some things ,like the LED on the network card and is very likely supplying power to your USB HDD. This happens to me no matter if it's WinXP or Ubuntu. I haven't tried sleep or hibernate.

---

### Post by quickshade on 2008-12-08
I have the same thing and opensuse shuts it down just fine.

---

### Post by MaX on 2008-12-09
When I shut down from Vista (Ultimate) it shuts down perfectly well too...
It's not supposed to be spinning when it's not in use...

---

### Post by David A Knight on 2008-12-09
Saw a similar thing last night with my seagate freeagentdesktop.  Turn my machine back on in recovery mode and ran a fsck on the disk just in case, no problems, shutdown again and the disk span down properly.  I am seeing strange problems this morning though with accessing the disk, hopefully it is a kernel problem or something rather than my disk giving up.

---

