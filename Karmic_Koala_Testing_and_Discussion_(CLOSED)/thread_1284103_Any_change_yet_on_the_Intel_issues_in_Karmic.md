---
title: "Any change yet on the Intel issues in Karmic?"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by exploder on 2009-10-06
I was testing Karmic until updates caused regressions with my Intel 8x on-board graphics. Randomly at boot I would loose desktop effects and my system would slow to a crawl. Sometimes a few reboots would get things working again but it was too unreliable to continue using.

I added to an existing bug report, the report now shows the bug as "Triaged", has the issue been resolved? No other major distribution is currently suffering from issues with Intel 8x graphics and I am wondering if this issue is going to be fixed for the final release of Karmic.

This issue needs to be fixed and not worked around like in Jaunty. Intel 8x on-board graphics are very common and need to be supported in this release.

---

### Post by psyke83 on 2009-10-06
> **exploder said:**
> I was testing Karmic until updates caused regressions with my Intel 8x on-board graphics. Randomly at boot I would loose desktop effects and my system would slow to a crawl. Sometimes a few reboots would get things working again but it was too unreliable to continue using.

I added to an existing bug report, the report now shows the bug as "Triaged", has the issue been resolved? No other major distribution is currently suffering from issues with Intel 8x graphics and I am wondering if this issue is going to be fixed for the final release of Karmic.

This issue needs to be fixed and not worked around like in Jaunty. Intel 8x on-board graphics are very common and need to be supported in this release.

I'm not sure which bug you're referencing, please link to it.

Nevertheless, I have an 855GM and the [worst]("https://bugs.freedesktop.org/show_bug.cgi?id=22877") performance bug has been resolved. Performance - 2D and 3D - is excellent.

One caveat. You need to disable KMS or else XVideo output will not initialize properly.

---

### Post by exploder on 2009-10-06
This is the bug report I mentioned.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694)

> 
One caveat. You need to disable KMS or else XVideo output will not initialize properly. 

This is the problem. Is this going to be fixed for the final release?

---

### Post by psyke83 on 2009-10-06
> **exploder said:**
> This is the bug report I mentioned.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694)



This is the problem. Is this going to be fixed for the final release?

That's not the same issue as the bug you linked to, and I don't know if it will be fixed.

---

### Post by exploder on 2009-10-06
Someone mentions in the bug report that a kernel update has resolved this issue. Can anyone confirm this?

---

### Post by VMC on 2009-10-06
Latest updates had that kernel12 from the LP you listed. I will try and see if that fixes my freezes, using i865.

---

### Post by exploder on 2009-10-06
There is another kernel mentioned in the bug report that may fix Intel 915 graphics problems too.

---

### Post by kxmas on 2009-10-06
Intel just released version 2.9 of their driver.  It looks like Karmic is using 2.8.1

From the release notes:
[I]* Multiple fixes to make the driver stable for 8xx chipsets, (855GM,
  865G, etc.). The 2.8 driver series was extremely unstable with many
  of these chipsets.[/I]

[http://lists.freedesktop.org/archives/xorg/2009-September/047439.html]("http://lists.freedesktop.org/archives/xorg/2009-September/047439.html")

---

### Post by VMC on 2009-10-06
> **kxmas said:**
> Intel just released version 2.9 of their driver.  It looks like Karmic is using 2.8.1

From the release notes:
[I]* Multiple fixes to make the driver stable for 8xx chipsets, (855GM,
  865G, etc.). The 2.8 driver series was extremely unstable with many
  of these chipsets.[/I]

[http://lists.freedesktop.org/archives/xorg/2009-September/047439.html]("http://lists.freedesktop.org/archives/xorg/2009-September/047439.html")

I installed that driver and my computer froze over. I have a [topic]("http://ubuntuforums.org/showthread.php?t=1278661") on that driver.

---

### Post by VMC on 2009-10-06
> **exploder said:**
> There is another kernel mentioned in the bug report that may fix Intel 915 graphics problems too.

Ok. I just installed intel driver 2.8. I'm now running with the latest kernel12 and it is not freezing , but it has a rather jerky behavior. Not near as smooth as when using the old intel-2.4.1 driver. Also, I still can't use any visual effects.

Edit: I guess if this doesn't freeze and stays like this I can try again to instill the newest 2.9 intel driver.

---

