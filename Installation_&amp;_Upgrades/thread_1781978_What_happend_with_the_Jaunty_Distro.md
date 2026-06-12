---
title: "What happend with the Jaunty Distro?"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by eaonflux on 2011-06-14
I am running several vps with ubuntu jaunty, but last 2 weeks i cant update anymore with apt-get.

So i checked what the problem was and see that jaunty is removed from [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

Why?????

I cant update, packages are broken now.

Can anyone help me to fix this.

i tried to update to a newer distro but i can't because it needs some files from Jaunty.
This time Ubuntu really ****** up, really  frustrating.

error msg apt-get:
```
Ign http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty-updates Release.gpg
Ign http://archive.ubuntu.com jaunty-security Release.gpg
Ign http://archive.ubuntu.com jaunty Release
Ign http://archive.ubuntu.com jaunty-updates Release
Ign http://archive.ubuntu.com jaunty-security Release
Ign http://archive.ubuntu.com jaunty/main Packages
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Ign http://archive.ubuntu.com jaunty/main Packages
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Err http://archive.ubuntu.com jaunty/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://archive.ubuntu.com jaunty/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://archive.ubuntu.com jaunty/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://archive.ubuntu.com jaunty-updates/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://archive.ubuntu.com jaunty-updates/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://archive.ubuntu.com jaunty-updates/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://archive.ubuntu.com jaunty-security/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://archive.ubuntu.com jaunty-security/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://archive.ubuntu.com jaunty-security/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Reading package lists... Done

```

---

### Post by mörgæs on 2011-06-14
Wouldn't it be better to do a fresh install of one of the supported releases? 

If you manage to find a repository, you will still not have an updated system, since not all important bug fixes are backported.

---

### Post by amauk on 2011-06-14
Jaunty is end-of-life

See this for details on how to upgrade EOL versions
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Basically, in /etc/apt/sources.lst, change
[http://archive.ubuntu.com](http://archive.ubuntu.com)
to
[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)
then dist-upgrade up to a supported version

On a server, it's best to stick to LTS releases, as they're supported for 5 years (so, upgrade to Lucid)

---

### Post by eaonflux on 2011-06-14
AH thanks for your quick response.

Crap reinstalling, is there no other way to update it to a supported version?

Dirty fix something like that?

---

### Post by eaonflux on 2011-06-14
oh sorry you just explained it how to do it, sorry i will get to it and try ;)

---

### Post by eaonflux on 2011-06-14
Uhm i tried this:
## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-proposed main restricted universe multiverseYou can make use of -backports, -proposed repositories if you want. For more information about repositories see [Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu"). 

[LIST]
[*]Update the package list and upgrade all the installed packages 
[/LIST]

sudo aptitude update && sudo aptitude safe-upgrade
[LIST]
[*]Perform the release upgrade. 
[/LIST]

sudo do-release-upgrade

but i get this error msg:
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg'
tar: Removing leading `/' from member names
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.

Reading cache

Checking package manager

Can not upgrade

An upgrade from 'jaunty' to 'lucid' is not supported with this tool.


funny is this because this tutorial is for to upgrade from Jaunty to Karmic

---

### Post by coffeecat on 2011-06-14
> **eaonflux said:**
> An upgrade from 'jaunty' to 'lucid' is not supported with this tool.


funny is this because this tutorial is for to upgrade from Jaunty to Karmic

That's probably because Karmic passed end-of-life in April and the community pages haven't been updated yet.

HEALTH WARNING: I really don't know whether this will work, and it might even bring in problems, but this is what I would try.

1 - Hand edit your sources.list so that all lines are "http://old-releases.ubuntu.com/ubuntu/ jaunty....". Then 'sudo apt-get update' and 'sudo apt-get upgrade' to bring everything up to date. It looks as though you have done that already.

2 - Now hand edit your sources.list again but this time replace every instance of "jaunty" with "karmic" (still keeping the old-releases.ubuntu.com bit). Run 'sudo apt-get update' and 'sudo apt-get upgrade' again. This will, in theory, upgrade your Jaunty system to a working Karmic. Hopefully, after this  you'll be able to upgrade to Lucid without hindrance.

I'm sure you have, but check that all 3rd-party repositories have been disabled before you try upgrading from one release to the next. My guess is that the presence of 3rd-party repos and their packages is probably the commonest cause of the failed upgrades you see reported in the forums.

---

### Post by mastablasta on 2011-06-14
Jaunty is not an LTS so you would first have to upgrade to 9.10 and then to 10.04. But the problem is that 9.10 support has also been dropped now.
 
reinstalls eems a much simpler way to do the "upgrade" in this case.

---

### Post by eaonflux on 2011-06-14
lol,

I am backupping all mine data from those vps that are running on jaunty and hope that mine provider has updated templates of this.

Just mine luck :popcorn:

---

### Post by eaonflux on 2011-06-14
thanks for your replies

---

### Post by eaonflux on 2011-06-14
oh, 

i said i mine first post that:
This time Ubuntu really ****** up, really  frustrating.

well i ****** up and NOT ubuntu. its only fair to admit that :KS

---

### Post by mörgæs on 2011-06-14
:-) 

Learning is no shame. Welcome to the fora.

---

