---
title: "64 bit Karmic @ 100% CPU"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-08-16
Don't know why but it seems to run 100% most of the time. Very sluggish. Checked process running and got 2 'ruby' zombies, what ever that means and couldn't kill/end them

---

### Post by psyke83 on 2009-08-16
[This]("https://bugs.launchpad.net/bugs/389686") is a possible culprit.

---

### Post by DougieFresh4U on 2009-08-16
> **psyke83 said:**
> [This]("https://bugs.launchpad.net/bugs/389686") is a possible culprit.
Thanks ,but no compiz. Got the ATI Radeon HD3200.
What would be the 2 'ruby' in process running as 'zombie'?

---

### Post by ronacc on 2009-08-16
use top to see which process(s) are hogging the CPU , you can try       kill -kill <process number> to end the zombies ( may need sudo) .

---

### Post by DougieFresh4U on 2009-08-16
> **ronacc said:**
> use top to see which process(s) are hogging the CPU , you can try       kill -kill <process number> to end the zombies ( may need sudo) .

'Top' isn't really showing much, unless I'm misreading.
Thanks for your reply :)

---

### Post by kopus on 2009-08-17
I'm having the similar problem on a Sony Vaio FW, the CPU is not at 100% but it's too hot!
There is no process that is consuming CPU to expalin the Temp, about 52º (Celsius) on idle. The normal temp should be about 45º/46º.

Any guess of what my be causing this?

---

### Post by jfernyhough on 2009-08-17
Have you tried creating a new user and log in in with no startup applications? This way we can narrow down whether it's you or Ubuntu. :D

---

### Post by ronacc on 2009-08-17
> **DougieFresh4U said:**
> 'Top' isn't really showing much, unless I'm misreading.
Thanks for your reply :)

are you sure your cpu is running at 100% ?  how are you checking it ?
the only thing I see is that xorg is taking alot of cpu , on my sys its taking 2>5% .

---

### Post by DougieFresh4U on 2009-08-17
> **ronacc said:**
> are you sure your cpu is running at 100% ?  how are you checking it ?
the only thing I see is that xorg is taking alot of cpu , on my sys its taking 2>5% .
Good Eve
I am using 'System Monitor' as a guide. It goes back and forth for each CPU
Running **AMD Athlon 64x2  5200** and the graphics is** ATI Radeon HD 3200**

---

### Post by psyke83 on 2009-08-17
Gnome System Monitor itself is a system hog - don't rely on it as an accurate measurement. It's likely that your graphics drivers aren't accelerating the cairo graphics in all those graphs, which is offloading to your CPU.

---

### Post by DougieFresh4U on 2009-08-17
> **psyke83 said:**
> Gnome System Monitor itself is a system hog - don't rely on it as an accurate measurement. It's likely that your graphics drivers aren't accelerating the cairo graphics in all those graphs, which is offloading to your CPU.

Thanks for your input. I suspected System Monitor as when I opened it, computer like comes to crawl.

---

### Post by ronacc on 2009-08-17
yes gnome system monitor eats cpu big time . trust top or htop , htop has a better display try it . I still think something may be flaky with your video driver 36% is awful high for xorg if all you had running was what is shown .for reference my sys is amd64x2 4600 and nvidia 7600gs .

---

### Post by DougieFresh4U on 2009-08-17
> **ronacc said:**
> yes gnome system monitor eats cpu big time . trust top or htop , htop has a better display try it . I still think something may be flaky with your video driver 36% is awful high for xorg if all you had running was what is shown .for reference my sys is amd64x2 4600 and nvidia 7600gs .

Never thought about hyop, thanks and here it is:

---

### Post by ronacc on 2009-08-17
here is a screenshot of my htop with about the same things running , note that xorg is 1% and FF is less than 1% try dumping firefox and see what happens mabye one of the plugins is running wild .

---

### Post by psyke83 on 2009-08-18
Correct me if I'm wrong, but isn't the fglrx driver currently non-functional in Karmic (as it's still using a RC kernel)? That would explain your problem.

Either your system is using the VESA driver, or it's using the radeon driver, but acceleration is not functioning properly. Check your Xorg.0.log.

---

