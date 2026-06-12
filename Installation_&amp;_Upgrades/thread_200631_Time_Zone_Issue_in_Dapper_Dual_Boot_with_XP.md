---
title: "Time Zone Issue in Dapper Dual Boot with XP"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by OneL on 2006-06-20
I have a minor annoyance that I hope someone can help me clear up.  I'm running a dual boot -- Dapper and XP.  I've set the time zone in Dapper for local (New York) time.  However, when I boot up, the time is set four hours earlier.

Apparently, somethng in Dapper is reading the system time and subtracting, which would make sense if my system time was UT, but it's not.

If I leave things as they are, then when I boot back into XP, the correct -- local -- time is displayed.  If I change Dapper, when I boot back into XP, the time is four hours later than it should be.

I've checked my BIOS and there is no indication there of what zone system time is.  I'm sure there is some config file in Dapper that I can edit to fix this, but I don't know which one it would be.  I have a lot of experience in Windows, but know only enough about Linux to be dangerous.

I know the work around is to set Dapper to UT, but that's too easy.

---

### Post by 5-HT on 2006-06-20
Not sure if this is the cause, but Dapper's default is to use UTC when setting the system clock whereas Windows uses local time.

If you change UTC=yes to UTC=no in /etc/default/rcS, Dapper will use local time instead.
That might do the trick.

Hope that helps.

---

### Post by OneL on 2006-06-20
Worked like a charm.  Many thanks for the assist.

---

