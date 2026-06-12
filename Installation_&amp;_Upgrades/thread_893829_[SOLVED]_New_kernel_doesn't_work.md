---
title: "[SOLVED] New kernel doesn't work"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by L337_K3y5 on 2008-08-18
To start things off, I'm using Ubuntu 8.04.1, updated recently, and this is the second time I've tried to install a new kernel, both with the same problems.  I'm trying to install kernel 2.6.26.2 from [http://www.kernel.org/]("http://www.kernel.org/").  Previously I've tried to install the 2.6.25.7 one.  After I log in at the log-in screen, it brings up my splash screen, then afterward, it goes to a black screen, goes to white, then it crashes to black, and the hard drive parks.  Although, if I log in using fail-safe gnome, I can get in, although a couple things do not work, like wireless, but I have a fix for that.  Something that catches my eye every time I try to get into the new kernel is that it shows text right before the Usplash comes up, and I see that it says "cannot get high resolution on Cpu 0" and it says the same about Cpu 1. (I have a AMD Turion 64 X2 CPU) 
Do not tell me to reinstall, because I'll just get the same end result, it takes too long, and I've already tried that on both kernels.  Also, I have uninstalled both properly afterward.  I did not do the installation wrong because otherwise it would not load, if you catch my drift.

FYI - I am using a ATI Mobility Radeon HD 2600 video card.  It is on a Asus F3-KA laptop.

*Please do not mind if I don't post back quick, I have to do other things also.

---

### Post by L337_K3y5 on 2008-08-21
For some reason my computer doesn't like new kernels...It only like the ones that came on it.  :(

---

### Post by oldos2er on 2008-08-21
You probably should stick with the kernels in Ubuntu's repositories.

---

### Post by L337_K3y5 on 2008-08-21
> **oldos2er said:**
> You probably should stick with the kernels in Ubuntu's repositories.
Well, the thing is, the newest in the repos. is 2.6.24-19-Generic...I already have that installed.  What I need is the newest, because I have problems with my sound coming out both speakers and headphones, and I need to either install a new kernel or new Alsa sound driver...The only way to install a new Alsa sound driver is to disable sound in the kernel building...and when you install the kernel you install the Alsa afterwards.  It's easier for me just to install a newer kernel, but none of them work for my computer...I'm going insane here.  The sound problem is getting on my nerves.  :mad:

---

### Post by oldos2er on 2008-08-21
Actually the newest one is 2.6.24-21.

---

### Post by L337_K3y5 on 2008-08-21
> **oldos2er said:**
> Actually the newest one is 2.6.24-21.

Are you talking about in Synaptic?  All I'm seeing is 2.6.24-19-Generic....Where is the kernel you're speaking of?  If its in the repo, what search term do I use, I've already searched for the kernel using the kernel number.

---

### Post by oldos2er on 2008-08-21
Do you have these lines in your /etc/apt/sources.list:

deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-proposed restricted main multiverse universe

?

---

