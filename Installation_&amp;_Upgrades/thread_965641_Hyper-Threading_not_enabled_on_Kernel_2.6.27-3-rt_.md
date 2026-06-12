---
title: "Hyper-Threading not enabled on Kernel 2.6.27-3-rt after upgrade"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by OPENyourmind on 2008-10-31
I just yesterday upgraded from Ubuntu Studio 8.04 to the 8.10 release. After finally working out the issues with the NVidia graphics drivers I noticed that none of my hardware monitors were showing statistics for two processors. Usually it automatically shows frequencies for CPU0 and CPU1, but it seems to only be showing one processor in system monitor and in all my applets. Even when I run "sensors" in terminal it still only gives me temperatures for one core and not both. All of the settings in the bios are set for the 2 logical processors but the kernel doesn't support it.

I know that this issue is addressed in the release notes:

[HTML]http://www.ubuntu.com/getubuntu/releasenotes/810#UbuntuStudio%20real-time%20kernel%20support 
[/HTML]
But, I figured someone might have found something that worked for them. 

System info:

```
.....:~$ uname -a
Linux BeastyHo 2.6.27-3-rt #1 PREEMPT RT Mon Oct 27 03:02:33 UTC 2008 x86_64 GNU/Linux
```

---

### Post by BennyLZ on 2009-02-16
Hi,
I have the same problem (I have a pentium 4 HT), but I couldn't found something that fixed it.

I still not upgraded to Intrepid, so I want to ask you:
is the hyper threading enabled when you boot the generic kernel?
did you do something to get the rt kernel works with your HT processor?

Do you think it's a good idea to upgrade to intrepid now, renouncing to the hyper threading when I use the rt kernel?

thanks ;)

---

### Post by OPENyourmind on 2009-02-18
I was able to do a fresh install of Intrepid using a normal kernel instead of the rt, and it supports hyper-threading. 

Linux BeastyHo 2.6.27-12-generic #1 SMP Thu Feb 5 09:26:42 UTC 2009 x86_64 GNU/Linux

---

