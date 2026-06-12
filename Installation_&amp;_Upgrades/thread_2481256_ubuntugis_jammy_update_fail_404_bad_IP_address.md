---
title: "ubuntugis jammy update fail 404 bad IP address"
date: 2022-11-23
forum: Installation &amp; Upgrades
---

### Post by brendand2 on 2022-11-23
Can anyone provide me with guidance on this?:
```
$ sudo apt update
Hit:1 https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/ InRelease
Hit:2 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy InRelease
Ign:4 https://ppa.launchpadcontent.net/ubuntugis/ppa/ubuntu jammy InRelease
Get:5 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease [114 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Err:8 https://ppa.launchpadcontent.net/ubuntugis/ppa/ubuntu jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Get:9 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [726 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [94.9 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [756 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [257 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:14 http://us.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [11.7 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [20.0 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [13.2 kB]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/ubuntugis/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
```

---

### Post by tea for one on 2022-11-23
> **brendand2 said:**
> 
```
$ sudo apt update
Ign:4 https://ppa.launchpadcontent.net/ubuntugis/ppa/ubuntu jammy InRelease
Err:8 https://ppa.launchpadcontent.net/ubuntugis/ppa/ubuntu jammy Release
  404  Not Found [IP: 185.125.190.52 443]
E: The repository 'https://ppa.launchpadcontent.net/ubuntugis/ppa/ubuntu jammy Release' [COLOR="#0000FF"]does not have a Release file[/COLOR].
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
If the ppa does not have a release file, then you should remove the ppa from your sources list.
If this software is essential to you, perhaps contact the provider to see if the package can be updated?

---

### Post by grahammechanical on 2022-11-23
> E: The repository 'https://ppa.launchpadcontent.net/ubuntugis/ppa/ubuntu jammy Release' does not have a Release file.

That message is telling you that the Personal Package Archive (PPA) for ubuntugis does not exist for Ubuntu 22.04 (Jammy). This page confirms it.

[https://launchpad.net/~ubuntugis/+archive/ubuntu/ppa](https://launchpad.net/~ubuntugis/+archive/ubuntu/ppa)

Click on technical details about this PPA and then on the Chose your Ubuntu version drop down and you will not find Jammy in the list. You can get the unstable version for 22.04

[https://launchpad.net/~ubuntugis/+archive/ubuntu/ubuntugis-unstable](https://launchpad.net/~ubuntugis/+archive/ubuntu/ubuntugis-unstable)

And the experimental version

[https://launchpad.net/~ubuntugis/+archive/ubuntu/ubuntugis-experimental](https://launchpad.net/~ubuntugis/+archive/ubuntu/ubuntugis-experimental)

Regards

---

### Post by brendand2 on 2022-11-23
Thanks so much. What I found confusing is that the only way to contact the PPA maintainers (that I could see) was the PPA mailing list. The Catch-22 is that only maintainers can sign up for the mailing list. Am I missing something else stupidly obvious?

---

### Post by deadflowr on 2022-11-23
You shouldn't have to signup for a mailing list to send an email to the address shown in the launchpad page here:
[https://launchpad.net/~ubuntugis]("https://launchpad.net/~ubuntugis")
Send it to this address  [email]ubuntu@lists.osgeo.org[/email]

---

### Post by brendand2 on 2022-11-24
Thank you!

---

