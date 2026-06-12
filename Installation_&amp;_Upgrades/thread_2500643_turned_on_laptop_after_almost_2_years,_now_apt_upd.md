---
title: "turned on laptop after almost 2 years, now apt update won't work."
date: 2024-09-07
forum: Installation &amp; Upgrades
---

### Post by dwater on 2024-09-07
Yeah, apt update and the gui also fails:

```

$ sudo apt update
Ign:1 http://archive.ubuntu.com/ubuntu kinetic InRelease
Ign:2 http://archive.ubuntu.com/ubuntu kinetic-updates InRelease
Ign:3 http://archive.ubuntu.com/ubuntu kinetic-backports InRelease    
Ign:4 http://archive.ubuntu.com/ubuntu kinetic-security InRelease     
Err:5 http://archive.ubuntu.com/ubuntu kinetic Release
  404  Not Found [IP: 185.125.190.81 80]
Hit:6 https://dl.google.com/linux/chrome/deb stable InRelease
Err:7 http://archive.ubuntu.com/ubuntu kinetic-updates Release
  404  Not Found [IP: 185.125.190.81 80]
Err:8 http://archive.ubuntu.com/ubuntu kinetic-backports Release
  404  Not Found [IP: 185.125.190.81 80]
Err:9 http://archive.ubuntu.com/ubuntu kinetic-security Release
  404  Not Found [IP: 185.125.190.81 80]
Reading package lists... Done
E: The repository 'http://archive.ubuntu.com/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu kinetic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu kinetic-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu kinetic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

IIRC, the installation is a pretty clean one - ie I've not used it much.

```
DISTRIB_ID=UbuntuDISTRIB_RELEASE=22.10
DISTRIB_CODENAME=kinetic
DISTRIB_DESCRIPTION="Ubuntu 22.10"

```

Any pointers how to get apt working again?

---

### Post by deadflowr on 2024-09-07
Either switch the sources and upgrade or reinstall a newer release.
22.10 is long gone now.
What you'd need to do to switch sources: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Since 22.10 only upgraded to 23.04 and 23.04 only upgraded to 23.10, you've got a lot of work and possible points of failure to deal with if going that route.
Easier to just grab a new version and install it fresh.

---

### Post by ubfan1 on 2024-09-07
22.10 is long end of life (9 months total), so search this site and askubuntu for upgrade EOL system or some such.  A reinstall of 22.04 or 24.04 would probably be easier. Better backup anything you want, sometimes an offer is made to reinstall over existing, but in your case, that existing is so old, that might not be a good idea.

---

### Post by dwater on 2024-09-08
Thanks for the answers. I don't think I'll bother changing it and I'll leave it as 22.10 - I don't have a backup system and I can't risk not having one working. I'll wait until I have another system.

---

### Post by yancek on 2024-09-08
For future use, remember that it is the releases in even years and in April which are LTS giving you 5 years of updates.  Had you installed 22.04, you would still have several years of updates avaialble.

---

