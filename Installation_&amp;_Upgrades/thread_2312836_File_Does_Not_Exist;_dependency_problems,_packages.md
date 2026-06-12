---
title: "File Does Not Exist; dependency problems, packages not configured, files missing"
date: 2016-02-07
forum: Installation &amp; Upgrades
---

### Post by ectomonomorphosis on 2016-02-07
**To start off, here's the Ubuntu Support terminal out:**

```
 teo@Blubot-L2:~$ ubuntu-support-statusSupport status summary of 'Blubot-L2':




You have 3608 packages (100.0%) that can not/no-longer be downloaded
You have 0 packages (0.0%) that are unsupported


Run with --show-unsupported, --show-supported or --show-all to see more details
teo@Blubot-L2:~$ cat /etc/dpkg/dpkg.cfg.d/multiarch
cat: /etc/dpkg/dpkg.cfg.d/multiarch: No such file or directory
teo@Blubot-L2:~$ dpkg --print-foreign-architectures
i386
teo@Blubot-L2:~$ sudo grep -R proxy /etc/apt/*
teo@Blubot-L2:~$ grep proxy  /etc/environment
teo@Blubot-L2:~$ echo $http_proxy


teo@Blubot-L2:~$ echo $ftp_proxy


teo@Blubot-L2:~$ grep proxy /etc/bash.bashrc
teo@Blubot-L2:~$ grep proxy ~/.bashrc
teo@Blubot-L2:~$ cat /etc/apt/apt.conf
cat: /etc/apt/apt.conf: No such file or directory
teo@Blubot-L2:~$ sudo fuser -vvv /var/lib/dpkg/lock
teo@Blubot-L2:~$ sudo fuser -vvv /var/cache/apt/archives/lock
teo@Blubot-L2:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
teo@Blubot-L2:~$ uname -a
Linux Blubot-L2 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
teo@Blubot-L2:~$ sudo rm /var/lib/apt/lists/lock 
rm: cannot remove '/var/lib/apt/lists/lock': No such file or directory
teo@Blubot-L2:~$ sudo rm  /var/cache/apt/archives/lock
teo@Blubot-L2:~$ sudo rm /var/lib/dpkg/lock
teo@Blubot-L2:~$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
teo@Blubot-L2:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
teo@Blubot-L2:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status  ||  sudo cp /var/backups/apt.extended_states.0 /var/lib/dpkg/status
teo@Blubot-L2:~$ sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-bad
teo@Blubot-L2:~$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
teo@Blubot-L2:~$ sudo rm -rf /var/lib/dpkg/updates/*
teo@Blubot-L2:~$ sudo rm -rf /var/lib/apt/lists
teo@Blubot-L2:~$ sudo rm /var/cache/apt/*.bin
teo@Blubot-L2:~$ sudo mkdir /var/lib/apt/lists
teo@Blubot-L2:~$ sudo mkdir /var/lib/apt/lists/partial
teo@Blubot-L2:~$ LANG=C;sudo apt-get clean
teo@Blubot-L2:~$ LANG=C;sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
teo@Blubot-L2:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libgtk2.0-cil:
 libgtk2.0-cil depends on libglib2.0-cil (= 2.12.10-5); however:
  Package libglib2.0-cil is not installed.


dpkg: error processing package libgtk2.0-cil (--configure):
 dependency problems - leaving unconfigured
Setting up libnunit2.6-cil (2.6.0.12051+dfsg-2) ...
* Installing 5 assemblies from libnunit2.6-cil into Mono


Unhandled Exception:
System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Security, Version=4.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Security, Version=4.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'
  at Mono.Tools.Driver.LoadConfig (Boolean quiet) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Security, Version=4.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Security, Version=4.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'
  at Mono.Tools.Driver.LoadConfig (Boolean quiet) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
E: installing Assembly /usr/lib/cli/nunit.core-2.6/nunit.core.dll failed
E: Installation of libnunit2.6-cil with /usr/share/cli-common/runtimes.d/mono failed
dpkg: error processing package libnunit2.6-cil (--configure):
 subprocess installed post-installation script returned error exit status 29
dpkg: dependency problems prevent configuration of libnunit-cil-dev:
 libnunit-cil-dev depends on libnunit2.6-cil (= 2.6.0.12051+dfsg-2); however:
  Package libnunit2.6-cil is not configured yet.


dpkg: error processing package libnunit-cil-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-cil-dev:
 libmono-cil-dev depends on libnunit-cil-dev (>= 2.4); however:
  Package libnunit-cil-dev is not configured yet.


dpkg: error processing package libmono-cil-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mono-devel:
 mono-devel depends on libmono-cil-dev (= 3.2.8+dfsg-4ubuntu1.1); however:
  Package libmono-cil-dev is not configured yet.


dpkg: error processing package mono-devel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mono-complete:
 mono-complete depends on mono-devel (= 3.2.8+dfsg-4ubuntu1.1); however:
  Package mono-devel is not configured yet.
 mono-complete depends on libmono-cil-dev (= 3.2.8+dfsg-4ubuntu1.1); however:
  Package libmono-cil-dev is not configured yet.


dpkg: error processing package mono-complete (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mono-xsp4-base:
 mono-xsp4-base depends on mono-devel; however:
  Package mono-devel is not configured yet.


dpkg: error processing package mono-xsp4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mono-xsp4:
 mono-xsp4 depends on mono-xsp4-base (= 3.0.11-1); however:
  Package mono-xsp4-base is not configured yet.


dpkg: error processing package mono-xsp4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of monodoc-http:
 monodoc-http depends on mono-xsp4 | mono-apache-server4 | mono-fastcgi-server4; however:
  Package mono-xsp4 is not configured yet.
  Package mono-apache-server4 is not installed.
  Package mono-fastcgi-server4 is not installed.


dpkg: error processing package monodoc-http (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of monodoc-manual:
 monodoc-manual depends on monodoc-browser | monodoc-http | monodoc-viewer; however:
  Package monodoc-browser is not installed.
  Package monodoc-http is not configured yet.
  Package monodoc-viewer is not installed.
  Package monodoc-http which provides monodoc-viewer is not configured yet.


dpkg: error processing package monodoc-manual (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgtk2.0-cil
 libnunit2.6-cil
 libnunit-cil-dev
 libmono-cil-dev
 mono-devel
 mono-complete
 mono-xsp4-base
 mono-xsp4
 monodoc-http
 monodoc-manual
teo@Blubot-L2:~$ sudo dpkg --clear-avail
teo@Blubot-L2:~$ LANG=C;sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  libglade2.0-cil libglib2.0-cil libgtk2.0-cil
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 2946 kB disk space will be freed.
Do you want to continue? [Y/n] Y
Abort.
teo@Blubot-L2:~$ LANG=C;sudo apt-get --fix-missing install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
teo@Blubot-L2:~$ LANG=C;sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
teo@Blubot-L2:~$ LANG=C;sudo apt-get --fix-missing update -o APT::Cache-Limit=100000000
Get:1 http://security.ubuntu.com trusty-security InRelease [64.4 kB]
Ign http://archive.ubuntu.com trusty InRelease                                 
Get:2 http://archive.ubuntu.com trusty-updates InRelease [64.4 kB]             
Ign http://archive.canonical.com trusty InRelease                              
Get:3 http://security.ubuntu.com trusty-security/main amd64 Packages [416 kB]  
Get:4 http://archive.ubuntu.com trusty Release.gpg [933 B]                     
Get:5 http://archive.canonical.com trusty Release.gpg [933 B]                  
Get:6 http://archive.ubuntu.com trusty-updates/main amd64 Packages [695 kB]
Get:7 http://security.ubuntu.com trusty-security/universe amd64 Packages [123 kB]
Get:8 http://archive.canonical.com trusty Release [9359 B]                     
Get:9 http://security.ubuntu.com trusty-security/main i386 Packages [389 kB]   
Get:10 http://security.ubuntu.com trusty-security/universe i386 Packages [123 kB]
Get:11 http://archive.canonical.com trusty/partner Sources [10.1 kB]           
Get:12 http://security.ubuntu.com trusty-security/main Translation-en [228 kB] 
Get:13 http://archive.canonical.com trusty/partner amd64 Packages [5608 B]     
Get:14 http://security.ubuntu.com trusty-security/universe Translation-en [72.1 kB]
Get:15 http://archive.canonical.com trusty/partner i386 Packages [6305 B]      
Get:16 http://archive.canonical.com trusty/partner Translation-en [4588 B]     
Get:17 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [336 kB]
Get:18 http://archive.ubuntu.com trusty-updates/main i386 Packages [670 kB]
Get:19 http://archive.ubuntu.com trusty-updates/universe i386 Packages [337 kB]
Get:20 http://archive.ubuntu.com trusty-updates/main Translation-en [352 kB]
Get:21 http://archive.ubuntu.com trusty-updates/universe Translation-en [179 kB]
Get:22 http://archive.ubuntu.com trusty Release [58.5 kB]       
Get:23 http://archive.ubuntu.com trusty/main amd64 Packages [1350 kB]
Get:24 http://archive.ubuntu.com trusty/universe amd64 Packages [5859 kB]
Get:25 http://archive.ubuntu.com trusty/main i386 Packages [1348 kB]
Get:26 http://archive.ubuntu.com trusty/universe i386 Packages [5866 kB]
Get:27 http://archive.ubuntu.com trusty/main Translation-en [762 kB]
Get:28 http://archive.ubuntu.com trusty/universe Translation-en [4089 kB]
Fetched 23.4 MB in 14s (1583 kB/s)                                             
Reading package lists... Done
teo@Blubot-L2:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=100000000 && sudo apt-get dist-upgrade
Hit http://security.ubuntu.com trusty-security InRelease
Ign http://archive.ubuntu.com trusty InRelease                                
Hit http://archive.ubuntu.com trusty-updates InRelease                         
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://archive.ubuntu.com trusty Release.gpg                               
Ign http://archive.canonical.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages  
Hit http://security.ubuntu.com trusty-security/main i386 Packages 
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages           
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages    
Hit http://security.ubuntu.com trusty-security/main Translation-en 
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://archive.ubuntu.com trusty-updates/main Translation-en   
Hit http://archive.canonical.com trusty Release                    
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://archive.ubuntu.com trusty Release 
Hit http://archive.canonical.com trusty/partner Sources             
Hit http://archive.ubuntu.com trusty/main amd64 Packages           
Hit http://archive.ubuntu.com trusty/universe amd64 Packages       
Hit http://archive.canonical.com trusty/partner amd64 Packages     
Hit http://archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en                 
Hit http://archive.canonical.com trusty/partner i386 Packages            
Hit http://archive.ubuntu.com trusty/universe Translation-en             
Hit http://archive.canonical.com trusty/partner Translation-en           
Reading package lists... Done                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
teo@Blubot-L2:~$ find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;


/etc/apt/sources.list.d/mc3man-trusty-media-trusty.list


     1    # deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
     2    # deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main


/etc/apt/sources.list.d/yorba-daily-builds-trusty.list


     1    # deb http://ppa.launchpad.net/yorba/daily-builds/ubuntu trusty main
     2    # deb-src http://ppa.launchpad.net/yorba/daily-builds/ubuntu trusty main


/etc/apt/sources.list.d/kxstudio-debian-ubuntus-trusty.list


     1    # deb http://ppa.launchpad.net/kxstudio-debian/ubuntus/ubuntu trusty main
     2    # deb-src http://ppa.launchpad.net/kxstudio-debian/ubuntus/ubuntu trusty main
     3    # deb-src http://ppa.launchpad.net/kxstudio-debian/ubuntus/ubuntu trusty main


/etc/apt/sources.list.d/relan-exfat-trusty.list


     1    # deb http://ppa.launchpad.net/relan/exfat/ubuntu trusty main
     2    # deb-src http://ppa.launchpad.net/relan/exfat/ubuntu trusty main


/etc/apt/sources.list.d/mc3man-gstffmpeg-keep-trusty.list


     1    # deb http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu trusty main
     2    # deb-src http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu trusty main


/etc/apt/sources.list.d/abiword-stable.list


     1    # deb http://ppa.launchpad.net/abiword-stable/ppa/ubuntu trusty main


/etc/apt/sources.list.d/directhex-monoxide-trusty.list


     1    # deb http://ppa.launchpad.net/directhex/monoxide/ubuntu trusty main
     2    # deb-src http://ppa.launchpad.net/directhex/monoxide/ubuntu trusty main


/etc/apt/sources.list.d/tombeckmann-ppa-trusty.list


     1    # deb http://ppa.launchpad.net/tombeckmann/ppa/ubuntu trusty main
     2    # deb-src http://ppa.launchpad.net/tombeckmann/ppa/ubuntu trusty main
     3    # deb-src http://ppa.launchpad.net/tombeckmann/ppa/ubuntu trusty main


/etc/apt/sources.list


     1    ## Note, this file is written by cloud-init on first boot of an instance
     2    ## modifications made here will not survive a re-bundle.
     3    ## if you wish to make changes you can:
     4    ## a.) add 'apt_preserve_sources_list: true' to /etc/cloud/cloud.cfg
     5    ##     or do the same in user-data
     6    ## b.) add sources in /etc/apt/sources.list.d
     7    ## c.) make changes to template file /etc/cloud/templates/sources.list.tmpl
     8    #
     9    
    10    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    11    # newer versions of the distribution.
    12    deb http://archive.ubuntu.com/ubuntu trusty main
    13    
    14    ## Major bug fix updates produced after the final release of the
    15    ## distribution.
    16    deb http://archive.ubuntu.com/ubuntu trusty-updates main
    17    
    18    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    19    ## team. Also, please note that software in universe WILL NOT receive any
    20    ## review or updates from the Ubuntu security team.
    21    deb http://archive.ubuntu.com/ubuntu trusty universe
    22    deb http://archive.ubuntu.com/ubuntu trusty-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    
    30    ## Uncomment the following two lines to add software from the 'backports'
    31    ## repository.
    32    ## N.B. software from this repository may not have been tested as
    33    ## extensively as that contained in the main release, although it includes
    34    ## newer versions of some applications which may provide useful features.
    35    ## Also, please note that software in backports WILL NOT receive any review
    36    ## or updates from the Ubuntu security team.
    37    
    38    ## Uncomment the following two lines to add software from Canonical's
    39    ## 'partner' repository.
    40    ## This software is not part of Ubuntu, but is offered by Canonical and the
    41    ## respective vendors as a service to Ubuntu users.
    42    deb http://archive.canonical.com/ubuntu trusty partner
    43    deb-src http://archive.canonical.com/ubuntu trusty partner
    44    
    45    deb http://security.ubuntu.com/ubuntu trusty-security main
    46    deb http://security.ubuntu.com/ubuntu trusty-security universe
    47    # deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    48    # deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
teo@Blubot-L2:~$ sudo dpkg –audit
dpkg: error: need an action option


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !

```

Separate terminal out for remove:

```
 The following packages will be REMOVED:
  libglade2.0-cil libglib2.0-cil libgtk2.0-cil libjpeg-progs
  libjpeg-turbo-progs
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 3,159 kB disk space will be freed.
Do you want to continue? [Y/n] Y
dpkg: warning: files list file for package 'libmono-security4.0-cil' missing; assuming package has no files currently installed
(Reading database ... 376000 files and directories currently installed.)
Removing libglade2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
dpkg: error processing package libglade2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libgtk2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: error processing package libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libglib2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac
dpkg: error processing package libglib2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libjpeg-progs (8c-2ubuntu8) ...
Removing libjpeg-turbo-progs (1.3.0-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 libglade2.0-cil
 libgtk2.0-cil
 libglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

apt-get update reveals files missing:

```
 teo@Blubot-L2:~$ sudo apt-get update
[sudo] password for teo: 
Hit http://security.ubuntu.com trusty-security InRelease
Ign http://archive.canonical.com trusty InRelease                              
Ign http://archive.ubuntu.com trusty InRelease                         
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://archive.canonical.com trusty Release.gpg
Get:1 http://archive.ubuntu.com trusty-updates InRelease [64.4 kB]
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://archive.canonical.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.ubuntu.com trusty Release.gpg                          
Hit http://archive.canonical.com trusty/partner amd64 Packages            
Get:2 http://archive.ubuntu.com trusty-updates/main amd64 Packages [695 kB]
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.canonical.com trusty/partner Translation-en             
Get:3 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [336 kB]
Get:4 http://archive.ubuntu.com trusty-updates/main i386 Packages [670 kB]
Get:5 http://archive.ubuntu.com trusty-updates/universe i386 Packages [337 kB]
Get:6 http://archive.ubuntu.com trusty-updates/main Translation-en [352 kB]
Get:7 http://archive.ubuntu.com trusty-updates/universe Translation-en [179 kB]
Hit http://archive.ubuntu.com trusty Release                   
Hit http://archive.ubuntu.com trusty/main amd64 Packages
Hit http://archive.ubuntu.com trusty/universe amd64 Packages               
Hit http://archive.ubuntu.com trusty/main i386 Packages                    
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 2,633 kB in 7s (350 kB/s)                                              
Reading package lists... Done
teo@Blubot-L2:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libglade2.0-cil libglib2.0-cil libgtk2.0-cil
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 2,946 kB disk space will be freed.
Do you want to continue? [Y/n] Y
dpkg: warning: files list file for package 'libmono-security4.0-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnome-keyring-common' missing; assuming package has no files currently installed
(Reading database ... 375974 files and directories currently installed.)
Removing libglade2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
dpkg: error processing package libglade2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libgtk2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: error processing package libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libglib2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac
dpkg: error processing package libglib2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libglade2.0-cil
 libgtk2.0-cil
 libglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

dpkg --configure --pending reveals dependency issues;

```
 teo@Blubot-L2:~$ sudo dpkg --configure --pending
Setting up libnunit2.6-cil (2.6.0.12051+dfsg-2) ...
* Installing 5 assemblies from libnunit2.6-cil into Mono


Unhandled Exception:
System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Security, Version=4.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Security, Version=4.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'
  at Mono.Tools.Driver.LoadConfig (Boolean quiet) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Security, Version=4.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Security, Version=4.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'
  at Mono.Tools.Driver.LoadConfig (Boolean quiet) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
E: installing Assembly /usr/lib/cli/nunit.core-2.6/nunit.core.dll failed
E: Installation of libnunit2.6-cil with /usr/share/cli-common/runtimes.d/mono failed
dpkg: error processing package libnunit2.6-cil (--configure):
 subprocess installed post-installation script returned error exit status 29
dpkg: dependency problems prevent configuration of libnunit-cil-dev:
 libnunit-cil-dev depends on libnunit2.6-cil (= 2.6.0.12051+dfsg-2); however:
  Package libnunit2.6-cil is not configured yet.


dpkg: error processing package libnunit-cil-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-cil-dev:
 libmono-cil-dev depends on libnunit-cil-dev (>= 2.4); however:
  Package libnunit-cil-dev is not configured yet.


dpkg: error processing package libmono-cil-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mono-devel:
 mono-devel depends on libmono-cil-dev (= 3.2.8+dfsg-4ubuntu1.1); however:
  Package libmono-cil-dev is not configured yet.


dpkg: error processing package mono-devel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mono-complete:
 mono-complete depends on mono-devel (= 3.2.8+dfsg-4ubuntu1.1); however:
  Package mono-devel is not configured yet.
 mono-complete depends on libmono-cil-dev (= 3.2.8+dfsg-4ubuntu1.1); however:
  Package libmono-cil-dev is not configured yet.


dpkg: error processing package mono-complete (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mono-xsp4-base:
 mono-xsp4-base depends on mono-devel; however:
  Package mono-devel is not configured yet.


dpkg: error processing package mono-xsp4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mono-xsp4:
 mono-xsp4 depends on mono-xsp4-base (= 3.0.11-1); however:
  Package mono-xsp4-base is not configured yet.


dpkg: error processing package mono-xsp4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of monodoc-http:
 monodoc-http depends on mono-xsp4 | mono-apache-server4 | mono-fastcgi-server4; however:
  Package mono-xsp4 is not configured yet.
  Package mono-apache-server4 is not installed.
  Package mono-fastcgi-server4 is not installed.


dpkg: error processing package monodoc-http (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of monodoc-manual:
 monodoc-manual depends on monodoc-browser | monodoc-http | monodoc-viewer; however:
  Package monodoc-browser is not installed.
  Package monodoc-http is not configured yet.
  Package monodoc-viewer is not installed.
  Package monodoc-http which provides monodoc-viewer is not configured yet.


dpkg: error processing package monodoc-manual (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libnunit2.6-cil
 libnunit-cil-dev
 libmono-cil-dev
 mono-devel
 mono-complete
 mono-xsp4-base
 mono-xsp4
 monodoc-http
 monodoc-manual
```

Tried to force dpkg:

```
 teo@Blubot-L2:~$ sudo dpkg -P --force-all libglade2.0-cil libgtk2.0-cil libglib2.0-cil
dpkg: warning: files list file for package 'libmono-security4.0-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnome-keyring-common' missing; assuming package has no files currently installed
(Reading database ... 375974 files and directories currently installed.)
Removing libglade2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
dpkg: error processing package libglade2.0-cil (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing libgtk2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: error processing package libgtk2.0-cil (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing libglib2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac
dpkg: error processing package libglib2.0-cil (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libglade2.0-cil
 libgtk2.0-cil
 libglib2.0-cil
```

Then tried moving and force dpkg, because I don't know what I'm doing:

 ```
teo@Blubot-L2:~$ sudo mv /var/lib/dpkg/info/libgtk2.0-cil.postrm /var/lib/dpkg/info/libgtk2.0-cil.postrm.tmp
teo@Blubot-L2:~$ sudo dpkg -P --force-all libgtk2.0-cil
dpkg: warning: files list file for package 'libmono-security4.0-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnome-keyring-common' missing; assuming package has no files currently installed
(Reading database ... 375974 files and directories currently installed.)
Removing libgtk2.0-cil (2.12.10-5) ..
```

This problem prohibits my updating, and has been persisting for a few days.

---

### Post by Bashing-om on 2016-02-07
ectomonomorphosis; Well ... hummm ...

> 
dpkg: dependency problems prevent configuration of libgtk2.0-cil:
 libgtk2.0-cil depends on libglib2.0-cil (= 2.12.10-5); however:
  Package libglib2.0-cil is not installed.

-bk-


As only one instance .

Got this one .. as a point of reference to the others ..
what returns:
```

apt-cache policy libglade2.0-cil libglib2.0-cil libgtk2.0-cil

```
As these files are not on my 14.04 system ->
Unsupported PPAs ?

[INDENT][INDENT]if it ain't ubuntu
[INDENT][INDENT][INDENT]can not blame ubuntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ectomonomorphosis on 2016-02-07
I ran:

```
teo@Blubot-L2:~$ apt-cache policy libglade2.0-cil libglib2.0-cil libgtk2.0-cil
libglade2.0-cil:
  Installed: 2.12.10-5
  Candidate: 2.12.10-5
  Version table:
 *** 2.12.10-5 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
libglib2.0-cil:
  Installed: 2.12.10-5
  Candidate: 2.12.10-5
  Version table:
 *** 2.12.10-5 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
libgtk2.0-cil:
  Installed: 2.12.10-5
  Candidate: 2.12.10-5
  Version table:
 *** 2.12.10-5 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status


```

Then:

```
teo@Blubot-L2:~$ sudo apt-get remove libglade2.0-cil libglib2.0-cil libgtk2.0-cil
[sudo] password for teo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libglade2.0-cil libglib2.0-cil libgtk2.0-cil
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 2,946 kB disk space will be freed.
Do you want to continue? [Y/n] Y
dpkg: warning: files list file for package 'libmono-security4.0-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnome-keyring-common' missing; assuming package has no files currently installed
(Reading database ... 375974 files and directories currently installed.)
Removing libglade2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
dpkg: error processing package libglade2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libgtk2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: error processing package libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libglib2.0-cil (2.12.10-5) ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac
dpkg: error processing package libglib2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libglade2.0-cil
 libgtk2.0-cil
 libglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Where can I go from here?

I see that my "Windows-infused" past has caught up with me here--irresponsible non-trustworthy downloading, and all. I'm learning.

---

### Post by tenmoi on 2016-02-08
How about 1) removing all the ppas with ppa-purge and then 2) reinstalling the three packages before you try to remove them again like this:
apt-get install  --reinstall libglade2.0-cil=2.12.10-5
Then
apt-get remove libglade2.0-cil

---

### Post by Bashing-om on 2016-02-08
@tenmoi; Great thought, appreciate the input .

ectomonomorphosis; Humm ...

That last blows my thought process of a PPA in this one instance at fault away. In this instance the packages are from our repo . ( tech me to jump to a early conclusion and not check further).

However, following this line of thought that PPAs are a factor, let's look at what you are fetching:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
verify they are valid, and go back to fighting with the package manager to get it in a happy state.

a lever and a fulcrum
[INDENT][INDENT][INDENT]to move the package manager
[/INDENT][/INDENT][/INDENT]

---

### Post by matt_symes on 2016-02-08
Hi

May i offer a some suggestions please.

@ectomonomorphosis

Firstly, please don't randomly copy commands from the Internet unless you know what they do.

Many commands are tailored for specific issues a user is having and may not be applicable to your issue.

You look at have run a whole bunch of commands in your first post that may have made the situation worse.

Please ask on the forums or in other support venues such as askubuntu or on IRC before running commands that you may not understand.

Anyway, my suggestion would be to try and install the single deb files themselves.

Copy and past these lines into the terminal.

```
cd && mkdir temp && cd $_
apt-get download libglade2.0-cil libglib2.0-cil libgtk2.0-cil

sudo dpkg -i ~/temp/libglib2.0-cil_2.12.10-5_amd64.deb
sudo dpkg -i ~/temp/libgtk2.0-cil_2.12.10-5_amd64.deb
sudo dpkg -i ~/temp/libglade2.0-cil_2.12.10-5_amd64.deb

sudo apt-get -f install
```

It will download the deb files into ~/temp and attempt to reinstall them for you. The ordering fo the dpkg commands is important to satisfy dependencies.

Please post back any errors. If you get errors then it'll show just how bad your package system is.

Kind regards

---

### Post by ectomonomorphosis on 2016-02-08
Thank you much, it worked, however my computer screen has been going black after the "Ubuntu Studio" spinning logo screen, with no assurance of ever flashing on. This has been happening for a day now, having begun prior to resolving this forum issue by entering mattsymes' terminal input via F1'ing at the load screen, preempting the video driver communication issue.(?)  

I ran failsafeX in the recovery menu and received:

X: cannot stat /etc/X11/X (No such file or directory), aborting

---

### Post by matt_symes on 2016-02-08
Hi

> **ectomonomorphosis said:**
> Thank you much, it worked, however my computer screen has been going black after the "Ubuntu Studio" spinning logo screen, with no assurance of ever flashing on. This has been happening for a day now, having begun prior to resolving this forum issue by entering mattsymes' terminal input via F1'ing at the load screen, preempting the video driver communication issue.(?)  

I ran failsafeX in the recovery menu and received:

X: cannot stat /etc/X11/X (No such file or directory), aborting

Please start a new thread with your new issue as it's not directly related to the package dependencies issue.

You can post a link to this thread in the new thread if you like and you can give the new thread a more appropriate title to your new problem. You'll get new eyes looking at it as well.

As this has fixed the package dependencies problem you had, please mark this thread as SOLVED using the thread tools menu located above post #1.

It'll help others looking for similar information.

Kind regards

---

### Post by vasa1 on 2016-02-08
> **matt_symes said:**
> ...
Many commands are tailored for specific issues ...
Hi Matt, I think the output provided by OP in the first post was based on the procedure specified here: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure).

---

### Post by matt_symes on 2016-02-08
Hi

> **vasa1 said:**
> Hi Matt, I think the output provided by OP in the first post was based on the procedure specified here: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure).

Thanks for posting this vasa. I had not come across that page.

I don't think that moving and deleting system files and directories should be on any Ubuntu wiki page without at least, and at minimum, an explanation of what they do and why, and for which error situations they are applicable to.

IMO, that's not the best wiki page Ubuntu has. 

I suspect you may be right in that may be where the OP got those commands from.

Kind regards

---

### Post by vasa1 on 2016-02-08
> **matt_symes said:**
> ...
IMO, that's not the best wiki page Ubuntu has. 
...
There were quite a few exchanges [here]("http://askubuntu.com/questions/725855/why-is-lang-csudo-apt-get-clean-etc-recommended") about the use of "LANG=C;" instead of just "LANG=C" in that same wiki page. People who tried to edit the wiki couldn't, perhaps because of security measures introduced after a bout of vandalism.

---

### Post by matt_symes on 2016-02-08
Hi

> **vasa1 said:**
> There were quite a few exchanges [here]("http://askubuntu.com/questions/725855/why-is-lang-csudo-apt-get-clean-etc-recommended") about the use of "LANG=C;" instead of just "LANG=C" in that same wiki page. People who tried to edit the wiki couldn't, perhaps because of security measures introduced after a bout of vandalism.

There are a number of issues with that page it seems.

Anyway, my only comment on the discussion on the askubuntu page would be to compare these:

```
EDITOR=vim sudo -E visudo
EDITOR=nano sudo -E visudo
```

```
EDITOR=vim; sudo -E visudo
EDITOR=nano; sudo -E visudo
```

Kind regards

---

### Post by vasa1 on 2016-02-09
> **matt_symes said:**
> ...
Anyway, my only comment on the discussion on the askubuntu page would be to compare these:

```
EDITOR=vim sudo -E visudo
EDITOR=nano sudo -E visudo
```

```
EDITOR=vim; sudo -E visudo
EDITOR=nano; sudo -E visudo
```

Kind regards
I'm too scared to try anything with *visudo*
but in simple English, isn't it this way ...?

running **LANG=C some_command** will set **LANG=C** for that command *only*
but
running **LANG=C; some_command** will set **LANG=C** not just for that command *but for subsequent commands until the terminal window is closed*?

---

### Post by matt_symes on 2016-02-09
Hi

> **vasa1 said:**
> I'm too scared to try anything with *visudo*
but in simple English, isn't it this way ...?

running **LANG=C some_command** will set **LANG=C** for that command *only*
but
running **LANG=C; some_command** will set **LANG=C** not just for that command *but for subsequent commands until the terminal window is closed*?

I'll post more later as i'm pretty busy at the moment, but if visudo worries you then compare these

```
TEST=hello; bash -c 'echo $TEST'
TEST=hello bash -c 'echo $TEST'
```

Kind regards

---

