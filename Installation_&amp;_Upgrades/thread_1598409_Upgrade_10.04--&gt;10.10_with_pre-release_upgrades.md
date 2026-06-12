---
title: "Upgrade 10.04--&gt;10.10 with pre-release upgrades activated?"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by Xorlium on 2010-10-16
Hi everyone,

I'm trying to upgrade from Kubuntu 10.04 x86_64 to 10.10, but I'm getting the following error message:
```
Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
```

I have indeed installed pre-release and backport packages, as well as some packages of my own (some that I made from source with "checkinstall"). Is there a way to see which packages are causing trouble so I can uninstall them manually or something?

Is there a way to do a complete clean install but keep home, if they are NOT on separate partitions?

Thanks
Xorlium

---

### Post by sikander3786 on 2010-10-16
Can you please post the output of /etc/apt/sources.list

```
cat /etc/apt/sources.list
```

Also post the output of (if unsuccessful)

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by Xorlium on 2010-10-16
Hi,

Here's cat /etc/apt/sources.list:
```
# deb cdrom:[Kubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

# deb http://apt.wxwidgets.org/ lucid-wx main
# deb-src http://apt.wxwidgets.org/ lucid-wx main

```

apt-get update:
```

Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_CA                                                  
Get:2 http://dl.google.com stable Release [1,338B]                                                                            
Hit http://linux.dropbox.com lucid Release.gpg                                                                                
Ign http://getswiftfox.com unstable Release.gpg                                                                               
Get:3 http://dl.google.com stable/main Packages [630B]                                                                        
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_CA                                                             
Ign http://getswiftfox.com/builds/debian/ unstable/non-free Translation-en_CA                                                 
Ign http://getswiftfox.com unstable Release                                                                                   
Hit http://linux.dropbox.com lucid Release                                                                                    
Ign http://getswiftfox.com unstable/non-free Packages                                                                         
Hit http://archive.canonical.com lucid Release.gpg                                                                            
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_CA                                                      
Hit http://security.ubuntu.com lucid-security Release.gpg                                                                     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_CA                                                  
Ign http://getswiftfox.com unstable/non-free Packages                                                                         
Hit http://ca.archive.ubuntu.com lucid Release.gpg                                                                            
Hit http://ca.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_CA                                                         
Hit http://getswiftfox.com unstable/non-free Packages                                                                         
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                
Ign http://ppa.launchpad.net/compiz/ppa/ubuntu/ lucid/main Translation-en_CA                                                  
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Hit http://linux.dropbox.com lucid/main Packages                                                                 
Hit http://archive.canonical.com lucid Release                                                                   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_CA                               
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_CA                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_CA                               
Hit http://security.ubuntu.com lucid-security Release                                                            
Hit http://packages.medibuntu.org lucid Release.gpg                                                              
Ign http://packages.medibuntu.org/ lucid/free Translation-en_CA                            
Hit http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA
Hit http://ca.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_CA                            
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_CA                          
Hit http://ca.archive.ubuntu.com lucid-updates Release.gpg                                           
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_CA                        
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_CA                  
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_CA                    
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_CA                  
Hit http://ca.archive.ubuntu.com lucid Release                                                                             
Ign http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/ lucid/main Translation-en_CA                                      
Hit http://ppa.launchpad.net lucid Release.gpg                                                       
Ign http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu/ lucid/main Translation-en_CA               
Hit http://ppa.launchpad.net lucid Release.gpg                                                                             
Ign http://ppa.launchpad.net/sunab/ppa/ubuntu/ lucid/main Translation-en_CA                                                
Hit http://ppa.launchpad.net lucid Release.gpg                                                                             
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main Translation-en_CA                                    
Hit http://ppa.launchpad.net lucid Release.gpg                                                                             
Ign http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu/ lucid/main Translation-en_CA                                         
Hit http://ppa.launchpad.net lucid Release.gpg                                                                             
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_CA                                  
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                
Ign http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/ lucid/main Translation-en_CA                               
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/ogre-team/ogre/ubuntu/ lucid/main Translation-en_CA           
Hit http://ppa.launchpad.net lucid Release.gpg                                             
Ign http://ppa.launchpad.net/rvm/mplayer/ubuntu/ lucid/main Translation-en_CA                                    
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Hit http://ca.archive.ubuntu.com lucid-updates Release                                                           
Hit http://archive.canonical.com lucid/partner Packages                                                          
Hit http://security.ubuntu.com lucid-security/main Packages                                                      
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ lucid/main Translation-en_CA                            
Hit http://ppa.launchpad.net lucid Release.gpg                                             
Ign http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/ lucid/main Translation-en_CA                    
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_CA                                  
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_CA                                
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_CA                                              
Hit http://ca.archive.ubuntu.com lucid/main Packages                                                                          
Hit http://ca.archive.ubuntu.com lucid/restricted Packages                                                                    
Hit http://ca.archive.ubuntu.com lucid/main Sources                                                                           
Hit http://ca.archive.ubuntu.com lucid/restricted Sources                                                                     
Hit http://ca.archive.ubuntu.com lucid/universe Packages                                                                      
Hit http://archive.canonical.com lucid/partner Sources                                                                        
Hit http://security.ubuntu.com lucid-security/restricted Packages                                                             
Hit http://security.ubuntu.com lucid-security/main Sources                                                                 
Hit http://security.ubuntu.com lucid-security/restricted Sources                                                           
Hit http://security.ubuntu.com lucid-security/universe Packages                                                            
Ign http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main Translation-en_CA                                  
Hit http://ppa.launchpad.net lucid Release                                                                                 
Hit http://ppa.launchpad.net lucid Release                                                                                    
Hit http://ppa.launchpad.net lucid Release                                                                                 
Hit http://ppa.launchpad.net lucid Release                                                                                 
Hit http://ppa.launchpad.net lucid Release                                                                                    
Hit http://ppa.launchpad.net lucid Release                                                                                    
Hit http://ca.archive.ubuntu.com lucid/universe Sources                                                                       
Hit http://ca.archive.ubuntu.com lucid/multiverse Packages                                                                    
Hit http://ca.archive.ubuntu.com lucid/multiverse Sources                                  
Hit http://ca.archive.ubuntu.com lucid-updates/main Packages                                                     
Hit http://ca.archive.ubuntu.com lucid-updates/restricted Packages                                               
Hit http://ca.archive.ubuntu.com lucid-updates/main Sources                                
Hit http://security.ubuntu.com lucid-security/universe Sources                                                   
Hit http://security.ubuntu.com lucid-security/multiverse Packages                                                
Hit http://security.ubuntu.com lucid-security/multiverse Sources                           
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://packages.medibuntu.org lucid Release                                            
Hit http://ca.archive.ubuntu.com lucid-updates/restricted Sources                          
Hit http://ca.archive.ubuntu.com lucid-updates/universe Packages     
Hit http://ca.archive.ubuntu.com lucid-updates/universe Sources      
Hit http://ca.archive.ubuntu.com lucid-updates/multiverse Packages   
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ca.archive.ubuntu.com lucid-updates/multiverse Sources    
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Fetched 2,157B in 1s (1,200B/s)

```

And apt-get upgrade:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I'm not sure how this is helpful. As I said before, I have installed pre-releases and backports, as well as extra packages.

Thanks,
Xorlium

---

### Post by sikander3786 on 2010-10-17
Uninstall your graphics drivers (if any), disable the third party repositories, clean the apt-get cache and again try dist-upgrade.

```
sudo apt-get clean
```

If still unsuccessful, please post the output of

```
cat /var/log/dist-upgrade/apt.log | grep broken
```

---

