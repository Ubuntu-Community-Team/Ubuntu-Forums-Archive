---
title: "Upgrading from Dapper to Hardy"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by aecrim on 2008-07-01
Hi Guys,

In the middle of the updating from Dapper to Hardy one package could not be installed and all the upgrade failed. The package that failed to install is xfonts-scalable. The error is 

Errors were enoucntered while processing xfonts-scalable
e: subprocess /usr/bin/dpkg returned error code (1)
A package failed to install. Trying to recover:
Setting up xfonts-scalable ...
usage error: unrecognized option
Usager update-fonts-dir DIRECTORY ...
[...]

When i said that i am in the middle of the updating i meant that i
1. aptitude updated && upgrade && upgrade-dist && autoclean
2. %s/dapper/hardy/g in /etc/apt/sources.list
3. aptitude update && upgrade && upgrade-dist

after the first time the update process failed, i tried to install the

  sudo aptitude install update-manager-core

which fails in the same way as the previous approach

Anybody has any idea what can I do now?

Thanks,
Mircea

---

### Post by aecrim on 2008-07-01
Ah and I forgot to mention, the fonts in the gnome environment are messed up and all the letters are squares :(

---

### Post by IcarusR on 2008-07-01
Hi, I believe you can not upgrade from Dapper to Hardy. 
Have to go Dapper > Edgy > Fiesty > Gutsy > Hardy.
Probably better to backup everything & do a fresh install of Hardy.

---

### Post by avtolle on 2008-07-01
[http://www.ubuntu.com/getubuntu/upgrading#head-db224ea9add28760e373240f8239afb9b817f197](http://www.ubuntu.com/getubuntu/upgrading#head-db224ea9add28760e373240f8239afb9b817f197) is the recommended way to upgrade from 6.06 LTS to 8.04 LTS. It may not work now, however, but you could give it a try. Otherwise, I think your most efficient way would be to do a clean install of 8.04.

---

### Post by talen.quickblade on 2009-01-12
While backing everything up and reinstalling is a great idea for desktop systems... Its not so great for corporate production environments (like the mail server our company is running). Here is documentation showing the 6.06 --> 8.04 upgrade path. Additionally, there is EVERY reason to expect that the previous LTS release is totally upgradeable to the most current LTS release (anything in between is a dice shoot).  Though I would hope I dont have to make the following statement, I will anyhow: Make sure you READ all the instructions before you even begin clicking or typing.

[http://www.ubuntu.com/getubuntu/upgrading-8.04](http://www.ubuntu.com/getubuntu/upgrading-8.04)

---

### Post by Kanga on 2009-01-12
I re-installed dapper from live cd, downloaded all updates, then upgraded to Hardy.
I did not have a cd of Hardy, and thought it could be faster this way.
Took a couple of hours though.

---

### Post by crimsun on 2009-01-29
> **aecrim said:**
> Hi Guys,

In the middle of the updating from Dapper to Hardy one package could not be installed and all the upgrade failed. The package that failed to install is xfonts-scalable. The error is 

Errors were enoucntered while processing xfonts-scalable
e: subprocess /usr/bin/dpkg returned error code (1)
A package failed to install. Trying to recover:
Setting up xfonts-scalable ...
usage error: unrecognized option
Usager update-fonts-dir DIRECTORY ...
[...]

When i said that i am in the middle of the updating i meant that i
1. aptitude updated && upgrade && upgrade-dist && autoclean
2. %s/dapper/hardy/g in /etc/apt/sources.list
3. aptitude update && upgrade && upgrade-dist

after the first time the update process failed, i tried to install the

  sudo aptitude install update-manager-core

which fails in the same way as the previous approach

Anybody has any idea what can I do now?

Thanks,
Mircea

This symptom is caused by [https://bugs.launchpad.net/ubuntu/+source/xfonts-scalable/+bug/107687](https://bugs.launchpad.net/ubuntu/+source/xfonts-scalable/+bug/107687)

---

