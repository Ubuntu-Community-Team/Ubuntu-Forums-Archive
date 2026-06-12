---
title: "upgrade from 18.10 to 19.04 does not work, tried everything"
date: 2019-08-17
forum: Installation &amp; Upgrades
---

### Post by rpra006 on 2019-08-17
Hi there,
I have now tried most of the commands to force upgrade from kubuntu 18.10 to 19.04 but this is not happening.
Here is what i have done so far:

```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.10
Release:        18.10
Codename:       cosmic

```

```
sudo do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

Please install all available updates for your release before upgrading. 
```

```
sudo apt-get update
Hit:1 http://nz.archive.ubuntu.com/ubuntu cosmic InRelease
Hit:2 http://nz.archive.ubuntu.com/ubuntu cosmic-updates InRelease
Hit:3 http://nz.archive.ubuntu.com/ubuntu cosmic-backports InRelease
Hit:4 http://nz.archive.ubuntu.com/ubuntu cosmic-security InRelease                                                                           
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                  
Hit:6 http://dl.google.com/linux/chrome/deb stable Release
Reading package lists... Done

```

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libfreetype6
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```


```
sudo apt-get update && sudo apt-get dist-upgrade
Hit:1 http://nz.archive.ubuntu.com/ubuntu cosmic InRelease
Hit:2 http://nz.archive.ubuntu.com/ubuntu cosmic-updates InRelease
Hit:3 http://nz.archive.ubuntu.com/ubuntu cosmic-backports InRelease
Hit:4 http://nz.archive.ubuntu.com/ubuntu cosmic-security InRelease
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:6 http://dl.google.com/linux/chrome/deb stable Release
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libfreetype6
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

```
at /etc/update-manager/release-upgrades
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting and upgrade behavior, valid options:
#
#  never  - Never check for, or allow upgrading to, a new release.
#  normal - Check to see if a new release is available.  If more than one new                                                                 
#           release is found, the release upgrader will attempt to upgrade to                                                                 
#           the supported release that immediately succeeds the
#           currently-running release.
#  lts    - Check to see if a new LTS release is available.  The upgrader                                                                     
#           will attempt to upgrade to the first LTS release available after                                                                  
#           the currently-running one.  Note that if this option is used and                                                                  
#           the currently-running release is not itself an LTS release the                                                                    
#           upgrader will assume prompt was meant to be normal.
Prompt=normal
```

Any other suggestions on how can i progress this. Also the GUI discover package manager does not discover that there is a new version and offer the upgrade.

---

### Post by Irihapeti on 2019-08-17
Because 18.10 isn't supported any more, you need to use the procedure for old releases. See [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Your other option, and the one I'd take if it were me, is to backup your personal files and do a clean install of 19.04.

---

### Post by guiverc on 2019-08-17
Have you done what the first message suggested?  ie. install all updates. (`sudo apt update; sudo apt full-upgrade` without errors?)  

My own mirror (in AU) still has cosmic sources available so you shouldn't need to change /archives/old-releases/ yet; but this may not apply to all archive mirrors.  (they can be dropped anytime after EOL)

---

### Post by Irihapeti on 2019-08-17
If the Australian mirrors are still carrying the Cosmic sources, you could try changing to those and seeing if that helps.

I see also (I missed it earlier) that you have a Google repository. I'd suggest disabling that during the upgrade process.

---

### Post by guiverc on 2019-08-17
Sorry I wasn't very specific (with *my mirror*), I'm using [https://launchpad.net/ubuntu/+mirror/ftp.iinet.net.au-archive](https://launchpad.net/ubuntu/+mirror/ftp.iinet.net.au-archive)  (my ISP's mirror rather than the au.archive.ubuntu.com), but I also see it in [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/) who provide the au.archive.ubuntu.com so changing nz to au should work.

---

### Post by Impavidus on 2019-08-18
The apt-get update output shows "Hit", not "Error", so it appears that the nz.archive.ubuntu.com mirror has cosmic still available too. The problem is that the package libfreetype6 is held back. Why?```
apt policy libfreetype6
```

---

### Post by rsteinmetz70112 on 2019-08-19
Have you tried to install that package individually?
```
sudo apt install libfreetype
```
or dot a full-upgrade?
```
sudo apt full-upgrade
```

---

