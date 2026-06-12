---
title: "How can i upgrade from 8.10 to karmic Alpha 6?"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kamalkochhar on 2009-09-21
Can i upgrade from 8.10 to karmic alpha 6 straight away without upgrading to 9.10 first?

---

### Post by psyke83 on 2009-09-21
> **kamalkochhar said:**
> Can i upgrade from 8.10 to karmic alpha 6 straight away without upgrading to 9.10 first?

I assume you meant "without upgrading to 9.04 (Jaunty) first". If that's the case, then no.

What you can do is backup your home directory, and do a fresh install of Karmic, and then move back your documents and settings (I personally wouldn't try to restore settings, as it could cause configuration issues with new versions of software).

---

### Post by waspbr on 2009-09-21
I would recomment a fresh install, leaping two releases is likely to lead to some serious breakage, even more so since karmic is still alpha

---

### Post by excogitation on 2009-09-21
If you feel like it you could also try doing 2 consecutive updates
by executing
```
sudo update-manager -d
```
and then again once you're on Jaunty.

As said before you shoud backup your data before doing so.
Also you'll save a lot of time by either just installing
Karmic as an alternative operating system or from scratch
and restoring your home dir (from your previously done backup)
afterwards.

Also you could just try out Karmic with a daily-live CD or USB-stick.

---

### Post by nanog on 2009-09-21
I think its funny how no one answered your question.
[COLOR="Red"][B]
Before any upgrade you should back up your system.[/B][/COLOR] I recommend learning how to image your drive using dd.

That being said, if you are willing to risk hosing your install (always a risk with ANY internet-based upgrade), it is trivial to upgrade from intrepid to karmic.

```
sudo sed -i "s/intrepid/karmic/g" /etc/apt/sources.list; sudo aptitude update; sudo aptitude dist-upgrade
```

followed by at least one more:

```
sudo apt-get dist-upgrade
```

Be sure to accept the packagers defaults (unless you hacked at a config file and understand what you are doing by bypassing the default).


____________________________________________________________

> I would recomment a fresh install, leaping two releases is likely to lead to some serious breakage

I have boxes that have been upgraded all the way from breezy with no problems. 
In fact, I have had far more problems with fresh installs than with upgrades. 
For example, known kernel bugs prevent fresh installs on 4 of my boxes.

---

### Post by VMC on 2009-09-21
> **nanog said:**
> I think its funny how no one answered your question. I thought psyke83 answered it very well.

> **nanog said:**
> Before any upgrade you should always backup your system. I recommend learning how to image your drive using dd.

That being said it is trivial to upgrade from intrepid to karmic.

```
sudo sed -i "s/intrepid/karmic/g" /etc/apt/sources.list; sudo aptitude update; sudo aptitude dist-upgrade
```

Be sure to accept the packagers defaults (unless you hacked at a config file and understand what you are doing by bypassing the default).

I personally have never had a problem with these types of upgrades.Then again, this looks interesting. Isn't this the same method going from last stable release to testing?

---

### Post by psyke83 on 2009-09-21
> **nanog said:**
> I think its funny how no one answered your question.


It was answered. The process you documented is discouraged by Ubuntu developers and is very risky, especially when upgrading to an alpha release. Even a fresh install of alpha 6 is precarious due to the recent updates to the various boot-related packages.

The only supported method of upgrading (from Jaunty) is documented in the release notes: [http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6)

With that in mind, the possible (and official) upgrade paths are either:

1. Intrepid -> Jaunty -> Karmic, using the official upgrade procedure listed in the respective release notes, or;
2. Backup home folder, and perform a fresh install of the latest Karmic release. 

The latter method will eliminate the risk of system cruft interfering in the operation of your system, and will also present the opportunity to upgrade to ext4 and/or an encrypted home folder (*as long as* you've backed up documents to an external drive or partition).

---

### Post by nanog on 2009-09-21
Psyke23, 

> The process you documented is discouraged by Ubuntu developers and is very risky.

You say its "very risk" but offer no proof. I agree that this is not the recommended way to upgrade Ubuntu but on most of my systems it works flawlessly. I think its definitely worth a try if you want to avoid the onerous full upgrade/sequential upgrade method. Any upgrade has the potential to complete hose your system whether you hav partitioned  home or not. 

IMO, the wipe everything and reinstall is a completely  unacceptable option when one has a large number of installed binaries that are not part of the standard install. I would also like to note that a development branch upgrade prior to the first alpha spin is still conducted via this method. Also, the server upgrade basically calls a script that runs this upgrade method.

---

### Post by psyke83 on 2009-09-21
> **nanog said:**
> Psyke23, 



You say its "very risk" but offer no proof. I agree that this is not the recommended way to upgrade Ubuntu but on most of my systems it works flawlessly. I think its definitely worth a try if you want to avoid the onerous full upgrade/sequential upgrade method. Any upgrade has the potential to complete hose your system whether you hav partitioned  home or not. 

IMO, the wipe everything and reinstall is a completely  unacceptable option when one has a large number of installed binaries that are not part of the standard install. I would also like to note that a development branch upgrade prior to the first alpha spin is still conducted via this method. Also, the server upgrade basically calls a script that runs this upgrade method.

On the contrary, it's your responsibility to provide proof that your method is safe. **All** documentation explicitly states not to upgrade across two distribution releases. For a starting point, see: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

While you may be right that the server upgrade script does essentially the same procedure as you documented, it does not skip over a distribution version like you suggest.

While the upgrade may work successfully, it is *not* supported, *not* recommended, and has the *maximum* chance of causing problems when used in favour of the official methods. I certainly wouldn't recommend this method to a new member with three beans.

P.S. If you have a significant amount of custom binaries installed, you're *doing things wrong*. Even if you're lazy, it's trivially easy to create a quick and dirty debian package from any source using checkinstall.

---

### Post by sultanoswing on 2009-09-22
Not to hijack this thread - but the above discussions illustrates a big advantage of rolling release distros, such as Arch.

---

### Post by VMC on 2009-09-22
> **sultanoswing said:**
> Not to hijack this thread - but the above discussions illustrates a big advantage of rolling release distros, such as Arch.

How about all the cuff and leftover useless files that brings, by staying with a rolling release.

 I prefer to have fresh install, and if you do that with Arch, what's the point anyway.

---

### Post by slakkie on 2009-09-22
> **sultanoswing said:**
> Not to hijack this thread - but the above discussions illustrates a big advantage of rolling release distros, such as Arch.

Go troll somewhere else please.

---

### Post by nanog on 2009-09-22
"it's your responsibility to provide proof that your method is safe."

Dpkg and apt. 
Amen.



"If you have a significant amount of custom binaries installed, you're doing things wrong. Even if you're lazy, it's trivially easy to create a quick and dirty debian package from any source using checkinstall."


Thanks for the helpful suggestion but sometimes source or dependencies are not available.

---

### Post by Amaranth on 2009-09-22
The main thing is that these upgrade paths are **not tested** so we have no idea what will happen. Although to be honest this has become less of a problem since hardy since we leave in all of the transitional things in order to cleanly upgrade from LTS to LTS. Before that upgrading in this way was very likely to miss a transition of some kind and you'd have to spend a lot of time cleaning things up and fixing them.

Even with all that said, I would not upgrade in this manner unless you really know what you are doing.

---

### Post by gaussian on 2009-09-22
> **psyke83 said:**
> 
P.S. If you have a significant amount of custom binaries installed, you're *doing things wrong*. Even if you're lazy, it's trivially easy to create a quick and dirty debian package from any source using checkinstall.

Without getting in to the heart of this discussion thread (I have done ```
sudo apt-get update && sudo apt-get dist-upgrade
``` upgrades in the past, recently though just with upgrade manager), I'd like to the above statement is not always true even if one had the source. I have some programming experience, my first experience with Unix was in the early eighties and I have been pretty much Linux exclusive for five years. This is just to state that I am not a complete newbie.

Last time I tried (this was couple years ago) to create a .deb-packages with checkinstall it would fail to create installable packages automatically to some of the programs I was trying to use it for (namely Emacs GTK-snapshot). It would create a .deb, but installing that would not create a working Emacs installation, while old ./config, make, make install would.

---

### Post by nanog on 2009-09-23
"Although to be honest this has become less of a problem since hardy since we leave in all of the transitional things in order to cleanly upgrade from LTS to LTS."

AFAIK, purging and reinstalling metapackages (ubuntu-desktop, ubuntu-base, ubuntu-minimal, xserver-xorg etc) *should* fix any transitional thingies.

---

### Post by psyke83 on 2009-09-23
> **gaussian said:**
> Without getting in to the heart of this discussion thread (I have done ```
sudo apt-get update && sudo apt-get dist-upgrade
``` upgrades in the past, recently though just with upgrade manager), I'd like to the above statement is not always true even if one had the source. I have some programming experience, my first experience with Unix was in the early eighties and I have been pretty much Linux exclusive for five years. This is just to state that I am not a complete newbie.

Last time I tried (this was couple years ago) to create a .deb-packages with checkinstall it would fail to create installable packages automatically to some of the programs I was trying to use it for (namely Emacs GTK-snapshot). It would create a .deb, but installing that would not create a working Emacs installation, while old ./config, make, make install would.

Yes, checkinstall isn't perfect. I noticed that it creates empty deb packages if you do not compile the source before invoking checkinstall (in otherwords, you need to run ./configure, make, checkinstall, not just ./configure, checkinstall).

Nevertheless, it works acceptably for me in most cases. Personally, I would use [these]("https://wiki.ubuntu.com/PackagingGuide/Complete#Updating%20an%20Ubuntu%20Package") instructions if I were not in a hurry.

---

### Post by Sophont on 2009-09-23
No idea where people get the idea from that fresh install is much better (except for fundamental new features like ext4 of course) than upgrades. Since Feisty I only re-istalled twice. Once because I wanted to repartition after XP wipe and now because it's a new machine. Otherwise I always just upgrade and that was never a problem. I'm sure that leaves a few old unused files lying around - but - shrug - why worry about a few MB here and there.

---

### Post by psyke83 on 2009-09-23
> **Sophont said:**
> No idea where people get the idea from that fresh install is much better (except for fundamental new features like ext4 of course) than upgrades. Since Feisty I only re-istalled twice. Once because I wanted to repartition after XP wipe and now because it's a new machine. Otherwise I always just upgrade and that was never a problem. I'm sure that leaves a few old unused files lying around - but - shrug - why worry about a few MB here and there.

The problem is not unused files sitting on your drive - it's obsolete or conflicting files/configuration files that don't get updated properly. Skipping distributions can possibly increase the chance of incompatibility between packages and create circumstances in which the packagers did not anticipate.

Let's imagine that application X exists as version 1.0 in Intrepid, 1.1 in Jaunty and 1.5 (a rewrite) in Karmic. Version 1.1 may import older configuration files properly, but version 1.5 may only import 1.1 configurations properly. Perhaps the 1.1 package included a script/workaround/hack for various reasons, but that workaround was removed from 1.5 of the package, even though it would still be needed if upgrading from 1.0. This is a gross oversimplification (and various other problems could occur, such as expecting a symlink created by package 1.1), but I think you can get the gist.

Having said that, I agree that a fresh install is not necessary - this one of Linux's distinct advantages over Windows. However, I believe that doing a distribution upgrade from a stable release to a release still in development is not a good idea for a new user, at least not until the beta milestone or later. And I would never suggest to skip a distribution. 

Think about it: if a user was prepared to handle broken packages that would result from doing a distribution upgrade across two distributions, they would not need to post on a forum looking for assistance in the first place.

---

### Post by gaussian on 2009-09-23
> **psyke83 said:**
> Yes, checkinstall isn't perfect. I noticed that it creates empty deb packages if you do not compile the source before invoking checkinstall (in otherwords, you need to run ./configure, make, checkinstall, not just ./configure, checkinstall).

Nevertheless, it works acceptably for me in most cases. Personally, I would use [these]("https://wiki.ubuntu.com/PackagingGuide/Complete#Updating%20an%20Ubuntu%20Package") instructions if I were not in a hurry.

Thanks for the link, that will probably come handy.


To continue on the main topic: I have a laptop that has been never reinstalled since Feisty. And it dual boots to 32 and 64 bit Ubuntu. Neither one has been ever reinstalled, the 64 now is running Karmic, 32 is doing Jaunty. What boggles my mind is the advice often given "backup your home and reinstall". This might be a semantic confusion, but based on my experience I would change that to "backup your documents and reinstall", if you want to go reinstall route. The reason is that I have found that 90% of the problems I have encountered lately with upgrades are caused by old config files in the *home-directory*, not caused by any system-wide settings (usually if you haven't hacked into those update-manager/apt handles these well).

---

### Post by VMC on 2009-09-23
> **gaussian said:**
> Thanks for the link, that will probably come handy.

... What boggles my mind is the advice often given "backup your home and reinstall". This might be a semantic confusion, but based on my experience I would change that to "backup your documents and reinstall", if you want to go reinstall route. The reason is that I have found that 90% of the problems I have encountered lately with upgrades are caused by old config files in the *home-directory*, not caused by any system-wide settings (usually if you haven't hacked into those update-manager/apt handles these well).

Yes that link was very useful. 

I totally agree. I always backup important documents and wipe "/home" clean. Actually I just have one partition "/" and I format that or create a new one.

Then again, I have never upgraded from an older release to a newer one. I just reinstall fresh.

---

### Post by Longinus00 on 2009-09-23
> **VMC said:**
> Yes that link was very useful. 

I totally agree. I always backup important documents and wipe "/home" clean. Actually I just have one partition "/" and I format that or create a new one.

Then again, I have never upgraded from an older release to a newer one. I just reinstall fresh.

I find that having "/" and "/home" separated onto separate disks is good because of how slow hard drives are to seek. It keeps the computer much snappier if you ever do any disk intensive operations (copying large files around).

---

### Post by nanog on 2009-09-28
> Skipping distributions can possibly increase the chance of incompatibility between packages and create circumstances in which the packagers did not anticipate.


If apt and dpkg are working correctly purge and restore will return these configuration files to default settings. IMO, this is a valid upgrade path for anyone who understands how apt and dpkg work. I also think its worth a try even for the inexperienced who want to avoid serial upgrades (very, very boring) [COLOR="Red"]**and have backed up /home**[/COLOR]. At the very worst you will learn more about how ubuntu works.

---

