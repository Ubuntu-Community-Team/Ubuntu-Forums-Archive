---
title: "Will Breezy wipe Hoary settings?"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by oliwally on 2005-07-23
When I do eventually install the Breezy Badger realease, will it completely wipe everything on my HD or will I be able to keep settings and programs I have installed with Hoary? Will it be a smooth upgrade or will I have to start from scratch? I know that Breezy is not going to be released for a while yet. Just wondering what will happen to my current Kubuntu installation (with which I am very happy!).

---

### Post by kahping on 2005-07-23
it shouldn't at all. Once Breezy is out u can just change all instances of Hoary in your apt repositories to Breezy in Synaptic, then Reload, Mark All Upgrades and finally Apply to upgrade to Breezy. All your current settings will be maintained and programs updated to latest available versions ;-)

if u have a fast internet connection(broadband), this works just fine. if you're on dialup, u'll have to do this using the Breezy CD unless you want a REALLY LOOOONG wait. i haven't tried an upgrade from CD before, so i can't help u there.

kahping

---

### Post by manicka on 2005-07-23
[QUOTE=kahping]it shouldn't at all. Once Breezy is out u can just change all instances of Hoary in your apt repositories to Breezy in Synaptic, then Reload, Mark All Upgrades and finally Apply to upgrade to Breezy. [/QUOTE]

or change your apt repositories then run in a terminal

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by oliwally on 2005-07-23
Cool. That sounds easy enough. So, I don't have to lose sleep over it from now until Breezy is released. 
Thanks for your help.

---

### Post by oliwally on 2005-09-19
> Once Breezy is out u can just change all instances of Hoary in your apt repositories to Breezy in Synaptic
and
> or change your apt repositories

How do I change/upate my repositories? (now that we're getting closer to the official release)

---

### Post by jeffreyvergara.NET on 2005-09-19
[QUOTE=oliwally]and


How do I change/upate my repositories? (now that we're getting closer to the official release)[/QUOTE]
 there's a tutorial in [www.ubuntuguide.org](www.ubuntuguide.org), but sometimes the site is down. but I read something that just change all the word "Hoary" and replace it with "Breezy" on your repository.

---

### Post by oliwally on 2005-09-20
Thanks for that. 

Are there any more definite ideas out there?

---

### Post by pgmario on 2005-09-20
[QUOTE=oliwally]Thanks for that. 

Are there any more definite ideas out there?[/QUOTE]
To change the repositories do:

GNOME
```
sudo gedit /etc/apt/sources.list
```

KDE
```
sudo kate /etc/apt/sources.list
```

And change every instance of "hoary" to "breezy".
Additionaly, if you have activated any backports-repositories (which you probably haven't if you don't know how to change the repository list) it would probably be a good idea to comment them out before doing the upgrade.

As was mentioned before, it's always a good idea to take a look at ubuntuguide.org . They also have a section on upgrading to Breezy.

---

### Post by oliwally on 2005-09-20
Cool, thanks for your help.

I do have backports-repositories (found instructions on how to up stick them in) but I'm uncertain about the finer points of linux usage.

---

### Post by pgmario on 2005-09-20
[QUOTE=oliwally]Cool, thanks for your help.

I do have backports-repositories (found instructions on how to up stick them in) but I'm uncertain about the finer points of linux usage.[/QUOTE]

You're welcome.
To comment out the backport and extra repositories, just add a "#" at the beginning of lines containing "hoary-extras" and "hoary-backports".

For example, the following line 
```
deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted
```

would be made into this:
```
#deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted
```

---

### Post by jdong on 2005-09-20
For the most part, **yes, it will be a smooth upgrade**, especially if you haven't installed too much software from repositories outside of Ubuntu-designed (official Ubuntu, Ubuntu Backports/Extras, and others) repositories. Usually, conflicts in this area are resolved quite well...

However, I would set aside a good amount of time (maybe 1-2 hours to do the upgrade, and plan the upgrade at a time where you would least need your computer. If you have a major deadline to meet in 3 days, now's not the time to do it! :) ) to perform the upgrade, because remember -- this is an **operating system and environment** upgrade, which is a fairly complex process for your system (and one command for you :) ) and is prone to snags along the road.




One common problem is the overwrite issue. You may get errors like:

```


Unpacking electricsheep (from
.../electricsheep_2.6.2-1~5.04ubp1_i386.deb) ...
dpkg: error processing
/var/cache/apt/archives/electricsheep_2.6.2-1~5.04ubp1_i386.deb (--unpack):
trying to overwrite `/usr/share/xscreensaver/config/electricsheep.xml',
which is also in package xscreensaver
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/electricsheep_2.6.2-1~5.04ubp1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is the result of packaging changes or errors that cause two package to own the same files -- a common occurence when the package structure is changed from distribution to distribution.

Note how you are given the full path to the package (/var/cache/apt/and so on). To remedy this situation, simply run:

**sudo dpkg -- install --force-overwrite /var/cache/apt/path/debian-package.deb** and your system will be all happy again :)


Try not to interrupt the install process when it's progressed from downloading to installing. That's generally a pretty bad idea (think of hitting the reset button in the middle of installing Windows) -- though Ubuntu can recover from the situation 99.% of the times, there is always a chance of nasty inconsistencies that would take many additional hours of toiling to solve.




I probably painted the worst-case scenario in upgrading, but that's great to keep in mind -- the fact that upgrading the OS isn't a risk-free procedure.




AFTER performing your "apt-get dist-upgrade" or Synaptic Smart Upgrade, **install the ubuntu-desktop** (and/or kubuntu-desktop  for KDE users) again to pick up additions and removals to the core Ubuntu system. This will reinstall some applications you might have opted to delete, in which case delete them again after the procedure is finished.

---

### Post by duffman25 on 2005-09-20
[QUOTE=jdong]For the most part, **yes, it will be a smooth upgrade**, especially if you haven't installed too much software from repositories outside of Ubuntu-designed (official Ubuntu, Ubuntu Backports/Extras, and others) repositories. Usually, conflicts in this area are resolved quite well...

However, I would set aside a good amount of time (maybe 1-2 hours to do the upgrade, and plan the upgrade at a time where you would least need your computer. If you have a major deadline to meet in 3 days, now's not the time to do it! :) ) to perform the upgrade, because remember -- this is an **operating system and environment** upgrade, which is a fairly complex process for your system (and one command for you :) ) and is prone to snags along the road.




One common problem is the overwrite issue. You may get errors like:

```


Unpacking electricsheep (from
.../electricsheep_2.6.2-1~5.04ubp1_i386.deb) ...
dpkg: error processing
/var/cache/apt/archives/electricsheep_2.6.2-1~5.04ubp1_i386.deb (--unpack):
trying to overwrite `/usr/share/xscreensaver/config/electricsheep.xml',
which is also in package xscreensaver
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/electricsheep_2.6.2-1~5.04ubp1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is the result of packaging changes or errors that cause two package to own the same files -- a common occurence when the package structure is changed from distribution to distribution.

Note how you are given the full path to the package (/var/cache/apt/and so on). To remedy this situation, simply run:

**sudo dpkg -- install --force-overwrite /var/cache/apt/path/debian-package.deb** and your system will be all happy again :)


Try not to interrupt the install process when it's progressed from downloading to installing. That's generally a pretty bad idea (think of hitting the reset button in the middle of installing Windows) -- though Ubuntu can recover from the situation 99.% of the times, there is always a chance of nasty inconsistencies that would take many additional hours of toiling to solve.




I probably painted the worst-case scenario in upgrading, but that's great to keep in mind -- the fact that upgrading the OS isn't a risk-free procedure.




AFTER performing your "apt-get dist-upgrade" or Synaptic Smart Upgrade, **install the ubuntu-desktop** (and/or kubuntu-desktop  for KDE users) again to pick up additions and removals to the core Ubuntu system. This will reinstall some applications you might have opted to delete, in which case delete them again after the procedure is finished.[/QUOTE]


Also, remember to read carefully the release notes after breezy has been released. It will talk about the most common upgrading scenarios. For example, I bet you will have to update your xorg.conf.

Anyway, you can always wait a few days after breezy is out & ask for peoples experiences upgrading their machines.

---

### Post by oliwally on 2005-09-21
Wow, you folks are awesome. I'm repeatedly amazed at how comprehensive and quick help is on this forum. 

Thanks again - I will wait for the official release. At least I now already have an idea of how to do it and what difficulties I may encounter.

> set aside a good amount of time (maybe 1-2 hours to do the upgrade

My internet connection is only relatively slow (256), so it will take some time. Perhaps upgrading from a CD woud be more quick? More difficult?

---

