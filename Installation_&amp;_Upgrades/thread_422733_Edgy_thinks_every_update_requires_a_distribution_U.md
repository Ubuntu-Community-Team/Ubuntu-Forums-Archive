---
title: "Edgy thinks every update requires a distribution Update"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Andy17MB on 2007-04-25
Every time I get an update flagged and run the Update manager I get a Pop-up stating that "not all upgrades can be installed" and advises running a distribution upgrade.  This is nothing to do with the release of Fiesty as it has been happening for 2 or 3 months now.  I am not aware of an update failing and I think I am running bog-standard Edgy.  I suspect I have inadvertently set or unset something.  Any Suggestions?

---

### Post by jda1701 on 2007-04-25
Try opening a console window and typing these in:

```
sudo aptitude update
```
```
sudo aptitude upgrade
```
```
sudo aptitude dist-upgrade
```

After that check and see if the error still exists.  If so you might have to do some digging around and using dpkg to finish some botched installation of some package.

Good luck!

---

### Post by Andy17MB on 2007-04-25
Thanks for that, unfortunately it Hasn't worked.  I'm a fairly new Linux user and Not familiar with dpkg - can you suggest a good starting point?

Thanks

---

