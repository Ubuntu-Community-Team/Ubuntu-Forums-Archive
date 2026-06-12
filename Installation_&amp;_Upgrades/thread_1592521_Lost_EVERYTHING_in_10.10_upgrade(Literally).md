---
title: "Lost EVERYTHING in 10.10 upgrade(Literally)"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Gameboyman99 on 2010-10-10
WOW, ISN'T IT A SURPRISE, I HAVE ANOTHER PROBLEM! :P Ok, not a :P, more like a :(

  Soooo! All I have are problems, this one being even bigger than my last one(loadfont)

  Pretty simple, the title says it all; I upgraded to 10.10, and lost everything except my extremely important data(Which is on my flash drive and another PC). My installations, data, updates(Actually there are none I need now, right??), settings, passwords(only the ones saved in FF) and all. Of course there's a 99% chance I'll never get it back, but even if I could it would save me at least a week of redoing things... My fault; WUBI asked me to uninstall Ubuntu first and _then_ I could install 10.10. I heard some crap about an easy install from the software center or someplace?? Is that true so I won't do this same thing next time??

 Ugh...

---

### Post by efflandt on 2010-10-10
Two of the known issues in the release notes are:

[LIST]
[*]**The Wubi Windows installer was reported to be unable to open Windows' boot configuration data store in some (but not all) cases.**  Investigation of the problems are ongoing ([613288]("https://bugs.launchpad.net/bugs/613288"))
[*]**You cannot upgrade if wubi is installed to a partition other than Windows.** ([610898]("https://bugs.launchpad.net/bugs/610898"),[653134]("https://bugs.launchpad.net/bugs/653134"))
[/LIST]

So maybe you should have held off, or finally gotten around to doing a normal installation to a regular partition.

---

### Post by dirtyburger on 2010-10-10
> **efflandt said:**
> Two of the known issues in the release notes are:

[LIST]
[*]**The Wubi Windows installer was reported to be unable to open Windows' boot configuration data store in some (but not all) cases.**  Investigation of the problems are ongoing ([613288]("https://bugs.launchpad.net/bugs/613288"))
[*]**You cannot upgrade if wubi is installed to a partition other than Windows.** ([610898]("https://bugs.launchpad.net/bugs/610898"),[653134]("https://bugs.launchpad.net/bugs/653134"))
[/LIST]

So maybe you should have held off, or finally gotten around to doing a normal installation to a regular partition.

or maybe they should fix a major glaring bug like this before releasing a os as "FINAL"

whats wrong with you, this man lost all of his data and its his fault? he shouldent be expected to read about bugs in a final release, final releases should have minor bugs, nothing this serious

terrible

---

### Post by bcbc on 2010-10-11
In this case the release notes wouldn't have helped. 

You can't upgrade a wubi ubuntu by re-installing it under windows. Whenever you try to install a new ubuntu through wubi it requires that you uninstall the existing wubi install. That's what happened and - unless you caught it right away and used undelete software - those virtual disks are likely gone for good. You need to boot the wubi install and upgrade from there (or not as it's not supported right now).

One of the 'features' of wubi is how easy it is to uninstall - I think it would be advantageous to also add "by the way, all your ubuntu data will be removed too". 

But I also agree that the release notes count for squat when you see the update manager pop up with an "A new release 10.10 is available." and an "Upgrade" button. Where are the release notes there?

---

### Post by gradinaruvasile on 2010-10-11
> **dirtyburger said:**
> or maybe they should fix a major glaring bug like this before releasing a os as "FINAL"

whats wrong with you, this man lost all of his data and its his fault? he shouldent be expected to read about bugs in a final release, final releases should have minor bugs, nothing this serious

terrible

People should NOT upgrade on the spot - wait 1-2 months until (hopefully) the big bugs are gone. And DO NOT trust the upgrader - many many small (or big) issues may result from leftover settings.
Do a clean reinstall to be sure you will not have these (not nice doing it every 6 months...).
Or just install a "rolling release" distro (debian testing, arch linux, linux mint etc).

---

### Post by Gameboyman99 on 2010-10-11
Ya, so it's gone then...:(

D*** right WUBI's easy to uninstall(took only 2 sec), and yes, they should also have a "This will erase all ur data".

And I think I will partition a place for Ubuntu before I install anything else...

Now I have a less immediate question: How the crap does WUBI uninstall that fast???(Off subject I know but I dnt care)

Anyway thx 4 the help and suggestions,

---

### Post by Gameboyman99 on 2010-10-11
Oops. How do I delete these???

---

### Post by Gameboyman99 on 2010-10-11
Sorry... I clicked too many times...

---

