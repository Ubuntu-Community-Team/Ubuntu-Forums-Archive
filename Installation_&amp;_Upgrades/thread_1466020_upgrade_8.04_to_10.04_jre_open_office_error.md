---
title: "upgrade 8.04 to 10.04 jre open office error"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by simonjester on 2010-04-29
During the upgrade from Hardy Heron tonight to 10.04 I got this fatal error message which aborted the upgrade.  If any can tell me how to fix and proceed I would appreciate it!

[COLOR="Red"]Could not install upgrades

Error during commit
'E:Couldn't configure pre-depend jre for openoffice.org-writer2latex, probably a dependency cycle.'
Restoring original system state[/COLOR]

---

### Post by zvacet on 2010-04-30
```
sudo dpkg --configure -a
```

or 

```
sudo apt-get -f install
```

---

### Post by gerpol on 2010-04-30
I am having the exact error and both the solutuons of zvacet don't work.

Any help would be great.

---

### Post by wlh1950 on 2010-04-30
I de-installed openoffice, then the upgrade worked.

---

### Post by simonjester on 2010-04-30
Thanks all.  I removed the offending package and installation was then successful.

---

