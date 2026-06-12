---
title: "aptitude versus synaptic to upgrade"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by tcdrewiv on 2008-03-27
I noticed when using aptitude update that it recommended holding back the upgrade of firefox 2.0.0.12 to 2.0.0.13..... while synaptic was recommending the upgrade to 2.0.0.13.

I was just curious why the recommendations were different.

---

### Post by bapoumba on 2008-03-27
Have you been using apt-get or synaptic on a regular basis so far, or aptitude ?

I'm using aptitude only and did get the Firefox upgrade. From /var/log/aptitude:
```
Will install 2 packages, and remove 0 packages.
12.3kB of disk space will be used
===============================================================================
[UPGRADE] firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10 -> 2.0.0.13+1nobinonly-0ubuntu0.7.10
[UPGRADE] firefox-gnome-support 2.0.0.12+2nobinonly+2-0ubuntu0.7.10 -> 2.0.0.13+1nobinonly-0ubuntu0.7.10
===============================================================================

Log complete.

```

---

### Post by tcdrewiv on 2008-03-27
I usually use apt-get for specific installs.....I usually use synaptic for the automatic updates.  lately I have been using aptitude after discovering its gui.  I like how you can see what other files are affected/dependencies prior to installation. 

I figured that synaptic and aptitude just got out of sync.

is there a way to correct or sync the two?
should i just stick to using aptitude update @ aptitude upgrade and use synaptic for searches?

---

### Post by bapoumba on 2008-03-27
I would recommend you start using aptitude after a fresh install, for ex after hardy comes out.
I did this some time ago (no sure if it was with breezy or dapper), and use aptitude only.

It may be too painful to mark all the packages as manually or automatically installed from aptitude, so that it knows exactly all the installed packages. What has been installed/upgraded/removed with apt-get/synaptic, aptitude has no log.

---

### Post by tcdrewiv on 2008-03-27
good suggestion
thanks

---

### Post by Peter Cordes on 2008-04-04
> **bapoumba said:**
> It may be too painful to mark all the packages as manually or automatically installed from aptitude.

 You can apply commands to more than one package at once.  e.g. if you select the "installed packages" line, and hit "M", _all_ installed packages will be marked as auto-installed.  Then you go through and mark packages as non-auto (with "m") until aptitude doesn't want to uninstall anything you don't want it to.

 Obviously you should start by marking ubuntu-desktop (or whatever), ubuntu-standard, and ubuntu-minimal.  build-essential is another good one.  To find other packages that depend on a lot of things, so you don't need to manually mark to many packages as non-auto, follow dependency chains back to their roots.  e.g. say you wanted to keep a bunch of cd/dvd burning progs, like genisoimage.  You could select it, go to "packages which depend on genisoimage" and follow the chain back to something like k3b, and just mark k3b as a keeper.

 Of course, there's no harm in having packages marked as non-auto if you specifically want them.  Package names don't change too often, unless they're library packages with lots of version numbers in their names.

 Anyway, that's what I sometimes do: mark everything as auto, then mark things as non-auto until hitting g won't uninstall anything I want to keep.


 BTW, does update-manager do any magic when upgrading from e.g. Gutsy to Hardy Beta?  I'd rather change /etc/apt/{sources.list,apt.conf,preferences} myself, and use aptitude instead of having update-manager e.g. stupidly uninstall fftw3-dev and not install libfftw3-dev.  Plus, I don't want to uninstall xmms-flac, because it's not available anymore so I can't just re-install it.

 Anyway, does update-manager actually do anything that any other frontend for apt wouldn't do, besides update sources.list and do some disk space checks?

---

### Post by Peter Cordes on 2008-04-06
> **Peter Cordes said:**
> 
 Anyway, does update-manager actually do anything that any other frontend for apt wouldn't do, besides update sources.list and do some disk space checks?


I just spellchecked all the files in hardy.tar.gz (downloaded by update-manager), and I did see some code to give apt a push in the right direction on resolving deps and removing obsolete packages.  It also removes known-broken prerm scripts from two packages.

 It looks like if you can fix that sort of problem yourself, there's no need to use update-manager instead of aptitude.

---

### Post by msundman on 2008-04-16
> **Peter Cordes said:**
> I just spellchecked all the files in hardy.tar.gz (downloaded by update-manager), and I did see some code to give apt a push in the right direction on resolving deps and removing obsolete packages.  It also removes known-broken prerm scripts from two packages.
That's something that really should be documented somewhere. Do you, or does anybody else, know if the information of what "extra stuff" (like resolving deps, removing packages, removing (pre|post)(rm|inst) scripts, and whatnot) update-manager does is available somewhere? Of course I could open up update-manager and try to look at what it does, but that's quite difficult and mistake-prone.

---

