---
title: "Intrepid updates cause beeps during bootstrap"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by remy06 on 2008-10-22
Hi,

I have installed Intrepid beta on my dell inspiron 1420 laptop.Everything was fine until i did an update, via "apt-get update".All packages seem to update properly without errors but when i tried to reboot,halfway during the bootstrap process my laptop gives out repeated beeping sound and stalls at blank screen.Then i have to shut it down.

My dell 1420 did not come with ubuntu btw and i wanted to install ubuntu on it.Have installed and used hardy for a month on it without problem.

Any assistance pls?

Thank you.

---

### Post by remy06 on 2008-10-22
bump

---

### Post by autocrosser on 2008-10-22
Take a look at my old bug: 
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)
There are links to several other bugs that might be able to help you.....

---

### Post by remy06 on 2008-10-23
I followed the threads in the link you provided and I have included back "quiet splash" in menu.lst and now it works!Hmm..is there a proper fix for this by doing an update?

However,I lost my wireless now.Icon is still there but its unable to detect wireless networks and wireless/wired options are greyed out.Any suggestions?

Thanks!

Intel Pro/Wireless 3945 ABG

---

### Post by autocrosser on 2008-10-23
N-M 0.7 had been having "issues"--there are a couple of threads about it--I'm running a Linksys card, so I can't help you there....

---

### Post by hikaricore on 2008-10-23
My roomie had this problem repeatidly on startup/shutdown.

For the time being I just unplugged the damn pc speaker from the board. ;p

---

### Post by remy06 on 2008-10-24
> **autocrosser said:**
> N-M 0.7 had been having "issues"--there are a couple of threads about it--I'm running a Linksys card, so I can't help you there....

Its ok.You helped me solve the booting issue already.Appreciated.I will still be looking around for solutions and hopefully someone else can help me here.

Hi hikaricore,

The sound problem is solved already and can log in to ubuntu now.But still got wireless connection problem.

---

