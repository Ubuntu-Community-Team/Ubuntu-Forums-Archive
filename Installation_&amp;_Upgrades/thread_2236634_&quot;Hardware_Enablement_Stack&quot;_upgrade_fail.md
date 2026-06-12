---
title: "&quot;Hardware Enablement Stack&quot; upgrade failed"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by spacemen12 on 2014-07-28
Here are the details:
```
"
New hardware support is available
Your current Hardware Enablement Stack (HWE) is going out of support
on 08/07/2014.  After this date security updates for critical parts (kernel
and graphics stack) of your system will no longer be available.

For more information, please see:
http://wiki.ubuntu.com/1204_HWE_EOL"
```

After I ask to upgrade:

```
"
Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details
The following packages have unmet dependencies:

libgl1-mesa-glx-lts-trusty: Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but 10.1.3-0ubuntu0.1~precise1 is to be installed
                            Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2.2 is to be installed
                            Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is to be installed
xserver-xorg-lts-trusty: Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) but 2:1.15.1-0ubuntu2~precise1 is to be installed"
```

What should I do?

---

### Post by ajgreeny on 2014-07-28
See what happens if you try by first refreshing the repos with ```
sudo apt-get update
``` then try updating the single package  **xserver-xorg-lts-trusty**.

That is what I did, using synaptic, after a few failed attempts, and that pulled in everything else that was needed as dependencies.  Synaptic is definitely worth using as it gives a lot more info in an easily readable manner even than the command line

This whole HWE update process seems to have been a disaster for many, and can also lead on to problems for those who like to run a distro update, eg from 12.04 to 14.04, which will apparently fail if the HWE has previously been upgraded.  I always clean install so that problem does not worry me but it might be something that affects you if distro updates are your way of moving from version to version.

---

