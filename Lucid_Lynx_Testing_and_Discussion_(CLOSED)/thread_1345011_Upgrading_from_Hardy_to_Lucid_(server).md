---
title: "Upgrading from Hardy to Lucid (server)"
date: 2009-12-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by davidshere on 2009-12-03
I manage a handful of Hardy servers.  I have been looking for information on how to upgrade directly to Lucid from Hardy (to test the process, of course!) and haven't been able to find that.  Will that be available soon?

Why do I always find pertinent information AFTER I post a new thread?
```
david@wildcat:~$ sudo do-release-upgrade --help
Usage: do-release-upgrade [options]

Options:
  -h, --help            show this help message and exit
  -d, --devel-release   Check if upgrading to the latest devel release is
                        possible
  -p, --proposed        Try upgrading to the latest release using the upgrader
                        from $distro-proposed
  -m MODE, --mode=MODE  Run in a special upgrade mode. Currently 'desktop' for
                        regular upgrades of a desktop system and 'server' for
                        server systems are supported.
  -f FRONTEND, --frontend=FRONTEND
                        Run the specified frontend
```

The -d option upgraded my machine to Karmic.  I wonder if -p would have done it to Lucid.

---

### Post by cariboo on 2009-12-03
The -p option should do what you want.

---

### Post by RAOF on 2009-12-03
Or it will, once upgrade-manager grows support for upgrading to Lucid; I don't think it has it at this point?

---

### Post by davidshere on 2009-12-04
> **RAOF said:**
> Or it will, once upgrade-manager grows support for upgrading to Lucid; I don't think it has it at this point?

Apparently not:
```
david@bearcat:~$ sudo do-release-upgrade -p
Checking for a new ubuntu release
No new release found

```

I get the same results from a freshly updated Karmic box.

---

### Post by Gina on 2009-12-04
That's because there isn't a new release after Karmic.  Lucid hasn't been released yet.

---

### Post by NCLI on 2009-12-05
I think it'll start working when Alpha 1 is released in a few days, just wait for that ;)

---

### Post by davidshere on 2010-04-26
This is what **sudo do-release-upgrade -d** does now:

```
david@thebone:~$ sudo do-release-upgrade -d
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg'
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
tar: Removing leading `/' from member names

...

```

What does the **"FutureWarning: apt API not stable yet warnings.warn("apt API not stable yet", FutureWarning)"** mean?

---

