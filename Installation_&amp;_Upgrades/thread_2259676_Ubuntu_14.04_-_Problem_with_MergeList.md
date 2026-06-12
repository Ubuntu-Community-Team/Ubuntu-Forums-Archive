---
title: "Ubuntu 14.04 - Problem with MergeList"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by penuel1310 on 2015-01-06
Hey guys, today while updating software for my ubuntu I got a message saying somethng like "untrusted source... can't install... then package manager just quit"
Now I have some kind of error with MergeList... Here are the screenshots
Please help me...Thanks.

[ATTACH=CONFIG]259031[/ATTACH][ATTACH=CONFIG]259032[/ATTACH][ATTACH=CONFIG]259033[/ATTACH]

---

### Post by Rex Bouwense on 2015-01-06
```
sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a
sudo apt-get -f install
```
That could fix your missing dependencies or broken packages.

---

### Post by penuel1310 on 2015-01-07
Hi Rex Bouwense, when I ran "sudo apt-get update" I got the following errors... Do you have any solution for this? These are Certificate errors I guess...


W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://download.videolan.org](http://download.videolan.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6BCA5E4DB84288D9
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 52BB8185076361AC
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
W: Failed to fetch [https://download.01.org/gfx/ubuntu/14.04/main/dists/trusty/main/binary-amd64/Packages](https://download.01.org/gfx/ubuntu/14.04/main/dists/trusty/main/binary-amd64/Packages)  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none

W: Failed to fetch [https://download.01.org/gfx/ubuntu/14.04/main/dists/trusty/main/binary-i386/Packages](https://download.01.org/gfx/ubuntu/14.04/main/dists/trusty/main/binary-i386/Packages)  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Rex Bouwense on 2015-01-07
Here are two people that had the same problem.  Notice both are solved.
[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)
[http://ubuntuforums.org/showthread.php?t=2241693](http://ubuntuforums.org/showthread.php?t=2241693)
The Googlubuntu search that yielded those two is
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+following+signatures+couldn%27t+be+verified+brcause+the+public+key+is+not+available.&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+following+signatures+couldn%27t+be+verified+brcause+the+public+key+is+not+available.&sa=Search&cof=FORID:9)

---

### Post by penuel1310 on 2015-01-09
Just fixed the problem... The following commands below worked for me.. Thank you Rex Bouwense for your help.

```

sudo rm -r /etc/apt/trusted.gpg.d/*.gpg
sudo rm -r /etc/apt/trusted.gpg.d/*.gpg~
sudo rm /var/lib/apt/lists/* -vf
sudo rm /var/lib/apt/lists/partial/* -vf
sudo apt-get clean

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
sudo apt-get update
sudo apt-get upgrade

```

---

