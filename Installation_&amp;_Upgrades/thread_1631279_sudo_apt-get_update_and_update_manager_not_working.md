---
title: "sudo apt-get update and update manager not working"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by Aryamaan on 2010-11-26
Ever since I upgraded from Ubuntu 10.04 to 10.10 my upgrade manager has stopped working and even the sudo apt-get update command seems to be giving me some error. 

Update Manager:

When it runs it gives me a message saying:

[COLOR="DarkRed"]Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by"
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu[/COLOR]

[COLOR="Black"]When I click on partial upgrade it gives me this(and i am sure there are no package management applications running):[/COLOR]

[COLOR="#8b0000"]Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first[/COLOR]

And when I don't click partial upgrade and close the message and click update it gives me this:

[COLOR="DarkRed"]CD/DVD 'Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)' is required

Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from it.[/COLOR]

[COLOR="Black"]After inserting the cd and continuing it says failed to get updates. Check internet connection.[/COLOR]


When I run sudo apt-get update this is what I get:

[COLOR="DarkRed"]aryaman@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                                                                                                
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                               
Ign [http://ppa.launchpad.net/alecive/antigone/ubuntu/](http://ppa.launchpad.net/alecive/antigone/ubuntu/) maverick/main Translation-en                              
Ign [http://ppa.launchpad.net/alecive/antigone/ubuntu/](http://ppa.launchpad.net/alecive/antigone/ubuntu/) maverick/main Translation-en_US                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                                               
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                                                            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                            
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                
Ign [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/) maverick/main Translation-en         
Ign [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/) maverick/main Translation-en_US      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                          
Ign [http://ppa.launchpad.net/tiheum/equinox/ubuntu/](http://ppa.launchpad.net/tiheum/equinox/ubuntu/) maverick/main Translation-en           
Ign [http://ppa.launchpad.net/tiheum/equinox/ubuntu/](http://ppa.launchpad.net/tiheum/equinox/ubuntu/) maverick/main Translation-en_US        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                          
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                                    
Ign [http://ppa.launchpad.net/unity/ppa/ubuntu/](http://ppa.launchpad.net/unity/ppa/ubuntu/) maverick/main Translation-en                                      
Ign [http://ppa.launchpad.net/unity/ppa/ubuntu/](http://ppa.launchpad.net/unity/ppa/ubuntu/) maverick/main Translation-en_US                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US                                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US                            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                                                               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US                                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                                                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                                                                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse i386 Packages
Media change: please insert the disc labeled
 'Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)'
in the drive '/cdrom/' and press enter

Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid Release
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main i386 Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted i386 Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main i386 Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted i386 Packages
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
[/COLOR]

[COLOR="Black"]Please help! I'm a beginner.[/COLOR]

---

### Post by d3v1150m471c on 2010-11-26
please post the output of this command:
```

cat /etc/apt/sources.list

```it helps to use code tags for terminal commands and output when pasting it on the forums, btw.

---

### Post by takisan on 2010-11-26
I would get the same problem, but only because I installed the Human theme from the Hardy repository.

Try running Synaptic and going to Preferences > Repositories, and find and decheck all of the CDROM choices.

---

### Post by Aryamaan on 2010-11-26
Here's the output:

```
aryaman@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
# deb http://www.sourceslist.eu/repo/ubuntu maverick main non-free # disabled on upgrade to maverick
# deb http://ppa.launchpad.net/bean123ch/burg/ubuntu maverick main # disabled on upgrade to maverick
# deb-src http://ppa.launchpad.net/bean123ch/burg/ubuntu maverick main # disabled on upgrade to maverick
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
aryaman@ubuntu:~$ 
```

---

### Post by d3v1150m471c on 2010-11-26
> **takisan said:**
> I would get the same problem, but only because I installed the Human theme from the Hardy repository.


```

sudo aptitude hold <package>
sudo aptitude unhold <package>

```

That could save you some trouble in the future, by telling your system to not upgrade the desired package. You can hold/unhold a package's version with the above commands.

---

### Post by d3v1150m471c on 2010-11-26
try this and send us the output. before you do this check off the cdrom option like takisan mentioned above.

```

cp /etc/apt/sources.list ~/sources.list
cat ~/sources.list | sed 's/lucid/maverick/g' > ~/file
sudo cp ~/file /etc/apt/sources.list
sudo apt-get update

```

---

### Post by Aryamaan on 2010-11-26
Thanks. I think takisan's comment helped. I unchecked cdrom and it starting upgrading normally. Yay ! Thanks for the quick responses :)

---

