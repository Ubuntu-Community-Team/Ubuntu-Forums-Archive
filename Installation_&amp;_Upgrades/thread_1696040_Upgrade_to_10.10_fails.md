---
title: "Upgrade to 10.10 fails"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by JaxJagsfan on 2011-02-26
I am now using Ubuntu 10.04 LTS.  I tried to upgrade to 10.10 and I keep getting this error:


An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


I don't know what happened there,  Do you know how to fix this? :confused:

---

### Post by LeftWIngPenguin on 2011-02-26
I'm actually getting this exact same problem. Not too worried about it at the moment, because 10.4 seems to be working pretty well for me so far, but it would be good to get an answer on what's causing it.

---

### Post by LeftWIngPenguin on 2011-02-28
*bump*

Any ideas on this one?

---

### Post by sikander3786 on 2011-02-28
Go to System > Administration > Software Sources and disable any custom added PPAs. Also disable them from your original sources.list if you've added some by hand. Then try these commands from Terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

```
sudo do-release-upgrade
```

Or against the 3rd one, you can use Update Manager as well.

---

