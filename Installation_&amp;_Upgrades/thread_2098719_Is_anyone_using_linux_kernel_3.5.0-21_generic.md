---
title: "Is anyone using linux kernel 3.5.0-21 generic?"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by dalpi on 2012-12-27
A week ago, on Ubuntu 12.10 64-bit I updated to linux kernel 3.5.0-21 through the update manager. I restarted, and I just ended up with a black screen with this (same problem as [http://www.techques.com/question/24-160718/Unable-to-boot-after-uninstalling-Jupiter-applet-and-removing-entries-related-to-Jupiter-in-Startup-applications]("http://www.techques.com/question/24-160718/Unable-to-boot-after-uninstalling-Jupiter-applet-and-removing-entries-related-to-Jupiter-in-Startup-applications"))

```
could not write bytes: Broken pipe
 * Stopping anac(h)ronistic cron               [OK]
 * Checking battery state...                   [OK]
 * stopping System V runlevel compatibility    [OK]
 * starting jupiter healthcheck                [OK]
 * stopping jupiter healthcheck                [OK]    
```

I tried everything to get past this (tty sessions, purging the jupiter applet) but I couldn't. I ended up installing a fresh Xubuntu 12.10 64-bit on my laptop. Xubuntu works awesome!

But I'm afraid to update to kernel 3.5.0-21 generic. Will it crash my system again? I have the jupiter applet installed. Is anyone using 3.5.0-21? Please reply.

---

### Post by ajgreeny on 2012-12-27
Even if you can't run the new 3.5.0-21 kernel when you try it this time, there is no need to re-install the whole system, assuming you can still boot to the previous kernel.

When you boot next time, hold shift to get the grub menu if you don't usually see it, and from that menu choose the kernel that does boot properly.  You can then either remove the errant kernel, or set up grub to boot to the older kernel by default.  Perhaps 3.5.0-22, when it arrives, will work OK.

I know nothing about jupiter apart from what iot is supposed to do, so can't really comment about that and whether or not it is the main cause of the problem.

---

### Post by dalpi on 2012-12-27
Thanks, I did use shift at the boot screen to change the kernels, but I didn't try making grub use an older version by default. Maybe that would have helped. I'll probably upgrade if nobody else replies to this thread within the next few days.

---

### Post by Frogs Hair on 2012-12-27
That kernel as been in place  on my computer (12.10) via proposed updates for quite a while. It was last updated 0n 12-11.```
Linux ubuntu 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux     
```

---

### Post by dalpi on 2012-12-31
Thanks guys, I updated successfully.:p

---

