---
title: "Ubuntu Software Centre Problems"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by noctisheart on 2010-07-02
When I try to install programs from the software center, almost 99% of the time it comes up with an error message that reads :
'Package Dependencies cannot be resolved: This error could be caused by required additional software packages being missing or not-installable. Alternatively, there could be a conflict between software packages that are not allowed to be installed at the same time.'

Anyone know what this is and how I can solve it? Thank you!

---

### Post by zipperback on 2010-07-02
Try this.


```

sudo apt-get -f install

```

The update with the following:

```

sudo apt-get update && sudo apt-get upgrade -y

```

This should resolve your broken dependencies, then update the apt database and then install any currently available updates for your currently installed version of Ubuntu on your system.

- zipperback
:popcorn:

---

### Post by noctisheart on 2010-07-02
Thank you for the quick reply! I tried that but I got his information:

brandon@brandon-desktop:~$ sudo apt-get update && sudo apt-get upgrade -y
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_CA
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA [663B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                
Ign [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/) lucid/main Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Fetched 663B in 1s (364B/s)
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead

Does that mean I am still missing things?

---

### Post by Jessi on 2010-07-02
Please help the poor lad... his windows has gone wonky and this is our last form of communication. 

I tried to help him by telling him which packages I had installed but it wouldn't let him install any of them. Anyway he can reinstall ubuntu without harming the partitions?

---

