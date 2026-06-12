---
title: "Installing 7.10 stuck at 82%"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Heeter on 2007-10-19
Hey all,

This is my first time installing Ubuntu

I am going dual boot with XPPro, with XP already installled

This is an 80gig HD, and XP only occupies 20gig, the rest has always been empty, unformatted and unpartitioned.

I started up 7.10 install from the liveCD install shortcut from the Ubuntu desktop.

I selected a 20gig partition to install Ubuntu on the partition slider.

Now I am still waiting for install to complete as it has been at 82% "Configuring APT, Scanning the Mirror" for the longest time.

I shut down the system and started over again with another partition of 25gig this time, again it is stuck at 82%

What am I doing wrong, or how can I fix this, as I cannot boot into Windows anymore.


Thanks,

Heeter

---

### Post by BoardDWorld on 2007-10-19
I don't mean to be rude but I have answered this 3 times myself in this very same category, this doesn't include everyone else. just search "install stuck"...

---

### Post by styrofoam cup on 2007-10-19
Hi,
I just had this same problem.
does it say checking mirror or something?
It is to do with the mirror being down or chocked (i think)
if you go to system settings and disable your network connection it will time out and then continue.
Warning - this means you will have to manually fix your sources.list file (you get a screen warning) later on after rebooting.
:KS

---

### Post by BoardDWorld on 2007-10-19
I see this question is being ignored by most now... Disable networking from the two monitors on the top right of your task bar.

---

### Post by mpp on 2007-10-19
I have experienced the same problem just now.  It does eventually time out without the need to disable networking... took 30 minutes to time out for me.  It then pops up a warning message to edit the sources file later.

have fun()
mike

---

### Post by Heeter on 2007-10-21
Sorry about this, BoardDWorld

I did search, because I was pretty sure that it was a common occurrence, but I did not find what I was looking for, maybe I did not look hard enough?

Anyways, you are not being percieved as rude. Thanks for answering.

I am soooo looking forward to using Ubuntu as my main OS.




Heeter

---

### Post by FredB on 2007-10-21
Just because servers are under a heavy load because of release time.

82% means : grabbing packages info (which software are updated or not), and for non english speakers (at least 60% of the people on Earth), translation file.

---

### Post by rahimveron on 2007-10-21
I had the same prob last might stuck at 82% as it was checking the mirrors.
So i just switched off my ADSL Modem and the installer resumed.

---

### Post by Davi0 on 2007-10-21
Just right click on the network icon on top right and untick. You will have to configure networks after install of course.

---

### Post by Nomen.Nescio on 2007-10-21
Sorry this doesnt work on my G4 Apple ibook.
I tried to disable the network, I unplugged the cable...

It takes longer for the error message, but I still cant pass this hurdle.

Need really some advice!

---

### Post by gregbzh on 2007-10-22
> **Davi0 said:**
> Just right click on the network icon on top right and untick. You will have to configure networks after install of course.


Worked a treat for me on my Gutsy installation.  Cheers.

---

### Post by alivtl on 2007-10-22
it means does'nt suck , you will be wait for long time til it would be installed

---

### Post by gonon on 2007-10-22
i have similar problem my installation goes to 6% and than gets stuck after few minutes red warning screen pops out telling me that software installation failed ,i dont know if this is important but i burned the iso on dvd not cdr i made 4 copies thinking that maybe i got bad disc but still no luck aha i have winxp on another partition .hope someone can help me thanks

---

### Post by thhjimmy on 2007-10-22
Encounter the same problem. I guess Ubuntu trying to download software from 
the server. I tried open a terminal console and kill the apt processes. Ubuntu 
will continue to setup. But after you finished setup you need to go
Applications > Add/Remove > Preference to change the download server.
Seem like the download server not very good at the moment as alot of Ubuntu
fans are downloading the iso so its very slow.
Give it a try. Please correct me if I am wrong. I also here to learn.

:popcorn::guitar:

---

### Post by gonon on 2007-10-24
yeah that worked like a charm everything went fine thanks a lot for your suggestion ,appreciated cheers:KS

---

### Post by pablofaria on 2007-11-22
Just for share my experience with you guys, I solved this problem like this:

- Open a terminal console;
- Did a "ps -A"
- Kill the process related to "apt-setup-verif" (or "apt-verif-setup", no sure now...)

That's it.

---

### Post by niceguy123 on 2007-12-27
> **BoardDWorld said:**
> I see this question is being ignored by most now... Disable networking from the two monitors on the top right of your task bar.

Thanks,

I've been stuck for hours, tried downloading and making new copies on the CD and finaly found your hint. disabled the network and after a few min. the installation resumed.

---

