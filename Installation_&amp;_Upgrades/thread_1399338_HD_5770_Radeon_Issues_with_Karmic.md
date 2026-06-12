---
title: "HD 5770 Radeon Issues with Karmic"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by r10crw on 2010-02-05
Gents, Im fairly new to Linux having previously only used live boot discs to repair windows. Hence the extents of my experience were moving and editing files using the terminal. Anyway after using the live boot disc on several occasions I was so impressed I decided to take the jump on my home machine. So Ive started off with a fresh build and almost everything has been smooth sailing but Ive still got problems with the graphics. Basically I'm looking to use the HDMI output only but when trying to start the machine it will not boot until the dvi port on the card has been connected to a monitor. It will then give me a mirrored display on both my TV and the monitor and boot correctly, I can even disconnect the monitor and it will work fine until I run a game at which point the screen goes blue on the TV, again connecting the monitor cures the issue. Ive installed the catalyst control centre and think Ive got the drivers installed properly but not entirely sure. So if anyones got any ideas that arnt too technical please feel free to post.

My system is set as follows,
AMD athlon II, Dont remember which one exactly
4 Gb ram
Radeon HD5770
4 500Gb drives set to RAID 5, Ubuntu Karmic 32 bit installed using complete drive at default settings. 

So impressed with Ubuntu Karmic that I dont want to give up and install windows  but dont want to have a semi working system that should be great.
Thanks Craig.
PS Sorry if this has been solved elsewhere but couldn't find anything the same.

---

### Post by r10crw on 2010-02-06
bump

---

### Post by khelben1979 on 2010-02-06
> **r10crw said:**
> Ive got the drivers installed properly but not entirely sure.

How did you install the drivers?

---

### Post by r10crw on 2010-02-07
Hi, first downloaded them from the AMD page then from the correct folder used "sudo sh ati*.run". This went through the process correctly and allows me to edit the configuration in the cat control centre.
However Ive made progress, Ive tried the machine on my main Tv and its working perfect so looks like its the cheap bedrrom tv thats the problem. I just thought that HDMI would work but guess there are issues.
Cheers Craig.

---

### Post by khelben1979 on 2010-02-07
Sounds positive. So, what do you think about the performance so far? Better or worse than expected?

---

### Post by khelben1979 on 2010-02-07
One other thing, you should be aware that whenever a new kernel gets installed in your Ubuntu system, it will brake your graphics drivers.

It's recommended to use the prop. drivers which comes delivered with Ubuntu, but I see in your case that you might benefit more from using the latest graphic drivers directly from the AMD webpage. In the future you might benefit more from changing back to what is recommended to get less hassles with Ubuntu whenever a new kernel upgrade occurs.

---

### Post by Mark Phelps on 2010-02-08
Would suggest you check out the Phoronix forums.  Folks there do a LOT of tweaking with ATI products and drivers.  You may find some info on hot patches that could help your ATI driver problem.

---

