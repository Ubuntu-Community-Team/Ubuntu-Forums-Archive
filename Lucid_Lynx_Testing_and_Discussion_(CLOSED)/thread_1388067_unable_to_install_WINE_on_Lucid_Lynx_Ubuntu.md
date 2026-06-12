---
title: "unable to install WINE on Lucid Lynx Ubuntu"
date: 2010-01-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Hulabear263 on 2010-01-22
Howdy!  Upgraded to Lucid Lynx from Karmic Koala today; seems to be mostly OK, but
I have not been able to install WINE.  When I attempt to do so, I get these messages:

installArchives() failed: Selecting previously deselected package ttf-symbol-replacement. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 138122 files and directories currently installed.) 
Unpacking ttf-symbol-replacement (from .../ttf-symbol-replacement_1.1.36-0ubuntu2_all.deb) ... 
Selecting previously deselected package ttf-tahoma-replacement. 
Unpacking ttf-tahoma-replacement (from .../ttf-tahoma-replacement_1.1.36-0ubuntu2_all.deb) ... 
Selecting previously deselected package libmpg123-0. 
Unpacking libmpg123-0 (from .../libmpg123-0_1.10.0-2ubuntu1_i386.deb) ... 
Selecting previously deselected package wine1.2. 
Unpacking wine1.2 (from .../wine1.2_1.1.36-0ubuntu2_i386.deb) ... 
Selecting previously deselected package wine1.2-gecko. 
Unpacking wine1.2-gecko (from .../wine1.2-gecko_1.0.0-0ubuntu3_i386.deb) ... 
Selecting previously deselected package winbind. 
Unpacking winbind (from .../winbind_2%3a3.4.3-2ubuntu2_i386.deb) ... 
Processing triggers for fontconfig ... 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for desktop-file-utils ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for python-support ... 
Setting up ttf-symbol-replacement (1.1.36-0ubuntu2) ... 
Setting up ttf-tahoma-replacement (1.1.36-0ubuntu2) ... 
Setting up libmpg123-0 (1.10.0-2ubuntu1) ... 
 
Setting up wine1.2 (1.1.36-0ubuntu2) ... 
dpkg: error processing wine1.2 (--configure): 
 subprocess installed post-installation script returned error exit status 10 
Setting up wine1.2-gecko (1.0.0-0ubuntu3) ... 
Setting up winbind (2:3.4.3-2ubuntu2) ... 
 * Starting the Winbind daemon winbind 
   ...done. 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 wine1.2 


What am I doing wrong?  Thanks!

---

### Post by tghe-retford on 2010-01-22
I have exactly the same problem when updating from the Ubuntu Wine PPA. Sounds like a bug with the package, not the first time, had a similar problem with an updated KMPlayer package doing this when I was testing Karmic.

---

### Post by inportb on 2010-01-22
Heh, I got that message while upgrading, which scared the crap out of me until I found that my laptop was fine after rebooting.

---

### Post by KrazyPenguin on 2010-01-22
There is a partial upgrade today, where wine is held back.
So ya, don't upgrade yet like the following people have, or else you may not be able to use WINE.

---

### Post by tghe-retford on 2010-01-22
> **KrazyPenguin said:**
> So ya, don't upgrade yet like the following people have, or else you may not be able to use WINE.
I have been able to continue upgrading and use Wine whilst the package failed to install. By the way, just did another update now and the package updated fine.

---

### Post by KrazyPenguin on 2010-01-23
> **tghe-retford said:**
> I have been able to continue upgrading and use Wine whilst the package failed to install. By the way, just did another update now and the package updated fine.

Ya that's good.  Sometimes the dependencies are not there, so that is why it is a partial upgrade.  So that is why programs break at times during the development phase.

I also noticed nothing was to be removed, but still held off because you just don't know what will happen.

Anyway, everything is fine now like the previous poster says.

;-)

---

### Post by inportb on 2010-01-23
Indeed, wine1.2 is all good now.

---

### Post by d3v1150m471c on 2010-01-23
I only update the security patches. Strongly recommend that for windows dual-booters on the ms os's.

---

### Post by Hulabear263 on 2010-01-23
WINE seems to be OK now.  Thanks everyone!  All updates are installing fine.

---

### Post by moviemaniac on 2010-01-23
I noticed one weird thing yesterday:

I've had problems running a few of my apps in wine (64 bit here) that ran just fine previously on 32bit Karmic. One example would be DVD Profiler.

Yesterday when I had installed the broken update all of these apps worked(!!!). Today the new Wine-version fixed the error on installing but the previously failing apps fail to start again, producing segfaults and whatnot else. Very weird.

---

### Post by dino99 on 2010-01-24
time to install 1.1.37

---

### Post by Allwynd on 2010-03-19
i upgraded from karmic to lucid with
```
update-manager -d
``` and i saw that there is a new version of wine - 1.1.41, but i cant update 
i currently have 1.1.40 and when i add the repository
```
ppa:ubuntu-wine/ppa
```
(i believe that is the repository i need)
it says:
```
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```
is there a way to update to 1.1.41?
i tried to search for a .deb package or a tarball with the source code that i could probably compile, but with no luck.. i guess i have to stick with my current 1.1.40 and wait for 29th of April, when 10.04 is officially out and probably wine will be supporting it from the start ^_^

---

### Post by aviramof on 2010-03-21
you can find it in synaptic.

---

