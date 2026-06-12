---
title: "updates screwed up AWN!!"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Flywaver on 2009-03-03
Greetings, this morning I got a partial upgrade that updated glib and python among other things and after a reboot things got messy! :(

Of course the sound is screwed but this seems to be a lot of users...but my main issue is that it totally screwed up AWN! If I start pidgin, it won't show on the desktop so I can't select it! It starts minimized and it doesn't show so I can't see the buddy list! 

Also, if I select docking preferences for AWN, the window does not load at all...so I can't even tweak AWN! :(

Here is an attached screenshot explaining my problem!

[[img]http://www.postimage.org/aVKnX8i.jpg[/img]](http://www.postimage.org/image.php?v=aVKnX8i)

Cheers!

---

### Post by mariner09 on 2009-03-03
I got bit by this as well, this morning.  So much that I'm about to re-install with a fresh Alpha 5 iso.  There's a sticky at the top of this forum which details the changes to python which directly affected the awn-manager package as well as some of the extras packages.

The AWN maintainers need to build new packages for this to be fixed, so look to cairo or docky or other alternatives in the meantime...

---

### Post by Triggerhapp on 2009-03-04
Or just dont do partial upgrades :P

---

### Post by neppakyo on 2009-03-04
awm-manager.

I'm not at my jaunty comp, but it has something to do with dependency problems with python, not sure which version of python tho. 

A few other programs are effected as well, not just awn

---

### Post by Flywaver on 2009-03-04
Well, when I check in Synaptic for AWN there's a few things that aren't installed and if I try to install them it says python < 2.6 required! :(

---

### Post by Flywaver on 2009-03-04
Alrighty...I d/l the Alpha 5 ISO, reinstalled from scratch and did the updates...everything works like a charm!! :D

Cheers!

---

### Post by mariner09 on 2009-03-04
That's bizarre, I did the same thing last night.  Fresh alpha5 install, applied updates and I can't install awn-manager because it depends on python-awn which depends on the older python package.

Is there a compat package that will allow this to work?

---

### Post by neppakyo on 2009-03-04
> **mariner09 said:**
> That's bizarre, I did the same thing last night.  Fresh alpha5 install, applied updates and I can't install awn-manager because it depends on python-awn which depends on the older python package.

Is there a compat package that will allow this to work?

Same thing here. Fresh alpha5 jaunty install, and python dependency error.

---

### Post by sebastjanp on 2009-03-05
The same here. Please someone compile awn-manager and applets with the new python.
PLEASEEEEEE

---

### Post by taavikko on 2009-03-05
> **sebastjanp said:**
> The same here. Please someone compile awn-manager and applets with the new python.
PLEASEEEEEE


Check for existing request, or file a new one
[https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator](https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator)

These things don't change by yelling in here, if it's not reported, it'll get's fixed only by chance...

---

### Post by ruik on 2009-03-05
[https://lists.ubuntu.com/archives/jaunty-changes/2009-March/006706.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-March/006706.html)

---

