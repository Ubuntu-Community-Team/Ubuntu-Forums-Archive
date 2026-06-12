---
title: "Edgy upgrade, dependency problems"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by PigCorpse on 2006-10-26
Hi

I followed the Edgy upgrade guide on [http://help.ubuntu.com](http://help.ubuntu.com). After I changed my sources.list and ran sudo aptitude dist-upgrade, it ended up having problems saying how some dependencies can't be resolved and proposed some sort of compromise with a score. Is there anything to worry about?

Thanks!

---

### Post by streeto on 2006-10-26
from [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

> If you want to upgrade from 6.06 LTS to 6.10, run the following command (either via ALT-F2 or a terminal):

gksu "update-manager -c"


This manages everything for you. Just done this a couple of hours ago.:cool:

Edit: corrected the URL

---

### Post by entropic_existence on 2006-10-26
I haven't been having much luck either with the upgrade. I run into dependency issues, etc. I'm using Kubuntu and so far none of the update methods have worked. I really, really, really don't want to do a fresh install. Took long enough to get everything pretty much configured how I wanted on dapper with various scientific packages, coding modules, etc.](*,)

---

### Post by sloggerkhan on 2006-10-26
On my computer the automatic upgrade also broke my install. I have an acer 4005 laptop. And when I tried using the new install disk to do a fresh install, it has a problem where it boots the gnome-ubuntu but it doesn't display on my laptop LCD. I think it might be defaulting to try and use my VGA out? Anyhow this seems like a major problem for an install disk that's supposed to be used by average users.

---

### Post by pielgrzym on 2006-10-26
Edgy destroyed also mine Ubunty. It's a totall flaw that such thing can happen so easy :(

---

### Post by Eman64 on 2006-10-26
When I try to install, it gives me a error and says that this
> COULD NOT DOWNLOAD ALL REPOSITORY INDEXES
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.bz2: Sub-process bzip2 returned an error code (2)
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.bz2: Sub-process bzip2 returned an error code (2)
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
```

Any clue why? Should I update my sources list or what?

---

### Post by Eman64 on 2006-10-26
Nevermind, I changed all of my sources to edgy and am currently updating.

---

### Post by dentoid88 on 2006-10-26
> **streeto said:**
> from [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)



This manages everything for you. Just done this a couple of hours ago.:cool:

Edit: corrected the URL

I am trying to run this without success.  First, the terminal outputs this:

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

Is this a problem?  Regardless, I can begin the 6.10 Distribution Upgrade, but the upgrade fails after the first stage when fetching is complete, with an error window saying:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz) Sub-process gzip returned an error code (1)

What is the problem?  I thought I don't have to modify sources.list using "gksu update-manager -c"

---

### Post by sloggerkhan on 2006-10-27
I've got mine working thanks to dpkg recongfigure all command, typed "dpkg reconfigure -a" I think. I'd look it up because I'm not sure that's it... Still, the CD doesn't work. 

**off topic**
And now I have Beryl working... it's pretty cool, but almost too many options, and no themes for scroll bars or the insides of windows.

update: themes for the inside of the windows are gtk2. I installed a utility to change them without having to go through the whole annoyance of the them preference cp.

---

### Post by streeto on 2006-10-27
> **dentoid88 said:**
> I am trying to run this without success.  First, the terminal outputs this:

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

Is this a problem?
Regardless, I can begin the 6.10 Distribution Upgrade, but the upgrade fails after the first stage when fetching is complete, with an error window saying:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz) Sub-process gzip returned an error code (1)

What is the problem?  I thought I don't have to modify sources.list using "gksu update-manager -c"

That warning in python happenned here too. It caused no problem, AFAIK.

About the error downloading Sources.gz, have you tried upgrading again? Maybe the download just failed --bad network or something.

---

### Post by dentoid88 on 2006-10-27
> **streeto said:**
> That warning in python happenned here too. It caused no problem, AFAIK.

About the error downloading Sources.gz, have you tried upgrading again? Maybe the download just failed --bad network or something.

That's good news about the python warning, of course no warning would be the best of all...

I haven't tried upgrading again, after reading Edgy upgrade horror stories I may do a clean install from the alternate CD.  I had just installed 6.06, so I don't need to reconfigure much other than my xorg.conf file.  And I purposely partitioned / for this kind of stuff.

---

