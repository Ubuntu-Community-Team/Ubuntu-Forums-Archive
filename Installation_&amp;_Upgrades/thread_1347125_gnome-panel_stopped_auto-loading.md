---
title: "gnome-panel stopped auto-loading"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by jctweb on 2009-12-05
I've been using Karmic since about 2 days after it was released and have been installing each update as it comes along.  today's update caused the gnome-panel to stop loading on startup.

I'd like to figure out why - but I don't know where to start?

I looked in /var/log to see if there's some sort of "startup errors" log and I'm not seeing anything right away.

Any suggestions on how to troubleshoot?  I'm curious as to why the last update broke something like gnome-panel ;)

---

### Post by itsjustarumour on 2009-12-06
Same thing here on my Ubuntu Jaunty 9.04 box - todays updates broke gnome-panel, it won't load on startup any more.



(Warning - rant alert!)

[RANT]

Sigh.  I've been with Ubuntu since Dapper, have used Ubuntu as my primary OS for 3 years and I've long passed "noob" status, but my morale is really starting to flag with this p***-poor quality control.  For one thing, I want to be able not just to use Ubuntu productively myself, but also be able to recommend it to family and friends as a Windows replacement.  And for the last 2 releases I've had to *stop* doing so, because its really just *way, way too buggy*.

Karmic has been - for me - a total calamity (5 installation attempts so far and I still haven't got a system that will load a fully-functioning desktop and get me online and working due to a raft of bugs with Kernels, KMS, 3G networking, XOrg and the Intel graphics driver stack (and yes I have contributed to bug-reporting) - but thats another story!!) and **this is the only functioning Ubuntu installation I have left**, so when I start getting these sorts of silly bugs I really start losing the will to live. Ubuntu, I love you dearly but I just can't go on with this sort of abusive relationship... this poor QC is driving me ever closer and closer to Mac or Windows 7, just so I can get some work done rather than my OS *being* the work all the time!  

[/RANT]

---

### Post by itsjustarumour on 2009-12-07
Still no joy...

I've tried recreating ~/.gconf but still same problem.  

I've also tried recreating ~/.local/share/applications/gnome-panel.desktop , but that had no effect either.

Out of curiosity I tried creating a new user and logging on with that ID, and it worked.  Strange.

I've run out of trouble-shooting time for today, so I've just added gnome-panel to Startup Applications - its an ugly workaround, but it will hopefully keep me going for now.

I'll investigate further if I get the chance...

---

### Post by jctweb on 2009-12-07
> **itsjustarumour said:**
> I'll investigate further if I get the chance...

I appreciate it.  I've been using *nix for awhile, but have rarely needed to dive in and really poke around the logs/config to see what's up when things go wrong.

---

### Post by jctweb on 2009-12-09
I've added gnome-panel to my autostart menu as well - still annoyed by the update.

---

### Post by itsjustarumour on 2009-12-09
> **jctweb said:**
> I've added gnome-panel to my autostart menu as well - still annoyed by the update.

Well, at least it works, lol! :)  In the meantime, I've still not managed to get to the bottom of this either...

---

### Post by itsjustarumour on 2009-12-12
> **jctweb said:**
> I've added gnome-panel to my autostart menu as well - still annoyed by the update.

I just found this bug report:

"Upper toolbar disappeared after use of ubuntu tweak"

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/413694](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/413694)

I had just used Ubuntu Tweak when the problem first occurred.  Do you use it too?

---

### Post by jctweb on 2009-12-12
I didn't use ubuntu tweak - but the update from yesterday seems to have fixed my issue.

---

