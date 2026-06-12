---
title: "Creating a local repo"
date: 2020-01-05
forum: Installation &amp; Upgrades
---

### Post by daryl9 on 2020-01-05
I am attempting to create a local repo for Trusty, Xenial and Bionic releases using apt-mirror.  This is a snippet for the mirrors.list, Trusty only
> #------------------------------------------------------------------------------#
#                            OFFICIAL TRUSTY REPOS                             #
#------------------------------------------------------------------------------#
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

I have a local NAS setup to mount on /var/spool/apt-mirror and the packages download to the NAS.  I then link that downloaded repos to /var/www/html:
> root@server: ls -l /var/www/html/total 12
-rw-r--r-- 1 root root 10701 Dec 28 17:41 index.html
lrwxrwxrwx 1 root root    56 Jan  5 15:23 security -> /var/spool/apt-mirror/mirror/security.ubuntu.com/ubuntu/
lrwxrwxrwx 1 root root    58 Jan  5 15:22 us_archive -> /var/spool/apt-mirror/mirror/us.archive.ubuntu.com/ubuntu/

This is the sources.list on the node that I am trying to update:
> #deb cdrom:[Edubuntu 14.04.5 LTS _Trusty Tahr_ - Release amd64 (20160803.1)]/ trusty main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://192.168.0.197/us_archive](http://192.168.0.197/us_archive) trusty main restricted
deb-src [http://192.168.0.197/us_archive](http://192.168.0.197/us_archive) trusty main restricted

Here are the errors that I get:
> root@HP:/etc/apt# apt update
Ign [http://192.168.0.197](http://192.168.0.197) trusty InRelease
Get:1 [http://192.168.0.197](http://192.168.0.197) trusty Release.gpg [933 B]
Get:2 [http://192.168.0.197](http://192.168.0.197) trusty Release [58.5 kB]
Get:3 [http://192.168.0.197](http://192.168.0.197) trusty/main Sources [1,064 kB]
Get:4 [http://192.168.0.197](http://192.168.0.197) trusty/restricted Sources [5,433 B]
Get:5 [http://192.168.0.197](http://192.168.0.197) trusty/main Translation-en [762 kB]
Get:6 [http://192.168.0.197](http://192.168.0.197) trusty/restricted Translation-en [3,457 B]
Err [http://192.168.0.197](http://192.168.0.197) trusty/main amd64 Packages 404  Not Found
Err [http://192.168.0.197](http://192.168.0.197) trusty/restricted amd64 Packages 404  Not Found
Err [http://192.168.0.197](http://192.168.0.197) trusty/main i386 Packages 404  Not Found
Err [http://192.168.0.197](http://192.168.0.197) trusty/restricted i386 Packages 404  Not Found
Ign [http://192.168.0.197](http://192.168.0.197) trusty/main Translation-en_US
Ign [http://192.168.0.197](http://192.168.0.197) trusty/restricted Translation-en_US
Fetched 1,895 kB in 5s (338 kB/s)
W: Failed to fetch [http://192.168.0.197/us_archive/dists/trusty/main/binary-amd64/Packages](http://192.168.0.197/us_archive/dists/trusty/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://192.168.0.197/us_archive/dists/trusty/restricted/binary-amd64/Packages](http://192.168.0.197/us_archive/dists/trusty/restricted/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://192.168.0.197/us_archive/dists/trusty/main/binary-i386/Packages](http://192.168.0.197/us_archive/dists/trusty/main/binary-i386/Packages)  404  Not Found
W: Failed to fetch [http://192.168.0.197/us_archive/dists/trusty/restricted/binary-i386/Packages](http://192.168.0.197/us_archive/dists/trusty/restricted/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

I don't know what Ign means, Ignore maybe??  Obviously, Err means [COLOR=#ff0000]Error [/COLOR]and 404 Not Found means that apt update can't find the packages.  

So my question is why can't apt update find the packages?  I've reviewed several docs online and for the most part they're all the same.  Install apt-mirror, apache, configure mirrors.list etc...  I don't see anything wrong.  Can someone spot something that might be causing these errors?

Thanks

Daryl

---

### Post by Frogs Hair on 2020-01-05
14.04 is no longer supported, so you would have to use the old releases repository. It may be time to install a supported release if possible.

From ask Ubuntu:  
[https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)

---

### Post by daryl9 on 2020-01-05
> **Frogs Hair said:**
> 14.04 is no longer supported, so you would have to use the old releases repository. It may be time to install a supported release if possible.

From ask Ubuntu:  
[https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)


Yes I understand that 14.04 is no longer supported, but its the release that I'm kinda sort of stuck with.  (Long story).  

So, what you're telling me is that [http://us.archive.ubuntu.com/ubuntu/dists/trusty/](http://us.archive.ubuntu.com/ubuntu/dists/trusty/)  will not provide the packages for Trusty.  Is that correct?  However, if I browse through [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/), I don't see Trusty listed at all.

Thanks

Daryl

---

### Post by Frogs Hair on 2020-01-06
14.04 has been added to [extended maintenance]("https://ubuntu.com/esm") for advantage customers and Ubuntu members  so the repository would be active for security updates. ESM refers to security patches.The old releases repository_ appears_ to included  those older point  releases below , but the latest are still active. The apt get/offline/repository info dates from 2011.
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
  

From old releases directory.

[COLOR=#000000][FONT=Ubuntu]_The following releases are also available_ which have been superseded by later point releases (the current point release is available on [/FONT][/COLOR][releases.ubuntu.com]("http://releases.ubuntu.com/")[COLOR=#000000][FONT=Ubuntu] as usual):[/FONT][/COLOR]
[LIST]
[*][Ubuntu 12.04.4 LTS (Precise Pangolin)]("http://old-releases.ubuntu.com/releases/precise/")
[*][Ubuntu 14.04.5 LTS (Trusty Tahr)]("http://old-releases.ubuntu.com/releases/trusty/")
[*][Ubuntu 16.04.5 LTS (Xenial Xerus)]("http://old-releases.ubuntu.com/releases/xenial/")
[*][Ubuntu 18.04.2 LTS (Bionic Beaver)]("http://old-releases.ubuntu.com/releases/bionic/")
[/LIST]

---

### Post by daryl9 on 2020-01-12
> **Frogs Hair said:**
> 14.04 has been added to [extended maintenance]("https://ubuntu.com/esm") for advantage customers and Ubuntu members  so the repository would be active for security updates. ESM refers to security patches.The old releases repository_ appears_ to included  those older point  releases below , but the latest are still active. The apt get/offline/repository info dates from 2011.
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
  

From old releases directory.

[COLOR=#000000][FONT=Ubuntu]_The following releases are also available_ which have been superseded by later point releases (the current point release is available on [/FONT][/COLOR][releases.ubuntu.com]("http://releases.ubuntu.com/")[COLOR=#000000][FONT=Ubuntu] as usual):[/FONT][/COLOR]
[LIST]
[*][Ubuntu 12.04.4 LTS (Precise Pangolin)]("http://old-releases.ubuntu.com/releases/precise/") 
[*][Ubuntu 14.04.5 LTS (Trusty Tahr)]("http://old-releases.ubuntu.com/releases/trusty/") 
[*][Ubuntu 16.04.5 LTS (Xenial Xerus)]("http://old-releases.ubuntu.com/releases/xenial/") 
[*][Ubuntu 18.04.2 LTS (Bionic Beaver)]("http://old-releases.ubuntu.com/releases/bionic/") 
[/LIST]


Hello,

It took me a while to get back to this, and work on it a bit more.  I followed the instructions for creating an offline repo  as you suggested with the link  [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository).   This doesn't really solve my dilemma.   There are no packages downloaded.

After creating the repo as instructed, I ran the apt update command, and all came back good. Then I ran the apt upgrade and received fail after fail because there where no packages found. Without apt-mirror, how does a person download the packages for the repo?  

Thanks

Daryl

---

### Post by daryl9 on 2020-01-20
Hello,

I'm still trying to get this issue resolved and I have some additional questions.

After following the instructions on [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository), I realized that apt-mirror isn't downloading everything that I need in order to create at local repo.  For example it doesn't download **Contents-amd64.gz** and **Contents-i386.gz **from **./ubuntu/dists/trusty**, nor does it download **./ubuntu/dists/trusty/main/binary-amd64** and its contents, so on and so on.....

I'm beginning to wonder if there are differences in apt-mirror?  I'm not using a Ubuntu machine to create this repo, I'm using a Raspberry Pi which is using **Raspbian Buster**.    I've always received an error telling me that apt-mirror couldn't find index files or packages or something for the **armhf **CPU, but I've just ignored that error because it doesn't pertain to what I'm doing and my mirrors.list file doesn't have anything that would even attempt to download armhf packages.  Now I'm beginning to wonder if this apt-mirror is only meant for Raspbian?  I wouldn't think that it would matter what apt-mirror I use, but perhaps it does?  

Does anyone know if the apt-mirror in Raspbian would only work for Rasbian repositories?

Thanks

Daryl

---

