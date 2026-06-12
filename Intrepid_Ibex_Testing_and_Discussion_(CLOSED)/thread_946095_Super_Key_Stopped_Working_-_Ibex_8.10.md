---
title: "Super Key Stopped Working - Ibex 8.10"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Arkhar on 2008-10-13
Hi all,

I'm running Ubuntu 8.10 Ibex beta and all of a sudden my windows(super) key stopped working. I tried rebinding it in the keyboards settings but still no dice. I'm not sure what I did and I suppose I should have been paying attention on the last list of updates I installed or packages, but I'm fairly sure it had nothing to do with it. I had been using my super key to bind a few Compiz functions to it and such, and it just stopped working. When I try to set a binding using "Grab Key Binding" in Compiz it doesn't even detect that I'm pushing the super key. I'm more or less a complete noob at Linux, so I'm not really sure where to go.

---

### Post by Arkhar on 2008-10-13
Oh, also it might be of interest to note that I had been playing with Wine a lot recently, and I was wondering if maybe that had something to do with it?

---

### Post by Saneless on 2008-10-16
bump.  I'm having the same issues.  I used to have a lot of Compiz functions tied to super, like Cube or Expo, but now they don't do anything after upgrading.

I'm pretty sure it worked RIGHT after upgrading to beta, but with constant updates everyday I can't pinpoint the day it happened.

---

### Post by TylerRick on 2008-10-22
I'm having the same problem here. Just did clean install of 8.10 beta about 5 days ago, and my compiz / desktop effects were working great -- including the many bindings that use <Super> -- until yesterday night some time.

I don't what to attribute this problem to either. True, it might have been one of the many updates I've installed via update-manager -- I install those every day when I see them. But if it were a regression bug related to a specific release, then why would it have affected you 7 days ago but not me until 1 day ago?

Will keep experimenting... I'm finding compiz is much less useful without those bindings.

---

### Post by TylerRick on 2008-10-22
It turns out that my problem was that I had xbindkeys running and had Super_L mapped to something in my .xbindkeysrc. Killing xbindkeys and restarting compiz fixed the problem.

---

