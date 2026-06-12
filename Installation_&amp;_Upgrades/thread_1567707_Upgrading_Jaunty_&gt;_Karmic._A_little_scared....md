---
title: "Upgrading Jaunty &gt; Karmic. A little scared..."
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by cyberfin on 2010-09-04
Hi everyone!

I've been running my current setup of Jaunty for a loooooong time now. Now I am finally going to upgrade to get some new yummy ubuntu goodness.

My problem i simple (?): As well as using it as my desktop, I run an apache server with a bunch of other services, home is on it's own partition which uses reiserfs and I'm wondering what kind of impact this is going to have on all of this.

My previous experience of a dist upgrade was quite bad (a few years ago) as it left me with broken stuff all over.

Does anyone have any pointers, ideas, opinions, experiences, insults?

Thanks a bunch!

---

### Post by davidmohammed on 2010-09-04
The old saying "if it ain't broke don't fix it" should be applied if  you are the cautious type.  For me, each upgrade has broken something, but I've always managed to find a work around.

Personally, I would backup whatever you have with something like "clonezilla".  Then try the upgrade.

---

### Post by -kg- on 2010-09-04
> **davidmohammed said:**
> The old saying "if it ain't broke don't fix it" should be applied if  you are the cautious type.  For me, each upgrade has broken something, but I've always managed to find a work around.

Personally, I would backup whatever you have with something like "clonezilla".  Then try the upgrade.

+1

The above has been my general experience, too, unless the installation I'm upgrading is new, or almost pristine.  I've successfully upgraded my desktop, but most all I use it for is crunching BOINC work units and light Internet usage.

My laptop is a different consideration.  I use my laptop for all sorts of experiments and poking, prodding, and reconfiguring, and I don't think I've ***ever*** had a successful upgrade.  I always back up my data and do a fresh install; even leaving the /home partition intact bollixes up the installation.  But that's just me.

It ***is*** a good idea to upgrade Jaunty.  Support for Jaunty ends next month.  Of course, support for Karmic ends in April of next year.  Lucid (10.04) is an LTS release, and desktop support for it ends in April of 2013, with the Server version ending in 2015.

Considering that, you might want to install the Server version of Lucid (with support ending in 5 years instead of 3) and install your DE on top of that.  Considering you're running Apache Server and all, that might even work out better for what you use it for.

All in all, when you are finally all but forced to upgrade, you might as well do it all the way to Lucid, which is the current LTS release.  That way, you'll have a lot of time with it, compared to a normal release which is only supported for 18 months, Server as well as Desktop.  If you're forced to fresh install and start over, you might as well start over with the LTS version.  You won't have to "start over" again nearly as soon.

Whatever transpires, it's always good to have a back up of your system.  You never know what might happen.  [Clonezilla]("http://www.clonezilla.org/") has always worked for me.

---

