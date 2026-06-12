---
title: "What to do with sources.list &amp; /sources.list.d/foo prior to dist-upgrade?"
date: 2018-01-17
forum: Installation &amp; Upgrades
---

### Post by accounts0 on 2018-01-17
Does the dist-upgrade command handle adjusting all the "deb url codename section" lines in all the relevant files?

Or do I need to manually handle all that?

---

### Post by cruzer001 on 2018-01-17
Are you asking about a version upgrade?  Look at #3:

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by accounts0 on 2018-01-17
At first glance, #3 looks like it's not doing what I aim to do. I'm currently on the 16.04.3 LTS release, & want to upgrade to the most recent non-LTS release. IIRC it's 17.10 now.

---

### Post by cruzer001 on 2018-01-17
You first need to set your Repository (Updates tab) to update to any new version.  Then you can update to 16.10 to 17.04 to 17.10.  A lengthy process that can pass or fail.

I also run 16.04 and do a direct LTS to LTS upgrade in April, skipping the short term versions.  Or wait for the first point release (18.04.1) and it will be automatically offered.
[URL="https://ubuntufhttps://ubuntuforums.org/showthread.php?t=2382317orums.org/showthread.php?t=2382317"]
[/URL][https://ubuntuforums.org/showthread.php?t=2382317]("https://ubuntuforums.org/showthread.php?t=2382317orums.org/showthread.php?t=2382317")

---

### Post by accounts0 on 2018-01-17
That sounds more like what I'm after, thanks. Do I uninstall all my PPA packages first then re-install them all with the new /sources.list.d/newfile  ?

---

### Post by cruzer001 on 2018-01-17
If all goes well, your PPAs will be automatically disabled at the start of the upgrade process.  But I would disable them manually; one less chance of a failure.  Have you considered a fresh install of 17.10?

---

### Post by accounts0 on 2018-01-17
Would be far more work than I want to put in. Only if I have to.

Thanks for your help. Hoping to save a day or so vs. a fresh install.

---

### Post by cruzer001 on 2018-01-17
This type of version upgrade will be a long process.  I suggest making a backup of your personal files.  I do not consider this a optimal way to upgrade in your case.

But none the less I wish you good luck and let us know how it turns out.

):P

---

### Post by accounts0 on 2018-01-17
> **cruzer001 said:**
> 
I also run 16.04 and do a direct LTS to LTS upgrade in April, skipping the short term versions.  Or wait for the first point release (18.04.1) and it will be automatically offered.


On second thought I think if I wait to do old LTS to new LTS, it's going to be less likely to fail as it'll be tested prior to release more than usual.


What's the difference between the first iteration of the new LTS & this "point release"? Why would that be automatically offered but not the first new LTS iteration?

---

### Post by deadflowr on 2018-01-17
What PPAs do you have?
The upgrade utility will disable PPAs, that's not an issue.
However, you may need to revert the package of a PPA back to the Ubuntu defaults in certain circumstances.
Any PPA worth their salt will explain such on their launchpad homepage.
(And will (or should) explain exactly how to do so)

---

### Post by accounts0 on 2018-01-17
[IMG]https://imgur.com/a/MksCT[/IMG][IMG]https://imgur.com/a/MksCT[/IMG]Attached screenshot of ppas, etc

---

### Post by DuckHook on 2018-01-17
> **accounts0 said:**
> On second thought I think if I wait to do old LTS to new LTS, it's going to be less likely to fail as it'll be tested prior to release more than usual.
Yes, this is more likely to go well. However, the upgrade process is a lot more complex than simply thinking that LTS to LTS is "better". A lot depends on how much you've diverged from default. The more you have diverged, the more risk you have of a borked upgrade.
> What's the difference between the first iteration of the new LTS & this "point release"? Why would that be automatically offered but not the first new LTS iteration?
LTS stands for _L_ong _T_erm **_S_upport**, not Long Term Stability, as some people think. The first few months of any release are usually filled with more bugs. By the first point release, many of those bugs have been squashed. Therefore, the devs in their wisdom, have seen fit to hold off the upgrade trigger until the first point release. I think it's a good decision. On my production machines, I always wait for the first LTS point release before upgrading. Let someone else deal with the problems. Ironically, that someone includes me because I don't wait for point releases on my experimentation boxes.

BTW, this is the reason I don't recommend standard releases for new users. They have the lifespan of mayflies and each one is, by definition, an initial release. They never get to a point release, being superseded by the next version.
> **accounts0 said:**
> &#8230;Attached screenshot of ppas, etc
Though not as bad as some I've seen, that's still a lot of PPAs. I'm with cruzer001 when it comes to PPAs. While modern versions do disable them before upgrading, you don't know what has been dragged in that may bork your upgrade. I'm also with cruzer001 when it comes to preferring virgin installs. I use it as an opportunity to clear out all of the cruft and baggage that I've accumulated the last two years.

Many people network upgrade successfully and happily. That could be your experience too. Just be fully prepared in case of failure (read my sig!) and you will at most be inconvenienced, but not dealing with a catastrophe. You also greatly improve your chances by putting your system back to its default state as much as possible.

---

