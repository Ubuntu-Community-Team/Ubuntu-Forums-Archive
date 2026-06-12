---
title: "Can't update packages using apt upgrade"
date: 2022-10-12
forum: Installation &amp; Upgrades
---

### Post by luncaaa on 2022-10-12
Hi o/


I have run **sudo apt update** on my terminal and it said that I can update 7 packages. After that, I ran **sudo apt upgrade** but it returned **0 updated, 0 installed, 0 removed and 7 not updated**.


Why won't those 7 update and how can I update them?


The packages are all related to pipewire and its dependencies and the problem is that, apparently, dependencies are broken


sudo apt upgrade pipewire:
The following packages have unmet dependencies:
 gstreamer1.0-pipewire : Depends: pipewire (= 0.3.48-1ubuntu1) but 0.3.48-1ubuntu2 is going to be installed
                         Depends: libpipewire-0.3-0 (= 0.3.48-1ubuntu1) but 0.3.48-1ubuntu2 is going to be installed
 pipewire : Depends: pipewire-bin (= 0.3.48-1ubuntu2)
 pipewire-bin : Depends: libpipewire-0.3-modules (= 0.3.48-1ubuntu1) but 0.3.48-1ubuntu2 is going to be installed
                Depends: libpipewire-0.3-0 (= 0.3.48-1ubuntu1) but 0.3.48-1ubuntu2 is going to be installed

---

### Post by MAFoElffen on 2022-10-12
What I see is that there are a newer versions available than the required and that logic for the dependecy resolve is broken. The logi should read as ">=" (version or newer) instead of just "="(equal to a version).

The math is wrong there... 

From that, as a work-around, you have two choices
#1) 
```

sudo apt dist-upgrade

```
...which would try to force installing the old dependencies, which then would later upgrade to the newer dependencies. This is dangerous sometimes, because you have the risk that it's going to resolve that by installing outdated packages, and force things without removing packages, so may then have conflicts.

or #2) Do
```

sudo apt full-upgrade

```
... which will remove packages & install new to try to resolve the dependency conflict.

You could try

---

### Post by luncaaa on 2022-10-12
Hey o/

Thanks for your reply!

Sadly, none of the solutions worked and I am still getting the same error. What other things can I try?

---

### Post by Frogs Hair on 2022-10-12
Was pipwire installed from a PPA or the Ubuntu repository ?

---

### Post by luncaaa on 2022-10-12
I don't know, I don't remember installing it... I guess it was pre-installed when I installed Ubuntu on my laptop so probably from the Ubuntu repository

---

### Post by Frogs Hair on 2022-10-12
Post the entire output of:

```
sudo apt update
```

---

### Post by ian-weisser on 2022-10-13
Those pipewire packages just appeared on my system, too, within the past 18 hours.

Answer: Phased Updates

```

$ apt-cache policy libpipewire-0.3-modules 
libpipewire-0.3-modules:
  Installed: 0.3.48-1ubuntu1
  Candidate: 0.3.48-1ubuntu2
  Version table:
     0.3.48-1ubuntu2 500 (**phased 30%**)
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
 *** 0.3.48-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

Take no action. Leave it alone. It's not an error. Nothing is wrong. Apt will install those packages when your turn comes.

Simply run "sudo apt upgrade" again in a couple days, and apt will install the packages automatically.

---

### Post by luncaaa on 2022-10-13
```
Des:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Obj:2 http://es.archive.ubuntu.com/ubuntu jammy InRelease                      
Des:3 http://es.archive.ubuntu.com/ubuntu jammy-updates InRelease [114 kB]     
Obj:4 https://dl.google.com/linux/chrome/deb stable InRelease                  
Obj:5 https://deb.nodesource.com/node_18.x jammy InRelease                     
Obj:6 https://ppa.launchpadcontent.net/git-core/ppa/ubuntu jammy InRelease     
Des:7 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease [7.453 B]
Des:8 http://es.archive.ubuntu.com/ubuntu jammy-backports InRelease [99,8 kB]
Des:9 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease [7.452 B]
Des:10 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages [139 kB]
Des:11 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [370 kB]
Des:12 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [84,3 kB]
Des:13 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [13,0 kB]
Des:14 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [12,4 kB]
Des:15 http://es.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [333 kB]
Des:16 http://es.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [633 kB]
Des:17 http://es.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [147 kB]
Des:18 http://es.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [93,1 kB]
Des:19 http://es.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [9.100 B]
Des:20 http://es.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [430 kB]
Des:21 http://es.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [281 kB]
Des:22 http://es.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [248 kB]
Des:23 http://es.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Des:24 http://es.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [12,6 kB]
Descargados 3.145 kB en 9s (348 kB/s)                                          
Creating a packages list... Done
Creating a dependency tree... Done
Reading status information... Done
7 packages can be updated. Execute «apt list --upgradable» to see them.

```

---

### Post by luncaaa on 2022-10-13
Thanks for your reply... I will wait a couple of days to see what happens.

---

