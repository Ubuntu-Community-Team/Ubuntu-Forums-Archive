---
title: "can't access repositories, so can't upgrade/install anything"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by Nicole on 2007-03-13
Hi,

Since I managed to get my wireless internet to work, I've not been able to access any of the repositories through Synaptic, or automatix or using apt-get. For some packages it doesn't matter, since I can download them through firefox, but it does become a problem when I'm trying to look for system updates, and if I want to upgrade from Dapper, which I would quite like to try. Or at any rate, I'd like the option!

I'm running Dapper on a Sony Vaio laptop, using a d-link wireless router - and it's only been since I've managed to get the wireless working that the repositories don't. Synaptic et al just time out when they try to download anything from them - but firefox/thunderbird/gyachi etc can access the internet fine.

I'm not really a very technical person, so be gentle! If there is more information I can give that would help, just let me know. Similarly, if this is in the wrong place, I'm more than happy to go to the right place to ask for help, if you could let me know!

Thanks a lot for your help,

Nicole

---

### Post by zvacet on 2007-03-13
Go to synaptic> settings>repositories
You will see list of repositories and box on the left of them.Chek all boxes> close >reload
synaptic again and under repositories you will see add on the right side.click on it and you will be able to add extra repositories.In new window first you will see repository and name under and 4 boxes.chek all of them>close>reloade.Repeat this procedure with all repositories(Dapper Drake,security upgrades and something else witch I don´t remember).When you are finish you will be able to  download software.

---

### Post by Nicole on 2007-03-14
Hi zvacet,

Thanks for your reply. I've tried doing that, and the repositories are all checked - but when I try to install something, it just times out - it's sort of like synaptic/the update manager doesn't know I'm connected to the internet, whereas firefox, for instance, can tell that I am. 

When trying to install 3dchess, for eaxmple, through synaptic, it tries to download the files for ages, and then comes up with: 

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5+E-9ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5+E-9ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-11.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-11.1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

I'm really hoping there is some basic thing I'm missing that will let synaptic know how to connect to the internet, because otherwise, it does make Ubuntu more difficult to use.

Thanks again for your suggestion,

Nicole

---

### Post by Kay The Bantu on 2007-03-14
had the same issue could you please post your repo file? maybe i can help

---

### Post by Kay The Bantu on 2007-03-14
alternatively go to synaptic>preferences>network see if that'll help

cheers

---

### Post by zvacet on 2007-03-14
```
gksudo gedit etc/apt/sources.list
```
If any line looks like for example
#deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse
make it deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe 
save the fle and exit.After that 

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Nicole on 2007-03-16
Thanks zvacet - I'll try those now - apologies Kay, but I'm not a very computer literate person, (although I'm trying!); what's a repo file? the list of repositories I'm trying to access?

Thanks,

N

---

### Post by Nicole on 2007-03-16
zvacet, Kay,

The list of repository files I'm trying to access (the sources.list file zvacet suggested I check) reads:

> ####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


I've checked synaptic's network preferences - it says it ought to connect directly, as it should. It just doesn't seem to manage it...

Any advice/random guesses welcome!

Thanks,

N

---

### Post by zvacet on 2007-03-17
Source list looking good but try to see Software Preferences tool.Maybe there is problem,because it is one option wich allow you to download software but not to install it.Chek box witch say chek for updates automaticly.Alternativly you can try with this source list
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

---

### Post by zvacet on 2007-03-17
[http://ubuntuforums.org/showthread.php?p=2307886#post2307886]("http://ubuntuforums.org/showthread.php?p=2307886#post2307886")

---

