---
title: "Ubuntu crashes"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by nir2000 on 2010-01-19
Hello everybody!
First said is the fact that I used Ubuntu 8.04 for over a year, alone on my PC, and there were no problems.
Few days ago I formated my PC, installed Win xp and immediately after I installed Ubuntu 8.04 from CD side by side with Win xp.
For few days everything worked more or less fine, but after few updates Ubuntu started crashing. The only way that I can work with Ubuntu is by choosing in the login menu something that is called Failsafe Gnome startup. If I choose this option everything works fine.
I must add that I made no changes to my hardware except the fact that now I have Win xp installed with my Ubuntu.
Please help me to solve this problem.
Thank you in advance.

---

### Post by gjatute on 2010-01-19
I would reinstall... I had kind of the same problem and a fresh installation solved it.

---

### Post by aaron3 on 2010-01-19
I had some problems recently also after installing updates, and ended up re-installing from scratch. I'm not sure what caused the problems, but I don't plan on installing any more updates until I do.

---

### Post by errigalmarten on 2010-01-21
I've recently begun having similar issues with Ubuntu. I ran 8.10 on my desktop for over a year, and I had no problems. My installation of XP became buggy, so I ran wipedisk on my hard drive and decided while I was reinstalling everything, that I'd try 9.04. And hey, it worked great. For a while. Then I got some updates and it started crashing randomly. My screen would go black, and all of the fans in my case would start spinng up faster.

Sometimes it'd be stable for several hours, while other times it would crash after only thirty or so minutes. It'd never crash in Windows. So, off I went and wiped everything again, going to 9.10. Same issue. Screw it, I went back to good old trustworthy 8.10. Darn.. Same problem after I got my updates. I'm at a total loss. I know it's not my hardware, since XP works fine, and all my temps are normal, though my chipset seems to be getting rather hot, but I've ordered a new copper heatsink and an intake fan to help remedy that.

Hoping this issue gets worked out.

---

### Post by nir2000 on 2010-01-23
Hi everybody!
Thank you very much for your response,I really appreciate it. Unfortunately I can't simply reinstall Ubuntu since I already have a lot of stuff on it, and secondly I'm not sure that this is going to solve the problem.
Please if any one of you stumbles upon a solution to this problem please let me know.
good bye

---

### Post by kansasnoob on 2010-01-24
Have you tried booting an older kernel?

I just did a reinstallation of 8.04.3 to do some testing and I see it's on 2.6.24-26. Does your menu.lst show an older kernel that you could try to boot?

Just looked and mine also shows 2.6.24-24 if I change this line in menu.lst from 1 to 2:

```
# howmany=1
```

---

