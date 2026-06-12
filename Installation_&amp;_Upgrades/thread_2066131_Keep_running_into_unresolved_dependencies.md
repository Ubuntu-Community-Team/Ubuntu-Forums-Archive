---
title: "Keep running into unresolved dependencies"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by roey.angel on 2012-10-03
Hi, 
I've been using Kubuntu for about a year and a half by now.
One of the main problems I keep encountering is unresolved dependencies which prevent me from updating my packages or installing new ones.
Typically I install things only from the repos so I don't understand why this should happen. Some packages regularly cause problems: skype, pgl and crossover but often also removing and reinstalling them doesn't help.
I'm also aware of the --full-resolver option in aptitude. I typically try to get around the issue of unresolved packages by running ```
sudo aptitude --full-resolve upgrade
``` but this doesn't always work. Now for instance (and this happened before as well) the --full-resolver solution is to delete over 200 packages! all of them btw are of 32 bit versions (i386). I cannot imagine that this is the best way to solve this (and i find it hard to believe that my system will run again if I ever choose to do that). Prob. what's causing the problem is one or two packages. How could it be then that the solution such an overkill?

I'd appreciate tips on how to resolve my current situation and how to avoid it in the future.

Thanks in advance,
Roey

p.s
I'm running kubuntu 12.04.1 64 bit, but had the same issue with previous versions.

---

### Post by sigmatht on 2012-10-03
I've had that problem with aptitude before as well; I tend to stick with apt-get and it generally works just fine.

---

### Post by drmrgd on 2012-10-03
It might be helpful to see what's bogging down the works.  Maybe posting the output of:

```
sudo apt-get update && sudo apt-get upgrade
```

so we can see what packages are causing the problems and what dependencies are needed.

---

### Post by oldos2er on 2012-10-03
> **roey.angel said:**
> Hi, 
I've been using Kubuntu for about a year and a half by now.
One of the main problems I keep encountering is unresolved dependencies which prevent me from updating my packages or installing new ones.

This is a known bug with aptitude and multiarch: [https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768)

Best solution I've found is to use apt-get instead, as sigmatht suggested.

---

### Post by sidzen on 2012-10-03
I ran into this problem with apt-get, as well.  I kept editing the */etc/apt/sources.list* file and made sure ppa's were correct and functional until I got rid of the errors.  

Aside @ olsos2er: I've seen your handle other forums, no?

---

### Post by roey.angel on 2012-10-04
Thanks a lot drmrgd and the rest.
Running apt-get instead of aptitude managed to update all packages without complaining (and following that running aptitude stopped complaining as well).
I know that the common wisdom is that it's a bad habit to be using both interchangeably. Would you recommend me to switch to using apt-get only now?
I thought aptitude is supposed to be superior to apt-get in maintaining proper dependencies (installing and uninstalling), apart from the helpful UI.

Roey

---

### Post by drmrgd on 2012-10-04
Not being an Aptitude user, and given the bug that oldos2er pointed out, I would say using the Apt system might give you better results.  I can say that I've used Apt for a while and never had any problems - well any that I didn't create for myself that is!

---

