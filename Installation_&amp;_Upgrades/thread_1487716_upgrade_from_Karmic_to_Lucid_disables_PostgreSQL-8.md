---
title: "upgrade from Karmic to Lucid disables PostgreSQL-8.3"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by wbloos on 2010-05-19
Hi,

I just upgraded a Ubuntu Desktop 64bit system from Karmic (9.10) to Lucid (10.04).
There were several PostgreSQL 8.3 clusters running on that machine.
After the upgrade, postgresql was not able to run anymore.

The package postgresql-8.3 was marked "rc" in dpkg -l
I was not able to re-install PostgreSQL 8.3 because of a mismatched dependency.
There was no warning. I guess i should have read the release notes, which i didn't.

There should have been a warning before it was too late to turn back and upgrade postgresql to 8.4 first.
I don't see how this is supposed to work, ever.

I'd like to know if this would be considered a bug, if it is known already and how to correctly file this bug correctly if appropriate (ubuntu-bug ?)

thx,

WBL

---

### Post by meldon on 2010-05-20
Hi elvar,

I'm in a similar situation. I just found this post:
[http://ubuntuforums.org/showthread.php?t=1473404#3](http://ubuntuforums.org/showthread.php?t=1473404#3)

That will get 8.3 installed. Then I ran this command:
```

pg_dropcluster 8.4 main  #this will wipe out the new databases from the new install
pg_upgradecluster 8.3 main  #this to upgrade the 8.3 data to 8.4

```

---

### Post by wbloos on 2010-05-21
Ok, adding the karmic repositories to the sources.list enabled the installation of postgresql-8.3.
I wonder if that can do any harm? I mean, how does apt know which packages (not) to install from the karmic repositories?

Anyway installing postgresql-8.3 re-enabled the databases, no data lost.
The dependency mismatch was because i tried to install the postgresql-8.3 package from debian with dpkg -i

However, it's no good to render people's data useless when they upgrade. When i upgraded from debian etch to lenny, the old packages were not removed, but i got a warning that there was no more support for the old postgresql version. I could then install the new version and upgrade the database cluster to the new dbms version.
I'd like to tell Canonical, or whoever manages the versioning, about my complaint. Should i file a bug with ubuntu-bug for that?
(I do not have commercial support.)
The doubt on my mind is: it's actually a bad feature, not a real bug (as in dysfunctional feature).

---

### Post by wbloos on 2010-05-30
also, i have a production server running on postgresql 8.3, on 8.04 LTS (Hardy).
if i'd want to upgrade to the next LTS version i would have extra trouble, because postgres 8.3 is not on ubuntu 8.04, and postgres 8.4 is not on ubuntu 10.04.
I'd have to do a dump/restore, that is a considerable downside to the upgrade. Besides, you'd have to make a database dump with the version that you want to restore to.. how am i supposed to do that? (yeah maybe get the 8.4 package from hardy-backports, but it's not elegant)

And worst of all, there is no clear warning to all this.
There is a list of packages that will be de-installed. But on the desktop system that i upgraded, it was piled with packeges that don't mean much to me. I saw names of gnome games and some system stuff, i just trust ubuntu to handle all that. But rendering my database useless is a different story!

I truly think that this is a bad way to work the versioning of this package. Is there a way to tell the maintainer about my ideas, other than on this forum? thx.

---

