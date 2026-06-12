---
title: "Cron and Anacron task"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by alkamid on 2008-02-22
Hi

I searched forums, but I haven't found a solution to my problem. My computer doesn't run 24/7 so I know I have to use Anacron for that. This is my task in crontab:
```
 02 18 * * * wget -P /home/adam/.qtstalker/data0/data/bossa/ http://bossa.pl/pub/ciagle/mstock/sesjacgl/sesjacgl.prn
```
I want it to execute exactly at 18:02 OR as soon as the computer is booted. 
If I use cron.daily or anacrontab. I'm not able to set the exact hour. On the other hand, if I use crontab, anacron doesn't seem to find that there's a job which should be executed.

---

### Post by alkamid on 2008-02-23
bump?

---

