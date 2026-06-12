---
title: "Upgrading from 11.04 to 11.10"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by fizzyorange on 2011-11-21
I've got two installations, more or less identical running on Virtual Box (4.1.6 on Windows 7 Professional)  that were on 10.10.

For some reason update manager on both stopped advertising that 11.04 was available, so I upgraded the first one using the do-release-upgrade command.  First to 11.04 and then to 11.10, no problems.  Have my doubts about Unity, but I'm sure I'll get the hang of it.

On the other instance the upgrade from 10.10 to 11.04 went OK but when I try to go from 11.04 to 11.10 it claims that there is no upgrade available.

What should I try next?

---

### Post by zvacet on 2011-11-22
Did you run 

```
sudo apt-get update && sudo apt-get upgrade
```

to be sure your system is up-to-date?

---

### Post by fizzyorange on 2011-11-23
I certainly did.  I have run them repeatedly and while the Update has installed some more stuff it still appears to make no difference to my ability to actually upgrade to 11.10.  The weird thing is the other installation went though without a hitch.

It's very strange.

---

### Post by BC59 on 2011-11-23
> **fizzyorange said:**
> I've got two installations, more or less identical running on Virtual Box (4.1.6 on Windows 7 Professional)  that were on 10.10.

For some reason update manager on both stopped advertising that 11.04 was available, so I upgraded the first one using the do-release-upgrade command.  First to 11.04 and then to 11.10, no problems.  Have my doubts about Unity, but I'm sure I'll get the hang of it.

On the other instance the upgrade from 10.10 to 11.04 went OK but when I try to go from 11.04 to 11.10 it claims that there is no upgrade available.

What should I try next?


Alt + F2

```
update-manager -d
```

---

### Post by fizzyorange on 2011-12-04
I know how to run the update manager.  It's persuading any of the update tools that there's an upgrade from 11.04 to 11.10 that's the problem.

---

