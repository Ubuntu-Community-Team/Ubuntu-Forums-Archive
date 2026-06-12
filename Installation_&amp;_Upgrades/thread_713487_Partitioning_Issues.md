---
title: "Partitioning Issues"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by alakalaka99 on 2008-03-02
So here is my dilema. I have tried Ubuntu in the past with Wubi, and have decided to dual boot it with Windows XP on my laptop. I downloaded the 7.10  LiveCD and burned it to a DVD, which is all I had at the time. I proceeded to launch Ubuntu from the DVD on my laptop, everything is working fine. When I try to install, there is no option for me to partition my drive, just to wipe it and install only Ubuntu on it.

 So I searched around the forums and found out to use GParted that came on the LiveCD. Well, for some reason it doesn't work at all, with a yellow "!" sign next to the drive I want to partition. Since that didn't work, I found out that I could use a GParted LiveCD. So I burn the iso onto another DVD, pop it in my computer, and then it leads me to a console and says the graphical interface could not be loaded, or something of that sort. Which leaves me with a wasted DVD-R :(

 The drive is ~80GB with 40GB free of space, and I want to allocate 10Gb for Ubuntu. I'm probably doing something wrong, but I'm not sure what it is. I've been at it for an hour or so and have yet to find a solution. Is there any other way to easily set aside 10gb for ubuntu, and install it. Is there anything I can do?

---

### Post by johnbouma on 2008-03-02
Disk druid inside of the install will let you resize the partitions to incorporate ubuntu onto the disk

---

### Post by alakalaka99 on 2008-03-02
Ok, so I figured out I needed to use the chkdsk /f command in windows, and now I can partition the drive. Though, do I need to make a whole seperate partition for the /swap thing? or what?

---

