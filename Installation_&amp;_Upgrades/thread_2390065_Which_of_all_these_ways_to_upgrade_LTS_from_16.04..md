---
title: "Which of all these ways to upgrade LTS from 16.04.3 to 18.04?"
date: 2018-04-25
forum: Installation &amp; Upgrades
---

### Post by accounts0 on 2018-04-25
Long ago I installed 16.04.3 LTS from a server variant iso, then added kubuntu. After so much customizing, I'd prefer not to have to do a fresh install once 18.04 is released.

Some quick Googling leads me to more upgrade options than I was aware of previously. I have all these PPAs, & I'm not sure which method handles that best.

PPA's:
```
/etc/apt/sources.list.d/brandonsnider-ubuntu-cdrtools-xenial.list:deb http://ppa.launchpad.net/brandonsnider/cdrtools/ubuntu xenial main
/etc/apt/sources.list.d/git-core-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/git-core/ppa/ubuntu xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial main
/etc/apt/sources.list.d/skype-stable.list:deb [arch=amd64] https://repo.skype.com/deb stable main
/etc/apt/sources.list.d/slack.list:deb https://packagecloud.io/slacktechnologies/slack/debian/ jessie main
/etc/apt/sources.list.d/spideroakone.list:deb http://APT.spideroak.com/ubuntu-spideroak-hardy/ release restricted
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
/etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-updates-xenial.list:deb http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu xenial main
/etc/apt/sources.list.d/virtualbox-ppa.list:deb http://download.virtualbox.org/virtualbox/debian xenial contrib
/etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list:deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial main

```


So this is what I'm basing the timing of all this on:
[https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule](https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule)


For the server variant I found this, which looks easy enough, but has caveats* apparently:
[https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)
*[COLOR=#333333][FONT=Ubuntu]LTS systems are only automatically considered for an upgrade to the next LTS via [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]*do-release-upgrade*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] with the first point release. 


[/FONT][/COLOR]This is a recent, albeit non-official tutorial detailing a few methods:
[https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver](https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver)


Again, not sure which way would handle my PPA's, or if I should just do it manually- as is mentioned in the 'Debian Way' part of the aforementioned article.

---

### Post by deadflowr on 2018-04-25
update-manager and do-release-upgrade method disables ppa's and 3rd party repos. 
The debian way updates all sources to the new release codename including ppa's and 3rd party repos. 

For Ubuntu it is better to run it the update-manager/do-release-upgrade way.

Per ppa, you'll need to read the fine print usually of the ppa or 3rd party repository about how to go about dealing with them.
Some, like google-chrome,. can be disabled and then simply re-enabled.
And then some will require you purge them out with ppa-purge.

Case in point, you'll need to ppa-purge the x-swat ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates]("https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates")
> If you are upgrading from one release to another with this PPA activated, please install the ppa-purge package and use it to downgrade everything in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/updates will do it.

So you'll have to search for which can be disabled and which need more done.

---

### Post by monkeybrain20122 on 2018-04-25
Just do a fresh install.

---

### Post by Autodave on 2018-04-25
+1 with monkeybrain. I have never had any luck upgrading from one version to the next.

I once tried it on 13 machines: one worked, one was somewhat easy to fix, the other 11 all had to be redone.

---

