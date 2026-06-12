---
title: "Penryn Macbook Pro and Intrepid Ibex Triple Boot?"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gutsy08 on 2008-10-15
Hello, I'm thinking about getting a Macbook Pro (the previous generation) [which is detailed here]("http://www.everymac.com/systems/apple/macbook_pro/stats/macbook-pro-core-2-duo-2.4-15-early-2008-penryn-specs.html"), and I was curious if anyone else had been able to get a triple boot working on it and if there were any problems?

I've taken a look at [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) though it does not mention if the little details like the keyboard backlighting work, and I'm curious about the details.  How does everything work overall?  Does anything else not work, like power management or some of the trackpad features?  Thanks in advance for any input on this subject!

---

### Post by hajk on 2008-10-15
Well, there should be no problem with triple booting as long as the two non-Mac "legacy" OS'es can boot from one of the primary partitions 1-4.

As far as using GNU/Linux on a MBP 4,1 (Penryn): most everything works, or can be made to work with a little tweaking, except keyboard backlighting, trackpad (beyond basic pointer movements), some of the temperature sensors (HD and CPU cores do work). The good news is that these missing features are close to being resolved in the 2.6.27 or 28 kernels. The reported wireless problems were solved with the recent Broadcom "wl" driver, also to be included in the 2.6.27 kernel.

So, nothing much that should hold you back.:)

---

### Post by cyberdork33 on 2008-10-15
> **hajk said:**
> Well, there should be no problem with triple booting as long as the two non-Mac "legacy" OS'es can boot from one of the primary partitions 1-4.

As far as using GNU/Linux on a MBP 4,1 (Penryn): most everything works, or can be made to work with a little tweaking, except keyboard backlighting, trackpad (beyond basic pointer movements), some of the temperature sensors (HD and CPU cores do work). The good news is that these missing features are close to being resolved in the 2.6.27 or 28 kernels. The reported wireless problems were solved with the recent Broadcom "wl" driver, also to be included in the 2.6.27 kernel.

So, nothing much that should hold you back.:)
Yes, in intrepid many of the major issues are working, or are close to working.

---

### Post by gutsy08 on 2008-10-15
Thanks for the quick replys.  I'm glad most of the features work.  However, in doing some research about the Macbook Pros, I've found out that the Nvidia GPU in these Macbooks is likely to have problems which [URL="http://mobile.slashdot.org/article.pl?sid=08/08/01/0142219&tid=128
"]some other manufacturers have attempted fix by cycling the fan on more often[/URL]. [Apple also admitted that the previous generation of Macbook Pros also had this problem.]("http://www.appleinsider.com/articles/08/10/10/apple_says_some_macbook_pros_affected_by_faulty_nvidia_chips.html") So I'm wondering how Ubuntu handles heat and power management on Macbooks.  Do they run hotter or spin up the fan less often?  Is battery life still reduced to about half of what it is in OS X?

Another big concern is that if the MacBook Pro does need repairs, will Apple give you a hard time about repairing your machine if they notice you've been triple booting it?  Just curious if anyone has had experience with this yet. :)

Maybe after considering all these problems, maybe the previous generation or next generation Macbooks are a better bet than the Pros for triple-boot. :(

---

### Post by xfile087 on 2008-10-15
> **gutsy08 said:**
> Thanks for the quick replys.  I'm glad most of the features work.  However, in doing some research about the Macbook Pros, I've found out that the Nvidia GPU in these Macbooks is likely to have problems which [URL="http://mobile.slashdot.org/article.pl?sid=08/08/01/0142219&tid=128
"]some other manufacturers have attempted fix by cycling the fan on more often[/URL]. [Apple also admitted that the previous generation of Macbook Pros also had this problem.]("http://www.appleinsider.com/articles/08/10/10/apple_says_some_macbook_pros_affected_by_faulty_nvidia_chips.html") So I'm wondering how Ubuntu handles heat and power management on Macbooks.  Do they run hotter or spin up the fan less often?  Is battery life still reduced to about half of what it is in OS X?

Another big concern is that if the MacBook Pro does need repairs, will Apple give you a hard time about repairing your machine if they notice you've been triple booting it?  Just curious if anyone has had experience with this yet. :)

Maybe after considering all these problems, maybe the previous generation or next generation Macbooks are a better bet than the Pros for triple-boot. :(

Apple did admit the graphics card is more likely to fail, but they have extended the warranty for the gpu for 2 years now because of it. *touch wood* I won't need to send it for repair. So I wouldn't worry too much about that one and as for the tripple boot thing I can't see why Apple would care! They designed BootCamp so you could install other operating systems like Windows  so it shouldn't matter.

On a side note, I received my MacBook Pro last week and even though new ones are out and I am extremely pleased about my purchase - it's an awesome machine.

---

### Post by gutsy08 on 2008-10-16
> **xfile087 said:**
> 
On a side note, I received my MacBook Pro last week and even though new ones are out and I am extremely pleased about my purchase - it's an awesome machine.

Congrats, I hope you got a good deal on it!  It'd be interesting to hear about how the details of your install go. :)

---

### Post by watered.down on 2008-10-18
> **gutsy08 said:**
> Thanks for the quick replys.  I'm glad most of the features work.  However, in doing some research about the Macbook Pros, I've found out that the Nvidia GPU in these Macbooks is likely to have problems which [URL="http://mobile.slashdot.org/article.pl?sid=08/08/01/0142219&tid=128
"]some other manufacturers have attempted fix by cycling the fan on more often[/URL]. [Apple also admitted that the previous generation of Macbook Pros also had this problem.]("http://www.appleinsider.com/articles/08/10/10/apple_says_some_macbook_pros_affected_by_faulty_nvidia_chips.html") So I'm wondering how Ubuntu handles heat and power management on Macbooks.  Do they run hotter or spin up the fan less often?  Is battery life still reduced to about half of what it is in OS X?



The battery life is about an hour tops (very hot). i would get probably 3 hours in OS X a couple days ago. I've not found any solution or work around posted and i've been looking for a couple days now. everyone else says their battery life is just as good as with OS x... i completely blew away os x though. will try re-install that and then boot camp my install to see if it helps (don't know how it could, but i can't think of any other differences). will post here if it does help.
 
the wireless was a bit of a pain too, though now seems to be limping along. 

why do you want a mac anyway? this is my fourth and every time i swear "never again". 

anyway, far and away the worst installation experience i've ever had.

---

### Post by hajk on 2008-10-18
Well, just to pitch in my 2 cent's worth, on the basis of my own MBP 4,1 Penryn bought in April of this year:

1. NVidia GPU works fine, but I'm keeping an eye on it in view of recent reports.

2. Tried various versions of GNU/Linux on it: Ubuntu 8.04 (Hardy) and currently Debian testing (Lenny). (I'm also running Ubuntu Intrepid on my desktop computer; and have run Ubuntu versions Dapper - Gutsy on my previous MacBook 1,1.)

3. Both Hardy and Lenny ran/run fine, in both cases with HD temperature around 39 deg C and the CPU cores at around 32 deg C. The nvidia-settings programme shows the GPU temperature in the green zone. The fans are always spinning at the default minimum 2000 RPM, I never hear them rev up above that. The top (keyboard, palmrests, speaker areas) feels decidedly cooler than when I run Mac OS X. 

4. CPU frequency monitor usually shows the cores running at 1/3 max, or 800MHz on my 2.4GHz machine, the reason for the low CPU temperature. Naturally, cpufreq-utils and powernowd are running on the amd64 kernel.

5. I often cycle the battery, I still get > 3 hours continuous work, whether in GNU/Linux or Mac OS X, although in practice this will be more as I have configured the MBP to sleep after 30 minutes idle. Sleeping works just fine, BTW, also when closing the lid, and waking up works just as well. No need to unload any drivers (like the Broadcom wl wireless driver). 

I don't consider myself an Apple fanboi, using GNU/Linux on a Mac has its quirks, and a yen for solving little problems and looking for work-arounds is a definite prerequisite on my MBP (and on the MacBook 1,1 before that). Making it all work on this elegant hardware is its own reward. Don't be put off by some with negative experiences, they're a small minority often caused by insufficient "yen"...

---

### Post by watered.down on 2008-10-19
ok, just to report back, everything is running *much* better today. i re-installed OS X and am now using rEFit to dual boot. 

i don't know if this accounts for the improved battery life. doesn't seem like it could, but it does seem like it has.... i don't know. 

i agree with hajk, it is nice hardware. still, i'd say if ubuntu will be your primary OS, better off to get something else. if you think OS X is the bomb (as many do) then yes, you should be able to get everything working in ubuntu with a little effort. 

good luck. oh, and teachers/students get discounts on macs if you're not considering the refurbished route.

---

### Post by gutsy08 on 2008-10-20
> **hajk said:**
> 
3. Both Hardy and Lenny ran/run fine, in both cases with HD temperature around 39 deg C and the CPU cores at around 32 deg C. The nvidia-settings programme shows the GPU temperature in the green zone. The fans are always spinning at the default minimum 2000 RPM, I never hear them rev up above that. The top (keyboard, palmrests, speaker areas) feels decidedly cooler than when I run Mac OS X. 


1. Hey, thanks for the useful post. Do fans turn go off on your Macbook Pro 4,1, either in OS X or Ubuntu?  Do the fans spin up more in OS X or in Ubuntu?  I do some audio editing, so I'm a bit curious which Mac system I should choose if I want to avoid fan noise.

2. [ According to Engadget,]("http://gizmodo.com/5021713/lots-of-nvidia-laptop-graphics-cards-are-overheating-dying") Nvidia's solution for it's 8M series cards is "a new driver that kicks in the cooling fans sooner, rather than later." So I'm a bit curious how often the fans spin up now, and how loud they can get, in OS X and Ubuntu.  If the fans almost always going to be on even at a low speed, perhaps I'm better off getting one of the Macbooks, either the newly released one or the early 2008 model.  I want to experiment with Ubuntu dual booting and virtualization, but I suspect I'll be stuck with a few of my apps in OS X at least for the foreseeable future.

3. I also heard recently that [Nvidia's has refused to release open source drivers for Linux]("http://blogs.zdnet.com/open-source/?p=2588") again, and I'm wondering if I should consider this part of my buying decision.  The older Macbooks still use the (slower) Intel integrated graphics chipsets which I assume have fully open sourced drivers.  Has anyone encountered problems of any sort with Nvidia's drivers yet?

---

