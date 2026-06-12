---
title: "Zsnes issues"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Tanjer1588 on 2007-12-03
So i have Zsnes installed on my computer and it worked great for 2 days or so, when i try to run it now it starts, shows the screen for less then a sec. and it gos away i cant seem to fingur out what the problem is so if any one can help me that would be great.

thanks in advance

---

### Post by acoustibop on 2007-12-03
How did you install ZSNES and which version is it, Tanjer1588?

The best thing to do is probably to delete your ZSNES configuration file (in ~/.zsnes, usually).  That means you'll have to re-configure it; t he most likely reason is you've changed a setting that makes the emulator un-runnable.  Have you uninstalled anything in the last few days?

---

### Post by Tanjer1588 on 2007-12-03
> **acoustibop said:**
> How did you install ZSNES and which version is it, Tanjer1588?

The best thing to do is probably to delete your ZSNES configuration file (in ~/.zsnes, usually).  That means you'll have to re-configure it; t he most likely reason is you've changed a setting that makes the emulator un-runnable.  Have you uninstalled anything in the last few days?

I installed my zsnes through the Synaptic Package Manager, about 4 days ago or so. its Version 1.51 i ran it in the terminal and it gave me the ...

```
 Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/sean/.kde/socket-Sean-Desktop.
can't create mcop directory

``` 

i seen this in other thred but nothing seemed to work, I ran a zsnes -ad oss command and it worked but when i closed it and tryed to start it again it didnt work

---

### Post by Tanjer1588 on 2007-12-03
U know what... i ran that zsnes -ad oss again and it seems to be working now

---

