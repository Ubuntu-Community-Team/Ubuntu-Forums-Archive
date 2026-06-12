---
title: "missing /etc/cron.daily/apt script for jaunty"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by okhowaboutthisusername on 2010-09-23
jaunty / 9.04
I've recently been trying out anacron, apticron, and unattended-upgrades. It appears that /etc/cron.daily/apt was replaced at some point, then removed when I uninstalled apticron (I think). I'm pretty confused as to what happened. I replaced the cron.daily/apt script but I'm uncertain which version it's for. I believe it's failing on:

apt-key net-update

I'm getting the following error msg:
```

/etc/cron.daily/apt:
Checking for new archive signing keys now
ERROR: '/usr/share/keyrings/ubuntu-master-keyring.gpg' not found

``` 

I'm coming from Fedora and am still pretty unsure of how Ubuntu does things. How can I reset apt-get to it's default state?

---

