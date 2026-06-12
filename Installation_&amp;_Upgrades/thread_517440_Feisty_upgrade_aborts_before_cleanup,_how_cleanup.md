---
title: "Feisty upgrade aborts before cleanup, how cleanup?"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by Ben Branch on 2007-08-04
I just (finally) upgraded from Edgy to Feisty. Most of the way through the 'install & configure'
it started encountering errors, configure errors (I assume) from powernowd, then nvidia-settings,
then a couple more, and then the upgrade itself crapped out. 

Things actually seem to be in reasonable shape (although vi in an xterm acts flaky), although
my upgrade never got to the 'cleanup' stage. The configure did run for quite a while before
blowing up, so perhaps I got most of it done.

But 'cleanup' never got done. What might I do to get that cleanup run?

Thanks!

---

### Post by benx009 on 2007-08-04
hmmm... well, i don't exactly know how to diagnose your problem, but i do know that when i installed ubuntu once, it didn't get to the cleanup stage because of an error it encountered when trying to configure the boot loader....

---

### Post by Ben Branch on 2007-08-05
Well, I don't know if it's all that the upgrade would have done had it completely normally,
but 'apt-get autoclean' sounded harmless and recovered about 1.5GB of disk space. From
'man apt-get':

 > Like clean, autoclean clears out the local repository of retrieved package files. The
          difference is that it only removes package files that can no longer be downloaded, and
          are largely useless. This allows a cache to be maintained over a long period without it
          growing out of control.

---

### Post by Gremlinzzz on 2007-08-05
i use the command sudo apt-get autoremove
:guitar:

---

