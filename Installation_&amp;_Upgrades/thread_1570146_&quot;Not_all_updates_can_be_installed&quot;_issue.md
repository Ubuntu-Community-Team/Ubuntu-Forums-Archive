---
title: "&quot;Not all updates can be installed&quot; issue"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by chronozphere on 2010-09-07
Hey,

When I start ubuntu, the update manager will automaticly start and tells me that "Not all updates can be installed". :?

I know this is a common issue people ask questions about, because I've seen a number of threads. Still, after reading about this issue, I'm unsure how to fix it. I'll describe my situation:

When I close the messagebox, I'm left with an update manager that presents me with 851 updates. Some checkboxes are unchecked and cannot be checked. It also shows me that I can upgrade to 10.4. I don't want to do that yet. I just want to recieve my updates to keep my system safe and up-to-date.

I've taken a look at the situation in synaptic. I clicked "Mark all upgrades". It marked a whole lot of them. I noticed that "gdm" and maybe 20 other packages were about to be removed. I became supsicious. Is this a good thing? :?

I've also added two third party repositories, as you can see in my sources.list:

```

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://www.hu.freepascal.org/lazarus/ lazarus-stable universe
deb http://ftp.nl.debian.org/debian sid main

```I needed these because I wanted the latest version of a few packages.

Finally, My ALSA-installation is desynced with the package manager. I don't want it to interfere, as I am expirimenting with my audio drivers. 

Is it safe to do "Mark all patches" -> "Apply" in synaptic? What should I do? 

Thanks a bunch! :)

---

### Post by tommcd on 2010-09-07
> **chronozphere said:**
> 
When I close the messagebox, I'm left with an update manager that presents me with 851 updates. ...
I've also added two third party repositories, as you can see in my sources.list:
```

deb http://ftp.nl.debian.org/debian sid main

```I needed these because I wanted the latest version of a few packages.

This is your problem. There are 851 updates? This should be a big red flag that you are about to break your system. APT is probably trying to upgrade half of your system to Debian sid. You should not be mixing Debian and Ubuntu repositories.

My recommendation would be to just do a clean install of Ubuntu 10.04. Many people use the dist-upgrade method though, so do that if you prefer.
You should remove all 3rd party repos from your system before you do a dist-upgrade.

---

### Post by chronozphere on 2010-09-08
Thanks alot. I allready thought the sollution would be in this direction. :)

However, the ubuntu repositories are not always up-to-date. For example, I needed the latest version of GIT, which wasn't in the repo. Thats why I added the debian repo. What should I do when I need something that isn't in the ubuntu repository? 

Also, what will the upgrade to 10.04 change? For example, will it affect my "expirimental" alsa-setup? What about the latest version of GIT I installed?

Thanks again! ;)

---

### Post by alphacrucis2 on 2010-09-08
> **chronozphere said:**
> Thanks alot. I allready thought the sollution would be in this direction. :)

However, the ubuntu repositories are not always up-to-date. For example, I needed the latest version of GIT, which wasn't in the repo. Thats why I added the debian repo. What should I do when I need something that isn't in the ubuntu repository? 

Also, what will the upgrade to 10.04 change? For example, will it affect my "expirimental" alsa-setup? What about the latest version of GIT I installed?

Thanks again! ;)

If possible use a PPA eg:

[https://launchpad.net/~git-core/+archive/ppa]("https://launchpad.net/~git-core/+archive/ppa")

---

