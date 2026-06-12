---
title: "upgrade breaks dual-screen on radeon"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by mikeh on 2006-06-14
I'm using a laptop with ATI mobility radeon, plus external monitor with xinerama.
Was working fine with 5.10, but broke with Dapper upgrade.
It starts OK, but after a while, Xorg gets horribly bogged. It doesn't quite halt, but far easier to go to another PC, ssh in and kill X.  Single-screen is still OK.
  The log is full of errors like:

(**) RADEON(1): Idle timed out: 64 entries, stat=0x8068c140
(EE) RADEON(1): Idle timed out, resetting engine...
(**) RADEON(1): EngineRestore (16/16)

full log at:  
[http://members.westnet.com.au/myk/Xorg.0.log-xinerama-problems](http://members.westnet.com.au/myk/Xorg.0.log-xinerama-problems)

There are warnings about DRI being disabled, but i dont think thats the problem.
  What should I do now? Is it a good idea to downgrade Xorg back to an older version?

Mike.

---

