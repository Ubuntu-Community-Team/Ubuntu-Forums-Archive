---
title: "ubuntu messes up my winxp clock"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by wrynn on 2005-10-29
if i boot into windows after using ubuntu, i'll notice my winxp clock is set about 5 hours ahead.

so i have to fix it everytime i boot into windows...


anyone else experienced this?

---

### Post by atoponce on 2005-10-29
[quote=wrynn]if i boot into windows after using ubuntu, i'll notice my winxp clock is set about 5 hours ahead.

so i have to fix it everytime i boot into windows...


anyone else experienced this?[/quote] 
When you installed Ubuntu, how did you set your clock?  The clock is a BIOS system internal, and Windows XP and Ubuntu both look to that for the current time.  The Ubuntu installer asks if your hardware clock is set to GMT, and shows you the time.  How did you answer that question, and what timezone are you in?

I imagine this is your problem: Ubuntu is resetting your hardware clock.  If that is the case, you will have to get into your BIOS and change the hardware clock.  I would recommend setting the hardware clock to GMT, and your Windows XP and Ubuntu clocks to your current time zone.

---

### Post by wrynn on 2005-10-29
thanks i'll try that :)

---

