---
title: "Unmet dependencies when trying to install Gimp"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by BrentP81 on 2012-04-18
For some reason, I went to use Gimp and it was no longer installed on my system.

I opened the terminal and ran sudo apt-get install gimp and got the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (>= 2.7.5) but it is not going to be installed
        Depends: libgimp2.0 (<= 2.7.5-z) but it is not going to be installed
        Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages.

```



Being new to Ubuntu, I have no idea why Gimp was ever deleted to begin with or how to go about getting it back.

---

### Post by BrentP81 on 2012-04-18
Bump...

---

