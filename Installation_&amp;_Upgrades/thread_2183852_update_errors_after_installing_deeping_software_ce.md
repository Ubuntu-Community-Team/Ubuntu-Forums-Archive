---
title: "update errors after installing deeping software center"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by wwwpuntoit on 2013-10-26
Hey guys,

as per title, after installing deeping software center my ubuntu 13.10 finds errors while trying to install  updates, it says not all updates can be installed and lets me choose from only partial update...
this happened to me on 12.04 lts too after installing deeping software centre, last time i had to install OS from scratch because i wasn't able to resolve the problem by myself this time i prefer to ask you guys what can be done to uninstall deeping software center and resolve the problems with updates

please get back if you have any suggestions

rgds

---

### Post by grahammechanical on 2013-10-26
How are you updating? Can you run this commands a post the error messages back here?

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

We need to know why is says not all updates can be installed. Of course you could try un-installing Deeping Software Center if you feel that application is causing this. Deeping might not yet be compatible with Ubuntu 13.10.

Regards.

Update: According to this Deeping is available for 13.10

[http://www.noobslab.com/2013/07/deepin-software-center-version-30-and.html](http://www.noobslab.com/2013/07/deepin-software-center-version-30-and.html)

---

### Post by wwwpuntoit on 2013-10-27
> **grahammechanical said:**
> How are you updating? Can you run this commands a post the error messages back here?

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

We need to know why is says not all updates can be installed. Of course you could try un-installing Deeping Software Center if you feel that application is causing this. Deeping might not yet be compatible with Ubuntu 13.10.

Regards.

Update: According to this Deeping is available for 13.10

[http://www.noobslab.com/2013/07/deepin-software-center-version-30-and.html](http://www.noobslab.com/2013/07/deepin-software-center-version-30-and.html)



hi mate,

i'm blaming deeping bacause it started to happen just after installation and because i remember it dd the same thinh on ubuntu 12.04 lts

here's the output of update command ,at least the final part where it gives errors :

**Fetched 15,7 kB in 22s (707 B/s)**
**W: GPG error: [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>**
**W: Failed to fetch [http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found**

**W: Failed to fetch [http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found**

**E: Some index files failed to download. They have been ignored, or old ones used instead.**


actually no error message wjen running upgrade command

---

### Post by wwwpuntoit on 2013-10-27
i've just restored my previous backup with clonezilla to resolve the problem, it was too frustrating
i don't know what messed up my system but any way i guess thread can be archived  as solved now.


thansk

---

### Post by oldos2er on 2013-10-27
The PPA you linked to doesn't have a repo for saucy (nor raring), so that's why the 404 errors are there. 

BADSIG errors can usually be fixed with ```
sudo -i

apt-get clean

cd /var/lib/apt

mv lists lists.old

mkdir -p lists/partial

apt-get clean

apt-get update
```

---

