---
title: "Gutsy Beta -&gt; Gutsy Final"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by picopir8 on 2007-10-01
If I install Gutsy Beta now, will the updates acquired between now and the final release essentially turn it into the final or will a clean install or manual upgrade be required?

I have a new PC arriving this week but the final Gutsy is still a few weeks off.  I REALLY do not want to live with Vista until that time, and I would prefer not to have to install Feisty/Gutsy Beta now only to blow everything away in a few weeks and install Gutsy Final.

---

### Post by cwhitehouse on 2007-10-01
That's a great question.  From my understanding as long as you apply all of the updates it should be the same as a fresh install.

Please correct me if I'm misinformed.

---

### Post by Soybean on 2007-10-01
I'm not actually sure, but I would guess that it will do one of two things:
1) Just applying normal updates will bring your system to the same state as if you had installed the Final
2) There will be an actual "upgrade" process, like the process for upgrading from Feisty-Gutsy. This process has gotten pretty painless in recent releases.

A suggestion, though: if you don't like reinstalling your OS, are you sure that a beta OS is a good idea? It might be worth it to install Feisty for now, and then upgrade that after Gutsy's been released for a while -- say, late November. That's what I'll be doing at work, where I want to avoid the time required for a clean install.

---

### Post by mjwood0 on 2007-10-01
It should be almost trivial to go from Feisty to Gutsy when the time comes.  It's not really a full re-install -- just an upgrade.

I'd tend to install the latest stable and upgrade when the time comes unless you have a reason not to use Feisty.

---

### Post by raydar on 2007-10-01
So, just to rule out one other possibility:  After upgrading from Feisty to Gutsy beta, when I'm notified that updates are available, accepting those updates won't revert me to Feisty versions of things, will it?

I upgraded from Feisty to Gutsy beta, and in playing around with nvidia drivers, I caught my system at one point automatically uninstalling the "nvidia-glx-new" driver I had installed and re-installing the "nvidia-glx" driver I originally had.  I was able to put it back to "nvidia-glx-new" (not that it helped my video), but that automatic reversion has left me a little cautious:  I'm currently getting a notification of 49 updates available for my system, among them a couple of restricted driver things (the restricted driver manager itself, if I remember correctly), and I don't want to break my Gutsy beta system now that it's running okay.  

(I've also seen quite a few comments in Ubuntu Forums about dependency problems and "partial upgrade" troubles resulting from updates, and I myself got a "partial upgrade" notification, but that was new to me so I canceled out so I could look it up before I did anything I might regret.)

Thanks for any caveats or reassurance!  :]

---

### Post by picopir8 on 2007-10-05
Per the last post, no, Feisty and Gutsy use different repositories.  The updates are independent and accepting any gutsy updates will not not revert any portion of your install to feisty.

Per the original question - bump.  FedEx just delivered my new Laptop.  If gutsy updates do not update the betas to the official release then it looks like the options are as follows:
1) Install gutsy beta now live with any bugs, reinstall gutsy release later
2) Install feisty now to be more stable, install gutsy release later
3) Suffer with vista for a week, install gutsy release later

If I dont get an answer by tonight Ill probably just install the gutsy beta anyway.  Hopefully it will update to the release so a reinstall is not necessary, but if its not, Ill probably need some of the drivers not available in feisty, and if I have to live with vista, I might as well not even have a computer.  #1 is the least painful, and it also offers the potential of being updated to the gutsy release and eliminating the need for a reinstall.

---

### Post by rsambuca on 2007-10-05
If you are running Gutsy beta version, then you will have the final stable release just by doing the regular updates.

---

### Post by wolfen69 on 2007-10-05
> **Soybean said:**
> I'm not actually sure, but I would guess that it will do one of two things:
1) Just applying normal updates will bring your system to the same state as if you had installed the Final
2) There will be an actual "upgrade" process, like the process for upgrading from Feisty-Gutsy. This process has gotten pretty painless in recent releases.

A suggestion, though: if you don't like reinstalling your OS, are you sure that a beta OS is a good idea? It might be worth it to install Feisty for now, and then upgrade that after Gutsy's been released for a while -- say, late November. That's what I'll be doing at work, where I want to avoid the time required for a clean install.

i have heard alot of horror stories doing an upgrade vs. clean install. to be on the safe side, i always do a clean install. gutsy will be very easy to install anyway.15-20min? but that's just me.

---

### Post by disposition on 2007-10-05
> **wolfen69 said:**
> i have heard alot of horror stories doing an upgrade vs. clean install. to be on the safe side, i always do a clean install. gutsy will be very easy to install anyway.15-20min? but that's just me.

Could you elaborate?

I'm a new Feisty user anxiously awaiting Gutsy, and I don't want to have to deal with a new reinstall so soon. 

I am curious though, in general, does upgrading wipe all installs and driver configurations?

---

### Post by feverfresh on 2007-10-10
> **disposition said:**
> Could you elaborate?

I'm a new Feisty user anxiously awaiting Gutsy, and I don't want to have to deal with a new reinstall so soon. 

Upgrading is, of course, not mandatory. Gutsy is the big story around here, and will be for a the next few weeks, but there are a lot of people who are still using Edgy and Dapper. 

> I am curious though, in general, does upgrading wipe all installs and driver configurations?

Look into creating a separate partition for your /home folder. I tried it using these directions: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome). While that did not go as well as I had planned, I shortly thereafter upgraded to Gutsy Beta on the main partition, and at least all of my personalizations after creating the partition were put into play in Gutsy. Even the wallpaper I had popped back up. My printer was instantly recognized as if nothing had happened. 

Some aps were wiped out... wine was lost, as were he attached windows aps, as were the aps that came with the kubuntu-desktop package. But as part of my reason for the fresh install was to clear out some of this clutter and start over, it was not a big loss.

---

### Post by mjwood0 on 2007-10-10
I generally do a clean install as well.  My home directory is totally separated onto a 320 GB RAID1 array so it's always backed up (by the nature of RAID1) and I never really have to worry about anything.   All my config files are saved in my home area as is my desktop backgrounds, etc...  

A clean install is nice as I often have patched and hacked things which start to clutter up my system.  Usually, the reason things are hacked and patched is that my HW wasn't supported under the current release.  I always figure that it's better to start over so any things which are now supported aren't fighting with my patching!

But again, that's just me! (...and I really don't mind tinkering with my system...)

---

