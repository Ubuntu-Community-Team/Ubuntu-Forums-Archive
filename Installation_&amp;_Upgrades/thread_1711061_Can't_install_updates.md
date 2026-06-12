---
title: "Can't install updates"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by frikinsweet on 2011-03-20
Every time i try to run update manager i get an error saying
 'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
i've also been getting an error while trying to open Synaptic Package Manager saying
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
Any help would be greatly appreciated

---

### Post by TexasRussian on 2011-03-20
You can use the update and upgrade commands, this will update ubuntu but not as sufficiently as the update manager would.

```
sudo apt-get update

``````

sudo apt-get upgrade
```

---

### Post by sikander3786 on 2011-03-21
Welcome to the forums *frikinsweet* :-)

The error suggests that there is some problem with the list files which store the repository information.

> E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

So, backup your existing list directory and re-create one.

```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.bad
```

```
sudo apt-get update
```

Hope there shouldn't be any errors afterwards.

> **TexasRussian said:**
> You can use the update and upgrade commands, this will update ubuntu but not as sufficiently as the update manager would.


Whereas I think apt-get is far more superior and lot less buggy than Update Manager at the moment. Things will improve I hope :-)

---

### Post by frikinsweet on 2011-03-27
Thank you very much [sikander3786]("http://ubuntuforums.org/member.php?u=806649") everything seemed to install fine now

---

