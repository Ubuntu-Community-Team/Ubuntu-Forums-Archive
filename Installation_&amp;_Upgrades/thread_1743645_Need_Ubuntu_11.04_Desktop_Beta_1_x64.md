---
title: "Need Ubuntu 11.04 Desktop Beta 1 x64"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Crath on 2011-04-29
I am looking for a copy of 11.04 desktop beta1 amd64 to download.

This is running on an x120e. Beta1 installs and works but freezes every few hours. Beta2 almost fully installs but pops up with a friendly error that says "installation has failed" with not much helpful in the syslogs. 11.04 Final kernel panics half way through installation.

At this point, I've tried almost everything, so I'm just trying to get back on Beta1 to get stable because this is my work computer. There are a lot of links on google, but every single one went dead as soon as final was released.

After that, I will work on trying to get 11.04 final installed properly. Thanks for any links!

---

### Post by mörgæs on 2011-04-29
Better to try the minimal installer:

[http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/)

After installing, run


```
sudo apt-get install ubuntu-desktop
```

having wired internet access during the entire process.

---

