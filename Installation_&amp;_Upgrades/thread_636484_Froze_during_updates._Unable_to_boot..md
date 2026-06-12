---
title: "Froze during updates. Unable to boot."
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2007-12-09
Now, mind you, I'm reinstalling Ubuntu as we speak. I was on my laptop installing Gutsy and it started to freeze during the updates. Me clicking around on things didn't help. Eventually I cut the power. Upon boot after logging in, it would just yield a solid tan screen and would hang there.

I just decided to reinstall since I have nothing to lose. But looking back, I took the cheap way out. Typically would there be a way around that? Or since power was cut during updates would it be very hard to get around that issue?

---

### Post by PmDematagoda on 2007-12-09
You can restart Ubuntu cleanly by following the instructions from this [page]("http://ubuntuforums.org/showthread.php?t=617349"), it can help reduce data corruption and also is much better than a cold reboot.

And did Ubuntu work well before this event?

---

### Post by Roasted on 2007-12-09
I wasn't running Ubuntu before this. I was running Fedora Core 8 due to Ubuntu's piss poor support for the sound card on my laptop. I however ran into similar (but not as problematic) issues in Fedora as well.

Hearing that my sound card is supported in OSSv4 now, and not Alsa, I came back to Ubuntu to get OSSv4 running in hopes of my sound being functional.

I'm having some strange errors that just drive me insane with Ubuntu. Mind you, I did a fresh install and have gone through the updates in a slow and systematic method. Everything was done correctly. Yet pidgin is constantly RANDOMLY shutting off unexpectedly. On top of that, when I reboot, it freezes at the black screen. Only way to get it to reboot is to power down completely and hit the power button again.

Keep it up Ubuntu. Fedora is about to take over again.

---

### Post by PmDematagoda on 2007-12-09
Post the complete specifications of your PC.

---

### Post by Roasted on 2007-12-10
AMD Turion 64 X2 TL-58 1.9GHz
1 GB DDR2 PC5300 ram
160 GB 5400 RPM HDD
ATI Radeon X1200 128mb (319 dynamically allocated shared) graphics card


I got pissed off and took Ubuntu off and put Fedora on. An hour later, I felt guilty that I let a problem go unsolved. I just installed Ubuntu, and for the last 6 minutes or so I've been waiting for it to log back in. Great.

---

### Post by PmDematagoda on 2007-12-10
I think your ATi card may be the issue, boot into Recovery Mode, then do:-
```

dpkg-reconfigure -phigh xserver-xorg
```

After that is done, do:-
```

startx
```

To see if you can get the GUI then.

---

### Post by Roasted on 2007-12-10
I don't see how it would be. I used to have Ubuntu running on this laptop. Everything was flawless except wireless and sound, which is why I ditched it for Fedora in the first place. Now I'm trying to give it a second whim and it won't even boot for me, damnit. 

I'm trying to reboot now, but it won't even let me reboot. I have to completely power it off and power it back on for it to function.

---

### Post by PmDematagoda on 2007-12-10
A lot of people have problems with ATi cards, especially since their drivers are still not as reliable as the Nvidia ones(Hopefully it will be fixed in the near future with the ATi drivers having gone Open Source). If it is a problem with your VGA card, then such a problem like the one you are mentioning does occur, so in that case the best bet is to use another, more reliable driver which in this case would be the vesa one which can be activated using the command I gave previously.

---

### Post by Roasted on 2007-12-10
That's the thing.

I used this video card before.
I used this driver before.
No problems.

NOW...

Problems out the wazoo. GRRRRRR

---

### Post by PmDematagoda on 2007-12-10
Roasted just give what I suggested a try, we may be able to at least to get the GUI to work using the vesa driver.

When that is done, then we could go on the path of trying to configure your ATi to work with your PC.

---

### Post by Roasted on 2007-12-10
Well when I was in class today I did a fresh install of Ubuntu while I was messing around in the lab. Everything seems to be working fine now. The only minor issue i came across is before when I was running Ubuntu on here I would get some lagging issues as I typed commands in the terminal. It was as if my system was lagging to process the text on screen that I had already typed. That was unimaginably annoying. So I did away with it, tried MInt, moved on to Fedora, moved back to Ubuntu, and here it works great.

I think my problem was the first time I had a bad disc. I have since burned a new copy and burned it at the slowest setting possible and it seems fine now. However, earlier I had that happen one time where something I was typing in terminal kind of lagged. I logged out, back in, and it seems great now. Only thing is my damn sound. I can't get it to work.

---

