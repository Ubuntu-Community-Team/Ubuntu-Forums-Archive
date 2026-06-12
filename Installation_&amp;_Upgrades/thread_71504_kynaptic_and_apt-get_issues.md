---
title: "kynaptic and apt-get issues"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by wspgeek on 2005-10-03
Ok quick disclaimer.......I am a bit of a noob...

I've got a fresh installation of Hoary 5.04 (KDE) on a desktop here at the office.  Due to some network restrictions kynaptic was unable to verify the two update sources forcing me to manually uncomment them in /etc/apt/sources.list.  I reloaded kynaptic and was able to refresh the DB and run a upgrade.  But for some reason I'm not able to download/install many extras, i.e. Firefox, Thunderbird, and their dependencies.

Just for comparison I went to the CLI and ran ```
sudo apt-get install mozilla-firefox
```  It kicked back with a list of dependencies it needed, all various libraries, but they were "not installable".

Within kynaptic all of the packages are listed, but on the affected ones I can't select "install".

Any thoughts?

---

### Post by Zelut on 2005-10-03
Well if you've commented/uncommented some of the sources in your sources.list it may not be able to find packages that it needs.  I know, from time to time, there are connection issues with the repositories.  It may have been a temporary issue and you might want to try again.  Make sure you've got your complete list of repositories available (and add additional from the [www.ubuntuguide.org](www.ubuntuguide.org)) to have access to everything you need to install.

---

