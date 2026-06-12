---
title: "disk usage and installed packages"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by dbrum on 2006-10-09
I was wondering, where are the packages that are downloaded by Synaptic kept?  I think my HD is getting filled up pretty quick by keeping a history of all the packages I have ever installed through Synaptic.  Is it safe to remove the older ones, just by deleting, or should I do anything special to get rid of them and not hurt the system in any way?

thanks!

---

### Post by Kateikyoushi on 2006-10-09
The cached packages are stored in /var/cache/apt/archives.

You can check your settings and remove files in synaptic >> settings >> preferences >> files.

Altogether it's 700MB in my case.

---

### Post by doggie on 2006-10-09
```

**sudo aptitude clean** or **sudo apt-get clean**
Removes  all  previously  downloaded .deb files from the package
cache directory (usually /var/cache/apt/archives).

**sudo aptitude autoclean** or **sudo apt-get autoclean**
Removes any cached packages which can no longer  be  downloaded.
This  allows  you to prevent a cache from growing out of control
over time without completely emptying it

```

---

