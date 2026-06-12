---
title: "No Monitor Display During Gutsy Install"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by leehach on 2008-02-04
I'm a Ubuntu newbie trying to install to a newly purchased Dell Inspiron 530s (Intel E2140 Dual Core 1.6 GHz processor).  My problem is that after the splash screen (orange status bar goes to 100%) the monitor goes into standby mode and the display goes blank.  The hard drive crunches, so I think it's still trying to do an install and then stops when it needs user input.  

Right before the monitor goes blank it gives me a message "Oversize Recommand Mode 1280 x 1024", which I suspect is a monitor message rather than a Ubuntu install message.

Most of the display resolution threads I've found talk about what happens after a successful install, which I haven't been able to get through.  

Here is (possibly) pertinent info:

Dell Inspiron 530s
Intel E2140 Dual Core 1.6 GHz processor
Chipset ICH9 and Intel G33
Intel Integrated Video
Monitor is a Princeton VL173

Any ideas?

Thanks in advance,
--Lee

---

### Post by leehach on 2008-02-05
I just ran the gparted LiveCD and had the same problem.  Based on other threads in the forum, I ran it again and used the option to force VESA, and this time the monitor didn't die on me.  How can I force VESA during a Ubuntu LiveCD install?

---

### Post by Scavok on 2008-02-05
Search for VESA--I found this post:

> When I installed Unbuntu I also had the black screen, the screen having gone into "standby", yellow light flashing. The first few times I thought I had commenced the install incorrectly, so I recommenced the install. On install attempt number 5 or 6 I accidentally pressed the "Enter" and Ubuntu install kept on going to ultimately install.

So as an idea just for the exercise at the point of the black screen press enter. Why, I can not answer but in my case it worked!

---

### Post by leehach on 2008-02-05
I'm a little hesitant to try that.  During install, you have to make a few choices about keyboard layout, timezone, etc.  And what happens to the HDD partitioning?

---

