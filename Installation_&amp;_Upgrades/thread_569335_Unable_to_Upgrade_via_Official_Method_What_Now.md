---
title: "Unable to Upgrade via Official Method: What Now?"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by Xanderfoxx on 2007-10-06
When I upgraded using the "Official Method," by entering the

```
gksu "update-manager -c"
```

Command, I returned this error:

```

Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

```

This is what the terminal looked like:

```

alex@alex-maurin-laptop:~$ gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpzA_S8I/edgy.tar.gz'
authenticate '/tmp/tmpzA_S8I/edgy.tar.gz' against '/tmp/tmpzA_S8I/edgy.tar.gz.gpg'
/tmp/tmpzA_S8I/DistUpgradeViewGtk.py:360: GtkWarning: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed
  self._term.realize()
alex@alex-maurin-laptop:~$


```

I am attempting to upgrade from Dapper to Edgy, and then to Feisty. I am encountering problems during the second stage, or between that and the one where I actually download the upgraded packages.

The ultimate reason for upgrading is so that I can get upgraded packages for Rosegarden (Once I get it to work.), and other applications.

I would really appreciate help.

---

### Post by houndhen on 2007-10-08
[email]maurin.alex@gmail.com[/email]

I have the same problem. Did you get an answer to what to do next?

Thanks,
houndhen

---

### Post by oilchangeguy on 2007-10-08
just back up your data. and do a fresh install of 7.04. or wait til 7.10 is out. there is no valid reason to go from 6.06, to 6.10, just to get 7.04. you'll save alot of time by just doing a clean install.

---

### Post by Xanderfoxx on 2007-10-22
> **oilchangeguy said:**
> Just back up your data, and do a fresh install.... You'll save a lot of time by just doing a clean install.

*sigh* Okay.

Getting to it.

Thanks. This issue has been solved.

Thank you, guys.

---

