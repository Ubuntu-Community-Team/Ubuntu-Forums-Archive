---
title: "Upgrade 13.10 t0 14.04 No candidate ver: upgrade problem"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by greensoma on 2014-07-24
Hallo together,

I am trying to upgrade my Ubuntu 13.10 to 14.04 but getting some "No candidate ver:" errors which are the reason my upgrade fails.

```
No candidate ver:  airtime
No candidate ver:  libavcodec53
No candidate ver:  libavutil51
No candidate ver:  libboost-date-time1.49.0
No candidate ver:  libboost-serialization1.49.0
No candidate ver:  libkms1
No candidate ver:  libllvm3.2
No candidate ver:  libopenimageio1.2
No candidate ver:  libopenscenegraph80
No candidate ver:  libopenshadinglanguage1.3
No candidate ver:  libruby1.8
No candidate ver:  linux-image-3.11.0-12-generic
No candidate ver:  linux-image-3.11.0-9-generic
No candidate ver:  linux-image-extra-3.11.0-12-generic
No candidate ver:  linux-image-extra-3.11.0-9-generic
```

I tried to remove those candidates with

```
sudo apt-get remove airtime ...
```

But apt tells me that they are not installed.
What can i do? Is there a way to ignore those packages?

---

### Post by ibjsb4 on 2014-07-24
Eventhough 13.10 has reached EOL, the sources are usually there for a few weeks.

Try disabling all third party software.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

and then
```
sudo apt-get update && sudo apt-get dist-upgrade
```
if that works without error
```
sudo do-release-upgrade
```

---

### Post by greensoma on 2014-07-24
I checked it. Only Ubuntu sources are active. Error message stays the same. I also tried to remove some meta packages which seem to contain some of the above mentioned packages. But the deinstallation wanted to remove my whole system then because of so many dependencies. Any further ideas?

---

