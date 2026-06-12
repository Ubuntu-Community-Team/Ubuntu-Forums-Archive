---
title: "Ubuntu 14.04 Installation problem."
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by 8LfOM1R0 on 2014-09-11
I received an automatic prompt to upgrade to the new version and I proceeded.
At stage two of the installation 'setting new software channels' I received a pop-up stating the following:

"[B]Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.[/B]"

I closed the pop-up and the 'original state of the system was recovered'.

This has happened to me twice now. The first time I sent an error report as the installation program allowed me to do so. 

The version of the OS I currently run is:

[B]uname -a

Linux Computer-1A 3.8.0-44-generic #66~precise1-Ubuntu SMP Tue Jul 15 04:01:04 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[/B]

---

### Post by kansasnoob on 2014-09-11
My best guess is that you're currently running Precise - more specifically Precise that was installed with the 12.04.3 iso, so you have the Precise running with the Raring HWE stack which is EOL - more info about HWE EOL and LTS HWE in these two links:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Please post the output of these three commands so we can be sure my best guess is correct and also to see what, if any, PPA's you may be using:

```
lsb_release -a
```

```
cat /etc/apt/sources.list
```

```
ls /etc/apt/sources.list.d
```

---

### Post by 8LfOM1R0 on 2014-09-11
**root@Computer-1A:/home/alex# lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

**alex@Computer-1A:~$ cat /etc/apt/sources.list**
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

**alex@Computer-1A:~$ ls /etc/apt/sources.list.d**
google-chrome.list              skunk-pepper-flash-precise.list
google-chrome.list.distUpgrade  skunk-pepper-flash-precise.list.distUpgrade
google-chrome.list.save


Apologies for the formatting.

---

### Post by kansasnoob on 2014-09-13
Sorry for the long delay but I've been away from the desk due to health reasons. That info verifies what I thought about the existing OS and the upgrade path.

My best guess is that some package(s) installed from a source other than the Ubuntu repos is causing a conflict. It looks like you have two PPA's installed:

```
alex@Computer-1A:~$ ls /etc/apt/sources.list.d
google-chrome.list skunk-pepper-flash-precise.list
google-chrome.list.distUpgrade skunk-pepper-flash-precise.list.distUpgrade
google-chrome.list.save
```

If you can narrow that down to the specific PPA sources you may be able to use 'ppa-purge' to try and get rid of the troublesome packages. My head's not up to the challenge ATM :(

---

### Post by 8LfOM1R0 on 2014-09-14
Thank you Kansasnoob, 

I myself don't have the time to work on this at the moment. I was hoping for a Guru quickfix from the Ubuntu community. 

Get well soon ;)

---

### Post by kansasnoob on 2014-09-15
I'll give you another bump in hopes that someone else has an idea. My brain is still kind of scrambled but I wonder if there is anything in /var/log/dist-upgrade? I'm not sure if the release upgrader even produces any logs when it determines it can't proceed????

---

### Post by ian-weisser on 2014-09-15
There's no secret guru-fix.
Kansasnoob is right.

If you don't know what is causing the conflict, then uninstall ALL your PPA software. You can't use it 12.04 PPAs on 14.04 anyway.
Your best chance for a successful upgrade is to get rid of all non-Ubuntu software (including PPAs); they are what cause most of the problems.
You can reinstall them after a successful upgrade.

---

### Post by 8LfOM1R0 on 2014-09-15
My /var/log/dist-upgrade directory contains the following:

20140911-1525                  apt.log    main.log
apt-clone_system_state.tar.gz  lspci.txt  term.log

20140911-1525 is a directory containing the following files:
apt.log  main.log  term.log
 
And for apt-clone_system_state.tar.gz:

root@Computer-1A:/var/log/dist-upgrade# tar -xvzf apt-clone_system_state.tar.gz 
./var/lib/apt-clone/uname                                                      
./var/lib/apt-clone/installed.pkgs
./var/lib/apt-clone/extended_states
./etc/apt/sources.list
./etc/apt/sources.list.d/
./etc/apt/sources.list.d/skunk-pepper-flash-precise.list
./etc/apt/sources.list.d/google-chrome.list
./etc/apt/preferences.d/
./etc/apt/trusted.gpg
./etc/apt/trusted.gpg.d/
./etc/apt/trusted.gpg.d/jockey-drivers.gpg~
./etc/apt/trusted.gpg.d/jockey-drivers.gpg
./var/lib/apt-clone/dpkg-status

Unfortunately, I am an administration novice - something I hope to fix with some quality study materials and a good dose of time. I do not therefore have an idea as to which log you would like me to display to you.

---

### Post by ian-weisser on 2014-09-15
Since the upgrade was cancelled (good decision!), there may not be a useful log.

---

### Post by 8LfOM1R0 on 2014-09-25
As I didn't need any of the ppa's in /etc/apt/sources.list.d I removed everything in the directory. 
The aforementioned installation problem still occurs. 
I have tried to purge everything on the system with sudo ppa-purge:* but the command line doesn't give any output, just a flashing cursor. 
There is nothing on this system I need now so I am prepared to take any measures to get my new installation. 
I await replies, thanks.

---

### Post by Bashing-om on 2014-09-25
alexander49; Hello;

Let's take a look and make sure the package manager is in a consistent state at this time:

Post back the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo lshw -C display

```

Then we see what is that next step.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-09-25
It's often not enough to merely disable the PPA sources.
The conflicting packages are still installed.
Disabling or removing the PPA merely ensures that they won't be upgraded.

---

### Post by 8LfOM1R0 on 2014-09-25
alex@Computer-1A:~/Desktop$ sudo apt-get update
[sudo] password for alex: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg                  
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [98.7 kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [50.7 kB]                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [110 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources                                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex                               
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [478 kB]                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                                                         
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]                    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [32.7 kB]                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,785 B]                          
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [425 kB]       
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [8,056 B]                          
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [110 kB]                                
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [8,886 B]                              
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages [836 kB]         
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]                        
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [97.9 kB]        
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages [13.7 kB]       
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages [248 kB]         
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,447 B]        
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [457 kB]              
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [15.3 kB]    
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [867 kB]              
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.7 kB]                                                                 
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [255 kB]                                                                    
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]                                                                 
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]                                                                    
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]                                                              
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]                                                              
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]                                                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources                                                                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources                                                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources                                                                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources                                                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main amd64 Packages                                                                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted amd64 Packages                                                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe amd64 Packages                                                                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse amd64 Packages                                                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages                                                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages                                                                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages                                                                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                                                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex                                                                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB                                                                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en                                                                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB                                                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en                                                                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB                                                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en                                                                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB                                                                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en                                                                                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB                                                                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en                                                                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB                                                                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB                                                                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB                                                                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en                                                                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en                                                                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en                                                                             
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]                                                                  
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [104 kB]                                                                     
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,638 B]                                                                  
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]                                                                        
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]                                                                  
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]                                                                  
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                                                                                
Fetched 4,276 kB in 9s (431 kB/s)                                                                                                                      
Reading package lists... Done
alex@Computer-1A:~/Desktop$

---

### Post by 8LfOM1R0 on 2014-09-25
alex@Computer-1A:~/Desktop$ sudo apt-get upgrade
[sudo] password for alex: 
Sorry, try again.
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bash
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 641 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main bash amd64 4.2-2ubuntu2.3 [641 kB]
Fetched 641 kB in 1s (455 kB/s)
(Reading database ... 521855 files and directories currently installed.)
Preparing to replace bash 4.2-2ubuntu2.2 (using .../bash_4.2-2ubuntu2.3_amd64.deb) ...
Unpacking replacement bash ...
Processing triggers for man-db ...
Setting up bash (4.2-2ubuntu2.3) ...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
alex@Computer-1A:~/Desktop$

---

### Post by 8LfOM1R0 on 2014-09-25
alex@Computer-1A:~/Desktop$ sudo apt-get dist-upgrade
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
alex@Computer-1A:~/Desktop$

---

### Post by 8LfOM1R0 on 2014-09-25
root@Computer-1A:/home/alex/Desktop# lshw -C display
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:4000(size=64)

---

### Post by 8LfOM1R0 on 2014-09-25
I submitted the above 4 posts separately because earlier I posed the output of the four commands as one post and it seems to have disapeared.

---

### Post by ian-weisser on 2014-09-25
> **alexander49 said:**
> There is nothing on this system I need now so I am prepared to take any measures to get my new installation.

Thanks for the outputs that Bashing-om requested.
They are lengthy, but they do help to identify a lot of problems.

The package manager seems in good shape.

I see two options for you:
1) Upgrade from 12.04 to 14.04
2) Install fresh 14.04

The former may still have those pesky PPA conflicts, but the process will show you a lot about how your system works.
The latter is much faster.

Your system, your choice.

---

### Post by 8LfOM1R0 on 2014-09-26
I would prefer to upgrade for the education.

---

### Post by ian-weisser on 2014-09-26
If you recall any specific applications or packages you installed from PPA, uninstall them.
Those still-installed PPA packages cause most upgrade failures.

Try to return your system package state as close to out-of-the-box as you can get.
That will significantly increase your chance of a successful version upgrade.

Next time you try to upgrade, look for any specific package names in the error messages.

---

