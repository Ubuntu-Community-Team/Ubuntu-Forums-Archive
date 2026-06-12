---
title: "duplictate sources.list entries not found"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by warfab on 2015-08-17
I get this when I use "sudo apt-get update":
```
Ign http://dl.google.com stable InReleaseHit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main Translation-en_PH                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://archive.ubuntu.com vivid InRelease                                  
Ign http://security.ubuntu.com vivid-security InRelease               
Ign http://ppa.launchpad.net vivid InRelease    
Ign http://archive.ubuntu.com vivid-updates InRelease
Hit http://security.ubuntu.com vivid-security Release.gpg
Ign http://ppa.launchpad.net vivid InRelease    
Ign http://archive.ubuntu.com vivid-backports InRelease
Hit http://security.ubuntu.com vivid-security Release
Ign http://archive.ubuntu.com vivid-security InRelease                 
Hit http://ppa.launchpad.net vivid Release.gpg  
Hit http://security.ubuntu.com vivid-security/main amd64 Packages
Hit http://archive.ubuntu.com vivid Release.gpg                                
Hit http://security.ubuntu.com vivid-security/restricted amd64 Packages
Hit http://ppa.launchpad.net vivid Release.gpg                        
Hit http://archive.ubuntu.com vivid-updates Release.gpg               
Hit http://security.ubuntu.com vivid-security/main i386 Packages
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://archive.ubuntu.com vivid-backports Release.gpg              
Hit http://security.ubuntu.com vivid-security/restricted i386 Packages
Hit http://ppa.launchpad.net vivid Release                            
Hit http://archive.ubuntu.com vivid-security Release.gpg               
Hit http://security.ubuntu.com vivid-security/main Translation-en     
Hit http://archive.ubuntu.com vivid Release                                    
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://security.ubuntu.com vivid-security/restricted Translation-en
Hit http://archive.ubuntu.com vivid-updates Release                   
Hit http://ppa.launchpad.net vivid/main i386 Packages                  
Hit http://archive.ubuntu.com vivid-backports Release
Hit http://ppa.launchpad.net vivid/main Translation-en
Hit http://archive.ubuntu.com vivid-security Release
Hit http://archive.ubuntu.com vivid/main Sources                       
Hit http://ppa.launchpad.net vivid/main amd64 Packages        
Hit http://archive.ubuntu.com vivid/restricted Sources         
Hit http://ppa.launchpad.net vivid/main i386 Packages             
Hit http://archive.ubuntu.com vivid/universe Sources
Hit http://ppa.launchpad.net vivid/main Translation-en        
Hit http://archive.ubuntu.com vivid/multiverse Sources        
Hit http://archive.ubuntu.com vivid/main amd64 Packages
Hit http://archive.ubuntu.com vivid/universe amd64 Packages
Hit http://archive.ubuntu.com vivid/multiverse amd64 Packages
Hit http://archive.ubuntu.com vivid/main i386 Packages
Hit http://archive.ubuntu.com vivid/universe i386 Packages                                                                                     
Hit http://archive.ubuntu.com vivid/multiverse i386 Packages                                                                                   
Hit http://archive.ubuntu.com vivid/main Translation-en                                                                                        
Hit http://archive.ubuntu.com vivid/multiverse Translation-en                                                                                  
Hit http://archive.ubuntu.com vivid/restricted Translation-en                                                                                  
100% [Packages 35.3 MB]                                                                                                                                                                                                                                     Hit http://archive.ubuntu.com vivid/universe Translation-en
Hit http://archive.ubuntu.com vivid-updates/main Sources      
Hit http://archive.ubuntu.com vivid-updates/restricted Sources
Hit http://archive.ubuntu.com vivid-updates/universe Sources  
Hit http://archive.ubuntu.com vivid-updates/multiverse Sources
Hit http://archive.ubuntu.com vivid-updates/main amd64 Packages
Hit http://archive.ubuntu.com vivid-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com vivid-updates/universe amd64 Packages
Hit http://archive.ubuntu.com vivid-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com vivid-updates/main i386 Packages
Hit http://archive.ubuntu.com vivid-updates/restricted i386 Packages
Hit http://archive.ubuntu.com vivid-updates/universe i386 Packages
Hit http://archive.ubuntu.com vivid-updates/multiverse i386 Packages                                                                           
Hit http://archive.ubuntu.com vivid-updates/main Translation-en                                                                                
Hit http://archive.ubuntu.com vivid-updates/multiverse Translation-en                                                                          
Hit http://archive.ubuntu.com vivid-updates/restricted Translation-en                                                                          
Hit http://archive.ubuntu.com vivid-updates/universe Translation-en                                                                            
Hit http://archive.ubuntu.com vivid-backports/main Sources                                                                                     
Hit http://archive.ubuntu.com vivid-backports/restricted Sources                                                                               
Hit http://archive.ubuntu.com vivid-backports/universe Sources                                                                                 
Hit http://archive.ubuntu.com vivid-backports/multiverse Sources                                                                               
Hit http://archive.ubuntu.com vivid-backports/main amd64 Packages                                                                              
Hit http://archive.ubuntu.com vivid-backports/restricted amd64 Packages                                                                        
Hit http://archive.ubuntu.com vivid-backports/universe amd64 Packages                                                                          
Hit http://archive.ubuntu.com vivid-backports/multiverse amd64 Packages                                                                        
Hit http://archive.ubuntu.com vivid-backports/main i386 Packages                                                                               
Hit http://archive.ubuntu.com vivid-backports/restricted i386 Packages                                                                         
Hit http://archive.ubuntu.com vivid-backports/universe i386 Packages                                                                           
100% [Waiting for headers]                                                      Hit http://archive.ubuntu.com vivid-backports/multiverse i386 Packages         
Hit http://archive.ubuntu.com vivid-backports/main Translation-en              
Hit http://archive.ubuntu.com vivid-backports/multiverse Translation-en        
Hit http://archive.ubuntu.com vivid-backports/restricted Translation-en        
Hit http://archive.ubuntu.com vivid-backports/universe Translation-en          
Hit http://archive.ubuntu.com vivid-security/main Sources                      
Hit http://archive.ubuntu.com vivid-security/restricted Sources                
Hit http://archive.ubuntu.com vivid-security/universe Sources                  
Hit http://archive.ubuntu.com vivid-security/multiverse Sources                
Hit http://archive.ubuntu.com vivid-security/main amd64 Packages               
Hit http://archive.ubuntu.com vivid-security/restricted amd64 Packages         
Hit http://archive.ubuntu.com vivid-security/universe amd64 Packages           
Hit http://archive.ubuntu.com vivid-security/multiverse amd64 Packages         
Hit http://archive.ubuntu.com vivid-security/main i386 Packages                
Hit http://archive.ubuntu.com vivid-security/restricted i386 Packages          
Hit http://archive.ubuntu.com vivid-security/universe i386 Packages            
Hit http://archive.ubuntu.com vivid-security/multiverse i386 Packages          
Hit http://archive.ubuntu.com vivid-security/main Translation-en               
Hit http://archive.ubuntu.com vivid-security/multiverse Translation-en         
Hit http://archive.ubuntu.com vivid-security/restricted Translation-en         
Hit http://archive.ubuntu.com vivid-security/universe Translation-en           
Hit http://archive.ubuntu.com vivid/restricted amd64 Packages                  
Hit http://archive.ubuntu.com vivid/restricted i386 Packages                   
Reading package lists... Done                                                  
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ vivid/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_vivid_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ vivid/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_vivid_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ vivid-updates/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_vivid-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ vivid-updates/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_vivid-updates_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

Here's my sources.list:
```
# deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main restricteddeb http://archive.ubuntu.com/ubuntu vivid main restricted
deb http://security.ubuntu.com/ubuntu/ vivid-security main restricted
deb http://archive.ubuntu.com/ubuntu vivid-updates main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu vivid restricted
deb-src http://archive.ubuntu.com/ubuntu vivid main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu vivid-updates restricted
deb-src http://archive.ubuntu.com/ubuntu vivid-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu vivid universe
deb-src http://archive.ubuntu.com/ubuntu vivid universe
deb http://archive.ubuntu.com/ubuntu vivid-updates universe
deb-src http://archive.ubuntu.com/ubuntu vivid-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu vivid multiverse
deb-src http://archive.ubuntu.com/ubuntu vivid multiverse
deb http://archive.ubuntu.com/ubuntu vivid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu vivid-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu vivid-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu vivid-backports main restricted universe multiverse


deb http://archive.ubuntu.com/ubuntu vivid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu vivid-security main restricted
deb http://archive.ubuntu.com/ubuntu vivid-security universe
deb-src http://archive.ubuntu.com/ubuntu vivid-security universe
deb http://archive.ubuntu.com/ubuntu vivid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu vivid-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu vivid partner
# deb-src http://archive.canonical.com/ubuntu vivid partner

```

The output from "[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list.d/*.list" is:
[/FONT][/COLOR]```
### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu vivid main
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu vivid main
deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main

```[COLOR=#000000][FONT=Ubuntu Mono]

I'm relatively a newb to linux. So if someone could point out the entries that I have to edit, I'd be grateful.[/FONT][/COLOR]

---

### Post by dino99 on 2015-08-17
i suppose you have made so much tweaks that you hit a huge mess: dont mix amd64 and i386, its not compatible, but an amd64 (which is a 64 bits installation, nothing related to that confusing named 'amd''64') installation can run 32 bits package (package_name:i386 into the archive).

better to understand what you are doing, than blindly install everything you can find because its new  ;)

---

### Post by warfab on 2015-08-17
The only things I installed after fresh Ubuntu 15.04 on Virtualbox was Google Chrome, Java and VLC. Didn't install anything after that and before my first post here.

---

### Post by ian-weisser on 2015-08-17
Duplication example:
```
deb http://archive.ubuntu.com/ubuntu vivid main restricted
deb http://archive.ubuntu.com/ubuntu vivid restricted
```

'main' and 'restricted' are separate repositories. The same URL can point to multiple repositories.
In the example above, the same URL is used twice. 'main' appears once (not a duplicate). 'restricted' appears twice (duplicate).




> **warfab said:**
> The only thing I installed after fresh Ubuntu 15.04 on Virtualbox was Google Chrome. Didn't install anything after that and before my first post here.

Chrome generally doesn't install PPAs for Java nor VLC.
So it does seem likely you have installed something more than Chrome, and dino99's sound advice seems appropriate.

If you are truly a "newb to linux", I recommend against PPAs until you understand perhaps a bit more how the package manager works. 
The package manager is designed to be admin-friendly, not newb-friendly. If you order the package manager to break your system, it will grudgingly obey your order.
User-friendly (safe) means sticking with the Ubuntu repositories. Not PPAs until you understand the dangers. PPAs are not supported software - not tested, sometimes not safe.

---

### Post by warfab on 2015-08-17
Got it sorted out. I found [http://askubuntu.com/questions/120621/how-to-fix-duplicate-sources-list-entry](http://askubuntu.com/questions/120621/how-to-fix-duplicate-sources-list-entry) and I was able to solve it.

---

