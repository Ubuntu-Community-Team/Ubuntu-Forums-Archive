---
title: "earlier apt-get was working now apt-get update or install is not working"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by mrityunjay23 on 2015-07-16
My Settings for ubuntu 12.04:
Synaptic package manager->Setting ->Repositories->ubuntu software center->Download from->Main server
> ~/.bash rc contains 
                                                         export tag ttp_proxy=http://<usernam>:<password>@<proxy ip>:<port>
export http_proxy                      

     
 
/etc/apt/apt.conf contains follwing 
                                                         Acquire::http:razz:roxy "http://<proxy ip>:<port>/";
Acquire::https:razz:roxy "https://<proxy ip>:<port>/";                      

     
 
out put of 
cat /etc/apt/sources.list
> # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise universe
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security main restricted
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security universe
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise main universe restricted multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise universe main multiverse restricted #Added by software-properties



I have also tried these commands
> sudo rm -rvf /var/lib/apt/lists/; apt-get update
sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
grep -E 'archive.ubuntu.com|security.ubuntu.com' /etc/apt/sources.list.d/*

Internet in my pc is working which is behind proxy.


But till now this problem has not resolved.

---

### Post by QIII on 2015-07-16
Hello!

It would be helpful if you would post the results of issuing 

```
sudo apt-get update
```

and 

```
sudo apt-get install whatever
```

---

### Post by grahammechanical on 2015-07-16
Ubuntu 12.04 (precise) is not yet an old release. Therefore, there will not be any archives for precise (12.04) in the old-releases repository. Having sources list files pointing to the URL of a repository that does not exist will cause problems with updating.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by v3.xx on 2015-07-16
> **grahammechanical said:**
> Ubuntu 12.04 (precise) is not yet an old release. Therefore, there will not be any archives for precise (12.04) in the old-releases repository. Having sources list files pointing to the URL of a repository that does not exist will cause problems with updating.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Maybe you updated from some older (non supported) version and this is the result.

---

### Post by deadflowr on 2015-07-16
Closed
You already have an existing thread on this here:
[http://ubuntuforums.org/showthread.php?t=2285109](http://ubuntuforums.org/showthread.php?t=2285109)

Please do not post duplicate threads.

---

