---
title: "Dependency problems upgrading to precise"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by jJackFlash on 2012-09-08
Hi,

I'm trying to upgrade from lucid to precise. When issuing do-release-upgrade, I get this error:

```
dpkg: dependency problems prevent configuration of libapt-pkg4.12:
 libapt-pkg4.12 depends on libstdc++6 (>= 4.6); however:
  Version of libstdc++6 on system is 4.4.3-4ubuntu5.1.
dpkg: error processing libapt-pkg4.12 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapt-inst1.4:
 libapt-inst1.4 depends on libapt-pkg4.12 (>= 0.8.16~exp12ubuntu6~upgrader1); however:
  Package libapt-pkg4.12 is not configured yet.
No apport report written because the error message indicates its a followup error from a previous failure.
```

Details of my current version:

```
$cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

```

Any help would be much appreciated.

j

---

### Post by raja.genupula on 2012-09-08
```
sudo dpkg --configure -a
sudo apt-get install -f

```
open your terminal and type them on one by one .

---

### Post by jJackFlash on 2012-09-08
Hi Raja,

Thanks for the quick help!

The second command upgraded the required libstdc++6. Unfortunately I haven´t gone much further as after relaunching do-release-upgrade I've run into this missing file error:

```
...
Hit http://security.ubuntu.com lucid-security/multiverse Packages                                                                                    
Hit http://security.ubuntu.com lucid-security/multiverse Sources                                                                                     
Hit http://ad.archive.ubuntu.com lucid-updates/universe Sources                                                                                      
Hit http://ad.archive.ubuntu.com lucid-updates/multiverse Packages                                                                                   
Hit http://ad.archive.ubuntu.com lucid-updates/multiverse Sources                                                                                    
Hit http://debian.oregonstate.edu sid/main Packages                                                                                                  
Fetched 0B in 0s (0B/s)                                                                                                                              
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
Fetched 0B in 0s (0B/s)                                                                                                                              
raceback (most recent call last):
  File "/tmp/tmpayHpOc/precise", line 3, in <module>
    from DistUpgradeMain import main
  File "/tmp/tmpayHpOc/DistUpgradeMain.py", line 25, in <module>
    import apt
  File "/usr/lib/release-upgrader-python-apt/apt/__init__.py", line 21, in <module>
    import apt_pkg
ImportError: /lib/libz.so.1: version `ZLIB_1.2.3.3' not found (required by /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12)
=== Command terminated with exit status 1 (Sat Sep  8 09:05:30 2012) ===
```

Again, any hint would be appreciated.

j

---

### Post by arpanaut on 2012-09-08
> DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"
Your lsb-release is showing that you have not done the upgrades to 10.04.4
so the release upgrade probably won't work.
do all the upgrades available for your present install then try the 
do-release-upgrade command again.
This will probably alleviate the conflicts.

---

### Post by jJackFlash on 2012-09-09
Thanks arpanaut for your hint.

I tried to upgrade to 10.04.4 by doing sudo apt-get upgrade. After some minor problems it seemed to be almost done. Just an error with hdparm was left. I decided to restart anyway (probably an error) just to find the system cannot boot anymore. I opened another thread to request help ([http://ubuntuforums.org/showthread.php?t=2055273](http://ubuntuforums.org/showthread.php?t=2055273)).

j

---

