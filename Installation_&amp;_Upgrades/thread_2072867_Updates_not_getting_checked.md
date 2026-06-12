---
title: "Updates not getting checked"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by peggysmouse on 2012-10-18
On one of my Ubuntu 12.04 computers, I never get any notifications of updates that are available. After a week or so, I get this message:

The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and then selecting 'Check for updates' and check if some of the listed repositories fail.

If I run ```
apt-get update
``` I get the following results with no errors: 

```
Ign http://extras.ubuntu.com precise InRelease                                                                            
Ign http://ppa.launchpad.net precise InRelease                                                                            
Ign http://archive.canonical.com precise InRelease                   
Ign http://ca.archive.ubuntu.com precise InRelease                   
Ign http://ca.archive.ubuntu.com precise-updates InRelease           
Ign http://ca.archive.ubuntu.com precise-backports InRelease         
Ign http://ca.archive.ubuntu.com precise-security InRelease          
Hit http://extras.ubuntu.com precise Release.gpg                     
Hit http://ppa.launchpad.net precise Release.gpg                     
Hit http://archive.canonical.com precise Release.gpg                 
Hit http://ca.archive.ubuntu.com precise Release.gpg                                       
Hit http://extras.ubuntu.com precise Release                                               
Hit http://ppa.launchpad.net precise Release                                                
Hit http://archive.canonical.com precise Release                                            
Hit http://ca.archive.ubuntu.com precise-updates Release.gpg                                
Hit http://ca.archive.ubuntu.com precise-backports Release.gpg                             
Hit http://extras.ubuntu.com precise/main Sources                                          
Hit http://ppa.launchpad.net precise/main i386 Packages                                    
Hit http://archive.canonical.com precise/partner i386 Packages       
Hit http://ca.archive.ubuntu.com precise-security Release.gpg        
Hit http://extras.ubuntu.com precise/main i386 Packages              
Ign http://extras.ubuntu.com precise/main TranslationIndex           
Ign http://ppa.launchpad.net precise/main TranslationIndex           
Ign http://archive.canonical.com precise/partner TranslationIndex    
Hit http://ca.archive.ubuntu.com precise Release                     
Hit http://ca.archive.ubuntu.com precise-updates Release             
Hit http://ca.archive.ubuntu.com precise-backports Release                                                        
Hit http://ca.archive.ubuntu.com precise-security Release                                                         
Hit http://ca.archive.ubuntu.com precise/main Sources                                                             
Hit http://ca.archive.ubuntu.com precise/restricted Sources                                
Hit http://ca.archive.ubuntu.com precise/universe Sources                                  
Hit http://ca.archive.ubuntu.com precise/multiverse Sources                                
Hit http://ca.archive.ubuntu.com precise/main i386 Packages                                
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages                          
Hit http://ca.archive.ubuntu.com precise/universe i386 Packages      
Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex                             
Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex                       
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex                       
Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex                         
Hit http://ca.archive.ubuntu.com precise-updates/main Sources                              
Hit http://ca.archive.ubuntu.com precise-updates/restricted Sources                        
Hit http://ca.archive.ubuntu.com precise-updates/universe Sources                          
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Sources                        
Hit http://ca.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://ca.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com precise-updates/main TranslationIndex                     
Hit http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex               
Hit http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex               
Hit http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex                 
Hit http://ca.archive.ubuntu.com precise-backports/main Sources                            
Hit http://ca.archive.ubuntu.com precise-backports/restricted Sources                      
Hit http://ca.archive.ubuntu.com precise-backports/universe Sources                        
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Sources                      
Hit http://ca.archive.ubuntu.com precise-backports/main i386 Packages                      
Ign http://extras.ubuntu.com precise/main Translation-en_CA                                
Hit http://ca.archive.ubuntu.com precise-backports/restricted i386 Packages                
Hit http://ca.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://ca.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise-backports/multiverse TranslationIndex             
Hit http://ca.archive.ubuntu.com precise-backports/restricted TranslationIndex             
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                
Ign http://archive.canonical.com precise/partner Translation-en_CA                         
Ign http://extras.ubuntu.com precise/main Translation-en             
Hit http://ca.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://ca.archive.ubuntu.com precise-security/main Sources       
Hit http://ca.archive.ubuntu.com precise-security/restricted Sources 
Hit http://ca.archive.ubuntu.com precise-security/universe Sources   
Hit http://ca.archive.ubuntu.com precise-security/multiverse Sources
Hit http://ca.archive.ubuntu.com precise-security/main i386 Packages
Hit http://ca.archive.ubuntu.com precise-security/restricted i386 Packages
Hit http://ca.archive.ubuntu.com precise-security/universe i386 Packages
Hit http://ca.archive.ubuntu.com precise-security/multiverse i386 Packages
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://archive.canonical.com precise/partner Translation-en
Hit http://ca.archive.ubuntu.com precise-security/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://ca.archive.ubuntu.com precise-security/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise-security/universe TranslationIndex
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA
Hit http://ca.archive.ubuntu.com precise/main Translation-en
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com precise/universe Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/main Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://ca.archive.ubuntu.com precise-security/main Translation-en
Hit http://ca.archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise-security/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise-security/universe Translation-en
Reading package lists... Done
```My /etc/apt/sources.list file is as follows:
```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://ca.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ precise-security universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://ca.archive.ubuntu.com/ubuntu/ precise-security multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
# deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main # disabled on upgrade to precise
```Updates are configured to be checked every day and displayed as soon as they are available.

When I run the updater, it initially tells me there are no available updates (if I haven't run apt-get update manually) but if I click the check button, it finds them.

Suggestions?

I assume Ign stands for ignore. Why are those lines there? Are they possibly getting in the way?

---

### Post by peggysmouse on 2012-10-19
I'm surprised not to see this issue come up for anyone else unless they have their sources.list incorrectly configured. Hm.... 

So, what controls when the notifications? What controls the checking? Would there be log messages somewhere that might provide some clues (if the update were failing silently)?

---

### Post by grahammechanical on 2012-10-19
This

> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en

Might be causing the problem. Disable the ppa.

running

```
sudo apt-get upgrade
```

might show other errors. It might show why the upgrade is being blocked.

This command will remove (delete) the scripts that are called sources lists

```
sudo rm /var/lib/apt/lists/* -rf
```

This command will replace them with new ones.

```
sudo apt-get update
```

I had to use it recently to solve a similar problem.

Regards.

---

### Post by peggysmouse on 2012-10-24
I tried your suggestion but no luck.

---

### Post by peggysmouse on 2012-10-24
Actually, I don't see the PPA you mention. It should be somewhere under /etc/apt?
```
root@ron-desktop:/etc/apt# grep -r launchpad *
sources.list:# deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main # disabled on upgrade to precise
sources.list:# deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main # disabled on upgrade to precise
sources.list.d/caffeine-developers-ppa-precise.list:# deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu precise main
sources.list.d/caffeine-developers-ppa-precise.list:# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu precise main
sources.list.d/caffeine-developers-ppa-precise.list.save:deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu precise main
sources.list.d/caffeine-developers-ppa-precise.list.save:# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu precise main
sources.list.distUpgrade:deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu oneiric main
sources.list.distUpgrade:deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu oneiric main
sources.list.save:# deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main # disabled on upgrade to precise
sources.list.save:# deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main # disabled on upgrade to precise
```

---

### Post by X9Tim on 2012-11-02
I have this exact same problem.  I've been looking for further info, but not found any help yet.

The problem is definitely not with sources that are unavailable, it is the Update Manager that is not successfully fetching the list of updates.  When I run a manual **[FONT=Fixedsys][COLOR=Navy]sudo apt-get update[/COLOR][/FONT]** it fetches them fine:
```
/home/username/scripts> sudo apt-get update
Ign http://archive.canonical.com precise InRelease
Ign http://archive.canonical.com precise InRelease
Ign http://mirror01.th.ifl.net precise InRelease
Ign http://mirror01.th.ifl.net precise-updates InRelease
Ign http://mirror01.th.ifl.net precise-security InRelease
Ign http://extras.ubuntu.com precise InRelease 
Hit http://archive.canonical.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://mirror01.th.ifl.net precise Release.gpg
Hit http://mirror01.th.ifl.net precise-updates Release.gpg
Hit http://archive.canonical.com precise Release.gpg                 
Hit http://extras.ubuntu.com precise Release                         
Hit http://mirror01.th.ifl.net precise-security Release.gpg
Hit http://archive.canonical.com precise Release
Hit http://mirror01.th.ifl.net precise Release                        
Hit http://archive.canonical.com precise Release                      
Hit http://mirror01.th.ifl.net precise-updates Release
Hit http://mirror01.th.ifl.net precise-security Release                                     
Hit http://extras.ubuntu.com precise/main i386 Packages                                     
Hit http://archive.canonical.com precise/partner i386 Packages                              
Ign http://extras.ubuntu.com precise/main TranslationIndex                                  
Hit http://mirror01.th.ifl.net precise/main Sources                                         
Ign http://archive.canonical.com precise/partner TranslationIndex    
Hit http://mirror01.th.ifl.net precise/restricted Sources
Hit http://mirror01.th.ifl.net precise/multiverse Sources
Hit http://mirror01.th.ifl.net precise/universe Sources
Hit http://mirror01.th.ifl.net precise/main i386 Packages
Hit http://mirror01.th.ifl.net precise/restricted i386 Packages
Hit http://mirror01.th.ifl.net precise/universe i386 Packages
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex    
Hit http://mirror01.th.ifl.net precise/multiverse i386 Packages      
Hit http://mirror01.th.ifl.net precise/main TranslationIndex         
Hit http://mirror01.th.ifl.net precise/multiverse TranslationIndex   
Hit http://mirror01.th.ifl.net precise/restricted TranslationIndex   
Hit http://mirror01.th.ifl.net precise/universe TranslationIndex     
Hit http://mirror01.th.ifl.net precise-updates/restricted Sources    
Hit http://mirror01.th.ifl.net precise-updates/main Sources          
Hit http://mirror01.th.ifl.net precise-updates/multiverse Sources    
Hit http://mirror01.th.ifl.net precise-updates/universe Sources      
Hit http://mirror01.th.ifl.net precise-updates/main i386 Packages    
Hit http://mirror01.th.ifl.net precise-updates/restricted i386 Packages
Hit http://mirror01.th.ifl.net precise-updates/universe i386 Packages
Hit http://mirror01.th.ifl.net precise-updates/multiverse i386 Packages
Hit http://mirror01.th.ifl.net precise-updates/main TranslationIndex
Hit http://mirror01.th.ifl.net precise-updates/multiverse TranslationIndex
Hit http://mirror01.th.ifl.net precise-updates/restricted TranslationIndex
Hit http://mirror01.th.ifl.net precise-updates/universe TranslationIndex
Hit http://mirror01.th.ifl.net precise-security/restricted Sources   
Hit http://mirror01.th.ifl.net precise-security/main Sources         
Hit http://mirror01.th.ifl.net precise-security/multiverse Sources   
Hit http://mirror01.th.ifl.net precise-security/universe Sources     
Hit http://mirror01.th.ifl.net precise-security/main i386 Packages   
Hit http://mirror01.th.ifl.net precise-security/restricted i386 Packages
Hit http://mirror01.th.ifl.net precise-security/universe i386 Packages
Hit http://mirror01.th.ifl.net precise-security/multiverse i386 Packages
Hit http://mirror01.th.ifl.net precise-security/main TranslationIndex
Hit http://mirror01.th.ifl.net precise-security/multiverse TranslationIndex
Hit http://mirror01.th.ifl.net precise-security/restricted TranslationIndex
Hit http://mirror01.th.ifl.net precise-security/universe TranslationIndex
Hit http://mirror01.th.ifl.net precise/main Translation-en_GB        
Hit http://mirror01.th.ifl.net precise/main Translation-en           
Hit http://mirror01.th.ifl.net precise/multiverse Translation-en_GB  
Hit http://mirror01.th.ifl.net precise/multiverse Translation-en     
Hit http://mirror01.th.ifl.net precise/restricted Translation-en_GB  
Hit http://mirror01.th.ifl.net precise/restricted Translation-en     
Hit http://mirror01.th.ifl.net precise/universe Translation-en_GB    
Hit http://mirror01.th.ifl.net precise/universe Translation-en
Hit http://mirror01.th.ifl.net precise-updates/main Translation-en_GB
Hit http://mirror01.th.ifl.net precise-updates/main Translation-en   
Hit http://mirror01.th.ifl.net precise-updates/multiverse Translation-en_GB
Hit http://mirror01.th.ifl.net precise-updates/multiverse Translation-en
Hit http://mirror01.th.ifl.net precise-updates/restricted Translation-en_GB
Hit http://mirror01.th.ifl.net precise-updates/restricted Translation-en
Hit http://mirror01.th.ifl.net precise-updates/universe Translation-en_GB
Hit http://mirror01.th.ifl.net precise-updates/universe Translation-en
Hit http://mirror01.th.ifl.net precise-security/main Translation-en  
Hit http://mirror01.th.ifl.net precise-security/multiverse Translation-en
Hit http://mirror01.th.ifl.net precise-security/restricted Translation-en
Hit http://mirror01.th.ifl.net precise-security/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_GB          
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_GB
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_GB
Ign http://archive.canonical.com precise/partner Translation-en
Reading package lists... Done
```What I noticed however, was that when I first installed Ubuntu (Lucid Lynx about 18months ago) it chose the standard **[FONT=Fixedsys][COLOR=Navy]archive.ubuntu.com[/COLOR][/FONT]** UK mirror.  This mirror updated regularly.  I had trouble with some patches not being available (I believe this may have been due to patches not being archived as they had later been reversed out).  The failure to check for updates only happened when I switched to **[FONT=Fixedsys][COLOR=Navy]mirror01.th.ifl.net[/COLOR][/FONT]**.
I can now install updates successfully, but I have to manually fetch the list!

I'm fairly sure that all the ppa repositories that I have ever used have been carefully removed ;)

---

### Post by rickhunt on 2012-11-02
I don't know if my problem falls in to this post or not, I am kind of having a similar problem, when I hit check for updates its only one repository that is failing. I get this message:

W:Failed to fetch [http://www.geekconnection.org/remastersys/repository/karmic/Sources](http://www.geekconnection.org/remastersys/repository/karmic/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

is that an old source? should I just remove that one?  I just bought this computer online, and it came with Ubuntu 12.04 installed, I did a bunch of updates the first day, and this error message is new to me.

It also says it has been 171 days since package info was updates, and to press check to update, when I press check I get that error message.

My current sources.lst is as follows:
___________________________________________________________________________
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
_____________________________________________________________________________

Are those current or should I have something different?

Thanks
Rick

---

### Post by peggysmouse on 2012-11-02
Hi Rick, I think you can safely delete those geekconnection sources. They are for a different version of Ubuntu. Then recheck for updates.

---

### Post by rickhunt on 2012-11-03
Hmmm, might need to download a fresh ISO, I tried to edit the sources.list file but it says it belongs to root and I don't have permission to edit it. Since the Ubuntu was installed when I bought the computer, I don't know what the root password is.

When I got the computer, the default administrator name was: user with a password of user, I changed both of those, but how do I switch to root user.

There is no option to log in as root.

Am I missing something?

I normally use PcLinux, so maybe I just don't know how to log in as root.

I tried opening a terminal and typing su, when it prompts for password, nothing seems to be the correct password.

I have only had this thing since the 31st of October, so if a fresh install is a good idea, i wont lose much, I haven't added much yet.

:-)

---

### Post by rickhunt on 2012-11-03
Ok, well I did figure out how to add a root login using the info found here
[http://www.liberiangeek.net/2012/05/login-as-root-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/05/login-as-root-in-ubuntu-12-04-precise-pangolin/)

By opening a terminal and typing

sudo passwd root
sudo sh -c 'echo "greeter-show-manual-login=true" >> /etc/lightdm/lightdm.conf'


So I was able to edit the sources.list file and now no error when checking for updates.

But I might still do a fresh install just so I know everything is good.

---

### Post by peggysmouse on 2012-11-03
RickHunt, there is really no need to uninstall. That source was for one specific piece of software from an old distribution that is no longer supported. You won't see any adverse affects from this. Just keep going!

---

### Post by X9Tim on 2012-11-05
@RickHunt
You should never be able to log in as root in Ubuntu.  You should (assuming you are allowed by the sudoers policy) be able to use [FONT=Courier New][COLOR=Blue]sudo[/COLOR][/FONT] as you clearly can from your previous post!

To spend a while logged in as root, you can use "[FONT=Courier New][SIZE=2][COLOR=Blue]sudo su[/COLOR][/SIZE][/FONT]" to actually be logged in as root, but this is not recommended.  I think the theory is that if you use [FONT=Courier New][COLOR=Blue]sudo[/COLOR][/FONT] to prefix every command that needs root permission, you will hopefully be reminded that what you are doing is potentially dangerous ;)

---

### Post by X9Tim on 2012-11-27
Here's a screenshot showing the problem a bit better!
The important bits are: "The package information was last updated 7 days ago"
and: "Automatically check for updates: Daily"

It clearly *hasn't* checked for updates for 7 days!!

[IMG]http://farm9.staticflickr.com/8206/8224021448_8d17bd48b8.jpg[/IMG]

---

### Post by X9Tim on 2013-01-04
bump!

---

### Post by Pjotr123 on 2013-01-04
Use the terminal instead:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by howefield on 2013-01-04
Was "Check for Updates" removed from the list of startup applications ?

---

### Post by peggysmouse on 2013-04-10
This issue resolved itself with recent updates. Anyone else?

---

