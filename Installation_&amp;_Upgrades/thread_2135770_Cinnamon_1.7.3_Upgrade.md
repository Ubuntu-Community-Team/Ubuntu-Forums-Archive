---
title: "Cinnamon 1.7.3 Upgrade"
date: 2013-04-15
forum: Installation &amp; Upgrades
---

### Post by chazdg24 on 2013-04-15
Is it possible to install Cinnamon 1.7.3 in 12.10?  I am currently running 1.6.7.  Thanks for any help.

---

### Post by fantab on 2013-04-15
1.6.7 is the stable version. I think you are looking for Cinnamon Nightly Builds.

You have to add the Nightly PPA to you 'software sources':


```
deb [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu) quantal main  
deb-src [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu) quantal main
```

Then apt-get update and either upgrade or re-install cinnamon.

---

### Post by chazdg24 on 2013-04-15
> **fantab said:**
> 1.6.7 is the stable version. I think you are looking for Cinnamon Nightly Builds.

You have to add the Nightly PPA to you 'software sources':


```
deb [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu) quantal main  
deb-src [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu) quantal main
```

Then apt-get update and either upgrade or re-install cinnamon.
Is it stable?  Or am I going to blow everything up?

---

### Post by fantab on 2013-04-16
Ok... Cinnamon in repos got updated to 1.7, just upgrade. Regarding 'Nightly PPA': No, the Nightly builds are not stable, expect issues and breakages. But since it is updated every day the fixes too will generally come daily. However, no guarantees.

---

### Post by chazdg24 on 2013-04-16
> **fantab said:**
> Ok... Cinnamon in repos got updated to 1.7, just upgrade. Regarding 'Nightly PPA': No, the Nightly builds are not stable, expect issues and breakages. But since it is updated every day the fixes too will generally come daily. However, no guarantees.
Was this updated with the stabble PPA?

---

### Post by chazdg24 on 2013-04-17
Just to clarify my previous post, I meant the stable PPA, not the Nightly Build.

---

### Post by fantab on 2013-04-17
I am using 13.04. Cinnamon is in [official Ubuntu repos]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=cinnamon"), at least for 13.04 it is. I don't know how you installed it. If you installed it from a ppa then that ppa will have definitely been updated. You should be able to get the latest version with "sudo apt-get upgrade" or whichever is your Update method.

---

### Post by chazdg24 on 2013-04-17
> **fantab said:**
> I am using 13.04. Cinnamon is in [official Ubuntu repos]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=cinnamon"), at least for 13.04 it is. I don't know how you installed it. If you installed it from a ppa then that ppa will have definitely been updated. You should be able to get the latest version with "sudo apt-get upgrade" or whichever is your Update method.
That is what I thought.  I am using this [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu) quantal.  It appears that Cinnamon has not been updated for quantal.

---

