---
title: "can't upgrade from 9.04, my system is &quot;up to date&quot;"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by spipe on 2010-02-12
I run three Ubuntu machines - work, home, and a laptop.  All were on 9.04, and I was able over the past week to painlessly upgrade the first two to 9.10.

Today I fired up the laptop for the first time in a while and saw that it hadn't had the upgrade yet, so went to the upgrade manager.  It had a bunch of package upgrades it wanted to do, so I let it.  But there was no option to go to 9.10, not even after catching it up on updates.  It just says the system is up to date.  Clicking "check" again just gives the same message.  It doesn't seem to know that there's a koala out there.

Settings on the update manager say to accept normal releases, so it's not an LTS thing.  Yes, it's on 9.04 now according to /etc/apt/sources.list.  Network connectivity is good.

What might I be missing that I ought to look for?  Go on, tell me it's something obvious.

---

### Post by mhgsys on 2010-02-12
Actually I recommend a fresh install of a new distribution, for it may save you headaches.

Anyway; the option to upgrade should indeed come up in update manager

Try this in terminal:
```
 sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```

---

### Post by snowpine on 2010-02-12
Easier from the command line:

```
sudo apt-get update 
sudo do-release-upgrade
```

("dist-upgrade" won't work! :))

---

### Post by mhgsys on 2010-02-12
-read below-
I've f*cked up my post
haha

---

### Post by mhgsys on 2010-02-12
> **snowpine said:**
> Easier from the command line:

```
sudo apt-get update 
sudo do-release-upgrade
```

("dist-upgrade" won't work! :))

I was reading about this; 


The recommended way to upgrade a Server Edition installation is to use the do-release-upgrade utility. Part of the update-manager-core package, it does not have any graphical dependencies and is installed by default.

Debian based systems can also be upgraded by using apt-get dist-upgrade. However, using do-release-upgrade is recommended because it has the ability to handle system configuration changes sometimes needed between releases. 


 Your right; I just tried it on my 9.04, sudo apt-get dist-upgrade will just upgrade packages and not releases.

```
sudo do-release-upgrade
``` it will be;

---

### Post by kansasnoob on 2010-02-12
> **spipe said:**
> I run three Ubuntu machines - work, home, and a laptop.  All were on 9.04, and I was able over the past week to painlessly upgrade the first two to 9.10.

Today I fired up the laptop for the first time in a while and saw that it hadn't had the upgrade yet, so went to the upgrade manager.  It had a bunch of package upgrades it wanted to do, so I let it.  But there was no option to go to 9.10, not even after catching it up on updates.  It just says the system is up to date.  Clicking "check" again just gives the same message.  It doesn't seem to know that there's a koala out there.

Settings on the update manager say to accept normal releases, so it's not an LTS thing.  Yes, it's on 9.04 now according to /etc/apt/sources.list.  Network connectivity is good.

What might I be missing that I ought to look for?  Go on, tell me it's something obvious.

Look in Synaptic and see if "ubuntu-desktop" is installed. Sometimes modifications remove the "ubuntu-desktop" package and it can hose upgrades.

Or if you prefer the terminal run:

```
aptitude show ubuntu-desktop|head -4

```

and see if it's installed.

---

### Post by spipe on 2010-02-13
Thanks for the replies.  It will be Monday before I get another look, but something up there ought to work. :)

---

### Post by spipe on 2010-02-15
ubuntu-desktop was there, so I still don't know why it wasn't detecting the upgrade automatically, but do-release-upgrade did make it detect the koala.  It's upgrading now.  Thanks for the help, peeps.

---

