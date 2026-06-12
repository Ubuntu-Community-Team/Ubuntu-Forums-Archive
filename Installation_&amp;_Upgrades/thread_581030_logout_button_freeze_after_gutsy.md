---
title: "logout button freeze after gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by daverich on 2007-10-19
this is weird.

I just upgraded to gutsy, and after having to set the screen res to widescreen to get 1440x900 it all looks great, apart from if I click the logout button the computer freezes.

I *can* logout by doing a CTRL+ALT+Backspace but I'd like to know why what was working fine is now not working.

Anyone else?

Kind regards

Dave Rich

---

### Post by daverich on 2007-10-19
hmm and now it's working....


oddness.


Kind regards

Dave Rich

---

### Post by daverich on 2007-10-19
and now it's not.

VERY strange.

It's a silly little thing,- but it'd be nice to find a reason?

Kind regards

Dave Rich

---

### Post by dada1958 on 2007-10-22
Same problem here, but it doesn't really freeze the desktop, just wait 50 seconds, than the options appear, silly thing, but it should be fixed though ...

---

### Post by Achille on 2007-10-23
rm -fr ~/.config/autostart/

solved the problem for me.

---

### Post by dada1958 on 2007-10-23
> **Achille said:**
> rm -fr ~/.config/autostart/

solved the problem for me.

Tnx!

---

### Post by ericcart on 2007-10-23
It was already reported, you have to re-enable Power Management service. :popcorn:

There's some odd dependency.


Thanks,
Eric

---

### Post by davescafe on 2007-10-30
> **ericcart said:**
> It was already reported, you have to re-enable Power Management service. :popcorn:

There's some odd dependency.


Thanks,
Eric

Thanks for this tip. The log-out button problem has been bugging me since Gutsy pre-release builds. I had disabled the Power Manager at startup because I didn't think I needed it for a desktop (as opposed to a laptop). But re-enabling it fixed thie problem. 

Thanks again,

Dave

---

### Post by king20878 on 2007-11-08
Thanks.  This worked for me.

---

### Post by AlexMR on 2007-11-10
Thank you for sharing this. Logout didn't work for me as well due to having disabled power management at sessions, now everything's fine again.

---

