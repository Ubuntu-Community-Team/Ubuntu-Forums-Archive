---
title: "Major Practical Dif 8.04 vs 9.xx?"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by clevertomato on 2009-12-03
What are SOME practical differences between 8.04 and 9.xx? Are there any reasons a person would want to consider running 8.04 now even though 9.xx are out? I'm asking because I'm curious but also a little because I've wondered if 8.04 would be better suited for my Gateway MX7118 laptop that is about 4 years old. It runs 9.04 pretty well but won't suspend on its own (it will suspend manually). 9.10 makes it lock hard upon resume so I couldn't keep it on here. It seems there are plenty of folks out there that run older versions of Ubuntu than the latest, so i'm wondering what the differences, advantages, disadvantages would be.

---

### Post by raymondh on 2009-12-03
> **shawnboy said:**
> What are SOME practical differences between 8.04 and 9.xx? Are there any reasons a person would want to consider running 8.04 now even though 9.xx are out? I'm asking because I'm curious but also a little because I've wondered if 8.04 would be better suited for my Gateway MX7118 laptop that is about 4 years old. It runs 9.04 pretty well but won't suspend on its own (it will suspend manually). 9.10 makes it lock hard upon resume so I couldn't keep it on here. It seems there are plenty of folks out there that run older versions of Ubuntu than the latest, so i'm wondering what the differences, advantages, disadvantages would be.

My $0.02 ....

8.04 is an LTS version.  Canonical promises to support the version for x number of years..... as opposed to the 6-month versions.  To me, that means canonical will devote X number of employees who will spend the next X amount of years supporting the LTS.  Imagine a developer doing/supporting the same version for X years .... the more you work on it, the better you get ;) 

On the other hand, the newer versions have the tweaks and drivers in them that make the ubuntu experience better.  As an example, my netbook uses the Realtek rtl8187se wireless card.  In 8.10, it did not work unless I installed a patched driver.  In 9.04, it works out of the box.  So on and so on.

I consider the 6-month versions as 'test versions' that culminate into an LTS version.  The pros are added ... the cons are tweaked .... etc.  

I still run 8.04 in one machine and 9.04 in 2 machines.  I am looking forward to LUCID, the next LTS . 

Of course, this is a non-verified opinion :)  I am neither a developer nor an employee of Canonical.

Regards

---

### Post by earthpigg on 2009-12-03
an older release will come with older more tried-and-true software. this includes both core components of your system (that most of us want to be tried and true) and user software such as firefox and pidgin (that most of us want to be the latest and greatest).

if you dont care about new firefox or openoffice features, then its best to stick with LTS.

a balance must be struck between 'latest and greatest' and 'tried and true'. 

which is more important to you? that will determine which route to take.

and, you may want to consider never bothering to install a release on hardware that didn't exist when the release was cut... for example, 8.04 would be fine on your computer older than the 4th month of 2008, but i wouldn't try it on a new Intel i7 CPU... in fact, i ***did*** try it and it was a horrible failure.

---

### Post by clevertomato on 2009-12-04
Thanks for the helpful replies. That helps me understand a little better. I downloaded 8.04 and may try it on my 4 yr old laptop. Actually, Jaunty works surprisingly well on it, except I can't solve the issue of it not honoring my power management preferences (I can manually suspend/resume, but if I set it to suspend after, say, 5 minutes of idle time, it never does).

Regarding software, these days I lean toward "tried and true" more often than not. Firefox is the one exception where I've grown accustomed to the niceties of 3.5.

I may shrink my XP partition a little more and squeeze 8.04 between XP and Jaunty to give it a spin. I would hope it would work pretty well. I mainly wonder about wifi (I have a broadcom b43) and the auto suspend, but again... it should be fairly easy to find out. If all works (or at least as many things work as in Jaunty), I may keep it around.

I dove into GNU/Linux (and began dabbling with FreeBSD) a couple months ago. It's still [pleasantly] strange to get used to so many choices and options. Sometimes it's a pain, but the more experience I gain, the more I appreciate it. There is a certain simplicity to not having any choice, but after tackling the learning curve a bit, choice is nice!

(I'm running FreeNAS on an AMD Athlon 1 Ghz, pfSense on a Pentium II 266 Mhz w/256 MB RAM, Damn Small Linux on a Toshiba Tecra Pentium 133 Mhz with 80 MB RAM, and playing with CrunchBang and Masonux on other old PCs.)

---

### Post by earthpigg on 2009-12-04
> 
Regarding software, these days I lean toward "tried and true" more often than not. Firefox is the one exception where I've grown accustomed to the niceties of 3.5.

if its only one or two apps you want to be current, you can certainly get them on older releases.

google search "ubuntu 8.04 [app name and desired version number]"

don't apply a solution that only one random website provides....

find a method that 3 or 4 different websites are telling you to do the same thing. if everyone agrees that ***-this-*** is the best way to get App X Version Y in 8.04, then that's probably the way to go.

---

