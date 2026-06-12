---
title: "apt-get update uses repositories not in the sources.list file"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by davidshere on 2008-06-02
If my sources.list file looks like this:

```
david@lancer:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _hardy Gibbon_ - Release i386 (20071016)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://archive.ubuntu.com/ubuntu hardy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

```

.... why does my apt-get update look like this:

```
david@lancer:~$ sudo apt-get update
Hit http://archive.ubuntu.com hardy-updates Release.gpg
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US                                          
Hit http://packages.medibuntu.org feisty Release.gpg                                                            
Hit http://security.ubuntu.com hardy-security Release.gpg                                                       
Ign http://security.ubuntu.com hardy-security/main Translation-en_US                                            
Hit http://us.archive.ubuntu.com hardy Release.gpg                                                               
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                                                    
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US                                              
Hit http://archive.canonical.com hardy Release.gpg                                                               
Ign http://archive.canonical.com hardy/partner Translation-en_US                                                 
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US                                         
Hit http://archive.ubuntu.com hardy-security Release.gpg                                   
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US                        
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US                  
Ign http://packages.medibuntu.org feisty/free Translation-en_US                            
Ign http://packages.medibuntu.org feisty/non-free Translation-en_US                        
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US                    
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US                                       
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US                                         
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US                                       
Hit http://security.ubuntu.com gutsy-security Release.gpg                                                        
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US                                       
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US                                         
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US                                                
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US                                              
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                                                       
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US                                            
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US                                      
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US                                        
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US                                      
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg                                                     
Hit http://archive.canonical.com hardy Release                                                                   
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US                                          
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US              
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US                
Hit http://security.ubuntu.com hardy-security Release                                      
Hit http://archive.ubuntu.com hardy-updates Release                                        
Hit http://archive.ubuntu.com hardy-security Release                                       
Hit http://packages.medibuntu.org feisty Release                                           
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US              
Hit http://archive.canonical.com hardy/partner Packages                                   
Hit http://security.ubuntu.com gutsy-security Release                                     
Hit http://us.archive.ubuntu.com gutsy Release.gpg                                                              
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US                                            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US                                              
Hit http://archive.canonical.com hardy/partner Sources                                                                      
Hit http://security.ubuntu.com hardy-security/main Packages                                                      
Hit http://security.ubuntu.com hardy-security/restricted Packages                                                
Hit http://security.ubuntu.com hardy-security/main Sources                                                       
Hit http://archive.ubuntu.com hardy-updates/universe Packages                                                    
Hit http://us.archive.ubuntu.com gutsy-updates Release.gpg                                 
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release                                     
Hit http://us.archive.ubuntu.com hardy-backports Release                                   
Hit http://packages.medibuntu.org feisty/free Packages                                                          
Hit http://us.archive.ubuntu.com gutsy Release                                                                  
Hit http://security.ubuntu.com hardy-security/restricted Sources                           
Hit http://security.ubuntu.com hardy-security/universe Packages                            
Hit http://security.ubuntu.com hardy-security/universe Sources                             
Hit http://security.ubuntu.com hardy-security/multiverse Packages                          
Hit http://security.ubuntu.com hardy-security/multiverse Sources                           
Hit http://security.ubuntu.com gutsy-security/multiverse Packages                          
Hit http://security.ubuntu.com gutsy-security/universe Packages                            
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                            
Hit http://archive.ubuntu.com hardy-security/main Packages                                 
Hit http://archive.ubuntu.com hardy-security/restricted Packages                           
Hit http://packages.medibuntu.org feisty/non-free Packages                                 
Hit http://us.archive.ubuntu.com gutsy-updates Release               
Hit http://archive.ubuntu.com hardy-security/universe Packages       
Hit http://archive.ubuntu.com hardy-security/multiverse Packages     
Hit http://us.archive.ubuntu.com hardy/main Packages                 
Hit http://us.archive.ubuntu.com hardy/restricted Packages          
Hit http://us.archive.ubuntu.com hardy/main Sources                 
Hit http://us.archive.ubuntu.com hardy/restricted Sources           
Hit http://packages.medibuntu.org feisty/free Sources               
Hit http://packages.medibuntu.org feisty/non-free Sources           
Hit http://us.archive.ubuntu.com hardy/universe Packages            
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Reading package lists... Done
david@lancer:~$ 

```

There's a whole bunch of Feisties and Gutsies in there.  Where did they come from?

---

### Post by EXCiD3 on 2008-06-02
Have you checked to see if there are any files in your /etc/apt/sources.list.d/ folder? Sometimes there are extra repository lists added into that folder, external from sources.list.

---

### Post by davidshere on 2008-06-02
hmm.. yes there are... and they're a hodgepodge of past versions all the way back to edgy.  It seems like everything should be hardy.  Should I just delete all of these?  Is there a "right way" to clean this up?  Or should I just not worry?

```
root@lancer:/etc/apt/sources.list.d# ls
edgy-multiverse.list              edgy-universe.list.save
edgy-multiverse.list.distUpgrade  medibuntu.list
edgy-multiverse.list.save         medibuntu.list.distUpgrade
edgy-universe.list                medibuntu.list.save
edgy-universe.list.distUpgrade
root@lancer:/etc/apt/sources.list.d# more edgy-multiverse.list
# automatically added by gnome-app-install on 2007-04-15 11:33:56.451630
deb http://us.archive.ubuntu.com/ubuntu gutsy multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates multiverse
root@lancer:/etc/apt/sources.list.d# more edgy-multiverse.list.distUpgrade 
# automatically added by gnome-app-install on 2007-04-15 11:33:56.451630
deb http://us.archive.ubuntu.com/ubuntu feisty multiverse
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://us.archive.ubuntu.com/ubuntu feisty-updates multiverse
root@lancer:/etc/apt/sources.list.d# more edgy-multiverse.list.save
# automatically added by gnome-app-install on 2007-04-15 11:33:56.451630
deb http://us.archive.ubuntu.com/ubuntu gutsy multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates multiverse
root@lancer:/etc/apt/sources.list.d# more edgy-universe.list
# automatically added by gnome-app-install on 2007-04-15 11:32:59.021825
deb http://us.archive.ubuntu.com/ubuntu gutsy universe
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe
root@lancer:/etc/apt/sources.list.d# more edgy-universe.list.distUpgrade 
# automatically added by gnome-app-install on 2007-04-15 11:32:59.021825
deb http://us.archive.ubuntu.com/ubuntu feisty universe
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe
root@lancer:/etc/apt/sources.list.d# more edgy-universe.list.save
# automatically added by gnome-app-install on 2007-04-15 11:32:59.021825
deb http://us.archive.ubuntu.com/ubuntu gutsy universe
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe
root@lancer:/etc/apt/sources.list.d# more medibuntu.list
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ feisty free non-free
deb-src http://packages.medibuntu.org/ feisty free non-free
root@lancer:/etc/apt/sources.list.d# more medibuntu.list.distUpgrade 
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://packages.medibuntu.org/ feisty free non-free
root@lancer:/etc/apt/sources.list.d# more medibuntu.list.save
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ feisty free non-free
deb-src http://packages.medibuntu.org/ feisty free non-free
root@lancer:/etc/apt/sources.list.d# 
```

---

### Post by EXCiD3 on 2008-06-02
You should be fine deleting those .list files from the folder. If you need to install any of the software from them you might need a new list file anyways. Its safe to just delete them from the folder without doing anything else. Just make sure to run apt-get update afterwards.

---

