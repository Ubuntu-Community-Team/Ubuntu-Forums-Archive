---
title: "Dapper get slower with very long system beep"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by krajok on 2006-09-10
I've just installed Dapper on IBM NetVista 8182.

My problem is when I turm on the system for about half a day, system will take longer time to response each command, especially system beep that take longer and longer so I have to disable it.

But not only longer system beep, I think that every think  related to the clock get slower. I try the following command
 bash$ date && sleep 1 && date
and I got 20 - 40 seconds delay, somtimes printed date is just 3-4 seconds difference but it really was about 20 seconds delay.

Thanks

---

