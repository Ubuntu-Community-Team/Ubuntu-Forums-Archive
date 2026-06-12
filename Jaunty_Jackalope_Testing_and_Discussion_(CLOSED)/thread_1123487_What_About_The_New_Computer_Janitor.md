---
title: "What About The New Computer Janitor"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hufferd on 2009-04-12
First I have to say I am REALLY liking Jaunty so far. I am just a novice user but have been using Ubuntu for a year now and started with 8.04.  Not that I know anything of importance but it would seem that Junty is much more stable then the other Ver. I have used to this point. 

I was looking at things a bit this morning and came across the "New Computer Janitor"  

There are some items that it found and I am not sure if I should even mess with it....  This was a clean install about 3 weeks ago now... 

Each one shows and error I guess or at least it thinks there is 

> 1. /media/sdb1 (this is a second hard drive i have on the system I am having no issues that I know of with access to it at this time 

2. Amazonmp3 - It says the package is no longer supported. I understand why that is it was installed from a third party web site ... bla bla... 

3. Both libindicate0 & libopal3.4.2 its says packages are not supported

4.It also says the two plug-ins packages are not supported  alsa >>>?? I am sure that one has to do with sound correct? 

5. The librsync1 it says that as well as the python ones were installed because another package needed them but they are all no longer needed. is that REALLY true can I trust this thing? 

Just found it interesting that on an install thats only about 3 weeks old it found so many issues

---

### Post by groggyboy on 2009-04-12
hufferd:

it sounds like Computer Janitor's recommendations are ones you can (mostly) trust.

1. /media/sdb1 - according to the screenshot, i gather that it wants to add the "relatime" option when mounting that particular partition/drive.  if this partition is ext3, this is a good idea.  it will speed up access times to that drive.  ubuntu sets this flag on linux partitions by default,and I'm surprised it's not already set.  even if you follow none of the other recommendations, i'd go ahead with this one.

2. amazonmp3 - if you installed this package yourself, and know you need it, don't follow this recommendation.

3. libindicate0 & libopal3.4.2 - i've removed both of these packages from my system with no ill effects.  they were probably pulled in by the ubuntu-desktop metapackage when you installed jaunty, but the developers have since changed things so they are not necessary any more.  these are safe to remove.

4. libpt2.4.2-plugins-alsa & libpt2.4.2-plugins-v4l2 - you are correct, ALSA is part of the linux sound system.  however, these plugins are not core parts of ALSA.  in fact, v4l2 stands for "Video4Linux" - not sound at all.  they are plugins for the Portable Windows tools library.  I'm not sure how they got installed on your system.  these two are probably safe to remove.

5. librsync1 & the python packages - as Computer Janitor says, these were probably pulled in when you installed some other package - a package which you later must've uninstalled.  I'd trust computer janitor on this one.

Really, it's up to you if you keep or remove these packages.  Aside from amazonmp3, it sounds like Computer Janitor has made some sane suggestions.  these packages aren't doing any harm by remaining on your computer, but if you are cramped for space, or if you just like a clean system, then follow the recommendations.  i suppose there is always the off-chance that some program still needs these packages, but that is not very likely. still, if you're really paranoid about screwing up your system, then leave it alone.

the only time i'd really not follow computer janitor's suggestions is when it wants to remove a program that i installed from a third-party source that i know i want to keep using.

---

### Post by Polmac on 2009-04-12
For me, Computer Janitor is a bit useless as it is conceived right now... it shows TONS of packages to be removed, and most of them were installed by me from official repos, and I want to keep them.

I think it should have some filtering options to choose which packages to remove. For example, it'd be interesting if it allowed me to easily remove old kernels, and only that. Or maybe it could allow to filter packages by the reasons it suggests to remove them.

In fact, if they only added an "uncheck all" option, so that I could check myself only the packages I'd like to remove, the program would be of much more utility to me. Right now I'd have to uncheck by hand a lot of packages, which is highly inconvenient to me...

---

### Post by Marlonsm on 2009-04-12
Besides deleting my Google Earth, it did nothing I could notice so far.
But Jaunty is buggy here, I hope it gets fixed when it releases, or else I'll have to do a clean install.

---

### Post by connorh123 on 2009-04-12
Little off-topic, but I noticed a wbar on Jaunty. Can you tell me in a message how you got this to work?
Thanks.

---

### Post by hufferd on 2009-04-12
> **groggyboy said:**
> hufferd:

it sounds like Computer Janitor's recommendations are ones you can (mostly) trust.

Thank you very much groggyboy for your feed back :)

---

### Post by hufferd on 2009-04-12
> **connorh123 said:**
> Little off-topic, but I noticed a wbar on Jaunty. Can you tell me in a message how you got this to work?
Thanks.

I'll get in touch

---

### Post by eragon100 on 2009-04-12
Don't touch it with a ten-foot pole. I ran the version in intrepid, and the result was:

The kernel packages were removed (yes, the kernel, linux!)

Opera was removed

The battle for wesnoth didn't run any more

---

### Post by uncibex on 2009-04-13
polmac, it looks as though by running computer-janitor through terminal, you can run an ignore command.  I have not yet used it, so I'm not sure if you can permanently ignore a particular package but I thought this might be useful for this.

---

### Post by Therion on 2009-04-13
Related thread:  [http://ubuntuforums.org/showthread.php?t=1120070](http://ubuntuforums.org/showthread.php?t=1120070)

I've removed Computer Janitor and use QuickStart instead.

---

