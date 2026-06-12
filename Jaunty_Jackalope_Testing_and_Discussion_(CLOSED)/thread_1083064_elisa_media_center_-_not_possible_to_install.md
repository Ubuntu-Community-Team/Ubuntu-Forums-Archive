---
title: "elisa media center - not possible to install"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by meborc on 2009-02-28
it has been so for a while... am i only one getting this?

> The following packages have unmet dependencies:
  elisa: Depends: python-elisa (= 0.5.28-1) but it is not going to be installed
         Depends: elisa-plugins-good but it is not going to be installed
         Depends: elisa-plugins-bad but it is not going to be installed
         Recommends: elisa-plugins-ugly but it is not going to be installed
E: Broken packages


i'm wondering if it is related to python troubles lately? although i have not been able to install elisa for 2 months in a row :D

---

### Post by zekopeko on 2009-02-28
not even from their repo?

---

### Post by meborc on 2009-02-28
> **zekopeko said:**
> not even from their repo?

there is no elisa ppa for jaunty... or i have seriously missed something :)

and of course i'm talking about the elisa package in ubuntu repos

---

### Post by zekopeko on 2009-02-28
hmmm.... i have elisa installed (but i will have to check from where).
btw you can upgrade (version 0.5.27+) by running gksudo elisa and then going to the plugins section -> upgrades.

---

### Post by meborc on 2009-02-28
> **zekopeko said:**
> hmmm.... i have elisa installed (but i will have to check from where).
btw you can upgrade (version 0.5.27+) by running gksudo elisa and then going to the plugins section -> upgrades.

yep, but i need to install it first... i could do the ugly subversion install :) but there is a reason why there is an elisa package in apt ;)

does anyone have the same issue?

just try to install elisa package and see if it can be done or not... so i know if it is my system or just broken packages in the repos

---

### Post by tretle on 2009-02-28
A new package will be in soon, they got freeze exception.

---

### Post by scaine on 2009-02-28
I just marked it successfully in Synaptic, so this must be fixed now.  No broken dependencies that I can see.  I do have another 178 python-related downloads on the way though, so maybe it'll be broken again after them.  I'll edit this post once my updates are complete...

[EDIT] Yep - that's it broken now.  This is definitely still an issue if you want Elisa on your Jaunty system right now.  I imagine that this won't last for long though.  The Python changes ongoing at the moment might take a bit of time to get through, that's all.

[EDIT2] Deluge is also broken by this update.  It removed my existing deluge install as part of the upgrade, but there's no replacement package for it yet.

[EDIT3] Someone has just posted in another thread that CCSM can be installed now, so this is obviously clearing up now.  Sadly, Elisa and Deluge are still hosed.

---

### Post by meborc on 2009-03-02
that's good to hear :) ... so it is not just my system that is borked up...

thanks

---

### Post by scaine on 2009-03-08
Looks like Elisa is good to go again.  Might be old news, but just in case you were waiting for a fanfare...

---

### Post by zekopeko on 2009-03-08
> **tretle said:**
> A new package will be in soon, they got freeze exception.

this is pretty good news. as i've stated before elisa can now update itself sans the ubuntu repository.

---

### Post by meborc on 2009-03-11
> **scaine said:**
> Looks like Elisa is good to go again.  Might be old news, but just in case you were waiting for a fanfare...

yep... the repo works again

---

