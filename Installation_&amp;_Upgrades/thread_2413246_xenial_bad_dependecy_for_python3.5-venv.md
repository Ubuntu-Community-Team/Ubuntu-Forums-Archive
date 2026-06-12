---
title: "xenial: bad dependecy for python3.5-venv"
date: 2019-02-23
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2019-02-23
the package python3.5-venv depends on 3.5.1 but 3.5.2 is what comes with 16.04:

```
lt2a/admin /home/admin 1> sudo apt-get -y install python3.5-venv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python3.5-venv : Depends: python3.5 (= 3.5.1-10) but 3.5.2-2ubuntu0~16.04.5 is to be installed
E: Unable to correct problems, you have held broken packages.
lt2a/admin /home/admin 2>
```

is this a matter of someone not keeping packages up to date with other things in Ubuntu 16.04.  does LTS mean they need to fix this?

---

