---
title: "Sbackup: help with custom cron time definition"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by texaswriter on 2010-03-01
Well, don't usually have to create a thread for my questions, but here is something very specific. 

I recently had a hard drive malfunction [lolz: computer got dropped bad... hd = dead]... Thankfully, I backup my documents daily to an additional source [independent of the hard drive]. However, I want to backup even more regularly, twice daily. Is there an easy way to set this using the custom cron time definition. A hint, I want simple backup enabled so that if the computer isn't turned on exactly at that time, it willl still update. Hopefully there is an easy way to do this. 

Thanks.

---

### Post by quixote on 2010-03-02
cron's first two times refer to minutes after the hour, and the hour of the day.  However, if you divide the day by a number instead of specifying an hour, it'll run after each specified interval.  E.g. ```
 #m h dom mon dow
* */2 * * *
```
would run twice a day.  */4 would run every six hours.  and so on.

hth.

---

### Post by texaswriter on 2010-03-03
Alright, thanks for that. I'll be sure to throw that in the sbackup, first thing in the morning. 

:popcorn::KS\\:D/

---

