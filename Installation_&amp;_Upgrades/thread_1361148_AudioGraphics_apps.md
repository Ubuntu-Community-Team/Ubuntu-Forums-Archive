---
title: "Audio/Graphics apps"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by spetroff on 2009-12-21
I'm officially giving up on Ubuntu Studio (9.04). The last update has cooked the networking and Xorg now sits punishing the CPU between 60-95%. I don't even want to fix it at this point because it was so flaky when it was working. My problems started after installing OpenOffice (apparently a big no-no), but I haven't been able to keep the up-time longer than a few days despite numerous attempts to remove Office (most of which failed, but one seemed to work). My problem is that Office is a must-have, so I want to move to the regular kernel and install whichever apps are appropriate for Audio recording and graphics work (this system is for my daughter). Studio is probably too ambitious for us at this point, I'd just like to get a list of which applications are appropriate for a beginning composer: some midi work, vocals and guitar. It also has to double as a school work system (hence Office). Which applications should I install in my new 9.10 box?

Also, am I likely to run into any issues just installing over top of Studio? Do I have to flatten and rebuild the box or can I keep at least the user data the same?

Thanks

Shane

---

### Post by hugmenot on 2009-12-21
I guess you have to flatten. You can save user data only if you have /home on a separate partition. Otherwise you have to copy that stuff off to another drive and copy it back.

---

### Post by audiomick on 2009-12-21
Hallo.
I am a bit surprised to hear of your problems with open-office. I have it on my Ubuntu Studio, and have no problems.

Anyway, you want to know what to install. If you open the Synaptic Package manager and search ubuntustudio you will get a list of metapackages and packages from Ubuntu studio. I would suggest making a note of what you have installed now, and installing the same ones after the new install. As far as I now, you shouldn't have any problems doing that.

Bear in mind (I am not trying to change your mind, just making an observation) that one of the main differences between the standard Ubuntu and Ubuntu Studio is the real time kernel, which is there to reduce latency. This is particulary relevant for music recording, where a long latency can lead to timing problems. If you find that this becomes a problem with your daughters projects, which it may not, it might be worth thinking about a dual boot Ubuntu - Ubuntu Studio.

I have also seen Abiword recommended for Ubuntu Studio as an alternative to Open Office.

Another observation: It is also possible, although I can't tell you how (sorry), to change the Kernel. If you can find out how to do that, it might solve your problems whilst saving your install.

---

### Post by spetroff on 2009-12-22
@hugmenot - Doesn't a standard studio install create 3 partitions?

@adiomick - I'm on an older version of studio than you, and there are boatloads of people who can't run OpenOffice. I'll check into it, and see if the 9.10 kernel doesn't conflict any longer, because I would prefer to stick with the real time kernel so long as it is stable (my current setup is orders of magnitude flakier than Win2K).

---

