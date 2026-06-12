---
title: "failed update: N: See apt-secure(8) manpage for repository creation and user configur"
date: 2020-02-21
forum: Installation &amp; Upgrades
---

### Post by emians on 2020-02-21
Hi,

here is my log,

any idea?

thanks for the attention.

[HTML]~$ sudo apt-get update 
Ign:1 http://it.archive.ubuntu.com/ubuntu cosmic InRelease
Ign:2 http://it.archive.ubuntu.com/ubuntu cosmic-updates InRelease
Ign:3 http://it.archive.ubuntu.com/ubuntu cosmic-backports InRelease
Err:4 http://it.archive.ubuntu.com/ubuntu cosmic Release
  404  Not Found [IP: 90.147.160.72 80]
Err:5 http://it.archive.ubuntu.com/ubuntu cosmic-updates Release
  404  Not Found [IP: 90.147.160.72 80]
Err:6 http://it.archive.ubuntu.com/ubuntu cosmic-backports Release
  404  Not Found [IP: 90.147.160.72 80]
Ign:7 http://security.ubuntu.com/ubuntu cosmic-security InRelease
Err:8 http://security.ubuntu.com/ubuntu cosmic-security Release
  404  Not Found [IP: 91.189.91.24 80]
Reading package lists... Done
E: The repository 'http://it.archive.ubuntu.com/ubuntu cosmic Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://it.archive.ubuntu.com/ubuntu cosmic-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://it.archive.ubuntu.com/ubuntu cosmic-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu cosmic-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
~$
[/HTML]

---

### Post by deadflowr on 2020-02-21
cosmic, Ubuntu 18.10, is out of service and no longer available.
You need to upgrade to a supported release.

By upgrade I mean you should install a fresh release like 19.10 or 18.04.
You can try an EOLUpgrade, but you'd only be moving to 19.04 which is also end of life.
more on EOLUpgrades: [https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by emians on 2020-02-22
Thanks, but I think the update did not execute maybe because of some settings,

Could you have a look at this:

[ATTACH=CONFIG]285068[/ATTACH]

---

### Post by emians on 2020-02-22
Anyway, it connects with the download upgrade helper now, but ask me to do a fresh install of the system it seems...

---

### Post by coffeecat on 2020-02-22
> **emians said:**
> Thanks, but I think the update did not execute maybe because of some settings,

Could you have a look at this:

[ATTACH=CONFIG]285068[/ATTACH]

The reason for the update failing to work is nothing to do with settings. It is because of what deadflowr has already explained - Ubuntu 18.10 (Cosmic) has been out of support for well over a year now. The repositories are closed. You cannot update it. It is finished, obsolete, dead. It is theoretically possible to upgrade to a supported version following the details in the link deadflowr provided, but you would have to upgrade first to 19.04 which is also end of life, and then upgrade to 19.10. That is not a route I would take in your situation - the possibility of failure is too high. There is only one sane course of action, in my opinion: backup your personal data, and make a fresh install of a supported release.

18.04, although released before 18.10, is a long-term support version (LTS) which has standard support until April 2023. 19.10 is an interim release with only 9 months of support, until July this year.

---

### Post by emians on 2020-02-22
Thanks for clarifying this. I'd rather go with an upgrade to 19.04  and see, since I have to backup anyway. 

Or, 

how to downgrade to 18.04 then?

---

### Post by deadflowr on 2020-02-22
Going backwards from a release like 18.10 to 18.04 requires a fresh clean installation of the older distribution.
(18.04 being the older distribution in this case)

---

