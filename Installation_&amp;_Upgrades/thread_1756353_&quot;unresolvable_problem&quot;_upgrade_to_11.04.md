---
title: "&quot;unresolvable problem&quot; upgrade to 11.04"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by sciarp on 2011-05-12
Hi guys! I tried to upgrade from 10.10 to 11.04 but I got an unmet dependencies error and while the upgrade tool was rolling back the system to the previous configuration the laptop shut down (I didn't recognize that the AC adapter of my laptop wasn't plugged in a good way...)
If I now try to upgrade I get this error:

```
An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
```Moreover if I open the update-manager, I have 1634 updates available, but I cannot install any of them.
My question is: how can I now upgrade to 11.04?

Thank you very much ;)

---

### Post by WthIteh on 2011-05-12
First edit /etc/apt/sources.list so it points to correct repositories of 10.10 (not the natty).
Then try
```

aptitude update
aptitude upgrade

```
You could also open
```

aptitude

```
so it founds packages which must be fixed and fix them.
When everything return to 10.10 standard place :) then start upgrading ....

---

### Post by sciarp on 2011-05-14
I restore the source.list as you suggested me; aptitude doesn't find anything that needs to be fixed, but when I run do-release-upgrade I still get some umet dependencies problems...what would you do?

Thanks :)

---

