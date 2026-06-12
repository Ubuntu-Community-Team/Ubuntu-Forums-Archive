---
title: "Does Ubuntu 13.10 have the concept of &quot;control + alt + delete&quot; to get out of hanging?"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by Jim_Granite on 2013-10-26
At least once a day, my new Ubuntu 13.10 setup hangs such that the mouse works, but nothing else does.
If I had a control + alt + delete key-like sequence, perhaps I could kill a few processes?

QUESTION: Does Ubuntu have a way to interact by keyboard to kill and restart the X-window process (or Firefox or whatever application is hanging the system)?

Also, is there a Ubuntu 13.10 debug switch so a normal USER can analyze system crashes?

Ever since I installed Ubuntu 13.10 a few days ago, it has been hanging on me, on the order of once every day or two.
It hangs mostly when multiple apps are running, but, once it hangs, NOTHING I can do short of rebooting will help.
I get a lot of these messages to send detailed debug information to Canonical, which I always do.
But, it's so frequent, that I was wondering:

Is there something I can do AHEAD of time to set a debug switch and then look at WHY this is happening?
[ATTACH=CONFIG]247247[/ATTACH][ATTACH=CONFIG]247248[/ATTACH]

---

### Post by Jim_Granite on 2013-10-31
> **Jim_Granite said:**
> If I had a control + alt + delete key-like sequence, perhaps I could kill a few processes?
I guess the lack of an answer means the answer is no.

---

### Post by grahammechanical on 2013-10-31
Question: Have you tried pressing Ctrl+Alt+Delete? Sometimes the three fingered salute will reboot the machine and that is not what you are asking for. But there is something that you need to keep in mind. Linux/Ubuntu is under continual development and do things change.

I also experienced system freezes during the last weeks of Saucy Salamander development. This freeze was so complete that even if we had some kind of Services Manager it would not be able to load. I had top running to see what it was that was using up resources and nothing was doing it. And at the time that the system froze so did top. There is not a lot we can do when we cannot even open a terminal with Ctrl+Alt+T or Ctrl+Alt+F2

The error messages that you were given show that the problem was caused by Xorg. It is my guess that there was some kind of conflict between a recently updated Linux kernel, Xorg and the video driver.

Regards.

---

### Post by Jim_Granite on 2013-11-05
> **grahammechanical said:**
> Question: Have you tried pressing Ctrl+Alt+Delete?
The three-fingered salute does nothing on my dual-boot laptop when I'm booted to Ubuntu 13.10.

> **grahammechanical said:**
> There is not a lot we can do when we cannot even open a terminal with Ctrl+Alt+T or Ctrl+Alt+F2
Exactly. That's why I wanted a hardware interrupt to at least bring up the "ps -elfww" command, so that we could "kill -9" whatever tasks were hanging the system. 

> **grahammechanical said:**
> The error messages that you were given show that the problem was caused by Xorg. 


The errors seem to vary, e.g., here is the latest set:
[ATTACH=CONFIG]247588[/ATTACH]

---

### Post by matt_symes on 2013-11-05
Hi

Try pressing 

```
alt + sysrq + r
```

at the same time <without the + key>  (if you have no sysrq key, use the prtsc key) and then type

```
ctrl +alt + f1
```

to get to a console and see what is happening.

Does that get you to a console ? Try both left and right alt keys.

Kind regards

---

### Post by oldfred on 2013-11-05
Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

If you can get to terminal with cntl-alt t , you can use top (q to quit) to see what is running and and terminate a process that is causing issues with a sudo kill (ID num from top). If essential system proces it may kill system and then you have to run the REISUB.

Log files show show what has happened, but there are many log files and you may have to review a lot if not sure what is causing issue.

---

