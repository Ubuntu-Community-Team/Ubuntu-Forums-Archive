---
title: "how to install tar without tar?"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Alex001 on 2010-10-28
I have accidentally unistalled 'tar'. (stupid)
Now when i try to install it, I get this message:

dpkg: warning: 'tar' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: warning: 'tar' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

'tar' needs 'tar'? :confused: Please someone help!

---

### Post by dasan on 2010-10-28
get the source of tar and install from it
get a zip or uncompress it from some of your frinds

---

### Post by babur on 2010-10-28
Install "tar" package/utility using "apt-get" in command line or using "Synaptic package manager", it should solve the problem.

---

### Post by kerry_s on 2010-10-28
> **Alex001 said:**
> I have accidentally unistalled 'tar'. (stupid)
Now when i try to install it, I get this message:

dpkg: warning: 'tar' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: warning: 'tar' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

'tar' needs 'tar'? :confused: Please someone help!


it looks like you changed the path, so it should still be there.
```
export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```
or
you could just reboot if you didn't set it permanent somewhere.

---

### Post by Alex001 on 2010-10-28
> **dasan said:**
> get the source of tar and install from it
get a zip or uncompress it from some of your frinds

this worked!!! Thanks!!!

---

### Post by Angel Zone on 2011-01-31
I have the same problem. could not solve it by:
export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

Please Help...Can't Install or upgrade ubuntu.....

---

