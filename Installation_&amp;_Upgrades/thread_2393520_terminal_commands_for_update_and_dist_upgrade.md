---
title: "terminal commands for update and dist upgrade"
date: 2018-06-04
forum: Installation &amp; Upgrades
---

### Post by bodhin2 on 2018-06-04
what are the correct terminal commands to update and also do a dist-upgrade?

---

### Post by TheFu on 2018-06-04
It depends on the release, but ... 
**sudo apt update && sudo apt full-upgrade**
Dist-upgrade has been deprecated because it was confusing many people, since it doesn't move from release to release.  The apt or apt-get manpage has the details.
From the apt manpage:```

       update (apt-get(8))
           update is used to download package information from all configured
           sources. Other commands operate on this data to e.g. perform
           package upgrades or search in and display details about all
           packages available for installation.

       upgrade (apt-get(8))
           upgrade is used to install available upgrades of all packages
           currently installed on the system from the sources configured via
           sources.list(5). New packages will be installed if required to
           statisfy dependencies, but existing packages will never be removed.
           If an upgrade for a package requires the remove of an installed
           package the upgrade for this package isn't performed.

       full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove
           currently installed packages if this is needed to upgrade the
           system as a whole.
```

For release-to-release things, there are different methods.

---

### Post by VMC on 2018-06-04
```
sudo apt update && sudo apt upgrade
```
and 
```
sudo apt update && sudo apt [COLOR=#111111][FONT=Consolas]dist-upgrade
```[/FONT][/COLOR]

---

### Post by bodhin2 on 2018-06-04
thank you - a bit different than i am used to.  great!

---

### Post by mörgæs on 2018-06-05
Please mark your thread 'solved'.

---

### Post by bodhin2 on 2018-06-06
how do i mark it?

---

### Post by slickymaster on 2018-06-06
> **bodhin2 said:**
> how do i mark it?

Just follow the link in my signature on how to mark the thread as solved

---

### Post by bodhin2 on 2018-06-06
thanks - i missed that!!!!

---

