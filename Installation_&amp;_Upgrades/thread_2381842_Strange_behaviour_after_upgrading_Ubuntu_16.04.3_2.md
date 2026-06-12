---
title: "Strange behaviour after upgrading Ubuntu 16.04.3 2-3 weeks ago"
date: 2018-01-06
forum: Installation &amp; Upgrades
---

### Post by janeku2 on 2018-01-06
Hello,
My computer is AMD X2 with 6 GB of RAM and Advanced Micro Devices, Inc. [AMD/ATI] RV620 LE [Radeon HD 3450] graphic card. Before 2-3 weeks I notice strange behaviour after booting, when desktop apear: freezing of screen. Sometimes it happened minute after show of desktop sometims it takes little longer. I had to restart 2-3 times in order to start worked properly. Yesterday I noticed this splash screen showing some message concerning graphic card work:
[ATTACH=CONFIG]278070[/ATTACH]

Somebody is familiar with this situation so can give me suggestion what to do next ? 
It started to be so annoying. 
I tried to activate AMD Micro Code in additional drivers tab, Selected Developer options, but no sucess :(



Regards,
Petrika

---

### Post by Xian on 2018-01-06
Have you tried and/or do you have this package installed?

xserver-xorg-video-ati

---

### Post by janeku2 on 2018-01-07
> **Xian said:**
> Have you tried and/or do you have this package installed?

xserver-xorg-video-ati

I checked under Synaptic and xserver-xorg-video-ati-hw is installed (Ver. 1.7.9.0) . There is version xserver-xorg-video-ati but 1.7.7.0 available but looks like it is older drivers.
I wanted to make replacement of existing Ubuntu open drivers but this card is discontinued from ATI support site so no other drivers are available for it under Ubuntu 16.04.3.

I hope that someone is familiar with this error so can help me solve it. I noticed crash report started to show couple of times since yesterday after restart of frozen system and every report was about Xorg error :(

Still stuck in the middle of nowhere with this problem. :(

In mean time while writing this message I reinstall xserver-xorg-video-ati-hw so I will see what will happened.

---

### Post by janeku2 on 2018-01-11
> **janeku2 said:**
> I checked under Synaptic and xserver-xorg-video-ati-hw is installed (Ver. 1.7.9.0) . There is version xserver-xorg-video-ati but 1.7.7.0 available but looks like it is older drivers.
I wanted to make replacement of existing Ubuntu open drivers but this card is discontinued from ATI support site so no other drivers are available for it under Ubuntu 16.04.3.

I hope that someone is familiar with this error so can help me solve it. I noticed crash report started to show couple of times since yesterday after restart of frozen system and every report was about Xorg error :(

Still stuck in the middle of nowhere with this problem. :(

In mean time while writing this message I reinstall xserver-xorg-video-ati-hw so I will see what will happened.


Looks like fresh install after update produce same result.
:(
Any one with the same problem or at least to suggest where to look to find out the problem ?
[ATTACH=CONFIG]278140[/ATTACH]

---

### Post by RobGoss on 2018-01-13
Please provide the** specs **for your machine it will help trouble shoot your problem

How does the live desktop work when you boot into the desktop?

---

