---
title: "CPU Throttling goes berserk...possible overheating with Lucid"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2010-05-04
Hello Everyone,

I am still investigating, but so far have not found a reason.  Fresh install of Lucid on my Toshiba Equium laptop, AMD64 X2, 1900Ghz.  Shortly after the install, I noticed the laptop getting very hot.  No stressful programs were running, but the CPU was running at full speed (I use on-demand throttling), and any attempt to change it would not work.  Finally, I rebooted and it settled down to normal on-demand throttling (usually 800Mhz with just lightweight programs.)  Several minutes later it did it again and the sensors command told me my temp as at 90c, way too hot.  This seems to happen out of the blue, the CPU just begins running at full speed.

This is really just a heads-up as I am sure I am not the only one with this problem.  You might want to keep an eye on your laptop temps until future updates sort this out.  I triple boot this laptop and it does not happen with the other two distros, nor did it happen with Karmic, so I am pretty sure this is a problem with running Lucid.

---

### Post by Skaperen on 2010-05-04
In a terminal session, run the command```
sudo top -d60
```and let it run for a couple minutes. It should show the top CPU hogs. What is the name of the busiest process(es) as named in the right column?

---

### Post by bobnutfield on 2010-05-04
> **Skaperen said:**
> In a terminal session, run the command```
sudo top -d60
```and let it run for a couple minutes. It should show the top CPU hogs. What is the name of the busiest process(es) as named in the right column?

Thanks for the suggestion, but I did that the first time I noticed the problem.  It was very odd that CPU cycles were being used normally (no runaway apps or hogs I could see).  It was just that the CPU kept running at the full 1900Mhz (full speed) even though I was using on demand throttling.

But as it turns out, it has now been several hours since this has occured.  It may be that it was just the first couple of boots that it did this.  So far it hasn't happened since.  I am just going to keep any eye on it.  If it does not occur again, I guess it is fine.

Thank you for replying.

---

### Post by badrra on 2010-05-12
I had the same issue with my Satellite A70. CPU usage is 100% and it shuts down after a few minutes. I tried Karmic and Lucid, both did the same thing. 

I found out that ondemand heats up my cpu badly. So i switched to userspace set it to the lowest cpu frequency and since then never had a problem. Watching movies surfing and compiling at the same time. CPU Temperature never went up to 60c. 

Mine is a dual processor P4 and both are set to 1.87 MHZ using userspace. Performance is as good.

---

### Post by squiddy on 2010-05-14
any updates ?

---

### Post by bobnutfield on 2010-05-15
Yes, in my case it turned out that the screen covering the fan had become dusty.  A can of air did the trick.  Temps are back to normal.

---

