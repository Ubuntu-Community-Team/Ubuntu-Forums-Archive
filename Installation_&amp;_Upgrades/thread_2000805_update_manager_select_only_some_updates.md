---
title: "update manager select only some updates"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by ahso4271 on 2012-06-10
Hi
how to select only some updates alike Firefox and gimp? I don't dare to 
select all as it crashed before...
Yea sure manually browse through but such a pain in the ***.
Thanks

---

### Post by dino99 on 2012-06-10
update-manager is not my favorite, better to install & use synaptic.

sudo apt-get install synaptic
sudo synaptic

you select the package(s) you want/need to upgrade

---

### Post by ahso4271 on 2012-06-10
Yes but does synaptic show newer Firefox versions for ex.?

---

### Post by wilee-nilee on 2012-06-10
You don't want to hunt and peck updates period, you can make your set up unstable.

You also do not want to do partial updates as well. If you have had problems with updates I suspect this is what happened, or you have added driver not in the repos.

If a higher release is available for firefox you will see it in the update.

Otherwise a PPA is probably what you want .

If you want gimp 2.8 the general consensus is a purge of the stock install and using a PPA if the 2.8 is not in synaptic

---

### Post by snowpine on 2012-06-10
Say "yes" to all updates, is my recommendation. They are bug fixes and security patches that will make your system more stable and secure, I see that as a good thing. :)

---

### Post by ahso4271 on 2012-06-11
Maybe I should try again...The crash could have been because of the very first 12.04 downloads...64bit was full of bugs.
But then why should i waste time on downloading stuff I don't want/need, even 
putting my production system at risk?-

---

### Post by snowpine on 2012-06-11
> **ahso4271 said:**
> Maybe I should try again...The crash could have been because of the very first 12.04 downloads...64bit was full of bugs.
But then why should i waste time on downloading stuff I don't want/need, even 
putting my production system at risk?-

I think your production system is at greater risk, if you don't apply security patches for known exploits.

If it's a mission-critical system, then do like the pro's, and test updates on another system before applying them to the production machine. :)

---

### Post by Cheesehead on 2012-06-11
> **ahso4271 said:**
> why should i waste time on downloading stuff I don't want/need, even putting my production system at risk?-

If it's a production system, then stuff you don't want/need should not be installed in the first place. Investigate removing it. If you have questions about the dependencies or any warnings, or you are worried that it will disrupt a mission-critical software, just ask.

Update Manager does not install new software you don't want; it merely updates what you already have.

The ability to pick-and-choose updates in Update Manager is temporary. Any unchosed unpdates will reappear next time your run UM. The only way to permanently prevent an update is to A) Uninstall that software, B) Use apt-pinning (experienced users) C) Disable updates (offline users).

---

### Post by VE6EFR on 2012-06-11
I am also of the mindset that it is important to install all available updates. Like what Cheesehead and others have said, the updates are for software that is already on your system and not random software that the update manager thinks you should install. Software isn't updated just for the sake of updating. There is always a reason that a new version has been released. So when trying to troubleshoot a problem that I may be having the first thing that I usually do is to make sure I have the latest updates. Sometimes if I find that an update is available the problem will correct itself once the update has been applied.

---

### Post by ahso4271 on 2012-06-12
Yes the problem is that there's no quality check at all.- I even had once a update that removed Nvidia! Now who but some sick * would want that?

---

### Post by wilee-nilee on 2012-06-12
> **ahso4271 said:**
> Yes the problem is that there's no quality check at all.- I even had once a update that removed Nvidia! Now who but some sick * would want that?

Was the nvidia from the repos or their site, and was it a partial update.

Nvidia drivers from the ubuntu repos are all that should be used unless they don't work at all then with an understanding of this use. 

A partial update should never be run.

There is a huge quality check, what is missing is the user understanding check, which I suspect is the crux of your problems.

---

### Post by snowpine on 2012-06-12
I really cannot over-emphasize this fact:

> **snowpine said:**
> If it's a mission-critical system, then do like the pro's, and test updates on another system before applying them to the production machine. :)

That being said, most upgrade problems I've seen on the forums come from one of two mistakes:

1. Mixing third-party repos
and/or
2. dist-upgrade while in X

---

