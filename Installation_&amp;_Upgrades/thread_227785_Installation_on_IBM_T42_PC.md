---
title: "Installation on IBM T42 PC"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by nmendham on 2006-08-02
Hi,

installed ubuntu dapper on my laptop as a dual-boot OS. Installed via live CD  "install" - pre-planned the install so had my drive partitioned to suit.

While running live CD, I note that I can connect to Synaptic package manager (I install XMMS - works perfectly).

So, I install no worries, OS is up and running and is looking good. So I run Synaptic to start loading up some apps... and no matter what I do, I cannot connect to the repositories. I've changed my source.list file a number of times, tried no country code, my country code (au.), USA country code, even Italian country code! No joy, I cannot connect to Synaptic and download/install software. 

Can someone offer any advice? This is starting to really annoy me! 

RPM's seem reasonable compared to this! I'm so close I can feel it, but I just can't get this laptop talking.

---

### Post by Ziox on 2006-08-02
> **nmendham said:**
> Hi,

installed ubuntu dapper on my laptop as a dual-boot OS. Installed via live CD  "install" - pre-planned the install so had my drive partitioned to suit.

While running live CD, I note that I can connect to Synaptic package manager (I install XMMS - works perfectly).

So, I install no worries, OS is up and running and is looking good. So I run Synaptic to start loading up some apps... and no matter what I do, I cannot connect to the repositories. I've changed my source.list file a number of times, tried no country code, my country code (au.), USA country code, even Italian country code! No joy, I cannot connect to Synaptic and download/install software. 

Can someone offer any advice? This is starting to really annoy me! 

RPM's seem reasonable compared to this! I'm so close I can feel it, but I just can't get this laptop talking.

can you show us your sources.list file? it is located at /etc/apt/sources.list

---

### Post by nmendham on 2006-08-02
Sure:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free 


Thanks in advance

---

### Post by nmendham on 2006-08-02
Hi,

just for the sake of interest, I booted into the "Live" version of ubuntu 6.06 again just to check my sanity. 

Running Synaptic Package Manager yeilds results I would expect;
Running sudo aptitude update also yeilds expected results.

How frustrating! Running ubuntu from CD gets me the ability to add software, but no way to save it! Running from hdd potentially offers maintainability through storing to hdd, but I can't add software through the ubuntu repository channels!!

Can anyone think why this situation might be?

Thanks

---

### Post by Ziox on 2006-08-02
> **nmendham said:**
> Hi,
 
just for the sake of interest, I booted into the "Live" version of ubuntu 6.06 again just to check my sanity. 
 
Running Synaptic Package Manager yeilds results I would expect;
Running sudo aptitude update also yeilds expected results.
 
How frustrating! Running ubuntu from CD gets me the ability to add software, but no way to save it! Running from hdd potentially offers maintainability through storing to hdd, but I can't add software through the ubuntu repository channels!!
 
Can anyone think why this situation might be?
 
Thanks
 
It has stumped me as well, for I have seen many cases like yours.  The sources.list seems legit., I have no idea why it wouldn't allow you to connect to the servers. 
 
what's the output when you do sudo aptitude update?

---

### Post by nmendham on 2006-08-02
Hi,

output from sduo aptitude update:

Reading package lists...
Building dependency tree...
Initializing package states...
Building tag database...
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Connection failed
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
  Connection failed
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 82.211.81.151 80]
Reading package lists...

---

### Post by nmendham on 2006-08-03
Hi,

slept for a while, then did some root cause analysis - all things being equal, my router *must* be blocking the traffic somehow... I even tried the KDE flavour ubuntu just to check - was doing the same thing. 

Found an obscure reference to my router (Netgear WG614v6) in some blog backwater, about how this guy had had problems with it word blocking words not in the block list. He disabled word blocking and presto! And for me too!

Happy now... back to *normal* problem solving :D 

Thanks to all

---

