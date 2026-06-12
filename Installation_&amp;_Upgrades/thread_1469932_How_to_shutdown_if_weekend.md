---
title: "How to shutdown if weekend"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by sitush on 2010-05-02
Just installed 10.04 Server (32 bit) and got scheduled RTC wake-ups working with an ancient MS-6368 mobo/Award BIOS and using general info from [this MythTV link]("http://www.mythtv.org/wiki/ACPI_Wakeup"). Automating shutdowns using a crontab job will not be a problem as I've done this previously.

However, what I really need is a system that wakes up at 0700 ONLY if it is a weekday (or, if it wakes up and finds that it is a weekend then it immediately shuts down again). I guess:

query date
if date = any Saturday or date = any Sunday then
  shutdown now
else 
  shutdown now + 10 hours

Are there any scripts out there that I might be able to modify to do this? Google has not been my friend on this occasion - although I have come across mentions of nvram, it looks to be dormant in support/development terms.

Advice much appreciated.

---

### Post by dino99 on 2010-05-02
better to post on programming or server forum

---

### Post by sitush on 2010-05-02
OK thanks. I'll leave it a few hours before crossposting, just in case.

---

### Post by sitush on 2010-05-03
Figured it out, in a botched sort of way.

Two crontab jobs, one running in the evening of Mon - Thurs and one running on Fridays. Jobs call scripts based on the link I referred to above that set the wakeup RTC alarm to 12 hours ahead and 60 hours ahead, respectively, and then shutdown the server.

I guess that over time there may be a bit of "creep" as the milliseconds to execute mount up but, hey, it's a start.

I guess it could all be done in one script but I come from a Windows background and need to get to grips with differences between batch and bash etc, which is one for a rainy day (we have a lot of them here...)

---

