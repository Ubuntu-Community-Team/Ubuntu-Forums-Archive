---
title: "Command line on boot"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by clockwork9 on 2008-12-01
when i install ubuntu i get a black and white command line promt asking me to run root and sudo commands. 

then i get the typical ubuntu@ubuntu:~% _

Here's my spec's: 

1.5 gHz AMD Athlon processor
512mb RAM
80Gb HDD
Averatec Laptop

Ubuntu versions up to 6.-- work fine with the UI and all

---

### Post by lemming465 on 2008-12-02
> when i install ubuntu i get a black and white command line promt asking me to run root and sudo commands
What happens if you just boot a live CD?  Does it get to a GUI desktop, or get stuck along the way?

Does Microsoft windows of some vintage work on this laptop, if that was ever installed?

Do you know what the video chip is?  
Can you run **sudo lspci** from a command prompt, and attach the output?

> Ubuntu versions up to 6.-- work fine with the UI and all
I'm not sure I understand you here.  Do you mean older versions such as 6.06 "dapper drake" or 6.10 "edgy eft" work, while newer ones such as 8.10 "intrepid ibex" don't?

Unfortunately, we're going to need more details before we can be of much help.

---

### Post by iponeverything on 2008-12-02
> command line promt asking me to run root and sudo commands.


hehehe

run:

```
startx
```

and then post the X log file:

```
/var/log/Xorg.0.log
```

Maybe we can see why it is not happy.

---

