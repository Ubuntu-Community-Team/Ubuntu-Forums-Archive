---
title: "Fresh install:  fails to shutdown"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by Speedwagon on 2010-09-14
Just did a fresh LiveCD, format drive(new drive even) of 10.04.1 64 bit.  When I click the power button, and select shutdown, it doesn't.  It ends up logging me off, but that's it.  No shutdown.  Can't say I've tried all the power options there, but the shutdown is the most important one to me.

Any ideas on what is going on/how to fix it?

---

### Post by tommcd on 2010-09-15
As a possible work around, try running from the terminal:
```
sudo shutdown -h now
```
If it gives errors and fails to shut down the system, post the errors here.

---

