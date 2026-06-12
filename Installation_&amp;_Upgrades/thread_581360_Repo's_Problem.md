---
title: "Repo's Problem"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Saponsky09 on 2007-10-19
Hi there, I have a problem with my sources.list I keep getting this message when I try to apt-get update:
```
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: Unable to lock the list directory
``` 
and then this one:
```
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

Then I went to /etc/apt/sources.list and guess what? all of my repo's are missing!!! Only some from the CD are left!!! and the same for sources.list.save.
Do you have any idea about how to get the default repo's back? I tried activating them with synaptic's software sources but I keep getting the same error.
Any ideas? Thanks for your time!

---

### Post by jbaerbock on 2007-10-19
Yeah I installed Gutsy and I have a crap load of repos missing too. And so I am trying to reload and half of them get failed. The ones that do load take forever to load. And during install GParted crashed every 5 minutes. Seriously did they not test 7.10 before release?

---

### Post by jbaerbock on 2007-10-19
Ok after reloading my repos I think I have most of them operational. Small price to pay I guess.

---

### Post by Saponsky09 on 2007-10-19
would you please tell me the address fro the repo's that are currently working for you??? I mean the one's from Ubuntu.

---

### Post by Saponsky09 on 2007-10-19
I think they did well correcting some bugs prior to the release candidate for Gutsy but I think they rushed out for Gutsy's final release. IMHO I guess this was due to some bussiness with Dell computers which were waiting for the final release to launch a series of laptops with Gutsy for OS.

---

### Post by ElSeeDee on 2007-10-19
> **jbaerbock said:**
> Yeah I installed Gutsy and I have a crap load of repos missing too. And so I am trying to reload and half of them get failed. The ones that do load take forever to load. And during install GParted crashed every 5 minutes. Seriously did they not test 7.10 before release?

It's not 7.10's fault. (unless by "fault" you mean tremendously popular) Everyone was/is trying to update at the same time. So the repos that got slammed the most are probably the ones that failed the most.

---

