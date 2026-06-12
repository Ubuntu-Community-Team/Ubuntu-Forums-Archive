---
title: "An unresolvable problem occurred while calculating the upgrade"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by baskar007 on 2009-11-13
```


Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'update-manager' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


```

I am getting this error while try to upgrade Ubuntu9.04 to 9.10

I have tried  "apt-get install -f", sudo dpkg --configure -a
But no solution.

anyone have a solution for this error?

---

### Post by wojox on 2009-11-13
Is 9.04 fully updated?

Press ALT+F2, a dialog will pop up. Type:

```
gksudo "update-manager -c"
```

---

### Post by madhusker on 2011-05-28
I have the same problem trying to update from 10.04.02 LTS to 10.10.  One thread said to remove ppa sources, but I dont have any that I know of...

What did work for me was to look at the logs /var/log/dist-upgrade/ and see what package was being held back.  After removing that package the upgrade went along as expected.

---

