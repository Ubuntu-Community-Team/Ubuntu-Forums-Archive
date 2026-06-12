---
title: "Why do my boot times fluctuate so much??"
date: 2010-01-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by KrazyPenguin on 2010-01-09
I installed Lucid yesterday, and installed bootchart.

I was wondering if anybody else was getting boot times that fluctuate???

Here is what I am getting: times from 19 seconds to 37 seconds. 

I've been doing updates every chance I can since yesterday morning, i probably did three upgrades yesterday and one this morning. 

I rebooted my laptop several times yesterday and everytime the boot time that bootchart showed was different. 

Just to add that even Karmic was taking 45-50 seconds so these numbers are a big improvement for me!!!!

Would this have anything to do with readahead??

thanks.

---

### Post by MacUntu on 2010-01-09
> **KrazyPenguin said:**
> Would this have anything to do with readahead?

Yes - certain package upgrades change the files that are read during the boot. To make ureadahead aware of those changes, it needs to retrace the boot process during the next boot (which will be slower). Subsequent boots should be faster again.

Upgrades that trigger the retracing happen a lot during the development cycle, so it's nothing to worry about.

---

### Post by k3lt01 on 2010-01-09
Ureadahead is a pain in the proverbial butt. It can make my boot times half an hour, no bull. I updated my Karmic (9.10) partition last night and have tried 4 times for it to boot to a usable stage, I'm sick and tired of it.

---

