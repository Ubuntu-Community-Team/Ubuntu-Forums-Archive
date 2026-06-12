---
title: "Downgrading from 9.10 64-bit to 32-bit"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by ExquisiteDeadGuy on 2009-12-06
Hey all,

Since the upgrade I've been getting constant freezing 2 or 3 times a day. Coupled with the data loss it's been causing, I'm getting fed up with it. I want to switch to the 32-bit version, as Googling makes it appear the 64-bit version is the culprit. What's the best way to do this?

Thanks

---

### Post by audiomick on 2009-12-06
I am afraid there is no easy way. As far as I know, it would require a fresh install. Wait for other responses before you do anything, I could be wrong.

Also, a couple of weeks ago there were a lot of threads being started about problems with freezing in 9.10, but I haven't been seeing many in the last few days. Maybe it is worth doing a bit of searching to see if there isn't a solution to your problem.

---

### Post by presence1960 on 2009-12-06
> **ExquisiteDeadGuy said:**
> Hey all,

Since the upgrade I've been getting constant freezing 2 or 3 times a day. Coupled with the data loss it's been causing, I'm getting fed up with it. I want to switch to the 32-bit version, as Googling makes it appear the 64-bit version is the culprit. What's the best way to do this?

Thanks

Did you do a dist-upgrade to 9.10? If so that is probably the culprit, not the fact that you have 64 bit Ubuntu.

The only way to go backward to an older version or switch architecture (32 bit to 64 bit or vice versa) is a clean install.

If you did a dist-upgrade to 9.10 I would do a clean install of 9.10 and stick with 64 bit.

---

### Post by LuisGMarine on 2009-12-06
Yeah if you haven't given the change to do a fresh 64-bit install I recommend you do it.  I'm had mine for a few days now and it runs flawlessly (Cross fingers)

:popcorn:

Did you try to search what could be causing your computer to freeze? :KS

---

### Post by ExquisiteDeadGuy on 2009-12-07
> **LuisGMarine said:**
> Yeah if you haven't given the change to do a fresh 64-bit install I recommend you do it.  I'm had mine for a few days now and it runs flawlessly (Cross fingers)

:popcorn:

Did you try to search what could be causing your computer to freeze? :KS

Thanks everyone for the help. Yes, I did do a dist-upgrade. I've tried Googling my problem, I find a number of people claiming similar problems (random hard freezes that even magic-SysRq can't get you out of), with no real solutions. The only similarities I can find is they're all on AMD64 systems with the proprietary nvidia driver. I tried downgrading my nvidia driver to an older driver and it didn't make a difference, I also tried upgrading to the beta driver and it still froze.

I'm leery to do a fresh install of the 64-bit version, because if it's a bug in the software and not just my installation, I'll then have to do a fresh 32-bit install if that doesn't fix it. Does anyone know of anybody with similar issues having their system fixed by a fresh reinstall?

Thanks

---

### Post by LuisGMarine on 2009-12-07
Although I haven't had your issue, I guess if 64-bit is making your system freeze then stick to 64-bit.  After a while give it another try.  I've had problems with 64-bit back in the 4.10 days and stuff, and I have given it a try with someone going completely wrong for every release now.  Then here I try it when 9.10 comes out and everything works like a charm! :KS

---

