---
title: "poll_schedule_timeout on System Monitor"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-10-06
Something weird has just started happening. When I use System Monitor, under Processes, I have almost every process on the Waiting Channel=poll_schedule_timeout . It doesn't show up in "top".

This just started happening. Anyone else have this?

---

### Post by VMC on 2009-10-07
Please, could someone run: **System Monitor** (System>Administration>System Monitor), and see if you get the same results as I have shown. Look to the far right under the heading "Waiting Channel". Thanks for your help.

---

### Post by vredley on 2009-10-07
I can confirm that all except 4 processes on my system are showing 'poll_schedule_timeout'. Hope that helps.

---

### Post by Akita on 2009-10-07
Same here FWIW.

---

### Post by VMC on 2009-10-07
Thank you all for reporting. I also get the same results on Fedora11, but not on jaunty. [FONT="Courier New"]top[/FONT] doesn't show anything like that, although the man pages has references.

---

### Post by daengbo on 2009-10-27
I get this problem on Karmic RC when Firefox becomes unresponsive.

---

