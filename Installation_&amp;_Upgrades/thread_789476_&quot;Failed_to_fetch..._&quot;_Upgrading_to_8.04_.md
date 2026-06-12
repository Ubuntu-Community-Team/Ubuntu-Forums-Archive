---
title: "&quot;Failed to fetch... &quot; Upgrading to 8.04 from 7.10"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by EmilyRose on 2008-05-10
Hi there, I'm trying to upgrade to 8.04 from 7.10 and am getting this error message: 

Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release](http://archive.canonical.com/ubuntu/dists/hardy/Release) Unable to find expected entry  commercial/binary-i386/Packages in Meta-index file (malformed Release file?)

My connection is great. I've tried several times and always get this message... how do I fix this? I really want to upgrade!!

---

### Post by Pumalite on 2008-05-10
System>Administration>Software Sources>Download From>Other>Let it choose the best for you.

---

### Post by EmilyRose on 2008-05-10
Ok, I switched to main servers and it now seems to be working, lots of thanks!!

---

### Post by Pumalite on 2008-05-10
I would absolutely double check the connection.
Post:
cat /etc/apt/sources.list

---

### Post by EdWh on 2008-05-10
Hi Pumalite
From- EdWh

I am having the exact same problem, the program fails to connect with the upgrade server and I tried your suggestion with no improvement.  :confused:

My program returns as "Failed to fetch" [http://archive.Ubuntu.com/ubuntu/dists/gutsy=security/release](http://archive.Ubuntu.com/ubuntu/dists/gutsy=security/release).  Multiverse.deb/source/sources. Meta-index file )malformed realease file.   

I can upgrade with cd but lose some third party installed program, Need help.  Thanks.

---

### Post by Pumalite on 2008-05-10
There are only two possible reasons to get that message: Server or connection. Try Main or US Servers.

---

### Post by EdWh on 2008-05-10
Hi Pumalite
No results here.  See cat return.## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://debian.charite.de/ubuntu/](http://debian.charite.de/ubuntu/) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://debian.charite.de/ubuntu/](http://debian.charite.de/ubuntu/) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://debian.charite.de/ubuntu/](http://debian.charite.de/ubuntu/) gutsy-security multiversedeb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

ed@ed-desktop:~$                                                        :confused:

---

### Post by EdWh on 2008-05-10
:confused:Hi Pumalite

I still need help, just sent you reply to cat request and I have tried the main and U.S. servers with no results.  I really need to do a Internet upgrade and thanks. Ed.

---

### Post by Pumalite on 2008-05-10
What about some other European Server?

---

### Post by EdWh on 2008-05-10
Nothing seems to work, according to search for others, 178 servers were pinged and it stopped on a European server but still would not upgrade. Any other suggestions????   Ed.:confused:

---

### Post by EdWh on 2008-05-10
Hi Pumalite
From. EdWh

Have to go out for about a hour or so, will check back and repost if necessary.  Thanks for help so far.   Ed.:confused:

---

### Post by forestpixie on 2008-05-10
> **EdWh said:**
> Hi Pumalite
No results here.  See cat return.## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://debian.charite.de/ubuntu/](http://debian.charite.de/ubuntu/) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://debian.charite.de/ubuntu/](http://debian.charite.de/ubuntu/) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://debian.charite.de/ubuntu/](http://debian.charite.de/ubuntu/) gutsy-security multiversedeb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

ed@ed-desktop:~$                                                        :confused:

You need to edit the file I think - you have mixed repos which I'm not sure about - but this line
```

deb-src http://debian.charite.de/ubuntu/ gutsy-security multiversedeb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy
``` needs to at least have the 

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy
```

removed from it's end - either use gedit or nano to edit it

```
gksudo gedit /etc/apt/sources.list
sudo nano /etc/apt/sources.list
```

---

