---
title: "Unable to install or update anything in 12.04"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by eiresans on 2013-07-08
Hi, recently I ran into a problem which seemed pretty similar to what's described in this post:

  [URL="http://askubuntu.com/questions/85641/how-do-i-deal-with-unauthenticated-sources-errors-in-the-software-center"]How do I deal with "unauthenticated sources" errors in the Software Center?
[/URL]

  I was receiving this error message anyway-
  ```

Requires installation of untrusted packages: The action would require the installation of packages from not authenticated sources.   I had tried to download installations and updates from a variety of  different sources, but all returned the same message. Likewise sudo apt-get update/upgrade/install failed. So I tried what was suggested in the above post:
  
sudo apt-get clean cd /var/lib/apt sudo mv lists lists.old sudo mkdir -p lists/partial sudo apt-get clean sudo apt-get update   But then when I open software center the install button has disappeared, not greyed out, totally missing.
  From terminal, if I try to install anything, it returns
  
Reading package lists... Done Building dependency tree        Reading state information... Done E: Unable to locate package    Update returns:
  
W: Failed to fetch [http://ftp.heanet.ie/pub/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://ftp.heanet.ie/pub/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Unable to connect to 213.94.177.16:80:  E: Some index files failed to download. They have been ignored, or old ones used instead.   This maybe an awful noob statement, but that IP address stays the  same no matter what server I direct update manager to download from.
  Finally, upgrade, for what it's worth, returns:
  
Reading package lists... Done Building dependency tree        Reading state information... Done 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.   I also uninstalled Ubuntu software, hoping against hope that somehow  I'd get it reinstalled and somehow that would fix everything.

Further information that might be helpful to anyone in proposing a solution includes my /etc/apt/sources.list.d folder being completely empty. I've now also attempted to edit my sources.list file according to the suggestions on this page: [http://ubuntuforums.org/showthread.php?t=1642254](http://ubuntuforums.org/showthread.php?t=1642254), but it hasn't fixedthe problem. My /etc/apt/sources.list file presently looks like this:

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) precise main # disabled on upgrade to precise

``````


Originally it had looked like this:

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main universe restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main universe restricted multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

```



  I'm a bit out of my depth here and would very much appreciate any  help anyone can give me. I really hope there is some way to fix this  problem without reinstalling the OS.

---

### Post by fantab on 2013-07-08
Post the output of:
```
sudo apt-get upgrade
```

and use the code tags to wrap the text. Use '#' in the editor to do so. It makes easier to read large chunks of text.

---

### Post by eiresans on 2013-07-09
Hi, 

the output of sudo apt-get upgrade is 

#Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.#

---

### Post by grahammechanical on 2013-07-09
> **eiresans said:**
> Hi, 

the output of sudo apt-get upgrade is 

#Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.#

Then your system is up to date. No error messages? Do you still think you have a problem? In the printout of the contents of your sources lists file all the lines marked ## are comments. If you remove them (in your imagination) then you will see that the contents of new sources lists file matches quiet well the contents of the old sources lists file.

If you go to System Settings>Software Sources I think that you will find that you have ticks for the repositories on the Ubuntu Software tab and ticks for some of the repositories in the Other Software tab.

Oh, I am on 13.04 and my sources.list.d folder is also empty. I do not think that is a problem.

You might want to have a look through this

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/707392](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/707392)

It seems, in regard to the original issue, that when Update Manager fails to give an option to continue with the installation of untrusted packages then use the terminal to update & upgrade and we get an option to accept the untrusted packages.

Regards.

---

