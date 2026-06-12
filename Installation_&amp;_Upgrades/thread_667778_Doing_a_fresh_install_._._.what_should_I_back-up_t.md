---
title: "Doing a fresh install . . .what should I back-up to make it easy?"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by CheshireMac on 2008-01-14
Hey folks. I'm cleaning my system out because I want to reorganize it. I also want to see if there's a dramatic difference between installing Gutsy and upgrading to it. 
I have an external HD, so backing up isn't an issue. What I should back up is an issue. I want to ensure that I retain the proper drivers etc. 
All my valued files are already on the external and so I can basically wipe the machine's drive clean, after I save the appropriate things.
Any thoughts would be appreciated. I've got HP nc8000, if anyone's curious.

---

### Post by wolfen69 on 2008-01-14
just try the live cd to make sure everything works. that would make the most sense to me.

---

### Post by CheshireMac on 2008-01-14
Well, I also want to clean up my system too. I know the CD works. Is there a way to back up my drivers, and codecs I chose?

---

### Post by kostkon on 2008-01-14
If you upgrade your Ubuntu, every package you have will be retained, it will just be updated to a newer version. If you do a clean install you'll have to install everything from the start, which is a little time consuming.

A thing you should backup is your applications' configuration files/folders. This is a good thing to do even if you upgrade, in order to be safe in the case the upgrade goes bad (small possibilty for this).

In the case of a clean install, you will copy back the configuration files/folders and this will allow your applications to be configured in the same way as in the previous install.

Just open a *Nautilus* window in your home folder, select *View -> Show Hidden Files* and then backup any file/folder that corresponds to an application's configuration you care to keep.

You don't need to keep any codecs, assuming that you did not install anything special by yourself, since they are offered in standarised packages for every Ubuntu version (I mean mostly the *ubuntu-restricted-extras* and *w32codecs* packages).

You cannot do anything about the drivers since they are in the kernel (again assuming that you did not do anything special).

---

### Post by CheshireMac on 2008-01-14
Can I retain my current kernel and install everything else anyway? It took me forever to get my wireless working.

---

### Post by zvacet on 2008-01-15
If you didn´t run autoclean in the past everything you installed should be in var/cache/apt/archives.Download AptOnCd and with it you can save all that files and more.Read [this](http://aptoncd.sourceforge.net/).

---

