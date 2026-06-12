---
title: "Update Manager won't update gparted, parted or udisks"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-03-10
I've noticed for a few days now that updates haven't resolved for gparted, parted and udisks.

Is anyone else having this problem? I didn't find anything in a quick search.

I opened up Synaptic and attempted to upgrade, but it failed since libparted0 wasn't installed. When attempting to install libparted0, it says its going to remove libparted-2.1-0 and libparted1.8-12.

Should I wait for this issue to resolve itself, or should I manually install libparted0 (removing libparted-2.1-0 and libparted1.8-12)?

---

### Post by phillw on 2010-03-10
I've had this occur a couple of times on upgrades, if you follow the instructions here --> [http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)  You should be okay (I do now and have been since)

From my last recall, there was a an install of about 1MB in size a waiting, when I went into synaptics it was marked with a grey box, clicking on it for upgrade said it would get rid of some stuff & install something else. I said okay and after a reboot, it then allowed the updates for kernel 2.6.32.16 to go through.

If you follow the the thread, it will allow you to determine which package is safe to go, when it wishes to remove things.

Regards,

Phill.

---

### Post by executorvs on 2010-03-10
a more direct solution to that problem is -->[http://ubuntuforums.org/showthread.php?t=1425946](http://ubuntuforums.org/showthread.php?t=1425946)

it's the thread on this subject I started a few hours ago.

the consensus was that installing libparted0 worked and nothing went obviously wrong.

---

### Post by kyleabaker on 2010-03-10
> **phillw said:**
> I've had this occur a couple of times on upgrades, if you follow the instructions here --> [http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)  You should be okay (I do now and have been since)
I always avoid partial upgrades and wait until they resolve, but this one has been here for several days now.

The affected packages won't have any immediate affect on Ubuntu 10.04 loading or running, only with Gparted...which I rarely use anyway...so I think I'll go ahead with the updates.

Wish you knew for sure, but thanks. ;)

---

### Post by kyleabaker on 2010-03-10
> **executorvs said:**
> a more direct solution to that problem is -->[http://ubuntuforums.org/showthread.php?t=1425946](http://ubuntuforums.org/showthread.php?t=1425946)

it's the thread on this subject I started a few hours ago.

the consensus was that installing libparted0 worked and nothing went obviously wrong.
Thanks! I was about to update it anyway. I wonder why search didn't pick up that post with many common keywords?

Anyhoo, problem solved. No immediate side affects. :D

---

### Post by executorvs on 2010-03-10
it may not have indexed the post yet. I'm thinking if it's still broken in a day or so I'll take the time to file a bug against the ubuntu-standard package which is what I think is causing the mess.

---

### Post by svaens on 2010-03-14
This seems to be fixed for me now. 
I didn't make any work-arounds such as removing clashing libraries, but this morning, after an update, I was able to install gparted without troubles.

---

