---
title: "Updateing fails"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by wdhpr on 2010-12-28
When I try to update using the update manager it fails.
If I try to fix the problem using the terminal I get the error shown below using the following cammand: [I]sudo apt-get autoremove -f (saw this solution from this forum)

What can I do with apt-get utility to correct this problem?[/I]


> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


---

### Post by Sef on 2010-12-28
> W: You may want to run apt-get update to correct these problems

Have you run that command: ```
sudo apt-get update
```?

---

### Post by wdhpr on 2010-12-28
> **Sef said:**
> Have you run that command: ```
sudo apt-get update
```?

Thanks for the quick reply
It still fails. It seems to stall when trying to connect with the following site:
[B]Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) maverick-updates/universe i386 Packages
  Unable to connect to cudlug.cudenver.edu:http:[/B]

I have Ubuntu 10.10 installed

Thank for the help

Wdhpr

---

### Post by wdhpr on 2010-12-28
I am still experiencing problems and I'm not sure if its me or the servers. My update manager says last update 9 days ago. I have tried to up date using the terminal using [COLOR=Blue]apt-get update[/COLOR] and it still fails with the following errors. Any help would be very appreciated

Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/maverick-(67.215.65.132]("http://cudlug.cudenver.edu/ubuntu/dists/maverick-%2867.215.65.132")). - connect (110: Connection timed out)
updates/Release.gpg  Could not connect to cudlug.cudenver.edu:80 Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to cudlug.cudenver.edu:http:
Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to cudlug.cudenver.edu:http:
Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to cudlug.cudenver.edu:http:
Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to cudlug.cudenver.edu:http:
Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to cudlug.cudenver.edu:http:
Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to cudlug.cudenver.edu:http:
Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to cudlug.cudenver.edu:http:
Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to cudlug.cudenver.edu:http:
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/main/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/restricted/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/universe/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/main/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/restricted/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/main/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/restricted/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/universe/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/universe/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/main/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/restricted/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/universe/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/main/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/universe/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/main/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/main/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/universe/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-updates/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://mirror.math.ucdavis.edu/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-security/main/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://ftp.unina.it/pub/linux/distributions/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  404  Not Found

---

### Post by davidmohammed on 2010-12-28
404 errors indicate that the mirror is down.  Suggest use a different mirror to download from in software-sources.

---

### Post by wdhpr on 2010-12-28
> **davidmohammed said:**
> 404 errors indicate that the mirror is down.  Suggest use a different mirror to download from in software-sources.

Thanks I tried many of the mirrors for the US. None that I tried seemed to work. Is it possible that the problem is with the servers themselves. Sorry if my questions sound simple but but this is the first time I have experienced this problem. Are update problems typical with Ubuntu? I just recently switched from Simply Mepis.

Thanks
Wdhpr

---

### Post by davidmohammed on 2010-12-28
maybe the holiday season?  Try an overseas such as the UK/Main server.  I presume internet connection in general is working OK?

---

### Post by wdhpr on 2010-12-28
I think I may have figured this out.
I installed Alurus a while back. I looked at the edit repository list and found duplicate entries that I then unchecked. I then checked fastest repositories and there was about a half dozen locations checked.  I unchecked those and picked two Locations here in the US. I went back and reloaded synaptic and everything went smoothly same applied to the update manager. I'm unsure how so many locations were selected for the repositories but it may have resulted from the various tweaks I made using the command line.

Cheers
Wdhpr

PS how do I mark this thread _[COLOR=Red]solved?[/COLOR]_

---

### Post by davidmohammed on 2010-12-29
well done - mark as solved (see my signature below)

---

