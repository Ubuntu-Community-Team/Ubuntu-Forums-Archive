---
title: "cannot upgrade to 10.10 from 10.04. Dependencies error"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by rpk94 on 2011-02-10
I tried upgrading to 10.10 from lucid, but it gives me the following error:
'An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.'
The system is updated. Please suggest some solution to this. I am pretty new to ubuntu.

---

### Post by Ubunterrific on 2011-02-10
Could you please try typing this in a terminal, then enter.

```
sudo apt-get -f install
```

and post the output of this for us:

```
sudo apt-get update
```


:)

---

### Post by TheFolklorist on 2011-02-10
Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

this is what mine said I have the same error as the above poster

oh and when i decided not to fool with upgrading and just install 10.10 from a disk I couldnt get the back light on my lap top to light up, but I could just barely make out that the install disk I made was working. Any ideas as to why this happens?

---

### Post by TheFolklorist on 2011-02-10
Never mind in another post a guy named rick b. said to get rid of the  package xserver-xorg-video-nouveau I did and that fixed it for me hopefuly that will work for you too topic creator

---

