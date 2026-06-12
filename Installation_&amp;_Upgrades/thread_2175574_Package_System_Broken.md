---
title: "Package System Broken"
date: 2013-09-19
forum: Installation &amp; Upgrades
---

### Post by blueboy1 on 2013-09-19
I am running 12.04 and updated my system and apparantly installed some packages for 13.1. I am unable to run wine and want to delete wine and reinstall it.  In the process it seems I messed up my System Manager with some third party repositoriies. 
I am trying to do the following:
Fix my Package Manager which is showing the follwoing message Package System Broken with the follwoing details. 

The following packages have unmet dependencies:

initramfs-tools: Depends: initramfs-tools-bin (>= 0.99ubuntu13.1) but 0.99ubuntu13.2 is installed
                 Depends: klibc-utils (>= 1.5.9-1) but 1.5.25-1ubuntu2 is installed
                 Depends: busybox-initramfs (>= 1:1.13.3-1ubuntu5) but 1:1.18.5-1ubuntu4.1 is installed
                 Depends: udev (>= 147~-5) but 175-0ubuntu9.4 is installed
                 Depends: findutils (>= 4.2.24) but 4.4.2-4ubuntu1 is installed
                 Depends: util-linux (> 2.15~rc1) but 2.20.1-1ubuntu3 is installed 



Secondly I am trying to delete and reinstall wine. 
I will be happy for any help I can get.  Thanks.

---

### Post by Bashing-om on 2013-09-19
blueboy1; Hi ! 

I have never seen nothing like that .. but, I will try and help .. see if we can restore ... be aware what you have asked for may turn out to be a tall order. Removing Wine can be a challenge !
Wine is to be removed as the 1st order of business:
a) Was Wine functional ?
b) How did you install Wine ?
c) What methods/actions have you taken to remove Wine ?

Post back the following - between code (#) tags - so we know what we are working with:
```

lsb_release -a
uname -a
cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d/

```

And Post back - between code (#) tags - the complete output of : So we know the condition of the package management system.
```

sudo apt-get update
sudo apt-get upgrade

``` 

[INDENT][INDENT]will see what there is to be done
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-24
Thanks for your response. Please see the the results of the codes.

```
alrick@Home:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
alrick@Home:~$ ###########################################################
alrick@Home:~$ uname -a
Linux Home 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
alrick@Home:~$ ###############################################################
alrick@Home:~$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports restricted main multiverse universe
alrick@Home:~$ ################################################################
alrick@Home:~$ ls -la /etc/apt/sources.list.d/
total 36
drwxr-xr-x 2 root root 4096 Sep 10 20:05 .
drwxr-xr-x 6 root root 4096 Sep 17 23:19 ..
-rw-r--r-- 1 root root  175 Sep 18 22:48 google-earth.list
-rw-r--r-- 1 root root  175 Sep 18 22:48 google-earth.list.save
-rw-r--r-- 1 root root  285 Sep 18 22:48 medibuntu.list
-rw-r--r-- 1 root root  285 Sep 18 22:48 medibuntu.list.save
-rw-r--r-- 1 root root  130 Sep 18 22:48 shnatsel-zram-precise.list
-rw-r--r-- 1 root root  130 Sep 18 22:48 shnatsel-zram-precise.list.save
-rw-r--r-- 1 root root    0 Sep 18 22:48 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root   69 Sep 18 22:48 ubuntu-wine-ppa-precise.list.save
alrick@Home:~$ ################################################################
alrick@Home:~$ sudo apt-get update
[sudo] password for alrick: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg                     
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg [198 B]          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release                              
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages [2,818 B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages [5,206 B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages [36.5 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages [2,825 B] 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages [36.3 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en              
Fetched 139 kB in 6s (22.1 kB/s)                                               
Reading package lists... Done
alrick@Home:~$ ##########################################################
alrick@Home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ ###########################################################
alrick@Home:~$ sudo apt-get -f
apt 0.8.16~exp12ubuntu10.12 for amd64 compiled on Jul 16 2013 18:00:51
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
alrick@Home:~$ ###############################################################
```

---

### Post by blueboy1 on 2013-09-24
Thanks for your response. Please see the the results of the codes.

```
alrick@Home:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
alrick@Home:~$ ###########################################################
alrick@Home:~$ uname -a
Linux Home 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
alrick@Home:~$ ###############################################################
alrick@Home:~$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports restricted main multiverse universe
alrick@Home:~$ ################################################################
alrick@Home:~$ ls -la /etc/apt/sources.list.d/
total 36
drwxr-xr-x 2 root root 4096 Sep 10 20:05 .
drwxr-xr-x 6 root root 4096 Sep 17 23:19 ..
-rw-r--r-- 1 root root  175 Sep 18 22:48 google-earth.list
-rw-r--r-- 1 root root  175 Sep 18 22:48 google-earth.list.save
-rw-r--r-- 1 root root  285 Sep 18 22:48 medibuntu.list
-rw-r--r-- 1 root root  285 Sep 18 22:48 medibuntu.list.save
-rw-r--r-- 1 root root  130 Sep 18 22:48 shnatsel-zram-precise.list
-rw-r--r-- 1 root root  130 Sep 18 22:48 shnatsel-zram-precise.list.save
-rw-r--r-- 1 root root    0 Sep 18 22:48 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root   69 Sep 18 22:48 ubuntu-wine-ppa-precise.list.save
alrick@Home:~$ ################################################################
alrick@Home:~$ sudo apt-get update
[sudo] password for alrick: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg                     
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg [198 B]          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release                              
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages [2,818 B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages [5,206 B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages [36.5 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages [2,825 B] 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages [36.3 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en              
Fetched 139 kB in 6s (22.1 kB/s)                                               
Reading package lists... Done
alrick@Home:~$ ##########################################################
alrick@Home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ ###########################################################
alrick@Home:~$ sudo apt-get -f
apt 0.8.16~exp12ubuntu10.12 for amd64 compiled on Jul 16 2013 18:00:51
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
alrick@Home:~$ ###############################################################
```

---

### Post by blueboy1 on 2013-09-24
```
alrick@Home:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
alrick@Home:~$ 
alrick@Home:~$ ##########################################################
alrick@Home:~$ uname -a
Linux Home 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
alrick@Home:~$ ##########################################################
alrick@Home:~$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports restricted main multiverse universe
alrick@Home:~$ #############################################################
alrick@Home:~$ ls -la /etc/apt/sources.list.d/
total 36
drwxr-xr-x 2 root root 4096 Sep 10 20:05 .
drwxr-xr-x 6 root root 4096 Sep 17 23:19 ..
-rw-r--r-- 1 root root  175 Sep 18 22:48 google-earth.list
-rw-r--r-- 1 root root  175 Sep 18 22:48 google-earth.list.save
-rw-r--r-- 1 root root  285 Sep 18 22:48 medibuntu.list
-rw-r--r-- 1 root root  285 Sep 18 22:48 medibuntu.list.save
-rw-r--r-- 1 root root  130 Sep 18 22:48 shnatsel-zram-precise.list
-rw-r--r-- 1 root root  130 Sep 18 22:48 shnatsel-zram-precise.list.save
-rw-r--r-- 1 root root    0 Sep 18 22:48 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root   69 Sep 18 22:48 ubuntu-wine-ppa-precise.list.save
alrick@Home:~$ ############################################################
alrick@Home:~$ sudo apt-get update
[sudo] password for alrick: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]            
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg [198 B]           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg                    
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]              
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release [49.6 kB]             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [418 kB]          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages                  
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]   
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [95.7 kB]     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages              
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [8,343 B]   
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [689 kB]   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [216 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [709 kB]   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [220 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex        
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources [88.4 kB]       
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources [28.0 kB]   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources [1,804 B] 
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages [318 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex              
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages [82.3 kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages [2,449 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [337 kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages [85.7 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages [2,640 B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex [74 B] 
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Fetched 3,472 kB in 4s (742 kB/s)
Reading package lists... Done
alrick@Home:~$ ############################################################
alrick@Home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ #############################################################
alrick@Home:~$ sudo apt-get -f
apt 0.8.16~exp12ubuntu10.12 for amd64 compiled on Jul 16 2013 18:00:51
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
alrick@Home:~$ ###################################################### 
```

---

### Post by Bashing-om on 2013-09-24
blueboy1;
So long as initramfs is not happy ... nothing is going to be done.
Let's see what results; Terminal code:
As a 1st approach:
```

sudo apt-get install -f initramfs-tools

```

Please put your outputs between code (#) tags -top of post. Surely makes the text more readable.

[INDENT][INDENT]one think at a time, other thinks in due time
[/INDENT][/INDENT]

---

### Post by Frogs Hair on 2013-09-24
blueboy1

To add code tags to the terminal output , highlight the text with your cursor and select the # symbol from the reply box tools. This makes for easy scrolling and saves space. :)

---

### Post by alrick_lothian on 2013-09-24
```
alrick@Home:~$ sudo apt-get install -f initramfs-tools
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  winetricks
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 58 not upgraded.
2 not fully installed or removed.
Need to get 0 B/49.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                     dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 apparmor
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$
```

---

### Post by Bashing-om on 2013-09-24
alrick_lothian;

This is going to take some thinking !
You have a later version of "initramfs-tools-bin" ::0.99ubuntu13.2.
If we fix it for this instance, will break whatever was installed that depends on the higher version.
Let's try and find out what it is going to break if we fix it:
This requires another tool to be used to ask a quick question of the package management system; namely "aptitude".
Let's see what happens if we try and install "aptitude":
```

sudo apt-get install aptitude

```
Now if it installs do:
```

aptitude why initramfs-tools-bin_0.99ubuntu13.2

```
To get an idea of what we have to do.
-----------------
Once more, please place your outputs between code tags. Makes it much easier to read and when you read as much "code" as we do .. IT makes a huge difference ! Me, I do it like so .. type {code] paste my text and then type {/code] -here replace "{ with [ ..see BBCode list.

[INDENT][INDENT][INDENT]just what I think
[/INDENT][/INDENT][/INDENT]

---

### Post by alrick_lothian on 2013-09-25
Thanks for all your efforts, please be patient with me. I am not so savvy with ubuntu yet.
Here is the out put for the code, it did not install. I am also placing the output of the codes you suggested between the number(#) lines. I did not understand how to place your outputs between code tags.

alrick@Home:~$ sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: libboost-iostreams1.46.1 (>= 1.46.1-1) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
            Recommends: libparse-debianchangelog-perl but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alrick@Home:~$ ########################################################

---

### Post by Bashing-om on 2013-09-25
alrick_lothian; Hey !

Not to know is not a sin ! .. None of us were born knowing what we know. This is as in all things a constant learning process.
Code tags- a biggy ! ///
Look above where you are posting at the 3 rows of tool bars, 2nd row, 3rd from right end is the "#" symbol.
click on it and that application will be placed onto the post page, right click (most browsers) and select "paste" and the contents are then pasted in between the code tags (provided that the cursor has not moved from that default position). Easy as that. Which does the same as my manual method instruction.

OK> Messing about with initramfs is not something to be entered into lightly, and I am going to exercise extraordinary care in this particular !
We need to know what application is using that later version of "initramfs-tools-bin" - that is holding us up. Now as we can not install anything we must use the tools at our disposal on the system.
initramfs == initiate ram file system ; That process is the heart and the soul of the operating system ! It even controls process identification number 1 (PID1).
Let's try this:
Software Sources -> other sources; uncheck all 3rd party sources;
now let's see if the package manager will run:
```

sudo apt-get update
sudo apt-get upgrade

```

If that runs successfully I have in mind a procedure to try, prior to getting dirty with that most crucial initramfs process. 

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by alrick_lothian on 2013-09-25
Thanks for your patience. I think we might accomplish a lot more if I could give you a call, or text a number I can call you at to 914-552-3364.  Then this process would be much faster. There a few things I am not getting.
Anyway.  Here is the output of the code with all the 3rd parties unchecked

```
alrick@Home:~$ sudo apt-get update
[sudo] password for alrick: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [418 kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [95.7 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [8,343 B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [689 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [216 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [709 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [220 kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources [88.4 kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources [28.0 kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources [1,804 B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages [318 kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages [82.3 kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages [2,449 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [337 kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages [85.7 kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages [2,640 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 3,471 kB in 2s (1,339 kB/s)               
Reading package lists... Done
alrick@Home:~$ #######################################################
```

---

### Post by Bashing-om on 2013-09-26
alrick_lothian;

There is no need to resort to the voice land line .. please follow instructions. // Be aware I am also actively working 4 other threads//
This forum is for all people seeking whatever .. keep all communications in the open for all to observe, and have our peer reviews.
May I suggest that you edit your post and remove the personal info - web crawlers and spiders, no telling what use will be made of the information.


Please use the code tags ! // conserves page space and increases readability ! - for any code output !

OK you did the first part and it looks good .. 
now /// between code tags.
```

sudo apt-get upgrade

```

will see what we will be able to do.

[INDENT][INDENT]it is all a process
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-26
alrick@Home:~$ sudo apt-get upgrade
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ ##########################################################

---

### Post by Bashing-om on 2013-09-26
blueboy1; Well, About what I had expected, but hoped for better.

Still reluctant to get down and dirty so, Let's try and stay within what the package manage may be able to do for us.
Manually removing  "initramfs-tools-bin" and then not able to (re)install it  would make for a real bad day.
Only as a start do terminal codes: - with all PPAs still not enabled -
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get -f install
##Then run:
sudo dpkg --configure -a
##Then run this again:
sudo apt-get -f install

```
If the output is:
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded; or similar,
That means it failed.-> Which I fully expect. I want to see where we stand with the above before continuing to allow the package manager to handle this situation. 

I am working toward an end.

[INDENT][INDENT]all things can be good
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-26
Thanks once agian, I hope we are getting somewhere.  Should I have no fear?
Hear is the out put for the instructed codes.

alrick@Home:~$ sudo apt-get clean
[sudo] password for alrick: 
alrick@Home:~$ sudo apt-get clean
alrick@Home:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alrick@Home:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 58 not upgraded.
2 not fully installed or removed.
Need to get 49.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main initramfs-tools all 0.99ubuntu13.2 [49.2 kB]
Fetched 49.2 kB in 0s (157 kB/s)           
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 initramfs-tools
 apparmor
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$ ##############################################################
alrick@Home:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 apparmor
alrick@Home:~$ ###############################################################
alrick@Home:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 58 not upgraded.
2 not fully installed or removed.
Need to get 0 B/49.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 initramfs-tools
 apparmor
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$ ##############

---

### Post by Bashing-om on 2013-09-26
blueboy1; 
Please please take the time to learn to use the code tags to relay your outputs !

OK, That last was pretty well as expected: next step do:
```

sudo apt-get -u dist-upgrade

```
Which I do not expect to see anything new .. just checking:

If it shows any held packages, it is best to eliminate them. Packages are held because of dependency conflicts that apt cannot resolve. Try this command to find and repair the conflicts:
```

sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade

```
If it cannot fix the conflicts, it will exit with:
0 upgraded, 0 newly installed, 0 to remove and 256 not upgraded. - or some such -
Now this is the dreaded point where we are down to ... manually interceding !

We are going to Delete the held packages one by one, running dist-upgrade each time, until there are no more held packages. Then reinstall any needed packages. Be sure to use the --dry-run option, so that you are fully informed of consequences: Before doing the actual real thing.
```

sudo apt-get remove --dry-run initramfs-tools-bin

```
Simply because I want to know what damage is going to be done when we do this for real.

[INDENT][INDENT]small steps but making progress
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-26
Hi I am sooo, sorry can you please help me once again learn to use the code tags to relay your outputs ! My machine is acting very slow going back and forth is difficult.
Anyway this is the output for the codes.


alrick@Home:~$ sudo apt-get -u dist-upgrade
[sudo] password for alrick: 
Sorry, try again.
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ ##########################################################
alrick@Home:~$ sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ #################################################################alrick@Home:~$ sudo apt-get remove --dry-run initramfs-tools-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (>= 0.99ubuntu13.1) but it is not going to be installed
                   Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alrick@Home:~$ ##########################################################

---

### Post by Bashing-om on 2013-09-26
blueboy1;
Code tag usage:
you have some text output "copied" to the system's clipboard - to be transferred to the thread, ready to insert that text.. ok,
above your posting are the tool bars (3), the second row of tool bars, 3rd symbol from the right end is "#".
Click "#", and that will place the code tag utility prompt within your post, at the position of the cursor;
right click and choose "paste" from that resulting drop down box and that clipboard text will be "pasted" between the code tags as required.

OK< back to the subject at hand...The package manager will not deal with the problem of initramfs-tools-bin for us; as much as I had hoped that it would. Good news is that it reports nothing else will be touched. The package manager advises it is On us to cope with it !

Presently we do not know what application has that higher version installed, but, several times the package manager has advised us to remove "winetricks".. Let's do so, as I can see no harm in doing so and then see what the package manager has to say. I really do not want to take the risk of (re-)installing initramfs-tools-bin until it is our last option.
```

sudo apt-get remove --purge winetricks

```
Chances are the package manager has already removed "winetricks", if so good !
Now to make sure all residual "orphaned" files are removed on your system:
```

sudo apt-get --purge autoremove

```

Finally let's see where we stand prior to removing "initramfs-tools-bin" .
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]prepared to JUMP
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-26
Thanks, I could not get to this screen before as I was doing quick reply. 
Here are our results. 

```

alrick@Home:~$ ##########################################################
alrick@Home:~$ 
alrick@Home:~$ 
alrick@Home:~$ 
alrick@Home:~$ sudo apt-get remove --purge winetricks
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alrick@Home:~$ #############################################################
alrick@Home:~$ sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ ######################################################
alrick@Home:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [216 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [689 kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [220 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [709 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en [127 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 2,072 kB in 2s (1,034 kB/s)
Reading package lists... Done
alrick@Home:~$ 
alrick@Home:~$ ##################################################
alrick@Home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ #######################################
```

---

### Post by blueboy1 on 2013-09-26
Thanks, I could not get to this screen before as I was doing quick reply. 
Here are our results. 


```
alrick@Home:~$ ##########################################################
alrick@Home:~$ 
alrick@Home:~$ 
alrick@Home:~$ 
alrick@Home:~$ sudo apt-get remove --purge winetricks
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

alrick@Home:~$ #############################################################
alrick@Home:~$ sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.

alrick@Home:~$ ######################################################
alrick@Home:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [216 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [689 kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [220 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [709 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en [127 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 2,072 kB in 2s (1,034 kB/s)
Reading package lists... Done


alrick@Home:~$ 
alrick@Home:~$ ##################################################
alrick@Home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ ####################################### 
```

---

### Post by Bashing-om on 2013-09-26
blueboy1; You are cross posting ! I caught your reply in the alternate thread,

OK Let's look first before we leap:
```

sudo apt-get remove -s initramfs-tools-bin

```
the "s" option is "simulate" will tell us what it will do.

[INDENT][INDENT]almost almost
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-26
```

```

alrick@Home:~$ sudo apt-get remove -s initramfs-tools-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (>= 0.99ubuntu13.1) but it is not going to be installed
                   Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alrick@Home:~$

---

### Post by oldfred on 2013-09-26
@blueboy1
You started two new threads. Please do not start new threads on same topic. Merged.

---

### Post by Bashing-om on 2013-09-27
blueboy1; See oldfred's last.

Jump !
```

sudo apt-get remove initramfs-tools-bin
sudo apt-get install initramfs-tools-bin
sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]where are we now
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-27
```
alrick@Home:~$ sudo apt-get remove -s initramfs-tools-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (>= 0.99ubuntu13.1) but it is not going to be installed
                   Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alrick@Home:~$ 
alrick@Home:~$ 
alrick@Home:~$ 
alrick@Home:~$ 
alrick@Home:~$ sudo apt-get remove initramfs-tools-bin
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (>= 0.99ubuntu13.1) but it is not going to be installed
                   Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alrick@Home:~$ #####################################################
alrick@Home:~$ sudo apt-get install initramfs-tools-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
initramfs-tools-bin is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alrick@Home:~$ ######################################################
alrick@Home:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [216 kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [689 kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [220 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [709 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 1,934 kB in 1s (1,030 kB/s)              
Reading package lists... Done
alrick@Home:~$ #######################################################
alrick@Home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
alrick@Home:~$ 
```

---

### Post by Bashing-om on 2013-09-27
blueboy1; 
See my last .. we are looking as good as can be .. go ahead and 
jump!
[INDENT][INDENT]standing by
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-27
I do not understand, can you explain?

---

### Post by Azyx on 2013-09-27
Why did you not try ```
**apt-get -f install**
``` as they recomended?

---

### Post by slickymaster on 2013-09-27
Try the following first:```
sudo dpkg --configure --pending
sudo apt-get -f install
```If the situation persists run```
sudo dpkg --audit
```to see if its output can provide you same more information.

---

### Post by Toz on 2013-09-27
Duplicate threads merged again.

---

### Post by Bashing-om on 2013-09-27
blueboy1; Good morning (mine) !
I am sorry if my use of American idioms is a source of confusion. I will refrain and henceforth use proper English grammar.

Your attention is invited to slickymaster's last advisement. Please comply with that advise given, as it is better to err on the side of caution.

Then we will continue in the effort to enable Wine on your system.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by mike112 on 2013-09-27
Hi all, I found this while searching to solve a nearly identical problem (although wine has nothing to do with it for me).  I just completed a dist-upgrade and had this problem afterwards.  Some outputs previously requested follow, and I expect blueboy's would look near identical.  Please see below as I walk through the process.

My solution is towards the bottom.  YMMV.

```
$ sudo dpkg --configure --pendingdpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 udev
 apparmor

```

So all three packages are waiting for the initramfs-tools-bin dependency to be met...  sudo apt-get -f install fails with the same dependency issues:

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-32-generic linux-headers-3.5.0-36-generic linux-headers-3.5.0-39-generic linux-headers-3.5.0-32 linux-headers-3.5.0-34 linux-headers-3.5.0-36 linux-headers-3.5.0-37 linux-headers-3.5.0-39
  linux-headers-3.5.0-34-generic linux-headers-3.5.0-37-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0 B/49.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfiguredNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                     No apport report written because the error message indicates its a followup error from a previous failure.
                  No apport report written because the error message indicates its a followup error from a previous failure.


Errors were encountered while processing:
 initramfs-tools
 apparmor
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And the audit confirms what we're looking at:

```
$ sudo dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 udev                 rule-based device node and kernel event manager
 apparmor             User-space parser utility for AppArmor


The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      tools for generating an initramfs
```

Seeing I am running this on a virtual machine, I just took a snapshot of the image and tried brute force:

```
$ sudo dpkg -P initramfs-tools-bin
$ # Override dependency (not recommended, but worked for me!):
$ sudo sed -i -e 's/0.99ubuntu13.1.1~/0.99ubuntu13.2~/' /var/lib/dpkg/status
$ sudo apt-get -f install

```

That worked.  After rebooting, I ran upgrade again, which brought initramfs-tools up to the same level as initramfs-tools-bin:

```
$ sudo apt-get upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  qemu-kvm
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/49.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
Selecting previously unselected package initramfs-tools.
(Reading database ... 58459 files and directories currently installed.)
Preparing to replace initramfs-tools 0.99ubuntu13.1 (using .../initramfs-tools_0.99ubuntu13.2_all.deb) ...
Unpacking replacement initramfs-tools ...
Processing triggers for man-db ...
Setting up initramfs-tools (0.99ubuntu13.2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-41-generic
$ 
```

As part of upgrading initramfs-tools, it also overwrote my dependency hack.  It looks like everything is safe and stable again, though I'm hanging on to that snapshot for a while!

---

### Post by blueboy1 on 2013-09-28
This seemed so similar to my experience. I noticed that only this line in the audit was different (udev rule-based device node and kernel event manager).
I tried some of what you suggested, except nothing happened when I tried the the following codes

$ # Override dependency (not recommended, but worked for me!):
$ sudo sed -i -e 's/0.99ubuntu13.1.1~/0.99ubuntu13.2~/' /var/lib/dpkg/status

---

### Post by blueboy1 on 2013-09-28
Here is the results from trying the suggested codes.
```

```

alrick@Home:~$ sudo dpkg --configure --pending
[sudo] password for alrick: 
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (>= 0.99ubuntu13.1); however:
  Package initramfs-tools-bin is not installed.
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.2~); however:
  Package initramfs-tools-bin is not installed.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 apparmor
alrick@Home:~$ #######################################################
alrick@Home:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  initramfs-tools initramfs-tools-bin
The following NEW packages will be installed:
  initramfs-tools-bin
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 1 newly installed, 0 to remove and 61 not upgraded.
2 not fully installed or removed.
Need to get 0 B/59.1 kB of archives.
After this operation, 122 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package initramfs-tools-bin.
(Reading database ... 594847 files and directories currently installed.)
Unpacking initramfs-tools-bin (from .../initramfs-tools-bin_0.99ubuntu13.2_amd64.deb) ...
Setting up initramfs-tools-bin (0.99ubuntu13.2) ...
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.2~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 initramfs-tools
 apparmor
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$ ####################################################
alrick@Home:~$ sudo dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 apparmor             User-space parser utility for AppArmor

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      tools for generating an initramfs

---

### Post by blueboy1 on 2013-09-28
I tried many times. Look under any of the threads.

---

### Post by Bashing-om on 2013-09-28
blueboy1; Hello .

I remain with you. Presently I do not have a means to (re)install "initramfs-tools-bin" properly. I continue to give this my consideration and seek a solution.

most intriguing 
most aggravating 

[INDENT][INDENT]I shall return
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-29
thanks for your persistence. waiting to follow any other suggestion you make.

---

### Post by Bashing-om on 2013-09-29
blueboy1; Good morning .

I presently do not understand:
1. winetricks: we have removed it and it is still popping up
> 
The following package was automatically installed and is no longer required:
winetricks

2. With the application of generic "apt-get remove  initramfs-tools-bin " does not remove both versions; (>= 0.99ubuntu13.1) and (<< 0.99ubuntu13.2~);as I had anticipated.

-------------
Maybe because the 3rd party PPAs are not enabled ?
Let's try this:
from the Software Center ->other sources; (re)enable those PPAs and see what results:
Terminal codes:
```

apt-get remove winetricks
apt-get remove initramfs-tools-bin

```
Else I am also considering the effects of forcing the removal of "initramfs-tools-bin" and the proper syntax to do so.
_________
Code tags; a picture is worth a thousand words: see if this gives better instruction on usage:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-29
Hey, look at what you got!!  That was brillantly simply.  Thanks a lot for you patience. Here is the result of the codes:
```
alrick@Home:~$ apt-get remove winetricks
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
alrick@Home:~$ 

```

```
alrick@Home:~$ apt-get remove initramfs-tools-bin
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
alrick@Home:~$ 

```

---

### Post by Bashing-om on 2013-09-29
blueboy1; Sorry,
That last of mine was thoughtless-ness on my part ..Got to have admin privileges - sudo !
do:
```

sudo apt-get remove winetricks
sudo apt-get remove initramfs-tools-bin

```
And Yes ! code tags makes it much easier to read that output -- formatting helps greatly !

[INDENT]still look'n to see what we can do
[/INDENT]

---

### Post by blueboy1 on 2013-09-29
```
alrick@Home:~$ sudo apt-get remove winetricks
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.2~) but 0.99ubuntu13.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```
alrick@Home:~$ sudo apt-get remove initramfs-tools-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (>= 0.99ubuntu13.1) but it is not going to be installed
                   Depends: initramfs-tools-bin (< 0.99ubuntu13.2~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alrick@Home:~$ 

```

---

### Post by Bashing-om on 2013-09-30
blueboy1; Well .......

I continue to flounder .. still looking for a solution .. I really do not think a forced removal would be any more effective than what has been attempted.
Nor do I fully understand what the package manager is telling us - 2 versions of "initramfs-tools-bin" installed ?
What results from terminal commands:
```

dpkg -l initramfs-tools-bin
apt-cache policy initramfs-tools-bin

```
EDIT: in addition:
```

apt-cache showpkg initramfs-tools-bin

```


Continue to look for a means to direct our efforts.

---

### Post by blueboy1 on 2013-09-30
Here is the output.
```
alrick@Home:~$ dpkg -l initramfs-tools-bin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  initramfs-tool 0.99ubuntu13.2 binaries used by initramfs-tools

```
```
alrick@Home:~$ apt-cache policy initramfs-tools-bin
initramfs-tools-bin:
  Installed: 0.99ubuntu13.2
  Candidate: 0.99ubuntu13.2
  Version table:
 *** 0.99ubuntu13.2 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.99ubuntu13 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```

```
alrick@Home:~$ apt-cache showpkg initramfs-tools-bin
Package: initramfs-tools-bin
Versions: 
0.99ubuntu13.2 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
                  MD5: 14e601bd8c0a0905d238d89be3036fa8
 Description Language: en
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: 14e601bd8c0a0905d238d89be3036fa8

0.99ubuntu13 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
                  MD5: 14e601bd8c0a0905d238d89be3036fa8
 Description Language: en
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: 14e601bd8c0a0905d238d89be3036fa8


Reverse Depends: 
  initramfs-tools,initramfs-tools-bin 0.99ubuntu13.2~
  initramfs-tools,initramfs-tools-bin 0.99ubuntu13.1
  initramfs-tools-bin:i386,initramfs-tools-bin
  initramfs-tools,initramfs-tools-bin 0.99ubuntu13.2.1~
  initramfs-tools,initramfs-tools-bin 0.99ubuntu13.2
  initramfs-tools-bin:i386,initramfs-tools-bin
  initramfs-tools,initramfs-tools-bin 0.99ubuntu13.1~
  initramfs-tools,initramfs-tools-bin 0.99ubuntu13
Dependencies: 
0.99ubuntu13.2 - libc6 (2 2.4) libudev0 (2 147) initramfs-tools-bin:i386 (0 (null)) 
0.99ubuntu13 - libc6 (2 2.4) libudev0 (2 147) initramfs-tools-bin:i386 (0 (null)) 
Provides: 
0.99ubuntu13.2 - 
0.99ubuntu13 - 
Reverse Provides: 

```

---

### Post by Bashing-om on 2013-09-30
blueboy1;
Hey.
I do believe that confirms that there are two versions on your system .. lets see if we can get the lower version to install in place of that higher version:
```

sudo apt-get install initramfs-tools-bin=0.99ubuntu13
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean

```

The result we want to see:
> 
The following packages will be DOWNGRADED:
initramfs-tools-bin
0 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 1 not upgraded.

[INDENT][INDENT]fingers are crossed
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-09-30
Here are the ouput for the codes:
```
alrick@Home:~$ sudo apt-get install initramfs-tools-bin=0.99ubuntu13
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (>= 0.99ubuntu13.1) but 0.99ubuntu13 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```
alrick@Home:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.2~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.

```

```
alrick@Home:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.2~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.

```

```
alrick@Home:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

### Post by Bashing-om on 2013-09-30
blueboy1; Yuk !

This situation is contrary to all documentation I can find; Can not remove, can not install, can not change. I was fairly sure that last would resolve the dependency issue. It "looked" good to do .

I am back to the drawing board once more.

[INDENT][INDENT]I'll Be Back
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-01
blueboy1; Hey !

I am at my wits end on this. I do not know how to determine the why in this situation and am left with a blind how:
let's try this to FORCE the removal:
With all sources and PPAs enabled:
first in specific:
```

dpkg --remove --force-remove-reinstreq initramfs-tools-bin_0.99ubuntu13.1
dpkg --remove --force-remove-reinstreq initramfs-tools-bin_0.99ubuntu13

```

Now DIS-able the 3rd party PPA's and try and install:
```

sudo apt-get install initramfs-tools-bin

```

Again; this is a case;
[INDENT][INDENT][INDENT]sometimes I wonder, other times I do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-01
I suppose not much has changed. 

```
alrick@Home:~$ sudo dpkg --remove --force-remove-reinstreq initramfs-tools-bin_0.99ubuntu13.1
[sudo] password for alrick: 
dpkg: warning: there's no installed package matching initramfs-tools-bin_0.99ubuntu13.1

```

```
alrick@Home:~$ sudo dpkg --remove --force-remove-reinstreq initramfs-tools-bin_0.99ubuntu13
dpkg: warning: there's no installed package matching initramfs-tools-bin_0.99ubuntu13

```

```
alrick@Home:~$ sudo apt-get install initramfs-tools-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
initramfs-tools-bin is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.2~) but 0.99ubuntu13.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by blueboy1 on 2013-10-01
Bashing-om, please take a look at page #4 at mike112 post. It is very similar to what I am experiencing. Their is only a one line difference. I tried it however and did not get the outcome as was expected. I am thinking that you could get a clue from that post.

---

### Post by Bashing-om on 2013-10-01
blueboy1; Yes I was aware of Mike's contribution .. and it may have merit. However, we do not know the why to this time and that makes any determination to how to fix very iffy; and in my mind may only add to our difficulties.

I will look at it once again, but I am always leery of doing anything to circumvent the checks and balances within the package manager's protocols.
Though admittedly there are those times the package manager does need a helping hand.

[INDENT][INDENT]always good to know why
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-01
I got you.

---

### Post by Bashing-om on 2013-10-01
blueboy1; my response:

> 
$ sudo sed -i -e 's/0.99ubuntu13.1.1~/0.99ubuntu13.2~/' /var/lib/dpkg/status

"sed" is Streamline EDitor, to manipulate text within a file. Be aware that that is a utility I rarely employ and not too familiar with it and with out research I do not completely understand the options and syntax that is in use in that instance. In essence - I think - search in the file "status" located in the path "/var/lib/dpkg", editing the file in place, 'looking for a separate entry, find the string  "/0.99ubuntu1.1~"', and replace all occurrences with the string "0.99ubuntu13.2.1". I can not say from my own knowledge where all those occurrences and exchanges would happen.

Now, If I read that correctly - is not what we want to do, -as in -  I think we need to downgrade that package. It is my hope that the force removal commands will fix this situation. And in the process tell us what application requires the later version of "initramfs-tools-bin" and point us to why we cannot rid our selfs of "winetricks". I am sure there must be a way .. outside of "aptitude". Presently I can not think of a way. 

My lack of familiarity with Wine could also be hampering us .. in that maybe "winetricks" as a component of Wine can not be removed so long as "wine" is present ... even though "winetricks" may have been installed separately and is a separate package.

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-01
blueboy1; Addendum to my last:

Further thought, let's say that the control file "status" is relaying bad information, Let's try and look at what is actually installed on the system:
```

sudo find / -name "initramfs-tools-bin*"

```
not that I actually expect it to find the binary files that have been installed, but hope for some additional guidance.
The command may take a bit of time to complete as it is searching all files on your system from the "/" directory.

[INDENT][INDENT]gotta be a way
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-01
So, here is somethings to consider. I did not tell you that I have virtual box installed on my system. I don't know if that has anything to do with anything, just FYI.
Also here is the output for the last code you suggested. 

```
alrick@Home:~$ sudo find / -name "initramfs-tools-bin*"
[sudo] password for alrick: 
/usr/share/doc/initramfs-tools-bin
/var/lib/dpkg/info/initramfs-tools-bin.md5sums
/var/lib/dpkg/info/initramfs-tools-bin.list
/var/cache/apt/archives/initramfs-tools-bin_0.99ubuntu13.2_amd64.deb

```

---

### Post by Bashing-om on 2013-10-01
blueboy1;

The mystery deepens:
your output;
> 
/var/cache/apt/archives/initramfs-tools-bin_0.99ubuntu13.2_amd64.deb

where in the world did that re-appear from, had we not cleared all cache earlier ?

And as to VM .. do you mean that you are running this install from inside that virtual world or that the VM is installed to be run from within this operating system. I do not see how it matters, a file system is a file system. But any way, we still have to get rid of that later version of /initramfs-tools-bin.

[INDENT][INDENT]got to be a way 
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-01
Hi it's the latter, it runs from within the operating system.

---

### Post by Bashing-om on 2013-10-01
blueboy1; 

Running in the VM, should not make a difference. That operating system is isolated and sandboxed. Software wise it is just a file system.

Let me get a fresh mind on this in my AM, look things over for a fresh perspective .. and see if we still want to do a forced removal in light of 
"/var/cache/apt/archives/initramfs-tools-bin_0.99ubuntu13.2_amd64.deb" popping up.

[INDENT][INDENT]still in the dark
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-01
We are not in the dark, we are a step closer. Will follow up in the AM.

---

### Post by Bashing-om on 2013-10-02
blueboy1;

I am working on this (have been all morning) trying to come up with a new plan of attack .

I will holler at ya soon as I have it formulated.

{just so you know I have not left you hanging}

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-02
blueboy1; shame-faced me.

I am in error and have been barking up the wrong tree, in respect to the version of "initrmafs-tools-bin: that should be installed !

Per:
[http://packages.ubuntu.com/search?suite=precise-updates&searchon=names&keywords=initramfs-tools-bin](http://packages.ubuntu.com/search?suite=precise-updates&searchon=names&keywords=initramfs-tools-bin)

UPDATED 12.04.3 should have version 0.99ubuntu13.2. 

Let's see what results when we try and install the correct version:
```

sudo dpkg -i /var/cache/apt/archives/initramfs-tools-bin_0.99ubuntu13.2_amd64.deb

```

And get a new perspective on things.

[INDENT][INDENT]2 steps forward and 3 back, better traction now ?
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-02
Here it is:

```
alrick@Home:~$ sudo dpkg -i /var/cache/apt/archives/initramfs-tools-bin_0.99ubuntu13.2_amd64.deb
[sudo] password for alrick: 
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace initramfs-tools-bin 0.99ubuntu13.2 (using .../initramfs-tools-bin_0.99ubuntu13.2_amd64.deb) ...
Unpacking replacement initramfs-tools-bin ...
Setting up initramfs-tools-bin (0.99ubuntu13.2) ...

```

---

### Post by Bashing-om on 2013-10-02
blueboy1; My My ..

That looks promising !
try:
```

sudo apt-get update
sudo apt-get upgrade

```
just to see if we are operational at this time.

[INDENT][INDENT]5 steps forward ?
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-02
So, here are the output
```
alrick@Home:~$ sudo apt-get update
[sudo] password for alrick: 
Hit http://archive.ubuntu.com precise Release.gpg
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://archive.ubuntu.com precise-backports Release.gpg
Get:2 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.ubuntu.com precise Release
Get:4 http://archive.ubuntu.com precise-updates Release [49.6 kB]
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]
Hit http://archive.ubuntu.com precise-backports Release                        
Get:6 http://archive.ubuntu.com precise-proposed Release [49.6 kB]
Get:7 http://security.ubuntu.com precise-security/universe amd64 Packages [82.8 kB]
Hit http://archive.ubuntu.com precise/universe Sources             
Hit http://archive.ubuntu.com precise/main Sources                 
Hit http://archive.ubuntu.com precise/multiverse Sources           
Hit http://archive.ubuntu.com precise/restricted Sources           
Hit http://archive.ubuntu.com precise/main amd64 Packages          
Hit http://archive.ubuntu.com precise/universe amd64 Packages      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages    
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages    
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/restricted i386 Packages
Hit http://archive.ubuntu.com precise/multiverse i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Get:8 http://archive.ubuntu.com precise-updates/universe amd64 Packages [217 kB]
Get:9 http://security.ubuntu.com precise-security/main amd64 Packages [324 kB] 
Get:10 http://archive.ubuntu.com precise-updates/main amd64 Packages [694 kB]
Get:11 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,449 B]
Get:12 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:13 http://security.ubuntu.com precise-security/universe i386 Packages [86.3 kB]
Get:14 http://security.ubuntu.com precise-security/main i386 Packages [343 kB] 
Get:15 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,640 B]
Get:16 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Get:17 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.9 kB]
Get:18 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [11.5 kB]
Get:19 http://archive.ubuntu.com precise-updates/universe i386 Packages [221 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Get:20 http://archive.ubuntu.com precise-updates/main i386 Packages [715 kB]   
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:21 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [14.0 kB]
Get:22 http://archive.ubuntu.com precise-updates/restricted i386 Packages [11.4 kB]
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://archive.ubuntu.com precise-backports/main i386 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Get:23 http://archive.ubuntu.com precise-proposed/universe amd64 Packages [22.6 kB]
Get:24 http://archive.ubuntu.com precise-proposed/main amd64 Packages [87.3 kB]
Get:25 http://archive.ubuntu.com precise-proposed/multiverse amd64 Packages [1,442 B]
Get:26 http://archive.ubuntu.com precise-proposed/restricted amd64 Packages [14 B]
Get:27 http://archive.ubuntu.com precise-proposed/universe i386 Packages [26.0 kB]
Get:28 http://archive.ubuntu.com precise-proposed/main i386 Packages [99.9 kB]
Get:29 http://archive.ubuntu.com precise-proposed/multiverse i386 Packages [1,449 B]
Get:30 http://archive.ubuntu.com precise-proposed/restricted i386 Packages [14 B]
Get:31 http://archive.ubuntu.com precise-proposed/main TranslationIndex [3,564 B]
Get:32 http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex [2,605 B]
Get:33 http://archive.ubuntu.com precise-proposed/restricted TranslationIndex [2,461 B]
Get:34 http://archive.ubuntu.com precise-proposed/universe TranslationIndex [2,850 B]
Hit http://archive.ubuntu.com precise/main Translation-en              
Hit http://archive.ubuntu.com precise/multiverse Translation-en       
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Get:35 http://archive.ubuntu.com precise-proposed/main Translation-en [33.1 kB]
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en
Get:36 http://archive.ubuntu.com precise-proposed/universe Translation-en [14.1 kB]
Fetched 3,195 kB in 2s (1,360 kB/s)                                 
Reading package lists... Done

```

```
alrick@Home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.2~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by Bashing-om on 2013-10-02
blueboy1; shucks !

Well, at least the error has changed to only less than - for some unknown package's requirement.

Lemme cogitate and look see what I am able to come up with now with this greater focus.


[INDENT][INDENT]what to do, what to do
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-02
blueboy1; Hey !

Maybe in fact the problem is "initramfs-tools" it's self is under-versioned !
let's look:
```

apt-cache policy initramfs-tools
dpkg -s initramfs-tools
dpkg -l initramfs-tools

```

[INDENT][INDENT]makes sense to me
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-02
Thanks once again for you patience. I think you are getting hot.  
Here is the code results:

```
alrick@Home:~$ apt-cache policy initramfs-tools
initramfs-tools:
  Installed: 0.99ubuntu13.1
  Candidate: 0.99ubuntu13.3
  Version table:
     0.99ubuntu13.3 0
        500 http://archive.ubuntu.com/ubuntu/ precise-proposed/main amd64 Packages
     0.99ubuntu13.2 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
 *** 0.99ubuntu13.1 0
        100 /var/lib/dpkg/status
     0.99ubuntu13 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```

```
alrick@Home:~$ dpkg -s initramfs-tools
Package: initramfs-tools
Status: install ok half-configured
Multi-Arch: foreign
Priority: optional
Section: utils
Installed-Size: 363
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: all
Version: 0.99ubuntu13.1
Config-Version: 0.99ubuntu13.1
Provides: linux-initramfs-tool
Depends: initramfs-tools-bin (>= 0.99ubuntu13.1), initramfs-tools-bin (<< 0.99ubuntu13.2~), klibc-utils (>= 1.5.9-1), busybox-initramfs (>= 1:1.13.3-1ubuntu5), cpio, module-init-tools, udev (>= 147~-5), findutils (>= 4.2.24), util-linux (>> 2.15~rc1)
Suggests: bash-completion
Breaks: cryptsetup (<< 2:1.1.0-2.1), elilo (<< 3.12-3.1~), lilo (<< 22.8-8.2~), mountall (<< 2.0~), s390-tools (<< 1.8.3-2~)
Conflicts: usplash (<< 0.5.50)
Conffiles:
 /etc/bash_completion.d/initramfs-tools 7eeb7184772f3658e7cf446945c096b1
 /etc/initramfs-tools/update-initramfs.conf e2026d4603e7161efaccca519aeb1297
 /etc/initramfs-tools/initramfs.conf 8801535d9bec98754eea6a172f956d42
 /etc/kernel/postrm.d/initramfs-tools e22d1ab0d7a7a1b66ae6d71ea4f21938
 /etc/kernel/postinst.d/initramfs-tools fe7713b9a74a10ed71d1e7dd93afc209
Description: tools for generating an initramfs
 This package contains tools to create and boot an initramfs for packaged 2.6
 Linux kernel. The initramfs is a gzipped cpio archive. At boot time, the
 kernel unpacks that archive into RAM, mounts and uses it as initial root file
 system. The mounting of the real root file system occurs in early user space.
 klibc provides utilities to setup root. Having the root on MD, LVM2, LUKS or
 NFS is also supported.
 Any boot loader with initrd support is able to load an initramfs archive.
Original-Maintainer: Debian kernel team <debian-kernel@lists.debian.org>

```

```
alrick@Home:~$ dpkg -l initramfs-tools
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iF  initramfs-tool 0.99ubuntu13.1 tools for generating an initramfs

```

---

### Post by Bashing-om on 2013-10-02
blueboy1; Regret the delay in responding.

I attempted to (re)boot into my 12.04 // and grub could no longer find my hard drives !

I continue to struggle with resolving initramfs-tool dependency.

I continue to be concerned with differing aspects of this situation.
For your reference, my apt-cache policy output:
> 
sysop1@1204-a:~$ apt-cache policy initramfs-tools
initramfs-tools:
  Installed: 0.99ubuntu13.2
  Candidate: 0.99ubuntu13.2
  Version table:
 *** 0.99ubuntu13.2 0
        500 [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.99ubuntu13 0
        500 [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) precise/main amd64 Packages
sysop1@1204-a:~$ 

note in your output the availability of version  0.99ubuntu13.3 0 (precise-proposed !)

My concern at this time is that if we attempt to update initramfs-tool ... will update to the latest available version, 

I am presently hung up on a method to download  the 0.99ubuntu13.2 0 .deb file, 

As soon as I get it fingered out I will be back !

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by oldfred on 2013-10-02
i am running 12.04.3, currently updated except for the upgrade to newer kernel that now comes with 12.04.3.

This is what I have:
```
fred@fred-Precise:~$ apt-cache policy initramfs-tools
initramfs-tools:
  Installed: 0.99ubuntu13.3
  Candidate: 0.99ubuntu13.3
  Version table:
 *** 0.99ubuntu13.3 0
        500 http://mirror.anl.gov/pub/ubuntu/ precise-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     0.99ubuntu13.2 0
        500 http://mirror.anl.gov/pub/ubuntu/ precise-updates/main amd64 Packages
     0.99ubuntu13 0
        500 http://mirror.anl.gov/pub/ubuntu/ precise/main amd64 Packages

```

---

### Post by Bashing-om on 2013-10-03
@ oldfred ; Thanks !

Now I am even more confused. My 12.04 ubuntu install is also fully updated but with the original 12.04.1 kernel series, recon that is the difference ?
In your opinion, is is safe to try and "apt-get install" initramfs-tools. What I had in mind was to see the result of attempting to go with "apt-get download" initramfs<version>.deb via '500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages' .
However, my lack of exact knowledge is biting me bad ! ... Do the archives house individual files ? Or, are we to download the wanted 13.2 version from "packages.ubuntu.com" with wget ??? Some time expended in attempting to see a .deb file in the archives ! Maybe I just do not have my syntax correct.

What is required at this time is the 13.2 version of initramfs-tools to be installed.

[INDENT][INDENT]still learning even after all these years 
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-10-03
I really do not know. 

Just tried updating laptop which I have not updated for months and got into a similar dependency loop which is with a :i386 file that should not even be there? So I am also working on my system.

---

### Post by blueboy1 on 2013-10-03
Sorry about your emerging predicament. Hope your solution comes faster than mine.

---

### Post by Bashing-om on 2013-10-03
@ oldfred, Thanks once more. All our systems "breaking" must be something in the air !

I will do the safe thing and try and download that .deb file ! Expanding my knowledge base .. I have yet to add to it this day, but it is early yet .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Azyx on 2013-10-03
Hope this can help. Checked my versions of 12.04LTS 64 bit, installed with about a year between.

I have different initramsf depending if I have checked in (Pre-released update) precise-proposed or not, in Repository settings...

initramfs-tools-bin 0.99ubuntu13.3  <-- precise-proposed checked
initramfs-tools-bin 0.99ubuntu13.2  <-- not checked


Azyx@Datorn:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

It was the same release on both my computes. One installed for a year ago and one just fore a couple of mounth ago, so It does not seems to depend on which version the orginal install was, but how you set repository updates?

/Cheers

Edit. I have backports also checked.

---

### Post by Bashing-om on 2013-10-03
@ Azyx; Thanks for the input, my thoughts also .. nice to have confirmation.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by Azyx on 2013-10-03
I have wonder why Ubuntu 12.04LTS 64bit, are instable compared to 10.04LTS 32-bit...and find now that I have backport checked....Maybe not a good idea to uncheck it ????

---

### Post by Bashing-om on 2013-10-03
@ Azyx; I agree, not a good thing to enable "backport" and "proposed" repository sources, unless one has a demonstrated need to do so .. When enabled one should be aware that these can and do break your stable system .. software from "backports" should work but can not fit every configuration; where as "proposed" is just that .. maybe ! .. proposed is for development work/testing -expect breakage.

[INDENT][INDENT]but ain't ubuntu wonderful
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-10-03
I found my fix. I went thru a lot on my own and had just about figured it out on my own, when I found this which was the bottom line. But I had to use dpkg with the force command to purge the incorrect versions which were i386 in my case and then download and force install of correct venison. Then it seems to let me update and work. 

Do not know if similar forcing of an uninstall & reinstall my work for you or not. Force can be dangous as you can get things totally out of sync.  -r is remove some other threads have used -P which is the same per man dpkg. And -i is install.

  Internal Error, No file name for libapt-pkg4.12
[http://ubuntuforums.org/showthread.php?t=2045321](http://ubuntuforums.org/showthread.php?t=2045321)
Put pre-released back on then,
sudo dpkg --configure -a
sudo dpkg --force-depends -r libapt-pkg4.12:i386
sudo dpkg --force-depends -r libapt-inst1.4:i386
sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb

---

### Post by blueboy1 on 2013-10-03
it this something worth trying.

---

### Post by Bashing-om on 2013-10-03
blueboy1; Certainly worth considering .. 

Presently I am working to get freed up and craft that code for "apt-get download" to make sure we get the desired file. Just need now to make sure my t's are crossed and the i's have dots in my prospective procedure.

Back soonest.

[INDENT][INDENT]it can happen
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-03
blueboy1; Yep, I am back !

Ok, let's try this:
In software sources turn off "proposed" repository;
and in terminal:
```

cd /var/cache/apt/archives/ ##unless you want to "keep" this file elsewhere
wget http://mirrors.us.kernel.org/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.2_all.deb
sudo dpkg -i /var/cache/apt/archives/initramfs-tools_0.99ubuntu13.2_all.deb
cd ## returns ya to /home as the  PWD
sudo update-initramfs -u
sudo apt-get update
sudo apt-get upgrade

```

Now are we in shape to address other issues ?

[INDENT][INDENT]I think, I hope, maybe
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-03
Seemed like we are unto something good. Some thing significant happened.  Please evaluate the outcome and see. 

```
Get:69 http://security.ubuntu.com/ubuntu/ precise-security/main python3.2-minimal amd64 3.2.3-0ubuntu3.5 [1,776 kB]
Get:70 http://security.ubuntu.com/ubuntu/ precise-security/main libraw5 amd64 0.14.4-0ubuntu2.2 [317 kB]
Get:71 http://security.ubuntu.com/ubuntu/ precise-security/main python-openssl amd64 0.12-1ubuntu2.1 [99.8 kB]
Get:72 http://security.ubuntu.com/ubuntu/ precise-security/main python-software-properties all 0.82.7.5 [22.3 kB]
Get:73 http://security.ubuntu.com/ubuntu/ precise-security/main rtkit amd64 0.10-2ubuntu0.12.04.1 [36.3 kB]
Get:74 http://security.ubuntu.com/ubuntu/ precise-security/universe samba-tools amd64 2:3.6.3-2ubuntu2.8 [11.6 MB]
Get:75 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-common all 0.82.7.5 [8,944 B]
Get:76 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-gtk all 0.82.7.5 [34.6 kB]
Get:77 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-globalmenu amd64 1:24.0+build1-0ubuntu0.12.04.1 [8,786 B]
Get:78 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en amd64 1:24.0+build1-0ubuntu0.12.04.1 [343 kB]
Get:79 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird amd64 1:24.0+build1-0ubuntu0.12.04.1 [29.5 MB]
Get:80 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-gnome-support amd64 1:24.0+build1-0ubuntu0.12.04.1 [9,132 B]
Get:81 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en-us all 1:24.0+build1-0ubuntu0.12.04.1 [14.0 kB]
Get:82 http://security.ubuntu.com/ubuntu/ precise-security/main ubuntu-system-service all 0.2.2.1 [12.1 kB]
Get:83 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-gtk amd64 0.2.38.2 [26.9 kB]
Get:84 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-common amd64 0.2.38.2 [23.6 kB]
Get:85 http://security.ubuntu.com/ubuntu/ precise-security/main vino amd64 3.4.2-0ubuntu1.3 [170 kB]
Fetched 167 MB in 14min 34s (191 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.12 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.14) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.12 (using .../apt_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp12ubuntu10.14) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10.12 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace python2.7-dev 2.7.3-0ubuntu3.3 (using .../python2.7-dev_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-dev ...
Preparing to replace libpython2.7 2.7.3-0ubuntu3.3 (using .../libpython2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement libpython2.7 ...
Preparing to replace python2.7 2.7.3-0ubuntu3.3 (using .../python2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7 ...
Preparing to replace python2.7-minimal 2.7.3-0ubuntu3.3 (using .../python2.7-minimal_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-minimal ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Setting up python2.7-minimal (2.7.3-0ubuntu3.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace language-selector-gnome 0.79.3 (using .../language-selector-gnome_0.79.4_all.deb) ...
Unpacking replacement language-selector-gnome ...
Preparing to replace language-selector-common 0.79.3 (using .../language-selector-common_0.79.4_all.deb) ...
Unpacking replacement language-selector-common ...
Preparing to replace libldap-2.4-2 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_amd64.deb) ...
De-configuring libldap-2.4-2:i386 ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace libldap-2.4-2:i386 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_i386.deb) ...
Unpacking replacement libldap-2.4-2:i386 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up libldap-2.4-2 (2.4.28-1.1ubuntu4.4) ...
Setting up libldap-2.4-2:i386 (2.4.28-1.1ubuntu4.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-gnutls 7.22.0-3ubuntu4.2 (using .../libcurl3-gnutls_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-gnutls ...
Preparing to replace libpolkit-gobject-1-0 0.104-1ubuntu1 (using .../libpolkit-gobject-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-gobject-1-0 ...
Preparing to replace libaudio2:i386 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_i386.deb) ...
De-configuring libaudio2 ...
Unpacking replacement libaudio2:i386 ...
Preparing to replace libaudio2 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_amd64.deb) ...
Unpacking replacement libaudio2 ...
Setting up libaudio2:i386 (1.9.3-4ubuntu0.1) ...
Setting up libaudio2 (1.9.3-4ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3:i386 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_i386.deb) ...
De-configuring libcurl3 ...
Unpacking replacement libcurl3:i386 ...
Preparing to replace libcurl3 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3 ...
Setting up libcurl3:i386 (7.22.0-3ubuntu4.3) ...
Setting up libcurl3 (7.22.0-3ubuntu4.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-nss 7.22.0-3ubuntu4.2 (using .../libcurl3-nss_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-nss ...
Preparing to replace libpolkit-agent-1-0 0.104-1ubuntu1 (using .../libpolkit-agent-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-agent-1-0 ...
Preparing to replace libpolkit-backend-1-0 0.104-1ubuntu1 (using .../libpolkit-backend-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-backend-1-0 ...
Preparing to replace libpulse0 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
De-configuring libpulse0:i386 ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse0:i386 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_i386.deb) ...
Unpacking replacement libpulse0:i386 ...
Setting up libpulse0 (1:1.1-0ubuntu15.4) ...
Setting up libpulse0:i386 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulse-mainloop-glib0:i386 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulse-mainloop-glib0 ...
Unpacking replacement libpulse-mainloop-glib0:i386 ...
Preparing to replace libpulse-mainloop-glib0 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Setting up libpulse-mainloop-glib0:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulse-mainloop-glib0 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulsedsp:i386 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulsedsp ...
Unpacking replacement libpulsedsp:i386 ...
Preparing to replace libpulsedsp 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulsedsp ...
Setting up libpulsedsp:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulsedsp (1:1.1-0ubuntu15.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpam-winbind 2:3.6.3-2ubuntu2.7 (using .../libpam-winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libpam-winbind ...
Preparing to replace winbind 2:3.6.3-2ubuntu2.7 (using .../winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Unpacking replacement winbind ...
Preparing to replace samba 2:3.6.3-2ubuntu2.7 (using .../samba_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
nmbd stop/waiting
smbd stop/waiting
Unpacking replacement samba ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.7 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.7 (using .../smbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.7 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.7 (using .../samba-common_2%3a3.6.3-2ubuntu2.8_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.7 (using .../libsmbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.12 (using .../apt-utils_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace isc-dhcp-client 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-client_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-client ...
Preparing to replace isc-dhcp-common 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-common_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-common ...
Preparing to replace rsyslog 5.8.6-1ubuntu8.4 (using .../rsyslog_5.8.6-1ubuntu8.5_amd64.deb) ...
Unpacking replacement rsyslog ...
Preparing to replace ifupdown 0.7~beta2ubuntu8 (using .../ifupdown_0.7~beta2ubuntu10_amd64.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.12 (using .../apt-transport-https_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace apt-xapian-index 0.44ubuntu5 (using .../apt-xapian-index_0.44ubuntu5.1_all.deb) ...
Unpacking replacement apt-xapian-index ...
Preparing to replace linux-libc-dev 3.2.0-53.81 (using .../linux-libc-dev_3.2.0-54.82_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace firefox 23.0+build2-0ubuntu0.12.04.1 (using .../firefox_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-globalmenu_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-en_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace firefox-locale-zh-hans 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-zh-hans_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-zh-hans ...
Preparing to replace printer-driver-postscript-hp 3.12.2-1ubuntu3.1 (using .../printer-driver-postscript-hp_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement printer-driver-postscript-hp ...
Preparing to replace libsane-hpaio 3.12.2-1ubuntu3.1 (using .../libsane-hpaio_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace hplip 3.12.2-1ubuntu3.1 (using .../hplip_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.12.2-1ubuntu3.1 (using .../libhpmud0_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.12.2-1ubuntu3.1 (using .../hplip-data_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace printer-driver-hpcups 3.12.2-1ubuntu3.1 (using .../printer-driver-hpcups_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement printer-driver-hpcups ...
Preparing to replace policykit-1 0.104-1ubuntu1 (using .../policykit-1_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement policykit-1 ...
Preparing to replace hplip-gui 3.12.2-1ubuntu3.1 (using .../hplip-gui_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-gui ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.10 (using .../jockey-gtk_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.10 (using .../jockey-common_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace libpython3.2 3.2.3-0ubuntu3.4 (using .../libpython3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement libpython3.2 ...
Preparing to replace python3.2 3.2.3-0ubuntu3.4 (using .../python3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2 ...
Preparing to replace python3.2-minimal 3.2.3-0ubuntu3.4 (using .../python3.2-minimal_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2-minimal ...
Preparing to replace libraw5 0.14.4-0ubuntu2.1 (using .../libraw5_0.14.4-0ubuntu2.2_amd64.deb) ...
Unpacking replacement libraw5 ...
Preparing to replace libsyncdaemon-1.0-1 3.0.2-0ubuntu1 (using .../libsyncdaemon-1.0-1_3.0.2-0ubuntu2_amd64.deb) ...
Unpacking replacement libsyncdaemon-1.0-1 ...
Preparing to replace ubuntuone-client 3.0.2-0ubuntu1 (using .../ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement ubuntuone-client ...
Preparing to replace python-ubuntuone-client 3.0.2-0ubuntu1 (using .../python-ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement python-ubuntuone-client ...
Preparing to replace pulseaudio-utils 1:1.1-0ubuntu15.3 (using .../pulseaudio-utils_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace pulseaudio 1:1.1-0ubuntu15.3 (using .../pulseaudio_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio ...
Preparing to replace pulseaudio-module-gconf 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-gconf_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-gconf ...
Preparing to replace pulseaudio-module-x11 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-x11_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-x11 ...
Preparing to replace python-openssl 0.12-1ubuntu2 (using .../python-openssl_0.12-1ubuntu2.1_amd64.deb) ...
Unpacking replacement python-openssl ...
Preparing to replace python-software-properties 0.82.7.3 (using .../python-software-properties_0.82.7.5_all.deb) ...
Unpacking replacement python-software-properties ...
Preparing to replace rtkit 0.10-2 (using .../rtkit_0.10-2ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement rtkit ...
Preparing to replace samba-tools 2:3.6.3-2ubuntu2.7 (using .../samba-tools_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-tools ...
Preparing to replace software-properties-common 0.82.7.3 (using .../software-properties-common_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-common ...
Preparing to replace software-properties-gtk 0.82.7.3 (using .../software-properties-gtk_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-gtk ...
Preparing to replace thunderbird-globalmenu 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird-locale-en 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace thunderbird-locale-en-us 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a24.0+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Preparing to replace ubuntu-system-service 0.2.2 (using .../ubuntu-system-service_0.2.2.1_all.deb) ...
Unpacking replacement ubuntu-system-service ...
Preparing to replace usb-creator-gtk 0.2.38 (using .../usb-creator-gtk_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-gtk ...
Preparing to replace usb-creator-common 0.2.38 (using .../usb-creator-common_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-common ...
Preparing to replace vino 3.4.2-0ubuntu1.2 (using .../vino_3.4.2-0ubuntu1.3_amd64.deb) ...
Unpacking replacement vino ...
Preparing to replace gnome-settings-daemon 3.4.2-0ubuntu0.6.2 (using .../gnome-settings-daemon_3.4.2-0ubuntu0.6.3_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace pulseaudio-module-bluetooth 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-bluetooth_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-bluetooth ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for cups ...
Updating PPD files for hpcups ...
Updating PPD files for postscript-hp ...
Processing triggers for menu ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Setting up initramfs-tools (0.99ubuntu13.2) ...
update-initramfs: deferring update (trigger activated)
Setting up apparmor (2.7.102-0ubuntu3.9) ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.14) ...
Setting up python2.7 (2.7.3-0ubuntu3.4) ...
Setting up libpython2.7 (2.7.3-0ubuntu3.4) ...
Setting up python2.7-dev (2.7.3-0ubuntu3.4) ...
Setting up language-selector-common (0.79.4) ...
Setting up language-selector-gnome (0.79.4) ...
Setting up libcurl3-gnutls (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-gobject-1-0 (0.104-1ubuntu1.1) ...
Setting up libcurl3-nss (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-agent-1-0 (0.104-1ubuntu1.1) ...
Setting up libpolkit-backend-1-0 (0.104-1ubuntu1.1) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common (2:3.6.3-2ubuntu2.8) ...
Setting up winbind (2:3.6.3-2ubuntu2.8) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 
Setting up libpam-winbind (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.8) ...
Setting up samba (2:3.6.3-2ubuntu2.8) ...
smbd start/running, process 15315
nmbd start/running, process 15353
Setting up smbclient (2:3.6.3-2ubuntu2.8) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.8) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.14) ...
Setting up isc-dhcp-common (4.1.ESV-R4-0ubuntu5.9) ...
Setting up isc-dhcp-client (4.1.ESV-R4-0ubuntu5.9) ...
Setting up rsyslog (5.8.6-1ubuntu8.5) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
rsyslog stop/waiting
rsyslog start/running, process 15503
Setting up ifupdown (0.7~beta2ubuntu10) ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.14) ...
Setting up apt-xapian-index (0.44ubuntu5.1) ...
Setting up linux-libc-dev (3.2.0-54.82) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-52-generic
Building for architecture x86_64
Building initial module for 3.2.0-52-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-52-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up firefox (24.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-zh-hans (24.0+build1-0ubuntu0.12.04.1) ...
Setting up libhpmud0 (3.12.2-1ubuntu3.3) ...
Setting up libsane-hpaio (3.12.2-1ubuntu3.3) ...
Setting up hplip-data (3.12.2-1ubuntu3.3) ...
Setting up printer-driver-hpcups (3.12.2-1ubuntu3.3) ...
Setting up policykit-1 (0.104-1ubuntu1.1) ...
Setting up hplip (3.12.2-1ubuntu3.3) ...
Creating/updating hplip user account...
Setting up printer-driver-postscript-hp (3.12.2-1ubuntu3.3) ...
Setting up hplip-gui (3.12.2-1ubuntu3.3) ...
Setting up jockey-common (0.9.7-0ubuntu7.11) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.11) ...
Setting up python3.2-minimal (3.2.3-0ubuntu3.5) ...
Setting up python3.2 (3.2.3-0ubuntu3.5) ...
Setting up libpython3.2 (3.2.3-0ubuntu3.5) ...
Setting up libraw5 (0.14.4-0ubuntu2.2) ...
Setting up python-ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up libsyncdaemon-1.0-1 (3.0.2-0ubuntu2) ...
Setting up pulseaudio-utils (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-gconf (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-x11 (1:1.1-0ubuntu15.4) ...
Setting up python-openssl (0.12-1ubuntu2.1) ...
Setting up python-software-properties (0.82.7.5) ...
Setting up rtkit (0.10-2ubuntu0.12.04.1) ...
Setting up samba-tools (2:3.6.3-2ubuntu2.8) ...
Setting up software-properties-common (0.82.7.5) ...
Setting up software-properties-gtk (0.82.7.5) ...
Setting up thunderbird (1:24.0+build1-0ubuntu0.12.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-globalmenu (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up ubuntu-system-service (0.2.2.1) ...
Setting up usb-creator-common (0.2.38.2) ...
Setting up usb-creator-gtk (0.2.38.2) ...
Setting up vino (3.4.2-0ubuntu1.3) ...
Setting up gnome-settings-daemon (3.4.2-0ubuntu0.6.3) ...
Setting up pulseaudio-module-bluetooth (1:1.1-0ubuntu15.4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-52-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-52-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$ cd /var/cache/apt/archives/ ##unless you want to "keep" this file elsewhere

```

```
Get:69 http://security.ubuntu.com/ubuntu/ precise-security/main python3.2-minimal amd64 3.2.3-0ubuntu3.5 [1,776 kB]
Get:70 http://security.ubuntu.com/ubuntu/ precise-security/main libraw5 amd64 0.14.4-0ubuntu2.2 [317 kB]
Get:71 http://security.ubuntu.com/ubuntu/ precise-security/main python-openssl amd64 0.12-1ubuntu2.1 [99.8 kB]
Get:72 http://security.ubuntu.com/ubuntu/ precise-security/main python-software-properties all 0.82.7.5 [22.3 kB]
Get:73 http://security.ubuntu.com/ubuntu/ precise-security/main rtkit amd64 0.10-2ubuntu0.12.04.1 [36.3 kB]
Get:74 http://security.ubuntu.com/ubuntu/ precise-security/universe samba-tools amd64 2:3.6.3-2ubuntu2.8 [11.6 MB]
Get:75 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-common all 0.82.7.5 [8,944 B]
Get:76 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-gtk all 0.82.7.5 [34.6 kB]
Get:77 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-globalmenu amd64 1:24.0+build1-0ubuntu0.12.04.1 [8,786 B]
Get:78 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en amd64 1:24.0+build1-0ubuntu0.12.04.1 [343 kB]
Get:79 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird amd64 1:24.0+build1-0ubuntu0.12.04.1 [29.5 MB]
Get:80 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-gnome-support amd64 1:24.0+build1-0ubuntu0.12.04.1 [9,132 B]
Get:81 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en-us all 1:24.0+build1-0ubuntu0.12.04.1 [14.0 kB]
Get:82 http://security.ubuntu.com/ubuntu/ precise-security/main ubuntu-system-service all 0.2.2.1 [12.1 kB]
Get:83 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-gtk amd64 0.2.38.2 [26.9 kB]
Get:84 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-common amd64 0.2.38.2 [23.6 kB]
Get:85 http://security.ubuntu.com/ubuntu/ precise-security/main vino amd64 3.4.2-0ubuntu1.3 [170 kB]
Fetched 167 MB in 14min 34s (191 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.12 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.14) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.12 (using .../apt_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp12ubuntu10.14) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10.12 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace python2.7-dev 2.7.3-0ubuntu3.3 (using .../python2.7-dev_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-dev ...
Preparing to replace libpython2.7 2.7.3-0ubuntu3.3 (using .../libpython2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement libpython2.7 ...
Preparing to replace python2.7 2.7.3-0ubuntu3.3 (using .../python2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7 ...
Preparing to replace python2.7-minimal 2.7.3-0ubuntu3.3 (using .../python2.7-minimal_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-minimal ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Setting up python2.7-minimal (2.7.3-0ubuntu3.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace language-selector-gnome 0.79.3 (using .../language-selector-gnome_0.79.4_all.deb) ...
Unpacking replacement language-selector-gnome ...
Preparing to replace language-selector-common 0.79.3 (using .../language-selector-common_0.79.4_all.deb) ...
Unpacking replacement language-selector-common ...
Preparing to replace libldap-2.4-2 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_amd64.deb) ...
De-configuring libldap-2.4-2:i386 ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace libldap-2.4-2:i386 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_i386.deb) ...
Unpacking replacement libldap-2.4-2:i386 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up libldap-2.4-2 (2.4.28-1.1ubuntu4.4) ...
Setting up libldap-2.4-2:i386 (2.4.28-1.1ubuntu4.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-gnutls 7.22.0-3ubuntu4.2 (using .../libcurl3-gnutls_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-gnutls ...
Preparing to replace libpolkit-gobject-1-0 0.104-1ubuntu1 (using .../libpolkit-gobject-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-gobject-1-0 ...
Preparing to replace libaudio2:i386 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_i386.deb) ...
De-configuring libaudio2 ...
Unpacking replacement libaudio2:i386 ...
Preparing to replace libaudio2 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_amd64.deb) ...
Unpacking replacement libaudio2 ...
Setting up libaudio2:i386 (1.9.3-4ubuntu0.1) ...
Setting up libaudio2 (1.9.3-4ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3:i386 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_i386.deb) ...
De-configuring libcurl3 ...
Unpacking replacement libcurl3:i386 ...
Preparing to replace libcurl3 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3 ...
Setting up libcurl3:i386 (7.22.0-3ubuntu4.3) ...
Setting up libcurl3 (7.22.0-3ubuntu4.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-nss 7.22.0-3ubuntu4.2 (using .../libcurl3-nss_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-nss ...
Preparing to replace libpolkit-agent-1-0 0.104-1ubuntu1 (using .../libpolkit-agent-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-agent-1-0 ...
Preparing to replace libpolkit-backend-1-0 0.104-1ubuntu1 (using .../libpolkit-backend-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-backend-1-0 ...
Preparing to replace libpulse0 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
De-configuring libpulse0:i386 ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse0:i386 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_i386.deb) ...
Unpacking replacement libpulse0:i386 ...
Setting up libpulse0 (1:1.1-0ubuntu15.4) ...
Setting up libpulse0:i386 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulse-mainloop-glib0:i386 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulse-mainloop-glib0 ...
Unpacking replacement libpulse-mainloop-glib0:i386 ...
Preparing to replace libpulse-mainloop-glib0 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Setting up libpulse-mainloop-glib0:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulse-mainloop-glib0 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulsedsp:i386 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulsedsp ...
Unpacking replacement libpulsedsp:i386 ...
Preparing to replace libpulsedsp 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulsedsp ...
Setting up libpulsedsp:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulsedsp (1:1.1-0ubuntu15.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpam-winbind 2:3.6.3-2ubuntu2.7 (using .../libpam-winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libpam-winbind ...
Preparing to replace winbind 2:3.6.3-2ubuntu2.7 (using .../winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Unpacking replacement winbind ...
Preparing to replace samba 2:3.6.3-2ubuntu2.7 (using .../samba_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
nmbd stop/waiting
smbd stop/waiting
Unpacking replacement samba ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.7 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.7 (using .../smbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.7 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.7 (using .../samba-common_2%3a3.6.3-2ubuntu2.8_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.7 (using .../libsmbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.12 (using .../apt-utils_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace isc-dhcp-client 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-client_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-client ...
Preparing to replace isc-dhcp-common 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-common_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-common ...
Preparing to replace rsyslog 5.8.6-1ubuntu8.4 (using .../rsyslog_5.8.6-1ubuntu8.5_amd64.deb) ...
Unpacking replacement rsyslog ...
Preparing to replace ifupdown 0.7~beta2ubuntu8 (using .../ifupdown_0.7~beta2ubuntu10_amd64.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.12 (using .../apt-transport-https_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace apt-xapian-index 0.44ubuntu5 (using .../apt-xapian-index_0.44ubuntu5.1_all.deb) ...
Unpacking replacement apt-xapian-index ...
Preparing to replace linux-libc-dev 3.2.0-53.81 (using .../linux-libc-dev_3.2.0-54.82_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace firefox 23.0+build2-0ubuntu0.12.04.1 (using .../firefox_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-globalmenu_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-en_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace firefox-locale-zh-hans 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-zh-hans_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-zh-hans ...
Preparing to replace printer-driver-postscript-hp 3.12.2-1ubuntu3.1 (using .../printer-driver-postscript-hp_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement printer-driver-postscript-hp ...
Preparing to replace libsane-hpaio 3.12.2-1ubuntu3.1 (using .../libsane-hpaio_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace hplip 3.12.2-1ubuntu3.1 (using .../hplip_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.12.2-1ubuntu3.1 (using .../libhpmud0_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.12.2-1ubuntu3.1 (using .../hplip-data_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace printer-driver-hpcups 3.12.2-1ubuntu3.1 (using .../printer-driver-hpcups_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement printer-driver-hpcups ...
Preparing to replace policykit-1 0.104-1ubuntu1 (using .../policykit-1_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement policykit-1 ...
Preparing to replace hplip-gui 3.12.2-1ubuntu3.1 (using .../hplip-gui_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-gui ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.10 (using .../jockey-gtk_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.10 (using .../jockey-common_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace libpython3.2 3.2.3-0ubuntu3.4 (using .../libpython3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement libpython3.2 ...
Preparing to replace python3.2 3.2.3-0ubuntu3.4 (using .../python3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2 ...
Preparing to replace python3.2-minimal 3.2.3-0ubuntu3.4 (using .../python3.2-minimal_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2-minimal ...
Preparing to replace libraw5 0.14.4-0ubuntu2.1 (using .../libraw5_0.14.4-0ubuntu2.2_amd64.deb) ...
Unpacking replacement libraw5 ...
Preparing to replace libsyncdaemon-1.0-1 3.0.2-0ubuntu1 (using .../libsyncdaemon-1.0-1_3.0.2-0ubuntu2_amd64.deb) ...
Unpacking replacement libsyncdaemon-1.0-1 ...
Preparing to replace ubuntuone-client 3.0.2-0ubuntu1 (using .../ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement ubuntuone-client ...
Preparing to replace python-ubuntuone-client 3.0.2-0ubuntu1 (using .../python-ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement python-ubuntuone-client ...
Preparing to replace pulseaudio-utils 1:1.1-0ubuntu15.3 (using .../pulseaudio-utils_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace pulseaudio 1:1.1-0ubuntu15.3 (using .../pulseaudio_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio ...
Preparing to replace pulseaudio-module-gconf 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-gconf_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-gconf ...
Preparing to replace pulseaudio-module-x11 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-x11_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-x11 ...
Preparing to replace python-openssl 0.12-1ubuntu2 (using .../python-openssl_0.12-1ubuntu2.1_amd64.deb) ...
Unpacking replacement python-openssl ...
Preparing to replace python-software-properties 0.82.7.3 (using .../python-software-properties_0.82.7.5_all.deb) ...
Unpacking replacement python-software-properties ...
Preparing to replace rtkit 0.10-2 (using .../rtkit_0.10-2ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement rtkit ...
Preparing to replace samba-tools 2:3.6.3-2ubuntu2.7 (using .../samba-tools_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-tools ...
Preparing to replace software-properties-common 0.82.7.3 (using .../software-properties-common_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-common ...
Preparing to replace software-properties-gtk 0.82.7.3 (using .../software-properties-gtk_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-gtk ...
Preparing to replace thunderbird-globalmenu 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird-locale-en 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace thunderbird-locale-en-us 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a24.0+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Preparing to replace ubuntu-system-service 0.2.2 (using .../ubuntu-system-service_0.2.2.1_all.deb) ...
Unpacking replacement ubuntu-system-service ...
Preparing to replace usb-creator-gtk 0.2.38 (using .../usb-creator-gtk_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-gtk ...
Preparing to replace usb-creator-common 0.2.38 (using .../usb-creator-common_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-common ...
Preparing to replace vino 3.4.2-0ubuntu1.2 (using .../vino_3.4.2-0ubuntu1.3_amd64.deb) ...
Unpacking replacement vino ...
Preparing to replace gnome-settings-daemon 3.4.2-0ubuntu0.6.2 (using .../gnome-settings-daemon_3.4.2-0ubuntu0.6.3_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace pulseaudio-module-bluetooth 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-bluetooth_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-bluetooth ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for cups ...
Updating PPD files for hpcups ...
Updating PPD files for postscript-hp ...
Processing triggers for menu ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Setting up initramfs-tools (0.99ubuntu13.2) ...
update-initramfs: deferring update (trigger activated)
Setting up apparmor (2.7.102-0ubuntu3.9) ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.14) ...
Setting up python2.7 (2.7.3-0ubuntu3.4) ...
Setting up libpython2.7 (2.7.3-0ubuntu3.4) ...
Setting up python2.7-dev (2.7.3-0ubuntu3.4) ...
Setting up language-selector-common (0.79.4) ...
Setting up language-selector-gnome (0.79.4) ...
Setting up libcurl3-gnutls (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-gobject-1-0 (0.104-1ubuntu1.1) ...
Setting up libcurl3-nss (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-agent-1-0 (0.104-1ubuntu1.1) ...
Setting up libpolkit-backend-1-0 (0.104-1ubuntu1.1) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common (2:3.6.3-2ubuntu2.8) ...
Setting up winbind (2:3.6.3-2ubuntu2.8) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 
Setting up libpam-winbind (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.8) ...
Setting up samba (2:3.6.3-2ubuntu2.8) ...
smbd start/running, process 15315
nmbd start/running, process 15353
Setting up smbclient (2:3.6.3-2ubuntu2.8) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.8) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.14) ...
Setting up isc-dhcp-common (4.1.ESV-R4-0ubuntu5.9) ...
Setting up isc-dhcp-client (4.1.ESV-R4-0ubuntu5.9) ...
Setting up rsyslog (5.8.6-1ubuntu8.5) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
rsyslog stop/waiting
rsyslog start/running, process 15503
Setting up ifupdown (0.7~beta2ubuntu10) ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.14) ...
Setting up apt-xapian-index (0.44ubuntu5.1) ...
Setting up linux-libc-dev (3.2.0-54.82) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-52-generic
Building for architecture x86_64
Building initial module for 3.2.0-52-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-52-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up firefox (24.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-zh-hans (24.0+build1-0ubuntu0.12.04.1) ...
Setting up libhpmud0 (3.12.2-1ubuntu3.3) ...
Setting up libsane-hpaio (3.12.2-1ubuntu3.3) ...
Setting up hplip-data (3.12.2-1ubuntu3.3) ...
Setting up printer-driver-hpcups (3.12.2-1ubuntu3.3) ...
Setting up policykit-1 (0.104-1ubuntu1.1) ...
Setting up hplip (3.12.2-1ubuntu3.3) ...
Creating/updating hplip user account...
Setting up printer-driver-postscript-hp (3.12.2-1ubuntu3.3) ...
Setting up hplip-gui (3.12.2-1ubuntu3.3) ...
Setting up jockey-common (0.9.7-0ubuntu7.11) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.11) ...
Setting up python3.2-minimal (3.2.3-0ubuntu3.5) ...
Setting up python3.2 (3.2.3-0ubuntu3.5) ...
Setting up libpython3.2 (3.2.3-0ubuntu3.5) ...
Setting up libraw5 (0.14.4-0ubuntu2.2) ...
Setting up python-ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up libsyncdaemon-1.0-1 (3.0.2-0ubuntu2) ...
Setting up pulseaudio-utils (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-gconf (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-x11 (1:1.1-0ubuntu15.4) ...
Setting up python-openssl (0.12-1ubuntu2.1) ...
Setting up python-software-properties (0.82.7.5) ...
Setting up rtkit (0.10-2ubuntu0.12.04.1) ...
Setting up samba-tools (2:3.6.3-2ubuntu2.8) ...
Setting up software-properties-common (0.82.7.5) ...
Setting up software-properties-gtk (0.82.7.5) ...
Setting up thunderbird (1:24.0+build1-0ubuntu0.12.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-globalmenu (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up ubuntu-system-service (0.2.2.1) ...
Setting up usb-creator-common (0.2.38.2) ...
Setting up usb-creator-gtk (0.2.38.2) ...
Setting up vino (3.4.2-0ubuntu1.3) ...
Setting up gnome-settings-daemon (3.4.2-0ubuntu0.6.3) ...
Setting up pulseaudio-module-bluetooth (1:1.1-0ubuntu15.4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-52-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-52-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$ wget http://mirrors.us.kernel.org/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.2_all.deb

```

```
Get:69 http://security.ubuntu.com/ubuntu/ precise-security/main python3.2-minimal amd64 3.2.3-0ubuntu3.5 [1,776 kB]
Get:70 http://security.ubuntu.com/ubuntu/ precise-security/main libraw5 amd64 0.14.4-0ubuntu2.2 [317 kB]
Get:71 http://security.ubuntu.com/ubuntu/ precise-security/main python-openssl amd64 0.12-1ubuntu2.1 [99.8 kB]
Get:72 http://security.ubuntu.com/ubuntu/ precise-security/main python-software-properties all 0.82.7.5 [22.3 kB]
Get:73 http://security.ubuntu.com/ubuntu/ precise-security/main rtkit amd64 0.10-2ubuntu0.12.04.1 [36.3 kB]
Get:74 http://security.ubuntu.com/ubuntu/ precise-security/universe samba-tools amd64 2:3.6.3-2ubuntu2.8 [11.6 MB]
Get:75 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-common all 0.82.7.5 [8,944 B]
Get:76 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-gtk all 0.82.7.5 [34.6 kB]
Get:77 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-globalmenu amd64 1:24.0+build1-0ubuntu0.12.04.1 [8,786 B]
Get:78 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en amd64 1:24.0+build1-0ubuntu0.12.04.1 [343 kB]
Get:79 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird amd64 1:24.0+build1-0ubuntu0.12.04.1 [29.5 MB]
Get:80 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-gnome-support amd64 1:24.0+build1-0ubuntu0.12.04.1 [9,132 B]
Get:81 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en-us all 1:24.0+build1-0ubuntu0.12.04.1 [14.0 kB]
Get:82 http://security.ubuntu.com/ubuntu/ precise-security/main ubuntu-system-service all 0.2.2.1 [12.1 kB]
Get:83 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-gtk amd64 0.2.38.2 [26.9 kB]
Get:84 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-common amd64 0.2.38.2 [23.6 kB]
Get:85 http://security.ubuntu.com/ubuntu/ precise-security/main vino amd64 3.4.2-0ubuntu1.3 [170 kB]
Fetched 167 MB in 14min 34s (191 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.12 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.14) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.12 (using .../apt_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp12ubuntu10.14) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10.12 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace python2.7-dev 2.7.3-0ubuntu3.3 (using .../python2.7-dev_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-dev ...
Preparing to replace libpython2.7 2.7.3-0ubuntu3.3 (using .../libpython2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement libpython2.7 ...
Preparing to replace python2.7 2.7.3-0ubuntu3.3 (using .../python2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7 ...
Preparing to replace python2.7-minimal 2.7.3-0ubuntu3.3 (using .../python2.7-minimal_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-minimal ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Setting up python2.7-minimal (2.7.3-0ubuntu3.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace language-selector-gnome 0.79.3 (using .../language-selector-gnome_0.79.4_all.deb) ...
Unpacking replacement language-selector-gnome ...
Preparing to replace language-selector-common 0.79.3 (using .../language-selector-common_0.79.4_all.deb) ...
Unpacking replacement language-selector-common ...
Preparing to replace libldap-2.4-2 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_amd64.deb) ...
De-configuring libldap-2.4-2:i386 ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace libldap-2.4-2:i386 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_i386.deb) ...
Unpacking replacement libldap-2.4-2:i386 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up libldap-2.4-2 (2.4.28-1.1ubuntu4.4) ...
Setting up libldap-2.4-2:i386 (2.4.28-1.1ubuntu4.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-gnutls 7.22.0-3ubuntu4.2 (using .../libcurl3-gnutls_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-gnutls ...
Preparing to replace libpolkit-gobject-1-0 0.104-1ubuntu1 (using .../libpolkit-gobject-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-gobject-1-0 ...
Preparing to replace libaudio2:i386 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_i386.deb) ...
De-configuring libaudio2 ...
Unpacking replacement libaudio2:i386 ...
Preparing to replace libaudio2 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_amd64.deb) ...
Unpacking replacement libaudio2 ...
Setting up libaudio2:i386 (1.9.3-4ubuntu0.1) ...
Setting up libaudio2 (1.9.3-4ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3:i386 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_i386.deb) ...
De-configuring libcurl3 ...
Unpacking replacement libcurl3:i386 ...
Preparing to replace libcurl3 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3 ...
Setting up libcurl3:i386 (7.22.0-3ubuntu4.3) ...
Setting up libcurl3 (7.22.0-3ubuntu4.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-nss 7.22.0-3ubuntu4.2 (using .../libcurl3-nss_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-nss ...
Preparing to replace libpolkit-agent-1-0 0.104-1ubuntu1 (using .../libpolkit-agent-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-agent-1-0 ...
Preparing to replace libpolkit-backend-1-0 0.104-1ubuntu1 (using .../libpolkit-backend-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-backend-1-0 ...
Preparing to replace libpulse0 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
De-configuring libpulse0:i386 ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse0:i386 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_i386.deb) ...
Unpacking replacement libpulse0:i386 ...
Setting up libpulse0 (1:1.1-0ubuntu15.4) ...
Setting up libpulse0:i386 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulse-mainloop-glib0:i386 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulse-mainloop-glib0 ...
Unpacking replacement libpulse-mainloop-glib0:i386 ...
Preparing to replace libpulse-mainloop-glib0 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Setting up libpulse-mainloop-glib0:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulse-mainloop-glib0 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulsedsp:i386 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulsedsp ...
Unpacking replacement libpulsedsp:i386 ...
Preparing to replace libpulsedsp 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulsedsp ...
Setting up libpulsedsp:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulsedsp (1:1.1-0ubuntu15.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpam-winbind 2:3.6.3-2ubuntu2.7 (using .../libpam-winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libpam-winbind ...
Preparing to replace winbind 2:3.6.3-2ubuntu2.7 (using .../winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Unpacking replacement winbind ...
Preparing to replace samba 2:3.6.3-2ubuntu2.7 (using .../samba_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
nmbd stop/waiting
smbd stop/waiting
Unpacking replacement samba ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.7 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.7 (using .../smbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.7 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.7 (using .../samba-common_2%3a3.6.3-2ubuntu2.8_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.7 (using .../libsmbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.12 (using .../apt-utils_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace isc-dhcp-client 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-client_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-client ...
Preparing to replace isc-dhcp-common 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-common_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-common ...
Preparing to replace rsyslog 5.8.6-1ubuntu8.4 (using .../rsyslog_5.8.6-1ubuntu8.5_amd64.deb) ...
Unpacking replacement rsyslog ...
Preparing to replace ifupdown 0.7~beta2ubuntu8 (using .../ifupdown_0.7~beta2ubuntu10_amd64.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.12 (using .../apt-transport-https_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace apt-xapian-index 0.44ubuntu5 (using .../apt-xapian-index_0.44ubuntu5.1_all.deb) ...
Unpacking replacement apt-xapian-index ...
Preparing to replace linux-libc-dev 3.2.0-53.81 (using .../linux-libc-dev_3.2.0-54.82_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace firefox 23.0+build2-0ubuntu0.12.04.1 (using .../firefox_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-globalmenu_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-en_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace firefox-locale-zh-hans 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-zh-hans_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-zh-hans ...
Preparing to replace printer-driver-postscript-hp 3.12.2-1ubuntu3.1 (using .../printer-driver-postscript-hp_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement printer-driver-postscript-hp ...
Preparing to replace libsane-hpaio 3.12.2-1ubuntu3.1 (using .../libsane-hpaio_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace hplip 3.12.2-1ubuntu3.1 (using .../hplip_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.12.2-1ubuntu3.1 (using .../libhpmud0_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.12.2-1ubuntu3.1 (using .../hplip-data_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace printer-driver-hpcups 3.12.2-1ubuntu3.1 (using .../printer-driver-hpcups_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement printer-driver-hpcups ...
Preparing to replace policykit-1 0.104-1ubuntu1 (using .../policykit-1_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement policykit-1 ...
Preparing to replace hplip-gui 3.12.2-1ubuntu3.1 (using .../hplip-gui_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-gui ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.10 (using .../jockey-gtk_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.10 (using .../jockey-common_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace libpython3.2 3.2.3-0ubuntu3.4 (using .../libpython3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement libpython3.2 ...
Preparing to replace python3.2 3.2.3-0ubuntu3.4 (using .../python3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2 ...
Preparing to replace python3.2-minimal 3.2.3-0ubuntu3.4 (using .../python3.2-minimal_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2-minimal ...
Preparing to replace libraw5 0.14.4-0ubuntu2.1 (using .../libraw5_0.14.4-0ubuntu2.2_amd64.deb) ...
Unpacking replacement libraw5 ...
Preparing to replace libsyncdaemon-1.0-1 3.0.2-0ubuntu1 (using .../libsyncdaemon-1.0-1_3.0.2-0ubuntu2_amd64.deb) ...
Unpacking replacement libsyncdaemon-1.0-1 ...
Preparing to replace ubuntuone-client 3.0.2-0ubuntu1 (using .../ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement ubuntuone-client ...
Preparing to replace python-ubuntuone-client 3.0.2-0ubuntu1 (using .../python-ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement python-ubuntuone-client ...
Preparing to replace pulseaudio-utils 1:1.1-0ubuntu15.3 (using .../pulseaudio-utils_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace pulseaudio 1:1.1-0ubuntu15.3 (using .../pulseaudio_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio ...
Preparing to replace pulseaudio-module-gconf 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-gconf_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-gconf ...
Preparing to replace pulseaudio-module-x11 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-x11_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-x11 ...
Preparing to replace python-openssl 0.12-1ubuntu2 (using .../python-openssl_0.12-1ubuntu2.1_amd64.deb) ...
Unpacking replacement python-openssl ...
Preparing to replace python-software-properties 0.82.7.3 (using .../python-software-properties_0.82.7.5_all.deb) ...
Unpacking replacement python-software-properties ...
Preparing to replace rtkit 0.10-2 (using .../rtkit_0.10-2ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement rtkit ...
Preparing to replace samba-tools 2:3.6.3-2ubuntu2.7 (using .../samba-tools_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-tools ...
Preparing to replace software-properties-common 0.82.7.3 (using .../software-properties-common_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-common ...
Preparing to replace software-properties-gtk 0.82.7.3 (using .../software-properties-gtk_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-gtk ...
Preparing to replace thunderbird-globalmenu 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird-locale-en 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace thunderbird-locale-en-us 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a24.0+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Preparing to replace ubuntu-system-service 0.2.2 (using .../ubuntu-system-service_0.2.2.1_all.deb) ...
Unpacking replacement ubuntu-system-service ...
Preparing to replace usb-creator-gtk 0.2.38 (using .../usb-creator-gtk_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-gtk ...
Preparing to replace usb-creator-common 0.2.38 (using .../usb-creator-common_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-common ...
Preparing to replace vino 3.4.2-0ubuntu1.2 (using .../vino_3.4.2-0ubuntu1.3_amd64.deb) ...
Unpacking replacement vino ...
Preparing to replace gnome-settings-daemon 3.4.2-0ubuntu0.6.2 (using .../gnome-settings-daemon_3.4.2-0ubuntu0.6.3_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace pulseaudio-module-bluetooth 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-bluetooth_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-bluetooth ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for cups ...
Updating PPD files for hpcups ...
Updating PPD files for postscript-hp ...
Processing triggers for menu ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Setting up initramfs-tools (0.99ubuntu13.2) ...
update-initramfs: deferring update (trigger activated)
Setting up apparmor (2.7.102-0ubuntu3.9) ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.14) ...
Setting up python2.7 (2.7.3-0ubuntu3.4) ...
Setting up libpython2.7 (2.7.3-0ubuntu3.4) ...
Setting up python2.7-dev (2.7.3-0ubuntu3.4) ...
Setting up language-selector-common (0.79.4) ...
Setting up language-selector-gnome (0.79.4) ...
Setting up libcurl3-gnutls (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-gobject-1-0 (0.104-1ubuntu1.1) ...
Setting up libcurl3-nss (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-agent-1-0 (0.104-1ubuntu1.1) ...
Setting up libpolkit-backend-1-0 (0.104-1ubuntu1.1) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common (2:3.6.3-2ubuntu2.8) ...
Setting up winbind (2:3.6.3-2ubuntu2.8) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 
Setting up libpam-winbind (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.8) ...
Setting up samba (2:3.6.3-2ubuntu2.8) ...
smbd start/running, process 15315
nmbd start/running, process 15353
Setting up smbclient (2:3.6.3-2ubuntu2.8) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.8) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.14) ...
Setting up isc-dhcp-common (4.1.ESV-R4-0ubuntu5.9) ...
Setting up isc-dhcp-client (4.1.ESV-R4-0ubuntu5.9) ...
Setting up rsyslog (5.8.6-1ubuntu8.5) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
rsyslog stop/waiting
rsyslog start/running, process 15503
Setting up ifupdown (0.7~beta2ubuntu10) ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.14) ...
Setting up apt-xapian-index (0.44ubuntu5.1) ...
Setting up linux-libc-dev (3.2.0-54.82) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-52-generic
Building for architecture x86_64
Building initial module for 3.2.0-52-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-52-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up firefox (24.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-zh-hans (24.0+build1-0ubuntu0.12.04.1) ...
Setting up libhpmud0 (3.12.2-1ubuntu3.3) ...
Setting up libsane-hpaio (3.12.2-1ubuntu3.3) ...
Setting up hplip-data (3.12.2-1ubuntu3.3) ...
Setting up printer-driver-hpcups (3.12.2-1ubuntu3.3) ...
Setting up policykit-1 (0.104-1ubuntu1.1) ...
Setting up hplip (3.12.2-1ubuntu3.3) ...
Creating/updating hplip user account...
Setting up printer-driver-postscript-hp (3.12.2-1ubuntu3.3) ...
Setting up hplip-gui (3.12.2-1ubuntu3.3) ...
Setting up jockey-common (0.9.7-0ubuntu7.11) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.11) ...
Setting up python3.2-minimal (3.2.3-0ubuntu3.5) ...
Setting up python3.2 (3.2.3-0ubuntu3.5) ...
Setting up libpython3.2 (3.2.3-0ubuntu3.5) ...
Setting up libraw5 (0.14.4-0ubuntu2.2) ...
Setting up python-ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up libsyncdaemon-1.0-1 (3.0.2-0ubuntu2) ...
Setting up pulseaudio-utils (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-gconf (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-x11 (1:1.1-0ubuntu15.4) ...
Setting up python-openssl (0.12-1ubuntu2.1) ...
Setting up python-software-properties (0.82.7.5) ...
Setting up rtkit (0.10-2ubuntu0.12.04.1) ...
Setting up samba-tools (2:3.6.3-2ubuntu2.8) ...
Setting up software-properties-common (0.82.7.5) ...
Setting up software-properties-gtk (0.82.7.5) ...
Setting up thunderbird (1:24.0+build1-0ubuntu0.12.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-globalmenu (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up ubuntu-system-service (0.2.2.1) ...
Setting up usb-creator-common (0.2.38.2) ...
Setting up usb-creator-gtk (0.2.38.2) ...
Setting up vino (3.4.2-0ubuntu1.3) ...
Setting up gnome-settings-daemon (3.4.2-0ubuntu0.6.3) ...
Setting up pulseaudio-module-bluetooth (1:1.1-0ubuntu15.4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-52-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-52-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$ sudo dpkg -i /var/cache/apt/archives/initramfs-tools_0.99ubuntu13.2_all.deb

```

```
Get:69 http://security.ubuntu.com/ubuntu/ precise-security/main python3.2-minimal amd64 3.2.3-0ubuntu3.5 [1,776 kB]
Get:70 http://security.ubuntu.com/ubuntu/ precise-security/main libraw5 amd64 0.14.4-0ubuntu2.2 [317 kB]
Get:71 http://security.ubuntu.com/ubuntu/ precise-security/main python-openssl amd64 0.12-1ubuntu2.1 [99.8 kB]
Get:72 http://security.ubuntu.com/ubuntu/ precise-security/main python-software-properties all 0.82.7.5 [22.3 kB]
Get:73 http://security.ubuntu.com/ubuntu/ precise-security/main rtkit amd64 0.10-2ubuntu0.12.04.1 [36.3 kB]
Get:74 http://security.ubuntu.com/ubuntu/ precise-security/universe samba-tools amd64 2:3.6.3-2ubuntu2.8 [11.6 MB]
Get:75 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-common all 0.82.7.5 [8,944 B]
Get:76 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-gtk all 0.82.7.5 [34.6 kB]
Get:77 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-globalmenu amd64 1:24.0+build1-0ubuntu0.12.04.1 [8,786 B]
Get:78 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en amd64 1:24.0+build1-0ubuntu0.12.04.1 [343 kB]
Get:79 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird amd64 1:24.0+build1-0ubuntu0.12.04.1 [29.5 MB]
Get:80 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-gnome-support amd64 1:24.0+build1-0ubuntu0.12.04.1 [9,132 B]
Get:81 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en-us all 1:24.0+build1-0ubuntu0.12.04.1 [14.0 kB]
Get:82 http://security.ubuntu.com/ubuntu/ precise-security/main ubuntu-system-service all 0.2.2.1 [12.1 kB]
Get:83 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-gtk amd64 0.2.38.2 [26.9 kB]
Get:84 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-common amd64 0.2.38.2 [23.6 kB]
Get:85 http://security.ubuntu.com/ubuntu/ precise-security/main vino amd64 3.4.2-0ubuntu1.3 [170 kB]
Fetched 167 MB in 14min 34s (191 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.12 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.14) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.12 (using .../apt_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp12ubuntu10.14) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10.12 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace python2.7-dev 2.7.3-0ubuntu3.3 (using .../python2.7-dev_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-dev ...
Preparing to replace libpython2.7 2.7.3-0ubuntu3.3 (using .../libpython2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement libpython2.7 ...
Preparing to replace python2.7 2.7.3-0ubuntu3.3 (using .../python2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7 ...
Preparing to replace python2.7-minimal 2.7.3-0ubuntu3.3 (using .../python2.7-minimal_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-minimal ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Setting up python2.7-minimal (2.7.3-0ubuntu3.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace language-selector-gnome 0.79.3 (using .../language-selector-gnome_0.79.4_all.deb) ...
Unpacking replacement language-selector-gnome ...
Preparing to replace language-selector-common 0.79.3 (using .../language-selector-common_0.79.4_all.deb) ...
Unpacking replacement language-selector-common ...
Preparing to replace libldap-2.4-2 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_amd64.deb) ...
De-configuring libldap-2.4-2:i386 ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace libldap-2.4-2:i386 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_i386.deb) ...
Unpacking replacement libldap-2.4-2:i386 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up libldap-2.4-2 (2.4.28-1.1ubuntu4.4) ...
Setting up libldap-2.4-2:i386 (2.4.28-1.1ubuntu4.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-gnutls 7.22.0-3ubuntu4.2 (using .../libcurl3-gnutls_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-gnutls ...
Preparing to replace libpolkit-gobject-1-0 0.104-1ubuntu1 (using .../libpolkit-gobject-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-gobject-1-0 ...
Preparing to replace libaudio2:i386 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_i386.deb) ...
De-configuring libaudio2 ...
Unpacking replacement libaudio2:i386 ...
Preparing to replace libaudio2 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_amd64.deb) ...
Unpacking replacement libaudio2 ...
Setting up libaudio2:i386 (1.9.3-4ubuntu0.1) ...
Setting up libaudio2 (1.9.3-4ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3:i386 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_i386.deb) ...
De-configuring libcurl3 ...
Unpacking replacement libcurl3:i386 ...
Preparing to replace libcurl3 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3 ...
Setting up libcurl3:i386 (7.22.0-3ubuntu4.3) ...
Setting up libcurl3 (7.22.0-3ubuntu4.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-nss 7.22.0-3ubuntu4.2 (using .../libcurl3-nss_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-nss ...
Preparing to replace libpolkit-agent-1-0 0.104-1ubuntu1 (using .../libpolkit-agent-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-agent-1-0 ...
Preparing to replace libpolkit-backend-1-0 0.104-1ubuntu1 (using .../libpolkit-backend-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-backend-1-0 ...
Preparing to replace libpulse0 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
De-configuring libpulse0:i386 ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse0:i386 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_i386.deb) ...
Unpacking replacement libpulse0:i386 ...
Setting up libpulse0 (1:1.1-0ubuntu15.4) ...
Setting up libpulse0:i386 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulse-mainloop-glib0:i386 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulse-mainloop-glib0 ...
Unpacking replacement libpulse-mainloop-glib0:i386 ...
Preparing to replace libpulse-mainloop-glib0 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Setting up libpulse-mainloop-glib0:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulse-mainloop-glib0 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulsedsp:i386 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulsedsp ...
Unpacking replacement libpulsedsp:i386 ...
Preparing to replace libpulsedsp 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulsedsp ...
Setting up libpulsedsp:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulsedsp (1:1.1-0ubuntu15.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpam-winbind 2:3.6.3-2ubuntu2.7 (using .../libpam-winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libpam-winbind ...
Preparing to replace winbind 2:3.6.3-2ubuntu2.7 (using .../winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Unpacking replacement winbind ...
Preparing to replace samba 2:3.6.3-2ubuntu2.7 (using .../samba_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
nmbd stop/waiting
smbd stop/waiting
Unpacking replacement samba ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.7 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.7 (using .../smbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.7 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.7 (using .../samba-common_2%3a3.6.3-2ubuntu2.8_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.7 (using .../libsmbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.12 (using .../apt-utils_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace isc-dhcp-client 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-client_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-client ...
Preparing to replace isc-dhcp-common 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-common_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-common ...
Preparing to replace rsyslog 5.8.6-1ubuntu8.4 (using .../rsyslog_5.8.6-1ubuntu8.5_amd64.deb) ...
Unpacking replacement rsyslog ...
Preparing to replace ifupdown 0.7~beta2ubuntu8 (using .../ifupdown_0.7~beta2ubuntu10_amd64.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.12 (using .../apt-transport-https_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace apt-xapian-index 0.44ubuntu5 (using .../apt-xapian-index_0.44ubuntu5.1_all.deb) ...
Unpacking replacement apt-xapian-index ...
Preparing to replace linux-libc-dev 3.2.0-53.81 (using .../linux-libc-dev_3.2.0-54.82_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace firefox 23.0+build2-0ubuntu0.12.04.1 (using .../firefox_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-globalmenu_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-en_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace firefox-locale-zh-hans 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-zh-hans_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-zh-hans ...
Preparing to replace printer-driver-postscript-hp 3.12.2-1ubuntu3.1 (using .../printer-driver-postscript-hp_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement printer-driver-postscript-hp ...
Preparing to replace libsane-hpaio 3.12.2-1ubuntu3.1 (using .../libsane-hpaio_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace hplip 3.12.2-1ubuntu3.1 (using .../hplip_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.12.2-1ubuntu3.1 (using .../libhpmud0_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.12.2-1ubuntu3.1 (using .../hplip-data_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace printer-driver-hpcups 3.12.2-1ubuntu3.1 (using .../printer-driver-hpcups_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement printer-driver-hpcups ...
Preparing to replace policykit-1 0.104-1ubuntu1 (using .../policykit-1_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement policykit-1 ...
Preparing to replace hplip-gui 3.12.2-1ubuntu3.1 (using .../hplip-gui_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-gui ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.10 (using .../jockey-gtk_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.10 (using .../jockey-common_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace libpython3.2 3.2.3-0ubuntu3.4 (using .../libpython3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement libpython3.2 ...
Preparing to replace python3.2 3.2.3-0ubuntu3.4 (using .../python3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2 ...
Preparing to replace python3.2-minimal 3.2.3-0ubuntu3.4 (using .../python3.2-minimal_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2-minimal ...
Preparing to replace libraw5 0.14.4-0ubuntu2.1 (using .../libraw5_0.14.4-0ubuntu2.2_amd64.deb) ...
Unpacking replacement libraw5 ...
Preparing to replace libsyncdaemon-1.0-1 3.0.2-0ubuntu1 (using .../libsyncdaemon-1.0-1_3.0.2-0ubuntu2_amd64.deb) ...
Unpacking replacement libsyncdaemon-1.0-1 ...
Preparing to replace ubuntuone-client 3.0.2-0ubuntu1 (using .../ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement ubuntuone-client ...
Preparing to replace python-ubuntuone-client 3.0.2-0ubuntu1 (using .../python-ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement python-ubuntuone-client ...
Preparing to replace pulseaudio-utils 1:1.1-0ubuntu15.3 (using .../pulseaudio-utils_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace pulseaudio 1:1.1-0ubuntu15.3 (using .../pulseaudio_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio ...
Preparing to replace pulseaudio-module-gconf 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-gconf_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-gconf ...
Preparing to replace pulseaudio-module-x11 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-x11_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-x11 ...
Preparing to replace python-openssl 0.12-1ubuntu2 (using .../python-openssl_0.12-1ubuntu2.1_amd64.deb) ...
Unpacking replacement python-openssl ...
Preparing to replace python-software-properties 0.82.7.3 (using .../python-software-properties_0.82.7.5_all.deb) ...
Unpacking replacement python-software-properties ...
Preparing to replace rtkit 0.10-2 (using .../rtkit_0.10-2ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement rtkit ...
Preparing to replace samba-tools 2:3.6.3-2ubuntu2.7 (using .../samba-tools_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-tools ...
Preparing to replace software-properties-common 0.82.7.3 (using .../software-properties-common_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-common ...
Preparing to replace software-properties-gtk 0.82.7.3 (using .../software-properties-gtk_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-gtk ...
Preparing to replace thunderbird-globalmenu 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird-locale-en 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace thunderbird-locale-en-us 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a24.0+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Preparing to replace ubuntu-system-service 0.2.2 (using .../ubuntu-system-service_0.2.2.1_all.deb) ...
Unpacking replacement ubuntu-system-service ...
Preparing to replace usb-creator-gtk 0.2.38 (using .../usb-creator-gtk_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-gtk ...
Preparing to replace usb-creator-common 0.2.38 (using .../usb-creator-common_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-common ...
Preparing to replace vino 3.4.2-0ubuntu1.2 (using .../vino_3.4.2-0ubuntu1.3_amd64.deb) ...
Unpacking replacement vino ...
Preparing to replace gnome-settings-daemon 3.4.2-0ubuntu0.6.2 (using .../gnome-settings-daemon_3.4.2-0ubuntu0.6.3_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace pulseaudio-module-bluetooth 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-bluetooth_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-bluetooth ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for cups ...
Updating PPD files for hpcups ...
Updating PPD files for postscript-hp ...
Processing triggers for menu ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Setting up initramfs-tools (0.99ubuntu13.2) ...
update-initramfs: deferring update (trigger activated)
Setting up apparmor (2.7.102-0ubuntu3.9) ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.14) ...
Setting up python2.7 (2.7.3-0ubuntu3.4) ...
Setting up libpython2.7 (2.7.3-0ubuntu3.4) ...
Setting up python2.7-dev (2.7.3-0ubuntu3.4) ...
Setting up language-selector-common (0.79.4) ...
Setting up language-selector-gnome (0.79.4) ...
Setting up libcurl3-gnutls (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-gobject-1-0 (0.104-1ubuntu1.1) ...
Setting up libcurl3-nss (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-agent-1-0 (0.104-1ubuntu1.1) ...
Setting up libpolkit-backend-1-0 (0.104-1ubuntu1.1) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common (2:3.6.3-2ubuntu2.8) ...
Setting up winbind (2:3.6.3-2ubuntu2.8) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 
Setting up libpam-winbind (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.8) ...
Setting up samba (2:3.6.3-2ubuntu2.8) ...
smbd start/running, process 15315
nmbd start/running, process 15353
Setting up smbclient (2:3.6.3-2ubuntu2.8) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.8) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.14) ...
Setting up isc-dhcp-common (4.1.ESV-R4-0ubuntu5.9) ...
Setting up isc-dhcp-client (4.1.ESV-R4-0ubuntu5.9) ...
Setting up rsyslog (5.8.6-1ubuntu8.5) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
rsyslog stop/waiting
rsyslog start/running, process 15503
Setting up ifupdown (0.7~beta2ubuntu10) ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.14) ...
Setting up apt-xapian-index (0.44ubuntu5.1) ...
Setting up linux-libc-dev (3.2.0-54.82) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-52-generic
Building for architecture x86_64
Building initial module for 3.2.0-52-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-52-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up firefox (24.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-zh-hans (24.0+build1-0ubuntu0.12.04.1) ...
Setting up libhpmud0 (3.12.2-1ubuntu3.3) ...
Setting up libsane-hpaio (3.12.2-1ubuntu3.3) ...
Setting up hplip-data (3.12.2-1ubuntu3.3) ...
Setting up printer-driver-hpcups (3.12.2-1ubuntu3.3) ...
Setting up policykit-1 (0.104-1ubuntu1.1) ...
Setting up hplip (3.12.2-1ubuntu3.3) ...
Creating/updating hplip user account...
Setting up printer-driver-postscript-hp (3.12.2-1ubuntu3.3) ...
Setting up hplip-gui (3.12.2-1ubuntu3.3) ...
Setting up jockey-common (0.9.7-0ubuntu7.11) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.11) ...
Setting up python3.2-minimal (3.2.3-0ubuntu3.5) ...
Setting up python3.2 (3.2.3-0ubuntu3.5) ...
Setting up libpython3.2 (3.2.3-0ubuntu3.5) ...
Setting up libraw5 (0.14.4-0ubuntu2.2) ...
Setting up python-ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up libsyncdaemon-1.0-1 (3.0.2-0ubuntu2) ...
Setting up pulseaudio-utils (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-gconf (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-x11 (1:1.1-0ubuntu15.4) ...
Setting up python-openssl (0.12-1ubuntu2.1) ...
Setting up python-software-properties (0.82.7.5) ...
Setting up rtkit (0.10-2ubuntu0.12.04.1) ...
Setting up samba-tools (2:3.6.3-2ubuntu2.8) ...
Setting up software-properties-common (0.82.7.5) ...
Setting up software-properties-gtk (0.82.7.5) ...
Setting up thunderbird (1:24.0+build1-0ubuntu0.12.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-globalmenu (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up ubuntu-system-service (0.2.2.1) ...
Setting up usb-creator-common (0.2.38.2) ...
Setting up usb-creator-gtk (0.2.38.2) ...
Setting up vino (3.4.2-0ubuntu1.3) ...
Setting up gnome-settings-daemon (3.4.2-0ubuntu0.6.3) ...
Setting up pulseaudio-module-bluetooth (1:1.1-0ubuntu15.4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-52-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-52-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$ cd ## returns ya to /home as the  PWD

```


```
Get:69 http://security.ubuntu.com/ubuntu/ precise-security/main python3.2-minimal amd64 3.2.3-0ubuntu3.5 [1,776 kB]
Get:70 http://security.ubuntu.com/ubuntu/ precise-security/main libraw5 amd64 0.14.4-0ubuntu2.2 [317 kB]
Get:71 http://security.ubuntu.com/ubuntu/ precise-security/main python-openssl amd64 0.12-1ubuntu2.1 [99.8 kB]
Get:72 http://security.ubuntu.com/ubuntu/ precise-security/main python-software-properties all 0.82.7.5 [22.3 kB]
Get:73 http://security.ubuntu.com/ubuntu/ precise-security/main rtkit amd64 0.10-2ubuntu0.12.04.1 [36.3 kB]
Get:74 http://security.ubuntu.com/ubuntu/ precise-security/universe samba-tools amd64 2:3.6.3-2ubuntu2.8 [11.6 MB]
Get:75 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-common all 0.82.7.5 [8,944 B]
Get:76 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-gtk all 0.82.7.5 [34.6 kB]
Get:77 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-globalmenu amd64 1:24.0+build1-0ubuntu0.12.04.1 [8,786 B]
Get:78 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en amd64 1:24.0+build1-0ubuntu0.12.04.1 [343 kB]
Get:79 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird amd64 1:24.0+build1-0ubuntu0.12.04.1 [29.5 MB]
Get:80 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-gnome-support amd64 1:24.0+build1-0ubuntu0.12.04.1 [9,132 B]
Get:81 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en-us all 1:24.0+build1-0ubuntu0.12.04.1 [14.0 kB]
Get:82 http://security.ubuntu.com/ubuntu/ precise-security/main ubuntu-system-service all 0.2.2.1 [12.1 kB]
Get:83 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-gtk amd64 0.2.38.2 [26.9 kB]
Get:84 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-common amd64 0.2.38.2 [23.6 kB]
Get:85 http://security.ubuntu.com/ubuntu/ precise-security/main vino amd64 3.4.2-0ubuntu1.3 [170 kB]
Fetched 167 MB in 14min 34s (191 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.12 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.14) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.12 (using .../apt_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp12ubuntu10.14) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10.12 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace python2.7-dev 2.7.3-0ubuntu3.3 (using .../python2.7-dev_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-dev ...
Preparing to replace libpython2.7 2.7.3-0ubuntu3.3 (using .../libpython2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement libpython2.7 ...
Preparing to replace python2.7 2.7.3-0ubuntu3.3 (using .../python2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7 ...
Preparing to replace python2.7-minimal 2.7.3-0ubuntu3.3 (using .../python2.7-minimal_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-minimal ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Setting up python2.7-minimal (2.7.3-0ubuntu3.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace language-selector-gnome 0.79.3 (using .../language-selector-gnome_0.79.4_all.deb) ...
Unpacking replacement language-selector-gnome ...
Preparing to replace language-selector-common 0.79.3 (using .../language-selector-common_0.79.4_all.deb) ...
Unpacking replacement language-selector-common ...
Preparing to replace libldap-2.4-2 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_amd64.deb) ...
De-configuring libldap-2.4-2:i386 ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace libldap-2.4-2:i386 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_i386.deb) ...
Unpacking replacement libldap-2.4-2:i386 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up libldap-2.4-2 (2.4.28-1.1ubuntu4.4) ...
Setting up libldap-2.4-2:i386 (2.4.28-1.1ubuntu4.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-gnutls 7.22.0-3ubuntu4.2 (using .../libcurl3-gnutls_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-gnutls ...
Preparing to replace libpolkit-gobject-1-0 0.104-1ubuntu1 (using .../libpolkit-gobject-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-gobject-1-0 ...
Preparing to replace libaudio2:i386 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_i386.deb) ...
De-configuring libaudio2 ...
Unpacking replacement libaudio2:i386 ...
Preparing to replace libaudio2 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_amd64.deb) ...
Unpacking replacement libaudio2 ...
Setting up libaudio2:i386 (1.9.3-4ubuntu0.1) ...
Setting up libaudio2 (1.9.3-4ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3:i386 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_i386.deb) ...
De-configuring libcurl3 ...
Unpacking replacement libcurl3:i386 ...
Preparing to replace libcurl3 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3 ...
Setting up libcurl3:i386 (7.22.0-3ubuntu4.3) ...
Setting up libcurl3 (7.22.0-3ubuntu4.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-nss 7.22.0-3ubuntu4.2 (using .../libcurl3-nss_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-nss ...
Preparing to replace libpolkit-agent-1-0 0.104-1ubuntu1 (using .../libpolkit-agent-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-agent-1-0 ...
Preparing to replace libpolkit-backend-1-0 0.104-1ubuntu1 (using .../libpolkit-backend-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-backend-1-0 ...
Preparing to replace libpulse0 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
De-configuring libpulse0:i386 ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse0:i386 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_i386.deb) ...
Unpacking replacement libpulse0:i386 ...
Setting up libpulse0 (1:1.1-0ubuntu15.4) ...
Setting up libpulse0:i386 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulse-mainloop-glib0:i386 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulse-mainloop-glib0 ...
Unpacking replacement libpulse-mainloop-glib0:i386 ...
Preparing to replace libpulse-mainloop-glib0 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Setting up libpulse-mainloop-glib0:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulse-mainloop-glib0 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulsedsp:i386 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulsedsp ...
Unpacking replacement libpulsedsp:i386 ...
Preparing to replace libpulsedsp 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulsedsp ...
Setting up libpulsedsp:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulsedsp (1:1.1-0ubuntu15.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpam-winbind 2:3.6.3-2ubuntu2.7 (using .../libpam-winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libpam-winbind ...
Preparing to replace winbind 2:3.6.3-2ubuntu2.7 (using .../winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Unpacking replacement winbind ...
Preparing to replace samba 2:3.6.3-2ubuntu2.7 (using .../samba_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
nmbd stop/waiting
smbd stop/waiting
Unpacking replacement samba ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.7 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.7 (using .../smbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.7 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.7 (using .../samba-common_2%3a3.6.3-2ubuntu2.8_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.7 (using .../libsmbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.12 (using .../apt-utils_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace isc-dhcp-client 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-client_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-client ...
Preparing to replace isc-dhcp-common 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-common_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-common ...
Preparing to replace rsyslog 5.8.6-1ubuntu8.4 (using .../rsyslog_5.8.6-1ubuntu8.5_amd64.deb) ...
Unpacking replacement rsyslog ...
Preparing to replace ifupdown 0.7~beta2ubuntu8 (using .../ifupdown_0.7~beta2ubuntu10_amd64.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.12 (using .../apt-transport-https_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace apt-xapian-index 0.44ubuntu5 (using .../apt-xapian-index_0.44ubuntu5.1_all.deb) ...
Unpacking replacement apt-xapian-index ...
Preparing to replace linux-libc-dev 3.2.0-53.81 (using .../linux-libc-dev_3.2.0-54.82_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace firefox 23.0+build2-0ubuntu0.12.04.1 (using .../firefox_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-globalmenu_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-en_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace firefox-locale-zh-hans 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-zh-hans_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-zh-hans ...
Preparing to replace printer-driver-postscript-hp 3.12.2-1ubuntu3.1 (using .../printer-driver-postscript-hp_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement printer-driver-postscript-hp ...
Preparing to replace libsane-hpaio 3.12.2-1ubuntu3.1 (using .../libsane-hpaio_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace hplip 3.12.2-1ubuntu3.1 (using .../hplip_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.12.2-1ubuntu3.1 (using .../libhpmud0_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.12.2-1ubuntu3.1 (using .../hplip-data_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace printer-driver-hpcups 3.12.2-1ubuntu3.1 (using .../printer-driver-hpcups_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement printer-driver-hpcups ...
Preparing to replace policykit-1 0.104-1ubuntu1 (using .../policykit-1_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement policykit-1 ...
Preparing to replace hplip-gui 3.12.2-1ubuntu3.1 (using .../hplip-gui_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-gui ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.10 (using .../jockey-gtk_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.10 (using .../jockey-common_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace libpython3.2 3.2.3-0ubuntu3.4 (using .../libpython3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement libpython3.2 ...
Preparing to replace python3.2 3.2.3-0ubuntu3.4 (using .../python3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2 ...
Preparing to replace python3.2-minimal 3.2.3-0ubuntu3.4 (using .../python3.2-minimal_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2-minimal ...
Preparing to replace libraw5 0.14.4-0ubuntu2.1 (using .../libraw5_0.14.4-0ubuntu2.2_amd64.deb) ...
Unpacking replacement libraw5 ...
Preparing to replace libsyncdaemon-1.0-1 3.0.2-0ubuntu1 (using .../libsyncdaemon-1.0-1_3.0.2-0ubuntu2_amd64.deb) ...
Unpacking replacement libsyncdaemon-1.0-1 ...
Preparing to replace ubuntuone-client 3.0.2-0ubuntu1 (using .../ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement ubuntuone-client ...
Preparing to replace python-ubuntuone-client 3.0.2-0ubuntu1 (using .../python-ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement python-ubuntuone-client ...
Preparing to replace pulseaudio-utils 1:1.1-0ubuntu15.3 (using .../pulseaudio-utils_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace pulseaudio 1:1.1-0ubuntu15.3 (using .../pulseaudio_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio ...
Preparing to replace pulseaudio-module-gconf 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-gconf_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-gconf ...
Preparing to replace pulseaudio-module-x11 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-x11_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-x11 ...
Preparing to replace python-openssl 0.12-1ubuntu2 (using .../python-openssl_0.12-1ubuntu2.1_amd64.deb) ...
Unpacking replacement python-openssl ...
Preparing to replace python-software-properties 0.82.7.3 (using .../python-software-properties_0.82.7.5_all.deb) ...
Unpacking replacement python-software-properties ...
Preparing to replace rtkit 0.10-2 (using .../rtkit_0.10-2ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement rtkit ...
Preparing to replace samba-tools 2:3.6.3-2ubuntu2.7 (using .../samba-tools_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-tools ...
Preparing to replace software-properties-common 0.82.7.3 (using .../software-properties-common_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-common ...
Preparing to replace software-properties-gtk 0.82.7.3 (using .../software-properties-gtk_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-gtk ...
Preparing to replace thunderbird-globalmenu 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird-locale-en 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace thunderbird-locale-en-us 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a24.0+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Preparing to replace ubuntu-system-service 0.2.2 (using .../ubuntu-system-service_0.2.2.1_all.deb) ...
Unpacking replacement ubuntu-system-service ...
Preparing to replace usb-creator-gtk 0.2.38 (using .../usb-creator-gtk_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-gtk ...
Preparing to replace usb-creator-common 0.2.38 (using .../usb-creator-common_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-common ...
Preparing to replace vino 3.4.2-0ubuntu1.2 (using .../vino_3.4.2-0ubuntu1.3_amd64.deb) ...
Unpacking replacement vino ...
Preparing to replace gnome-settings-daemon 3.4.2-0ubuntu0.6.2 (using .../gnome-settings-daemon_3.4.2-0ubuntu0.6.3_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace pulseaudio-module-bluetooth 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-bluetooth_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-bluetooth ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for cups ...
Updating PPD files for hpcups ...
Updating PPD files for postscript-hp ...
Processing triggers for menu ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Setting up initramfs-tools (0.99ubuntu13.2) ...
update-initramfs: deferring update (trigger activated)
Setting up apparmor (2.7.102-0ubuntu3.9) ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.14) ...
Setting up python2.7 (2.7.3-0ubuntu3.4) ...
Setting up libpython2.7 (2.7.3-0ubuntu3.4) ...
Setting up python2.7-dev (2.7.3-0ubuntu3.4) ...
Setting up language-selector-common (0.79.4) ...
Setting up language-selector-gnome (0.79.4) ...
Setting up libcurl3-gnutls (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-gobject-1-0 (0.104-1ubuntu1.1) ...
Setting up libcurl3-nss (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-agent-1-0 (0.104-1ubuntu1.1) ...
Setting up libpolkit-backend-1-0 (0.104-1ubuntu1.1) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common (2:3.6.3-2ubuntu2.8) ...
Setting up winbind (2:3.6.3-2ubuntu2.8) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 
Setting up libpam-winbind (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.8) ...
Setting up samba (2:3.6.3-2ubuntu2.8) ...
smbd start/running, process 15315
nmbd start/running, process 15353
Setting up smbclient (2:3.6.3-2ubuntu2.8) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.8) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.14) ...
Setting up isc-dhcp-common (4.1.ESV-R4-0ubuntu5.9) ...
Setting up isc-dhcp-client (4.1.ESV-R4-0ubuntu5.9) ...
Setting up rsyslog (5.8.6-1ubuntu8.5) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
rsyslog stop/waiting
rsyslog start/running, process 15503
Setting up ifupdown (0.7~beta2ubuntu10) ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.14) ...
Setting up apt-xapian-index (0.44ubuntu5.1) ...
Setting up linux-libc-dev (3.2.0-54.82) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-52-generic
Building for architecture x86_64
Building initial module for 3.2.0-52-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-52-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up firefox (24.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-zh-hans (24.0+build1-0ubuntu0.12.04.1) ...
Setting up libhpmud0 (3.12.2-1ubuntu3.3) ...
Setting up libsane-hpaio (3.12.2-1ubuntu3.3) ...
Setting up hplip-data (3.12.2-1ubuntu3.3) ...
Setting up printer-driver-hpcups (3.12.2-1ubuntu3.3) ...
Setting up policykit-1 (0.104-1ubuntu1.1) ...
Setting up hplip (3.12.2-1ubuntu3.3) ...
Creating/updating hplip user account...
Setting up printer-driver-postscript-hp (3.12.2-1ubuntu3.3) ...
Setting up hplip-gui (3.12.2-1ubuntu3.3) ...
Setting up jockey-common (0.9.7-0ubuntu7.11) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.11) ...
Setting up python3.2-minimal (3.2.3-0ubuntu3.5) ...
Setting up python3.2 (3.2.3-0ubuntu3.5) ...
Setting up libpython3.2 (3.2.3-0ubuntu3.5) ...
Setting up libraw5 (0.14.4-0ubuntu2.2) ...
Setting up python-ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up libsyncdaemon-1.0-1 (3.0.2-0ubuntu2) ...
Setting up pulseaudio-utils (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-gconf (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-x11 (1:1.1-0ubuntu15.4) ...
Setting up python-openssl (0.12-1ubuntu2.1) ...
Setting up python-software-properties (0.82.7.5) ...
Setting up rtkit (0.10-2ubuntu0.12.04.1) ...
Setting up samba-tools (2:3.6.3-2ubuntu2.8) ...
Setting up software-properties-common (0.82.7.5) ...
Setting up software-properties-gtk (0.82.7.5) ...
Setting up thunderbird (1:24.0+build1-0ubuntu0.12.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-globalmenu (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up ubuntu-system-service (0.2.2.1) ...
Setting up usb-creator-common (0.2.38.2) ...
Setting up usb-creator-gtk (0.2.38.2) ...
Setting up vino (3.4.2-0ubuntu1.3) ...
Setting up gnome-settings-daemon (3.4.2-0ubuntu0.6.3) ...
Setting up pulseaudio-module-bluetooth (1:1.1-0ubuntu15.4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-52-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-52-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$ sudo apt-get update

```

```
Get:69 http://security.ubuntu.com/ubuntu/ precise-security/main python3.2-minimal amd64 3.2.3-0ubuntu3.5 [1,776 kB]
Get:70 http://security.ubuntu.com/ubuntu/ precise-security/main libraw5 amd64 0.14.4-0ubuntu2.2 [317 kB]
Get:71 http://security.ubuntu.com/ubuntu/ precise-security/main python-openssl amd64 0.12-1ubuntu2.1 [99.8 kB]
Get:72 http://security.ubuntu.com/ubuntu/ precise-security/main python-software-properties all 0.82.7.5 [22.3 kB]
Get:73 http://security.ubuntu.com/ubuntu/ precise-security/main rtkit amd64 0.10-2ubuntu0.12.04.1 [36.3 kB]
Get:74 http://security.ubuntu.com/ubuntu/ precise-security/universe samba-tools amd64 2:3.6.3-2ubuntu2.8 [11.6 MB]
Get:75 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-common all 0.82.7.5 [8,944 B]
Get:76 http://security.ubuntu.com/ubuntu/ precise-security/main software-properties-gtk all 0.82.7.5 [34.6 kB]
Get:77 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-globalmenu amd64 1:24.0+build1-0ubuntu0.12.04.1 [8,786 B]
Get:78 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en amd64 1:24.0+build1-0ubuntu0.12.04.1 [343 kB]
Get:79 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird amd64 1:24.0+build1-0ubuntu0.12.04.1 [29.5 MB]
Get:80 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-gnome-support amd64 1:24.0+build1-0ubuntu0.12.04.1 [9,132 B]
Get:81 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en-us all 1:24.0+build1-0ubuntu0.12.04.1 [14.0 kB]
Get:82 http://security.ubuntu.com/ubuntu/ precise-security/main ubuntu-system-service all 0.2.2.1 [12.1 kB]
Get:83 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-gtk amd64 0.2.38.2 [26.9 kB]
Get:84 http://security.ubuntu.com/ubuntu/ precise-security/main usb-creator-common amd64 0.2.38.2 [23.6 kB]
Get:85 http://security.ubuntu.com/ubuntu/ precise-security/main vino amd64 3.4.2-0ubuntu1.3 [170 kB]
Fetched 167 MB in 14min 34s (191 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.12 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.14) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.12 (using .../apt_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp12ubuntu10.14) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10.12 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace python2.7-dev 2.7.3-0ubuntu3.3 (using .../python2.7-dev_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-dev ...
Preparing to replace libpython2.7 2.7.3-0ubuntu3.3 (using .../libpython2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement libpython2.7 ...
Preparing to replace python2.7 2.7.3-0ubuntu3.3 (using .../python2.7_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7 ...
Preparing to replace python2.7-minimal 2.7.3-0ubuntu3.3 (using .../python2.7-minimal_2.7.3-0ubuntu3.4_amd64.deb) ...
Unpacking replacement python2.7-minimal ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Setting up python2.7-minimal (2.7.3-0ubuntu3.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace language-selector-gnome 0.79.3 (using .../language-selector-gnome_0.79.4_all.deb) ...
Unpacking replacement language-selector-gnome ...
Preparing to replace language-selector-common 0.79.3 (using .../language-selector-common_0.79.4_all.deb) ...
Unpacking replacement language-selector-common ...
Preparing to replace libldap-2.4-2 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_amd64.deb) ...
De-configuring libldap-2.4-2:i386 ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace libldap-2.4-2:i386 2.4.28-1.1ubuntu4.3 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.4_i386.deb) ...
Unpacking replacement libldap-2.4-2:i386 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up libldap-2.4-2 (2.4.28-1.1ubuntu4.4) ...
Setting up libldap-2.4-2:i386 (2.4.28-1.1ubuntu4.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-gnutls 7.22.0-3ubuntu4.2 (using .../libcurl3-gnutls_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-gnutls ...
Preparing to replace libpolkit-gobject-1-0 0.104-1ubuntu1 (using .../libpolkit-gobject-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-gobject-1-0 ...
Preparing to replace libaudio2:i386 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_i386.deb) ...
De-configuring libaudio2 ...
Unpacking replacement libaudio2:i386 ...
Preparing to replace libaudio2 1.9.3-4 (using .../libaudio2_1.9.3-4ubuntu0.1_amd64.deb) ...
Unpacking replacement libaudio2 ...
Setting up libaudio2:i386 (1.9.3-4ubuntu0.1) ...
Setting up libaudio2 (1.9.3-4ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3:i386 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_i386.deb) ...
De-configuring libcurl3 ...
Unpacking replacement libcurl3:i386 ...
Preparing to replace libcurl3 7.22.0-3ubuntu4.2 (using .../libcurl3_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3 ...
Setting up libcurl3:i386 (7.22.0-3ubuntu4.3) ...
Setting up libcurl3 (7.22.0-3ubuntu4.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libcurl3-nss 7.22.0-3ubuntu4.2 (using .../libcurl3-nss_7.22.0-3ubuntu4.3_amd64.deb) ...
Unpacking replacement libcurl3-nss ...
Preparing to replace libpolkit-agent-1-0 0.104-1ubuntu1 (using .../libpolkit-agent-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-agent-1-0 ...
Preparing to replace libpolkit-backend-1-0 0.104-1ubuntu1 (using .../libpolkit-backend-1-0_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libpolkit-backend-1-0 ...
Preparing to replace libpulse0 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
De-configuring libpulse0:i386 ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse0:i386 1:1.1-0ubuntu15.3 (using .../libpulse0_1%3a1.1-0ubuntu15.4_i386.deb) ...
Unpacking replacement libpulse0:i386 ...
Setting up libpulse0 (1:1.1-0ubuntu15.4) ...
Setting up libpulse0:i386 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulse-mainloop-glib0:i386 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulse-mainloop-glib0 ...
Unpacking replacement libpulse-mainloop-glib0:i386 ...
Preparing to replace libpulse-mainloop-glib0 1:1.1-0ubuntu15.3 (using .../libpulse-mainloop-glib0_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Setting up libpulse-mainloop-glib0:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulse-mainloop-glib0 (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpulsedsp:i386 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_i386.deb) ...
De-configuring libpulsedsp ...
Unpacking replacement libpulsedsp:i386 ...
Preparing to replace libpulsedsp 1:1.1-0ubuntu15.3 (using .../libpulsedsp_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement libpulsedsp ...
Setting up libpulsedsp:i386 (1:1.1-0ubuntu15.4) ...
Setting up libpulsedsp (1:1.1-0ubuntu15.4) ...
(Reading database ... 594853 files and directories currently installed.)
Preparing to replace libpam-winbind 2:3.6.3-2ubuntu2.7 (using .../libpam-winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libpam-winbind ...
Preparing to replace winbind 2:3.6.3-2ubuntu2.7 (using .../winbind_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Unpacking replacement winbind ...
Preparing to replace samba 2:3.6.3-2ubuntu2.7 (using .../samba_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
nmbd stop/waiting
smbd stop/waiting
Unpacking replacement samba ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.7 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.7 (using .../smbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.7 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.7 (using .../samba-common_2%3a3.6.3-2ubuntu2.8_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.7 (using .../libsmbclient_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.12 (using .../apt-utils_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace isc-dhcp-client 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-client_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-client ...
Preparing to replace isc-dhcp-common 4.1.ESV-R4-0ubuntu5.8 (using .../isc-dhcp-common_4.1.ESV-R4-0ubuntu5.9_amd64.deb) ...
Unpacking replacement isc-dhcp-common ...
Preparing to replace rsyslog 5.8.6-1ubuntu8.4 (using .../rsyslog_5.8.6-1ubuntu8.5_amd64.deb) ...
Unpacking replacement rsyslog ...
Preparing to replace ifupdown 0.7~beta2ubuntu8 (using .../ifupdown_0.7~beta2ubuntu10_amd64.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.12 (using .../apt-transport-https_0.8.16~exp12ubuntu10.14_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace apt-xapian-index 0.44ubuntu5 (using .../apt-xapian-index_0.44ubuntu5.1_all.deb) ...
Unpacking replacement apt-xapian-index ...
Preparing to replace linux-libc-dev 3.2.0-53.81 (using .../linux-libc-dev_3.2.0-54.82_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace firefox 23.0+build2-0ubuntu0.12.04.1 (using .../firefox_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-globalmenu_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-en_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace firefox-locale-zh-hans 23.0+build2-0ubuntu0.12.04.1 (using .../firefox-locale-zh-hans_24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-zh-hans ...
Preparing to replace printer-driver-postscript-hp 3.12.2-1ubuntu3.1 (using .../printer-driver-postscript-hp_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement printer-driver-postscript-hp ...
Preparing to replace libsane-hpaio 3.12.2-1ubuntu3.1 (using .../libsane-hpaio_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace hplip 3.12.2-1ubuntu3.1 (using .../hplip_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.12.2-1ubuntu3.1 (using .../libhpmud0_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.12.2-1ubuntu3.1 (using .../hplip-data_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace printer-driver-hpcups 3.12.2-1ubuntu3.1 (using .../printer-driver-hpcups_3.12.2-1ubuntu3.3_amd64.deb) ...
Unpacking replacement printer-driver-hpcups ...
Preparing to replace policykit-1 0.104-1ubuntu1 (using .../policykit-1_0.104-1ubuntu1.1_amd64.deb) ...
Unpacking replacement policykit-1 ...
Preparing to replace hplip-gui 3.12.2-1ubuntu3.1 (using .../hplip-gui_3.12.2-1ubuntu3.3_all.deb) ...
Unpacking replacement hplip-gui ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.10 (using .../jockey-gtk_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.10 (using .../jockey-common_0.9.7-0ubuntu7.11_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace libpython3.2 3.2.3-0ubuntu3.4 (using .../libpython3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement libpython3.2 ...
Preparing to replace python3.2 3.2.3-0ubuntu3.4 (using .../python3.2_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2 ...
Preparing to replace python3.2-minimal 3.2.3-0ubuntu3.4 (using .../python3.2-minimal_3.2.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python3.2-minimal ...
Preparing to replace libraw5 0.14.4-0ubuntu2.1 (using .../libraw5_0.14.4-0ubuntu2.2_amd64.deb) ...
Unpacking replacement libraw5 ...
Preparing to replace libsyncdaemon-1.0-1 3.0.2-0ubuntu1 (using .../libsyncdaemon-1.0-1_3.0.2-0ubuntu2_amd64.deb) ...
Unpacking replacement libsyncdaemon-1.0-1 ...
Preparing to replace ubuntuone-client 3.0.2-0ubuntu1 (using .../ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement ubuntuone-client ...
Preparing to replace python-ubuntuone-client 3.0.2-0ubuntu1 (using .../python-ubuntuone-client_3.0.2-0ubuntu2_all.deb) ...
Unpacking replacement python-ubuntuone-client ...
Preparing to replace pulseaudio-utils 1:1.1-0ubuntu15.3 (using .../pulseaudio-utils_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace pulseaudio 1:1.1-0ubuntu15.3 (using .../pulseaudio_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio ...
Preparing to replace pulseaudio-module-gconf 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-gconf_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-gconf ...
Preparing to replace pulseaudio-module-x11 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-x11_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-x11 ...
Preparing to replace python-openssl 0.12-1ubuntu2 (using .../python-openssl_0.12-1ubuntu2.1_amd64.deb) ...
Unpacking replacement python-openssl ...
Preparing to replace python-software-properties 0.82.7.3 (using .../python-software-properties_0.82.7.5_all.deb) ...
Unpacking replacement python-software-properties ...
Preparing to replace rtkit 0.10-2 (using .../rtkit_0.10-2ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement rtkit ...
Preparing to replace samba-tools 2:3.6.3-2ubuntu2.7 (using .../samba-tools_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Unpacking replacement samba-tools ...
Preparing to replace software-properties-common 0.82.7.3 (using .../software-properties-common_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-common ...
Preparing to replace software-properties-gtk 0.82.7.3 (using .../software-properties-gtk_0.82.7.5_all.deb) ...
Unpacking replacement software-properties-gtk ...
Preparing to replace thunderbird-globalmenu 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird-locale-en 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_1%3a24.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace thunderbird-locale-en-us 1:17.0.8+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a24.0+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Preparing to replace ubuntu-system-service 0.2.2 (using .../ubuntu-system-service_0.2.2.1_all.deb) ...
Unpacking replacement ubuntu-system-service ...
Preparing to replace usb-creator-gtk 0.2.38 (using .../usb-creator-gtk_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-gtk ...
Preparing to replace usb-creator-common 0.2.38 (using .../usb-creator-common_0.2.38.2_amd64.deb) ...
Unpacking replacement usb-creator-common ...
Preparing to replace vino 3.4.2-0ubuntu1.2 (using .../vino_3.4.2-0ubuntu1.3_amd64.deb) ...
Unpacking replacement vino ...
Preparing to replace gnome-settings-daemon 3.4.2-0ubuntu0.6.2 (using .../gnome-settings-daemon_3.4.2-0ubuntu0.6.3_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace pulseaudio-module-bluetooth 1:1.1-0ubuntu15.3 (using .../pulseaudio-module-bluetooth_1%3a1.1-0ubuntu15.4_amd64.deb) ...
Unpacking replacement pulseaudio-module-bluetooth ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for cups ...
Updating PPD files for hpcups ...
Updating PPD files for postscript-hp ...
Processing triggers for menu ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Setting up initramfs-tools (0.99ubuntu13.2) ...
update-initramfs: deferring update (trigger activated)
Setting up apparmor (2.7.102-0ubuntu3.9) ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.14) ...
Setting up python2.7 (2.7.3-0ubuntu3.4) ...
Setting up libpython2.7 (2.7.3-0ubuntu3.4) ...
Setting up python2.7-dev (2.7.3-0ubuntu3.4) ...
Setting up language-selector-common (0.79.4) ...
Setting up language-selector-gnome (0.79.4) ...
Setting up libcurl3-gnutls (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-gobject-1-0 (0.104-1ubuntu1.1) ...
Setting up libcurl3-nss (7.22.0-3ubuntu4.3) ...
Setting up libpolkit-agent-1-0 (0.104-1ubuntu1.1) ...
Setting up libpolkit-backend-1-0 (0.104-1ubuntu1.1) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common (2:3.6.3-2ubuntu2.8) ...
Setting up winbind (2:3.6.3-2ubuntu2.8) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 
Setting up libpam-winbind (2:3.6.3-2ubuntu2.8) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.8) ...
Setting up samba (2:3.6.3-2ubuntu2.8) ...
smbd start/running, process 15315
nmbd start/running, process 15353
Setting up smbclient (2:3.6.3-2ubuntu2.8) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.8) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.14) ...
Setting up isc-dhcp-common (4.1.ESV-R4-0ubuntu5.9) ...
Setting up isc-dhcp-client (4.1.ESV-R4-0ubuntu5.9) ...
Setting up rsyslog (5.8.6-1ubuntu8.5) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
rsyslog stop/waiting
rsyslog start/running, process 15503
Setting up ifupdown (0.7~beta2ubuntu10) ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.14) ...
Setting up apt-xapian-index (0.44ubuntu5.1) ...
Setting up linux-libc-dev (3.2.0-54.82) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-52-generic
Building for architecture x86_64
Building initial module for 3.2.0-52-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-52-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up firefox (24.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (24.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-zh-hans (24.0+build1-0ubuntu0.12.04.1) ...
Setting up libhpmud0 (3.12.2-1ubuntu3.3) ...
Setting up libsane-hpaio (3.12.2-1ubuntu3.3) ...
Setting up hplip-data (3.12.2-1ubuntu3.3) ...
Setting up printer-driver-hpcups (3.12.2-1ubuntu3.3) ...
Setting up policykit-1 (0.104-1ubuntu1.1) ...
Setting up hplip (3.12.2-1ubuntu3.3) ...
Creating/updating hplip user account...
Setting up printer-driver-postscript-hp (3.12.2-1ubuntu3.3) ...
Setting up hplip-gui (3.12.2-1ubuntu3.3) ...
Setting up jockey-common (0.9.7-0ubuntu7.11) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.11) ...
Setting up python3.2-minimal (3.2.3-0ubuntu3.5) ...
Setting up python3.2 (3.2.3-0ubuntu3.5) ...
Setting up libpython3.2 (3.2.3-0ubuntu3.5) ...
Setting up libraw5 (0.14.4-0ubuntu2.2) ...
Setting up python-ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up ubuntuone-client (3.0.2-0ubuntu2) ...
Setting up libsyncdaemon-1.0-1 (3.0.2-0ubuntu2) ...
Setting up pulseaudio-utils (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-gconf (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-x11 (1:1.1-0ubuntu15.4) ...
Setting up python-openssl (0.12-1ubuntu2.1) ...
Setting up python-software-properties (0.82.7.5) ...
Setting up rtkit (0.10-2ubuntu0.12.04.1) ...
Setting up samba-tools (2:3.6.3-2ubuntu2.8) ...
Setting up software-properties-common (0.82.7.5) ...
Setting up software-properties-gtk (0.82.7.5) ...
Setting up thunderbird (1:24.0+build1-0ubuntu0.12.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-globalmenu (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:24.0+build1-0ubuntu0.12.04.1) ...
Setting up ubuntu-system-service (0.2.2.1) ...
Setting up usb-creator-common (0.2.38.2) ...
Setting up usb-creator-gtk (0.2.38.2) ...
Setting up vino (3.4.2-0ubuntu1.3) ...
Setting up gnome-settings-daemon (3.4.2-0ubuntu0.6.3) ...
Setting up pulseaudio-module-bluetooth (1:1.1-0ubuntu15.4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-52-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-52-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
alrick@Home:~$ sudo apt-get upgrade
```

---

### Post by Bashing-om on 2013-10-03
blueboy1
Info for you .. codes -> the "#" symbol denotes a comment, not to be entered or executed, it and all after that line.


The outputs are not what I had expected, though I had expected to perhaps have to once more (re)install "initramfs-tool-bin".
However; This:
> 
gzip: stdout: No space left on device

says we have more problems, and maybe the cause of all of this to start with. Let's see what the disk usage is.
```

du -h --max-depth=1 | sort -hr
df -i
ls -la /boot

```

And this:
> 
Errors were encountered while processing:
 initramfs-tools
says we still have problems, and the package manager gives no hints this time what the nature is.

As we are out of disk space, have no operating room, that situation now takes priority before we can continue with "initramfs-tools(-bin).

[INDENT][INDENT]trials troubles and tribulations
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-04
```
alrick@Home:~$ du -h --max-depth=1 | sort -hr
du: cannot read directory `./.config/nautilus-actions': Permission denied
121G	.
50G	./Downloads
24G	./Work
20G	./Pictures
13G	./Desktop
3.5G	./.wine
3.3G	./X-Plane 10 Demo
2.9G	./.googleearth
1.3G	./Videos
1.2G	./Documents
1002M	./.thunderbird
825M	./Airports
794M	./.cache
303M	./.PlayOnLinux
207M	./.mozilla
115M	./VirtualBox VMs
86M	./.local
68M	./.adobe
66M	./AI
63M	./.minecraft
62M	./.shotwell
49M	./Terrain
42M	./C130
40M	./thunderbird
37M	./.config
33M	./.webex
32M	./.eclipse
25M	./.thumbnails
19M	./757-200
16M	./SR71-BlackBird
15M	./777-200
13M	./.Skype
13M	./ec130
13M	./787
12M	./res
11M	./texinfo-4.13a.dfsg.1
9.4M	./737NG900
7.1M	./lib
5.1M	./.rpmdb
5.1M	./Models
4.7M	./Objects
3.6M	./.icedtea
3.0M	./X15
2.9M	./.gconf
2.2M	./.fgfs
2.0M	./__MACOSX
1.6M	./.launchpadlib
1.5M	./.teamviewer
1.5M	./Music
1.5M	./.compiz-1
952K	./$PLUGINSDIR
908K	./.gstreamer-0.10
864K	./paraglider
736K	./.fontconfig
524K	./.gimp-2.6
484K	./.spumux
424K	./Euro Truck Simulator 2
388K	./Nasal
356K	./workspace
224K	./META-INF
224K	./.macromedia
184K	./YSFLIGHT.COM
164K	./.mypaint
156K	./.torcs
136K	./Lothian
128K	./.rsrc
128K	./Docs
124K	./.kde
112K	./.VirtualBox
100K	./.pulse
64K	./.ICAClient
56K	./.tuxmath
56K	./$SHELL[17]
48K	./.subversion
36K	./.pki
36K	./.gnome2
36K	./assets
28K	./.dvdcss
24K	./.gnupg
24K	./.fltk
20K	./.etracer
16K	./.x-plane
16K	./Templates
16K	./.swt
16K	./.sane
16K	./.gegl-0.0
16K	./.dbus
16K	./cn
12K	./.mission-control
12K	./.hplip
12K	./2.ICAClient
8.0K	./.synaptic
8.0K	./.mplayer
8.0K	./.mono
4.0K	./Ubuntu One
4.0K	./Public
4.0K	./Podcasts
4.0K	./New Folder2
4.0K	./New Folder
4.0K	./.gphoto
4.0K	./.gnome2_private
4.0K	./.fgo
0	./.gvfs

```

```
alrick@Home:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda2       6447104 628063  5819041   10% /
udev             952601    661   951940    1% /dev
tmpfs            954803    583   954220    1% /run
none             954803      3   954800    1% /run/lock
none             954803      8   954795    1% /run/shm
/dev/sda1         85680    331    85349    1% /boot
/dev/sda4      76324864 245967 76078897    1% /home
/dev/sda5       8511488   8468  8503020    1% /media/a40d396c-78c0-41d2-9cef-c0974ff5abde

```

```
alrick@Home:~$ ls -la /boot
total 313322
drwxr-xr-x  5 root root     5120 Oct  3 22:38 .
drwxr-xr-x 26 root root     4096 Aug  5 22:53 ..
-rw-r--r--  1 root root   791023 Apr 10  2012 abi-3.2.0-23-generic
-rw-r--r--  1 root root   791075 May 21  2012 abi-3.2.0-24-generic
-rw-r--r--  1 root root   791132 May 23  2012 abi-3.2.0-25-generic
-rw-r--r--  1 root root   791326 Jun 14  2012 abi-3.2.0-26-generic
-rw-r--r--  1 root root   791281 Jul  6  2012 abi-3.2.0-27-generic
-rw-r--r--  1 root root   791281 Jul 27  2012 abi-3.2.0-29-generic
-rw-r--r--  1 root root   791446 Aug 24  2012 abi-3.2.0-30-generic
-rw-r--r--  1 root root   791446 Sep  7  2012 abi-3.2.0-31-generic
-rw-r--r--  1 root root   792532 Sep 26  2012 abi-3.2.0-32-generic
-rw-r--r--  1 root root   792532 Oct 18  2012 abi-3.2.0-33-generic
-rw-r--r--  1 root root   792587 Nov 15  2012 abi-3.2.0-34-generic
-rw-r--r--  1 root root   795365 Jun 18 14:20 abi-3.2.0-49-generic
-rw-r--r--  1 root root   795365 Jul  9 15:44 abi-3.2.0-50-generic
-rw-r--r--  1 root root   795365 Jul 26 13:08 abi-3.2.0-52-generic
-rw-r--r--  1 root root   140279 Apr 10  2012 config-3.2.0-23-generic
-rw-r--r--  1 root root   140341 May 21  2012 config-3.2.0-24-generic
-rw-r--r--  1 root root   140407 May 23  2012 config-3.2.0-25-generic
-rw-r--r--  1 root root   140454 Jun 14  2012 config-3.2.0-26-generic
-rw-r--r--  1 root root   140454 Jul  6  2012 config-3.2.0-27-generic
-rw-r--r--  1 root root   140432 Jul 27  2012 config-3.2.0-29-generic
-rw-r--r--  1 root root   140432 Aug 24  2012 config-3.2.0-30-generic
-rw-r--r--  1 root root   140459 Sep  7  2012 config-3.2.0-31-generic
-rw-r--r--  1 root root   140488 Sep 26  2012 config-3.2.0-32-generic
-rw-r--r--  1 root root   140488 Oct 18  2012 config-3.2.0-33-generic
-rw-r--r--  1 root root   140505 Nov 15  2012 config-3.2.0-34-generic
-rw-r--r--  1 root root   140622 Jun 18 14:20 config-3.2.0-49-generic
-rw-r--r--  1 root root   140629 Jul  9 15:44 config-3.2.0-50-generic
-rw-r--r--  1 root root   140629 Jul 26 13:08 config-3.2.0-52-generic
drwxr-xr-x  3 root root     1024 Sep 10 17:57 extlinux
drwxr-xr-x  3 root root     8192 Aug  5 22:54 grub
-rw-r--r--  1 root root 14171220 Apr 30  2012 initrd.img-3.2.0-23-generic
-rw-r--r--  1 root root 14172899 May 25  2012 initrd.img-3.2.0-24-generic
-rw-r--r--  1 root root 14171640 Jun 15  2012 initrd.img-3.2.0-25-generic
-rw-r--r--  1 root root 14186606 Jul  2  2012 initrd.img-3.2.0-26-generic
-rw-r--r--  1 root root 14202578 Jul 23  2012 initrd.img-3.2.0-27-generic
-rw-r--r--  1 root root 14199834 Aug 16  2012 initrd.img-3.2.0-29-generic
-rw-r--r--  1 root root 14200509 Sep  6  2012 initrd.img-3.2.0-30-generic
-rw-r--r--  1 root root 14206185 Oct  4  2012 initrd.img-3.2.0-31-generic
-rw-r--r--  1 root root 14205079 Nov  5  2012 initrd.img-3.2.0-32-generic
-rw-r--r--  1 root root 14203578 Nov 19  2012 initrd.img-3.2.0-33-generic
-rw-r--r--  1 root root 12747267 Jun 26 23:38 initrd.img-3.2.0-34-generic
-rw-r--r--  1 root root 14246449 Jun 27 00:08 initrd.img-3.2.0-49-generic
-rw-r--r--  1 root root 14245881 Jul 24 13:13 initrd.img-3.2.0-50-generic
-rw-r--r--  1 root root 14246843 Aug  5 22:54 initrd.img-3.2.0-52-generic
drwx------  2 root root    12288 Apr 30  2012 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2884358 Apr 10  2012 System.map-3.2.0-23-generic
-rw-------  1 root root  2884673 May 21  2012 System.map-3.2.0-24-generic
-rw-------  1 root root  2886695 May 23  2012 System.map-3.2.0-25-generic
-rw-------  1 root root  2881851 Jun 14  2012 System.map-3.2.0-26-generic
-rw-------  1 root root  2882027 Jul  6  2012 System.map-3.2.0-27-generic
-rw-------  1 root root  2882108 Jul 27  2012 System.map-3.2.0-29-generic
-rw-------  1 root root  2883362 Aug 24  2012 System.map-3.2.0-30-generic
-rw-------  1 root root  2883401 Sep  7  2012 System.map-3.2.0-31-generic
-rw-------  1 root root  2884076 Sep 26  2012 System.map-3.2.0-32-generic
-rw-------  1 root root  2884306 Oct 18  2012 System.map-3.2.0-33-generic
-rw-------  1 root root  2885127 Nov 15  2012 System.map-3.2.0-34-generic
-rw-------  1 root root  2893287 Jun 18 14:20 System.map-3.2.0-49-generic
-rw-------  1 root root  2893555 Jul  9 15:44 System.map-3.2.0-50-generic
-rw-------  1 root root  2893555 Jul 26 13:08 System.map-3.2.0-52-generic
-rw-r--r--  1 root root  4965840 Apr 25  2012 vmlinuz-3.2.0-23-generic
-rw-------  1 root root  4965968 May 21  2012 vmlinuz-3.2.0-24-generic
-rw-------  1 root root  4969488 May 23  2012 vmlinuz-3.2.0-25-generic
-rw-------  1 root root  4960080 Jun 14  2012 vmlinuz-3.2.0-26-generic
-rw-------  1 root root  4960848 Jul  6  2012 vmlinuz-3.2.0-27-generic
-rw-------  1 root root  4960752 Jul 27  2012 vmlinuz-3.2.0-29-generic
-rw-------  1 root root  4963280 Aug 24  2012 vmlinuz-3.2.0-30-generic
-rw-------  1 root root  4963792 Sep  7  2012 vmlinuz-3.2.0-31-generic
-rw-------  1 root root  4966768 Sep 26  2012 vmlinuz-3.2.0-32-generic
-rw-------  1 root root  4966896 Oct 18  2012 vmlinuz-3.2.0-33-generic
-rw-------  1 root root  4967632 Nov 15  2012 vmlinuz-3.2.0-34-generic
-rw-------  1 root root  4978416 Jun 18 14:20 vmlinuz-3.2.0-49-generic
-rw-------  1 root root  4978672 Jul  9 15:44 vmlinuz-3.2.0-50-generic
-rw-------  1 root root  4978224 Jul 26 13:08 vmlinuz-3.2.0-52-generic

```

---

### Post by Azyx on 2013-10-04
> **Bashing-om said:**
> @ Azyx; I agree, not a good thing to enable "backport" and "proposed" repository sources, unless one has a demonstrated need to do so .. When enabled one should be aware that these can and do break your stable system .. software from "backports" should work but can not fit every configuration; where as "proposed" is just that .. maybe ! .. proposed is for development work/testing -expect breakage.
[INDENT][INDENT]but ain't ubuntu wonderful
[/INDENT]
[/INDENT]


But if you ones have them enabled 'proposed' and/or 'backports' and when uncheck them results in higher risk of dependency problems? Like if you try to downgrade from 6.10 to 6.04?

I always have root, / and /home on different partitions, so if something get broken, you only reinstall the system and it takes an half hour and then installing application I missed. Take also back up for samba shares (smb.conf) and stuff, that are not placed in /home. 

I have not have any big problems for years.

Ubuntu is the best!!!! I don't think there are another GNU/Linux system that have 5 years support, as for LTS..Otherwise I maybee tried another distrubition as Debian or so...

/Cheers

---

### Post by Bashing-om on 2013-10-04
blueboy1; Hi !

Disk usage does not appear real bad, downloads could stand cleaning up and a bit of house keeping for the old boot kernels you no longer have a use for. But, to get a better picture of what is going on:
```

df -h

```
I should have asked for that one too .. just did not think too.

@ Azyx. Yeah, I also run split partitions on multiple hard drives. In the learning curve I have broke my system numerous times to the point of practice and good backups (learned the hard way) and my scripts; I can (RE-)install from scratch and be back up in 20 minutes. For those of us who have an idea as to what we are doing and what we require of out operating system of choice, enabling  "BackPorts" and "ProPosed" repositories is all right. For those just getting introduced to 'buntu, enabling those repositories can result in more difficulties than they are prepared to cope with. Particularly in our expanding world of software and integration.

[INDENT][INDENT]all things can work to the good
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-04
Hey, he is back, here we go.

```
alrick@Home:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        97G   13G   80G  14% /
udev            3.7G  4.0K  3.7G   1% /dev
tmpfs           1.5G  1.3M  1.5G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.7G  216K  3.7G   1% /run/shm
/dev/sda1       324M  322M     0 100% /boot
/dev/sda4       1.2T  122G  967G  12% /home
/dev/sda5       128G  733M  121G   1% /media/a40d396c-78c0-41d2-9cef-c0974ff5abde

```

---

### Post by varunendra on 2013-10-04
Hey Bashing-om ! Looks like you found it !! :P
> **blueboy1 said:**
> 
```
alrick@Home:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        97G   13G   80G  14% /
udev            3.7G  4.0K  3.7G   1% /dev
tmpfs           1.5G  1.3M  1.5G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.7G  216K  3.7G   1% /run/shm
**/dev/sda1       324M  322M     [COLOR="#FF0000"]0 100%[/COLOR] /boot**
/dev/sda4       1.2T  122G  967G  12% /home
/dev/sda5       128G  733M  121G   1% /media/a40d396c-78c0-41d2-9cef-c0974ff5abde

```
Only 2 MB (or less) space remaining on /boot where initrd.img is created.

I must say I was watching this thread since two days, tried a couple of things, but with the kind of results I got, didn't dare to suggest them.:P

@ blueboy1,

If you can still boot the system (I doubt with the remaining space, but since it is just /boot, you should be able to), please post back the output of -
```
dpkg -l | grep linux-image
```
We expect it to be a long list, of which you should be able to manually remove some to free space (the recommended "apt-get-purge" method will almost certainly fail with so little space).

---

### Post by blueboy1 on 2013-10-04
The system is partitioned. Can I transition some of the info, or backages to unused space on a more vacant drive. Pleae let me know. While you ponder that thought here is the output for the code:

```
alrick@Home:~$ dpkg -l | grep linux-image
ii  linux-image-3.2.0-23-generic                                3.2.0-23.36                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-24-generic                                3.2.0-24.39                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-25-generic                                3.2.0-25.40                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-26-generic                                3.2.0-26.41                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-27-generic                                3.2.0-27.43                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-29-generic                                3.2.0-29.46                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-30-generic                                3.2.0-30.48                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic                                3.2.0-31.50                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-32-generic                                3.2.0-32.51                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-33-generic                                3.2.0-33.52                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-34-generic                                3.2.0-34.53                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-49-generic                                3.2.0-49.75                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-50-generic                                3.2.0-50.76                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic                                3.2.0-52.78                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP

```

---

### Post by varunendra on 2013-10-04
> **blueboy1 said:**
> The system is partitioned. Can I transition some of the info, or backages to unused space on a more vacant drive.
With the ridiculously huge size of your drive, why did you allocate such a ridiculously small space to /boot in the first place? ;)

323 **MB**?? C'mon ! Give it at the least 2 GB, or may I recommend 5-8 GB to be free from this kind of trouble for eternity. :D

Anyway -
```
alrick@Home:~$ dpkg -l | grep linux-image
[COLOR="#FF0000"]ii  linux-image-3.2.0-23-generic                                3.2.0-23.36                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-24-generic                                3.2.0-24.39                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-25-generic                                3.2.0-25.40                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-26-generic                                3.2.0-26.41                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-27-generic                                3.2.0-27.43                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-29-generic                                3.2.0-29.46                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-30-generic                                3.2.0-30.48                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic                                3.2.0-31.50                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-32-generic                                3.2.0-32.51                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-33-generic                                3.2.0-33.52                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-34-generic [/COLOR]                               3.2.0-34.53                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-49-generic                                3.2.0-49.75                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-50-generic                                3.2.0-50.76                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic                                3.2.0-52.78                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP

```

The highlighted in RED are all much older kernels which I don't think you are using anymore. Make sure you are not running one of them -
```
uname -mr
```
..should return "linux-image-3.2.0-50-generic" or "linux-image-3.2.0-52-generic". If yes, try this-
```
sudo apt-get purge linux-image-3.2.0-23-generic
```
Does it successfully get removed? If yes, remove a couple more (preferably all from **linux-image-3.2.0-24-generic** to  **linux-image-3.2.0-34-generic**).

If having error, just browse to your /boot directory, and move (cut-paste) these -
```
initrd.img-3.2.0-24-generic
.....(all the way to)....
initrd.img-3.2.0-34-generic
```
from /boot to some other secure location. Once you have fixed your current problem, we can move them back and purge them one by one like gentlemen do.

---

### Post by Bashing-om on 2013-10-04
@ varunendra; Pleased that you dropped in ! .. Yeah, this one has had me tied in a knot for several days, Working through it and do not see an end in sight yet . Have yet to even get to the point of looking at multi-arch.

@blueboy1 ; As Varun advises this could get difficult with 100 % usage .. but lets give this a try and see if "dpkg" can work for us.
"uname" gives the kernel that you are presently running , DO NOT remove it as that may/probably complicate things even more. 
```

uname -r
sudo dpkg -P linux-image-3.2.0-{23,24,25,26,27,29,30,31,32,33,34}-generic

```
If that runs, next we want to remove the header files, look to see:
```

dpkg -l | grep linux-headers

```
[INDENT][INDENT]hope burns eternal
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-04
Hey Bashing-om, It appears that it runs fine see output. In the mean time I will be trying what varunendra suggest to delete some things.


```
alrick@Home:~$ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-23                                      3.2.0-23.36                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-23-generic                              3.2.0-23.36                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-24                                      3.2.0-24.39                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-24-generic                              3.2.0-24.39                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-25                                      3.2.0-25.40                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-25-generic                              3.2.0-25.40                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-26                                      3.2.0-26.41                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-26-generic                              3.2.0-26.41                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-27                                      3.2.0-27.43                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-27-generic                              3.2.0-27.43                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-29                                      3.2.0-29.46                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic                              3.2.0-29.46                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-30                                      3.2.0-30.48                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-30-generic                              3.2.0-30.48                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-31                                      3.2.0-31.50                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic                              3.2.0-31.50                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-32                                      3.2.0-32.51                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic                              3.2.0-32.51                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-33                                      3.2.0-33.52                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic                              3.2.0-33.52                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-34                                      3.2.0-34.53                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic                              3.2.0-34.53                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-49                                      3.2.0-49.75                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic                              3.2.0-49.75                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-50                                      3.2.0-50.76                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-50-generic                              3.2.0-50.76                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52                                      3.2.0-52.78                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic                              3.2.0-52.78                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53                                      3.2.0-53.81                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic                              3.2.0-53.81                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.2.0.53.63                             Generic Linux kernel headers

```

---

### Post by Bashing-om on 2013-10-04
blueboy1; Outstanding !

Let's look:
```

dpkg -l | grep linux-image

```
--IF----- all that is left of the kernel images is the 40 serires, we are ready then to remove the header files; do:
```

sudo dpkg -P linux-headers-3.2.0-{23,24,25,26,27,29,30,31,32,33,34}
sudo dpkg -P linux-headers-3.2.0-{23,24,25,26,27,29,30,31,32,33,34}-generic

```
and now to see where we stand for final cleanup :
```

dpkg -l | grep linux-image
dpkg -l | grep linux-headers

```
when all done all remaining image and header versions must must match.

[INDENT][INDENT]good progress
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-04
Sorry guys, will return in 24hrs. Thanks for all you do will continue tomorrow.

---

### Post by blueboy1 on 2013-10-05
Look who is back, hey guys. Here are the output for the codes:

```
alrick@Home:~$ dpkg -l | grep linux-image
ii  linux-image-3.2.0-49-generic                                3.2.0-49.75                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-50-generic                                3.2.0-50.76                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic                                3.2.0-52.78                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP

```

```
alrick@Home:~$ sudo dpkg -P linux-headers-3.2.0-{23,24,25,26,27,29,30,31,32,33,34}
[sudo] password for alrick: 
Sorry, try again.
[sudo] password for alrick: 
dpkg: dependency problems prevent removal of linux-headers-3.2.0-23:
 linux-headers-3.2.0-23-generic depends on linux-headers-3.2.0-23.
dpkg: error processing linux-headers-3.2.0-23 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-24:
 linux-headers-3.2.0-24-generic depends on linux-headers-3.2.0-24.
dpkg: error processing linux-headers-3.2.0-24 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-25:
 linux-headers-3.2.0-25-generic depends on linux-headers-3.2.0-25.
dpkg: error processing linux-headers-3.2.0-25 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-26:
 linux-headers-3.2.0-26-generic depends on linux-headers-3.2.0-26.
dpkg: error processing linux-headers-3.2.0-26 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-27:
 linux-headers-3.2.0-27-generic depends on linux-headers-3.2.0-27.
dpkg: error processing linux-headers-3.2.0-27 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-29:
 linux-headers-3.2.0-29-generic depends on linux-headers-3.2.0-29.
dpkg: error processing linux-headers-3.2.0-29 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-30:
 linux-headers-3.2.0-30-generic depends on linux-headers-3.2.0-30.
dpkg: error processing linux-headers-3.2.0-30 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-31:
 linux-headers-3.2.0-31-generic depends on linux-headers-3.2.0-31.
dpkg: error processing linux-headers-3.2.0-31 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-32:
 linux-headers-3.2.0-32-generic depends on linux-headers-3.2.0-32.
dpkg: error processing linux-headers-3.2.0-32 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-33:
 linux-headers-3.2.0-33-generic depends on linux-headers-3.2.0-33.
dpkg: error processing linux-headers-3.2.0-33 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.2.0-34:
 linux-headers-3.2.0-34-generic depends on linux-headers-3.2.0-34.
dpkg: error processing linux-headers-3.2.0-34 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.2.0-23
 linux-headers-3.2.0-24
 linux-headers-3.2.0-25
 linux-headers-3.2.0-26
 linux-headers-3.2.0-27
 linux-headers-3.2.0-29
 linux-headers-3.2.0-30
 linux-headers-3.2.0-31
 linux-headers-3.2.0-32
 linux-headers-3.2.0-33
 linux-headers-3.2.0-34

```

```
alrick@Home:~$ sudo dpkg -P linux-headers-3.2.0-{23,24,25,26,27,29,30,31,32,33,34}-generic
(Reading database ... 549395 files and directories currently installed.)
Removing linux-headers-3.2.0-23-generic ...
Removing linux-headers-3.2.0-24-generic ...
dpkg: warning: while removing linux-headers-3.2.0-24-generic, directory '/lib/modules/3.2.0-24-generic' not empty so not removed.
Removing linux-headers-3.2.0-25-generic ...
Removing linux-headers-3.2.0-26-generic ...
Removing linux-headers-3.2.0-27-generic ...
Removing linux-headers-3.2.0-29-generic ...
Removing linux-headers-3.2.0-30-generic ...
Removing linux-headers-3.2.0-31-generic ...
Removing linux-headers-3.2.0-32-generic ...
Removing linux-headers-3.2.0-33-generic ...
Removing linux-headers-3.2.0-34-generic ...

```

```
alrick@Home:~$ dpkg -l | grep linux-image
ii  linux-image-3.2.0-49-generic                                3.2.0-49.75                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-50-generic                                3.2.0-50.76                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic                                3.2.0-52.78                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP

```

```
alrick@Home:~$ dpkg -l | grep linux-headers
pi  linux-headers-3.2.0-23                                      3.2.0-23.36                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-24                                      3.2.0-24.39                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-25                                      3.2.0-25.40                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-26                                      3.2.0-26.41                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-27                                      3.2.0-27.43                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-29                                      3.2.0-29.46                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-30                                      3.2.0-30.48                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-31                                      3.2.0-31.50                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-32                                      3.2.0-32.51                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-33                                      3.2.0-33.52                             Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-34                                      3.2.0-34.53                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49                                      3.2.0-49.75                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic                              3.2.0-49.75                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-50                                      3.2.0-50.76                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-50-generic                              3.2.0-50.76                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52                                      3.2.0-52.78                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic                              3.2.0-52.78                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53                                      3.2.0-53.81                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic                              3.2.0-53.81                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.2.0.53.63                             Generic Linux kernel headers

```

---

### Post by Bashing-om on 2013-10-05
blueboy1; Looking good !
now do:
```

sudo dpkg -P linux-headers-3.2.0-{23,24,25,26,27,29,30,31,32,33,34}

```
and let's see what initramfs looks like:
```

sudo update-initramfs -u

```
The package system in general:
```

dpkg --audit
sudo apt-get check

```

[INDENT][INDENT]hope and fingers crossed
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-05
Here we go:

```
alrick@Home:~$ sudo dpkg -P linux-headers-3.2.0-{23,24,25,26,27,29,30,31,32,33,34}
[sudo] password for alrick: 
(Reading database ... 459886 files and directories currently installed.)
Removing linux-headers-3.2.0-23 ...
Removing linux-headers-3.2.0-24 ...
Removing linux-headers-3.2.0-25 ...
Removing linux-headers-3.2.0-26 ...
Removing linux-headers-3.2.0-27 ...
Removing linux-headers-3.2.0-29 ...
Removing linux-headers-3.2.0-30 ...
Removing linux-headers-3.2.0-31 ...
Removing linux-headers-3.2.0-32 ...
Removing linux-headers-3.2.0-33 ...
Removing linux-headers-3.2.0-34 ...

```

```
alrick@Home:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-52-generic

```

```
alrick@Home:~$ dpkg --audit

```

```
alrick@Home:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

### Post by Bashing-om on 2013-10-05
blueboy1; WELL WELL .. 

Everyone says they are happy happy.

Try wine and see if your apps run.

[INDENT][INDENT]It can happen
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-05
I think Wine was removed, wasn't it?

---

### Post by blueboy1 on 2013-10-05
Also till unable to upen Synoptic Package manager from the Dash.

---

### Post by Bashing-om on 2013-10-05
blueboy1; I believe you had said - how long ago ? that you had tried to remove it.

OK Let's see what We can do with completing that removal.
Once more so the output is handy,:
```

sudo apt-get update
sudo apt-get upgrade
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```

[INDENT][INDENT]take'n off again, I do hope
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-05
I did try but when I ran into that broken package everything went awry. So what I really wanted to do was to delete it and reinstall it before all the problem that you were so instrumental in helping me to resolve.   I still have a few unresolved issues. 
1. I wanted to reinstall Wine.
2. I wanted to increase the space on my boot drive to prevent any recurrance of what we just went through. 
3. I wanted to be able to open Synaptic Package System from my dash. 

Let me hope I am not taxing you too much.

Any way first things first, here is the output for the codes you gave. 

```
alrick@Home:~$ sudo apt-get update
[sudo] password for alrick: 
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://archive.ubuntu.com precise-backports Release.gpg
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://security.ubuntu.com precise-security Release   
Hit http://archive.ubuntu.com precise Release
Hit http://archive.ubuntu.com precise-backports Release               
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Get:2 http://archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise/universe Sources
Hit http://archive.ubuntu.com precise/main Sources
Hit http://archive.ubuntu.com precise/multiverse Sources
Hit http://archive.ubuntu.com precise/restricted Sources
Hit http://archive.ubuntu.com precise/main amd64 Packages
Hit http://archive.ubuntu.com precise/universe amd64 Packages
Hit http://archive.ubuntu.com precise/restricted amd64 Packages
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise/main i386 Packages
Hit http://archive.ubuntu.com precise/universe i386 Packages
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise/restricted i386 Packages
Hit http://archive.ubuntu.com precise/multiverse i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://archive.ubuntu.com precise-backports/main i386 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Get:3 http://archive.ubuntu.com precise-updates/universe amd64 Packages [217 kB]
Get:4 http://archive.ubuntu.com precise-updates/main amd64 Packages [694 kB]
Get:5 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.9 kB]
Get:6 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [11.5 kB]
Get:7 http://archive.ubuntu.com precise-updates/universe i386 Packages [221 kB]
Get:8 http://archive.ubuntu.com precise-updates/main i386 Packages [714 kB]
Get:9 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [14.0 kB]
Get:10 http://archive.ubuntu.com precise-updates/restricted i386 Packages [11.4 kB]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Fetched 1,947 kB in 2s (854 kB/s)                
Reading package lists... Done

```


```
alrick@Home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic
The following packages will be upgraded:
  apport apport-gtk python-apport python-problem-report
4 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 247 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise-updates/main python-problem-report all 2.0.1-0ubuntu17.5 [9,466 B]
Get:2 http://archive.ubuntu.com/ubuntu/ precise-updates/main python-apport all 2.0.1-0ubuntu17.5 [81.1 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise-updates/main apport all 2.0.1-0ubuntu17.5 [147 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ precise-updates/main apport-gtk all 2.0.1-0ubuntu17.5 [9,200 B]
Fetched 247 kB in 1s (160 kB/s)       
(Reading database ... 307229 files and directories currently installed.)
Preparing to replace python-problem-report 2.0.1-0ubuntu17.4 (using .../python-problem-report_2.0.1-0ubuntu17.5_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport 2.0.1-0ubuntu17.4 (using .../python-apport_2.0.1-0ubuntu17.5_all.deb) ...
Unpacking replacement python-apport ...
Preparing to replace apport 2.0.1-0ubuntu17.4 (using .../apport_2.0.1-0ubuntu17.5_all.deb) ...
apport stop/waiting
Unpacking replacement apport ...
Preparing to replace apport-gtk 2.0.1-0ubuntu17.4 (using .../apport-gtk_2.0.1-0ubuntu17.5_all.deb) ...
Unpacking replacement apport-gtk ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up python-problem-report (2.0.1-0ubuntu17.5) ...
Setting up python-apport (2.0.1-0ubuntu17.5) ...
Setting up apport (2.0.1-0ubuntu17.5) ...
apport start/running
Setting up apport-gtk (2.0.1-0ubuntu17.5) ...

```

```
alrick@Home:~$ cat -n /etc/apt/sources.list
     1	
     2	# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
     3	# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
     4	
     5	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     6	# newer versions of the distribution.
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	
    11	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12	## team. Also, please note that software in universe WILL NOT receive any
    13	## review or updates from the Ubuntu security team.
    14	
    15	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    16	## team, and may not be under a free licence. Please satisfy yourself as to 
    17	## your rights to use the software. Also, please note that software in 
    18	## multiverse WILL NOT receive any review or updates from the Ubuntu
    19	## security team.
    20	
    21	## N.B. software from this repository may not have been tested as
    22	## extensively as that contained in the main release, although it includes
    23	## newer versions of some applications which may provide useful features.
    24	## Also, please note that software in backports WILL NOT receive any review
    25	## or updates from the Ubuntu security team.
    26	
    27	
    28	## Uncomment the following two lines to add software from Canonical's
    29	## 'partner' repository.
    30	## This software is not part of Ubuntu, but is offered by Canonical and the
    31	## respective vendors as a service to Ubuntu users.
    32	# deb http://archive.canonical.com/ubuntu precise partner
    33	# deb-src http://archive.canonical.com/ubuntu precise partner
    34	
    35	## This software is not part of Ubuntu, but is offered by third-party
    36	## developers who want to ship their latest software.
    37	# deb http://extras.ubuntu.com/ubuntu precise main
    38	# deb-src http://extras.ubuntu.com/ubuntu precise main
    39	deb http://archive.ubuntu.com/ubuntu precise main universe restricted multiverse
    40	deb-src http://archive.ubuntu.com/ubuntu precise universe main multiverse restricted #Added by software-properties
    41	deb http://security.ubuntu.com/ubuntu/ precise-security universe main multiverse restricted
    42	deb http://archive.ubuntu.com/ubuntu precise-backports universe main multiverse restricted
    43	deb http://archive.ubuntu.com/ubuntu precise-updates universe main multiverse restricted

```

```
alrick@Home:~$ ls -la /etc/apt/sources.list.d
total 36
drwxr-xr-x 2 root root 4096 Sep 10 20:05 .
drwxr-xr-x 6 root root 4096 Oct  3 22:34 ..
-rw-r--r-- 1 root root  177 Oct  3 22:13 google-earth.list
-rw-r--r-- 1 root root  177 Oct  3 22:13 google-earth.list.save
-rw-r--r-- 1 root root  287 Oct  3 22:13 medibuntu.list
-rw-r--r-- 1 root root  287 Oct  3 22:13 medibuntu.list.save
-rw-r--r-- 1 root root  134 Oct  3 22:13 shnatsel-zram-precise.list
-rw-r--r-- 1 root root  134 Oct  3 22:13 shnatsel-zram-precise.list.save
-rw-r--r-- 1 root root    0 Sep 18 22:48 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root   69 Sep 18 22:48 ubuntu-wine-ppa-precise.list.save

```

---

### Post by Bashing-om on 2013-10-05
blueboy1; shesshh

I only see about 1/2 of what should be the sources.list file (???).
```

ls -la /etc/apt/sources.*

``` to see if there is a backup file, else will have to generate a new one.

and let's see how Wine was installed from that PPA:
```

cat /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list

```

And not to think of my efforts as a taxation, I am here to help, guide, assist and learn.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-05
```
alrick@Home:~$ ls -la /etc/apt/sources.*
-rw-r--r-- 1 root root 2313 Oct  3 22:13 /etc/apt/sources.list
-rw-r--r-- 1 root root 2224 Oct  3 22:13 /etc/apt/sources.list.save

/etc/apt/sources.list.d:
total 36
drwxr-xr-x 2 root root 4096 Sep 10 20:05 .
drwxr-xr-x 6 root root 4096 Oct  3 22:34 ..
-rw-r--r-- 1 root root  177 Oct  3 22:13 google-earth.list
-rw-r--r-- 1 root root  177 Oct  3 22:13 google-earth.list.save
-rw-r--r-- 1 root root  287 Oct  3 22:13 medibuntu.list
-rw-r--r-- 1 root root  287 Oct  3 22:13 medibuntu.list.save
-rw-r--r-- 1 root root  134 Oct  3 22:13 shnatsel-zram-precise.list
-rw-r--r-- 1 root root  134 Oct  3 22:13 shnatsel-zram-precise.list.save
-rw-r--r-- 1 root root    0 Sep 18 22:48 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root   69 Sep 18 22:48 ubuntu-wine-ppa-precise.list.save

```

```
alrick@Home:~$ cat /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list

```

---

### Post by Bashing-om on 2013-10-05
blueboy1; Yuk

Backup file is the same size for the sources.list file. I do have a solution.

I now see that the file for Wine's PPA contains nothing - file length 0 - . We can get around that, just a bit of work. -but maybe the backup file will help us:
```

cat /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save

```
For now lets get you a valid sources.list file.
Enable the 3rd party PPAs in Software Sources -> Other Software ,
and then: 
Go here to regenerate that sources.list file, following all the directions/prompts to do so - carefully !
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

[INDENT][INDENT]getting our foundation solid
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-05
From the Website for the source list generator provided should I be checking the boxes where the green check marks are indicated, I am not sure?

```
alrick@Home:~$ cat /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

```

---

### Post by Bashing-om on 2013-10-05
blueboy1; 
In regards to the repogen;
I suggest
DO NOT enable "proposed"
DO NOT enable "backports"
and do not enable ANY of of the 3rd party repos -> " should I be checking the boxes where the green check marks are indicated" == NO.

carry on.

[INDENT]we will see what results
[/INDENT]

---

### Post by blueboy1 on 2013-10-05
In that case there is nothing for me to do. What next must I do.

---

### Post by Bashing-om on 2013-10-05
blueboy1;
I fail to understand the question.
At the repogen site go ahead and check all other sources at the top of the page, and at the bottom of the page click on "regenerate".

That should make you a new sources.list file as we require it.
Future actions to restore Wine, as well as all else to your system require a valid up-to-date sources.list file.

When sources.list has been restored, post that file back here for us to verify it ... and then we can continue.

We will verify your system integrity 
expunge Wine from your system
(RE-)install Wine 
Take a look at what we can do to re-arrange partitions to enlarge the /boot partition.

Tall order, 
[INDENT][INDENT]will not conclude this night
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-05
blueboy1; Hey;

It has become difficult for me to maintain focus on my thinking processes. Have developed a head acke from eye strain. I am going to pack it in for the night.
And I will pick this up refreshed on my AM.

[INDENT][INDENT]A good night to you also
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-05
Here is what we have,

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main

---

### Post by Bashing-om on 2013-10-06
blueboy1; That makes no sense to me at all !
What in the world is not going on ????????
I should have hung around and seen that result last night.

I may have a solution .. pull the source's list form my install and copy it to yours ... however, I can not do that at this time. I must be away from the keyboard for a few hours. I will return.

[INDENT][INDENT]later. later
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-06
That is a hilarious response, if you did then you would not be able to sleep.  I was totally unsure. Any I do not know what sources list you are referring to on the website I need to check something but you have not told me what to check. I do not understand this statement "pull the source's list form my install and copy it to yours". please explain.

---

### Post by varunendra on 2013-10-06
> **blueboy1 said:**
> 
1. I wanted to reinstall Wine.
2. I wanted to increase the space on my boot drive to prevent any recurrance of what we just went through. 
3. I wanted to be able to open Synaptic Package System from my dash.

IMHO, all these questions should be asked in different threads. These are independent problems that are not necessarily related to each other. As such, are easier to answer in separate threads as well as more useful for future searchers who may have just one of these and are looking for help.

The third one *maybe* slightly related, but I think the original topic of the thread is solved already, since you are able to do the updates, install/uninstall normally with dpkg or apt-get. So what the title suggests - "Package System Broken" - is fixed.

Mixing more issues will only confuse the issue and thus will make a "now-useful" thread mostly useless therefore (anyone looking at it after some days will directly look at first and last pages --> will get confused with what's going on --> will move on).

As such, I believe it is best to just fix the sources.list file --> ensure apt-get and normal repositories are working --> start new threads for above topics and let us know.

> I do not understand this statement "pull the source's list form my install and copy it to yours". please explain
He meant to post his own "sources.list" file that you can download (or copy-paste) to replace your erroneous one.

For reference, here's mine (from Precise 64 bit):
```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise universe main restricted
deb-src http://archive.ubuntu.com/ubuntu precise universe main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main universe restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main universe restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main multiverse universe restricted
deb-src http://archive.ubuntu.com/ubuntu precise-backports main multiverse universe restricted

deb http://archive.ubuntu.com/ubuntu precise-security main universe restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main universe restricted
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
[COLOR="#FF0000"]deb http://www.remastersys.com/ubuntu precise main[/COLOR]
deb-src http://extras.ubuntu.com/ubuntu precise main
[COLOR="#FF0000"]## Depôt MultiSystem
deb http://liveusb.info/multisystem/depot all main[/COLOR]
deb http://archive.ubuntu.com/ubuntu precise-proposed universe main multiverse restricted
```

The lines highlighted in red are custom entries that may cause errors sometimes, so delete those lines if copy-pasting this one. There are some other repositories in above which, as per Bashing-om, should be disabled (by deleting the line or adding a '**#**' before the line).

I'll let Bashing-om deal with this file and related suggestions now. :)

---

### Post by blueboy1 on 2013-10-06
Varunendra, makes sense, I wll make different threads for those questions. 
I really wanted to know also, how do I get to Bashing-om source list. You showed me your source list but not how to get there.

---

### Post by varunendra on 2013-10-06
> **blueboy1 said:**
> I really wanted to know also, how do I get to Bashing-om source list. You showed me your source list but not how to get there.
You can just copy-paste the contents of my file into your original sources.list file (located in **/etc/apt** directory) then delete the lines highlighted in red.

However, taking a second look at **post #102**, it seems you already had all the default (plus recommended) repositories enabled. It looked shorter because usually we have different lines for the "**multiverse**" repositories, while you had it in the same lines as for others -
> **blueboy1 said:**
> 
```
     2	# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
     3	# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
     4	
     5	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     6	# newer versions of the distribution.
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	
    11	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12	## team. Also, please note that software in universe WILL NOT receive any
    13	## review or updates from the Ubuntu security team.
    14	
    15	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    16	## team, and may not be under a free licence. Please satisfy yourself as to 
    17	## your rights to use the software. Also, please note that software in 
    18	## multiverse WILL NOT receive any review or updates from the Ubuntu
    19	## security team.
    20	
    21	## N.B. software from this repository may not have been tested as
    22	## extensively as that contained in the main release, although it includes
    23	## newer versions of some applications which may provide useful features.
    24	## Also, please note that software in backports WILL NOT receive any review
    25	## or updates from the Ubuntu security team.
    26	
    27	
    28	## Uncomment the following two lines to add software from Canonical's
    29	## 'partner' repository.
    30	## This software is not part of Ubuntu, but is offered by Canonical and the
    31	## respective vendors as a service to Ubuntu users.
    32	# deb http://archive.canonical.com/ubuntu precise partner
    33	# deb-src http://archive.canonical.com/ubuntu precise partner
    34	
    35	## This software is not part of Ubuntu, but is offered by third-party
    36	## developers who want to ship their latest software.
    37	# deb http://extras.ubuntu.com/ubuntu precise main
    38	# deb-src http://extras.ubuntu.com/ubuntu precise main
    39	deb http://archive.ubuntu.com/ubuntu **precise** main universe restricted **multiverse**
    40	**[COLOR="#006400"]deb-src[/COLOR]** http://archive.ubuntu.com/ubuntu **precise** universe main multiverse restricted #Added by software-properties
    41	deb http://security.ubuntu.com/ubuntu/ **precise-security** universe main **[COLOR="#FF0000"]multiverse[/COLOR]** restricted
    42	deb http://archive.ubuntu.com/ubuntu **precise-backports** universe main **[COLOR="#FF0000"]multiverse[/COLOR]** restricted
    43	deb http://archive.ubuntu.com/ubuntu **precise-updates** universe main **[COLOR="#FF0000"]multiverse[/COLOR]** restricted

```
..plus you don't have the "source-code" (deb-src) repositories enabled for any category except for default one, which is perfectly okay. Adding sources for those additional repositories would add another 3 lines in it (or 6, if we used different lines for multiverse ;)). These and other possible changes cab be done any time via "Software Settings" box (press "Alt-F2" > type "software-properties-gtk" > press "Enter").

The unusual placement of these lines is probably because you might have tried to disable/re-enable all the repositories in one go. I'm not sure, but whatever be the reason, the above file is technically correct and shouldn't cause any issues (and you being able to successfully update the system is a proof of it).

So if you can just check again if your sources.list file is still same or not -
```
cat /etc/apt/sources.list
```
If it appears different than above, post back and we may give you an attachment file and procedure of how and where to copy it, backing up your original one.

But if it is same as the one quoted above from post #102, then it's perfectly okay and nothing more is needed to be done. The additional repositories, and/or the sources should be enabled only when required.

**EDIT:**
Just noticed you already marked the thread as [SOLVED], I appreciate and thank you for that. Hope Bashing-om would be pleased too. :)
When you start new threads, please post links to them here so we can follow.
Similarly, you may also post a link to this thread, preferably this very page, as context/reference in those threads. I believe the rest of your problems should get fixed quickly.

---

### Post by blueboy1 on 2013-10-06
Ok, here is the source list.

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu precise main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu precise universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ precise-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu precise-backports universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu precise-updates universe main multiverse restricted

```

---

### Post by varunendra on 2013-10-06
Looks rock-solid to me. Just to be extra sure, please do -
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Watch out for errors, and give us the good news that there were none !

---

### Post by blueboy1 on 2013-10-06
Here is the output for the codes. I think there were errors.

```
alrick@Home:~$ sudo apt-get update
[sudo] password for alrick: 
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://archive.ubuntu.com precise-backports Release.gpg
Hit http://archive.ubuntu.com precise-updates Release.gpg
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://archive.ubuntu.com precise Release
Hit http://archive.ubuntu.com precise-backports Release
Hit http://archive.ubuntu.com precise-updates Release                 
Hit http://security.ubuntu.com precise-security Release
Hit http://archive.ubuntu.com precise/universe Sources
Hit http://archive.ubuntu.com precise/main Sources
Hit http://archive.ubuntu.com precise/multiverse Sources
Hit http://archive.ubuntu.com precise/restricted Sources
Hit http://archive.ubuntu.com precise/main amd64 Packages
Hit http://archive.ubuntu.com precise/universe amd64 Packages
Hit http://archive.ubuntu.com precise/restricted amd64 Packages
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise/main i386 Packages
Hit http://archive.ubuntu.com precise/universe i386 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://archive.ubuntu.com precise/restricted i386 Packages
Hit http://archive.ubuntu.com precise/multiverse i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://archive.ubuntu.com precise-backports/main i386 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://archive.ubuntu.com precise-updates/main i386 Packages
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Reading package lists... Done

```

```
alrick@Home:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.2.0-54 linux-headers-3.2.0-54-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.7 MB of archives.
After this operation, 67.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main linux-headers-3.2.0-54 all 3.2.0-54.82 [11.7 MB]
Get:2 http://security.ubuntu.com/ubuntu/ precise-security/main linux-headers-3.2.0-54-generic amd64 3.2.0-54.82 [981 kB]
Get:3 http://security.ubuntu.com/ubuntu/ precise-security/main linux-headers-generic amd64 3.2.0.54.64 [2,260 B]
Fetched 12.7 MB in 3s (3,228 kB/s)                
Selecting previously unselected package linux-headers-3.2.0-54.
(Reading database ... 307233 files and directories currently installed.)
Unpacking linux-headers-3.2.0-54 (from .../linux-headers-3.2.0-54_3.2.0-54.82_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-54-generic.
Unpacking linux-headers-3.2.0-54-generic (from .../linux-headers-3.2.0-54-generic_3.2.0-54.82_amd64.deb) ...
Preparing to replace linux-headers-generic 3.2.0.53.63 (using .../linux-headers-generic_3.2.0.54.64_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-headers-3.2.0-54 (3.2.0-54.82) ...
Setting up linux-headers-3.2.0-54-generic (3.2.0-54.82) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
Setting up linux-headers-generic (3.2.0.54.64) ...

```

---

### Post by Bashing-om on 2013-10-06
@ varunendra; && blueboy1;

Fully agree with closing this thread .. and once more my regrets in not following standard operating procedures. -one problem one thread.
Varun, I do appreciate your -and the other moderators - oversight .

blueboy1 I am very pleased to be at this point and I will look for the new threads and take up those other smaller issues there.

[INDENT][INDENT]I love the feel of a closed thread
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-06
Ok, you guys have been amazing, thanks a ton.  I will follow up with the other concerns on different threads. I will consider this closed.

---

