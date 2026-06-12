---
title: "No updates since 04-25-13... wired and unlikely.."
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by Lubelaczek on 2013-05-01
I did distr-upgrade from 12.10 to 13.04 on 04-25-2013 on my Asus G51JX-X1 with nvidia GeForce GTS360M. A looooooot of bugs since then: skype, nvidia, no sound etc. But I had hope that updates will fix some of them. However it is very strange that I don't get any updates since then. I did try few times manualy check for any fixes but it is saying that system is up to date. I don't think so... What could be a root of this. Repos? Any ideas?

---

### Post by ibjsb4 on 2013-05-01
What happens when you do

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

---

### Post by 2F4U on 2013-05-01
What mirror are you using? Try to change the mirror and see if you are then able to receive updates.

---

### Post by Lubelaczek on 2013-05-01
After apt-get update:

```
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring Release.gpg
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates Release.gpg               
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security Release.gpg              
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed Release.gpg              
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports Release.gpg             
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring Release                           
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates Release                   
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security Release                  
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed Release                  
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports Release                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/main Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/restricted Sources                
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/universe Sources                  
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/multiverse Sources                
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/main amd64 Packages               
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/restricted amd64 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/universe amd64 Packages  
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/multiverse amd64 Packages         
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/main i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                      
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/restricted i386 Packages          
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/universe i386 Packages            
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/multiverse i386 Packages          
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/main Translation-en               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/multiverse Translation-en         
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/restricted Translation-en         
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/universe Translation-en           
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/main Sources              
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/restricted Sources        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/universe Sources          
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/multiverse Sources        
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/main amd64 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages     
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/restricted amd64 Packages 
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/universe amd64 Packages   
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/multiverse amd64 Packages 
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/main i386 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages      
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/restricted i386 Packages  
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/universe i386 Packages    
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/multiverse i386 Packages  
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/main Translation-en       
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/multiverse Translation-en 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/restricted Translation-en 
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/universe Translation-en
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/main Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/restricted Sources       
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/universe Sources         
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/multiverse Sources       
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/main amd64 Packages      
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/restricted amd64 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/universe amd64 Packages  
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/multiverse amd64 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/main i386 Packages       
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/restricted i386 Packages 
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/universe i386 Packages   
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/multiverse i386 Packages 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/main Translation-en      
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages                 
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/restricted Translation-en
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/universe Translation-en  
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/restricted amd64 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/main amd64 Packages      
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/multiverse amd64 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/universe amd64 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/restricted i386 Packages 
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/main i386 Packages       
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/multiverse i386 Packages 
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/universe i386 Packages   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US                     
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/main Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                         
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/multiverse Translation-en
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/universe Translation-en  
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/restricted amd64 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/main amd64 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/multiverse amd64 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/universe amd64 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/restricted i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                          
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/main i386 Packages      
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/multiverse i386 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/universe i386 Packages
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/main Translation-en
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/multiverse Translation-en
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/restricted Translation-en
Hit [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_US  
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/multiverse Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/restricted Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring/universe Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/main Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/multiverse Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/restricted Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-updates/universe Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/main Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/multiverse Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/restricted Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-security/universe Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/main Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/restricted Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en       
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-proposed/universe Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/multiverse Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/restricted Translation-en_US
Ign [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) raring-backports/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Reading package lists... Done
```

And after apt-get upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Hard to believe that there are no updates for me. What am I missing?

I am located on Long Island and tried US servers and select best server option. No difference. Currently I am set on [http://ubuntu.mirror.constatnt.com](http://ubuntu.mirror.constatnt.com)

---

### Post by ibjsb4 on 2013-05-01
You have a mix of 12.10 and 13.04 sources.  Not good, lets have a look.  Please post the output of:

```
cat /etc/apt/sources.list
```

You got some hits on maverick too.

---

### Post by Lubelaczek on 2013-05-01
I realy appreciate your time. Here is result:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.mirror.constant.com/ raring main restricted
deb-src http://ubuntu.mirror.constant.com/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.mirror.constant.com/ raring-updates main restricted
deb-src http://ubuntu.mirror.constant.com/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.mirror.constant.com/ raring universe
deb-src http://ubuntu.mirror.constant.com/ raring universe
deb http://ubuntu.mirror.constant.com/ raring-updates universe
deb-src http://ubuntu.mirror.constant.com/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.mirror.constant.com/ raring multiverse
deb-src http://ubuntu.mirror.constant.com/ raring multiverse
deb http://ubuntu.mirror.constant.com/ raring-updates multiverse
deb-src http://ubuntu.mirror.constant.com/ raring-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main

deb http://ubuntu.mirror.constant.com/ raring-security main restricted
deb-src http://ubuntu.mirror.constant.com/ raring-security main restricted
deb http://ubuntu.mirror.constant.com/ raring-security universe
deb-src http://ubuntu.mirror.constant.com/ raring-security universe
deb http://ubuntu.mirror.constant.com/ raring-security multiverse
deb-src http://ubuntu.mirror.constant.com/ raring-security multiverse
deb http://archive.canonical.com/ raring partner
deb-src http://archive.canonical.com/ raring partner
deb http://ubuntu.mirror.constant.com/ raring-proposed restricted main multiverse universe
deb http://ubuntu.mirror.constant.com/ raring-backports restricted main multiverse universe


```

Where should I start to clean this mess?

---

### Post by ibjsb4 on 2013-05-01
Lets try a simple way of getting those unwanted sources removed.

Open up your software sources and go to "other software".

From there you should be able to either remove or just uncheck all unwanted quantal and maverick sources.  Then close software sources and update.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

---

### Post by Lubelaczek on 2013-05-01
I used Ubuntu Sources List Generator and replaced /etc/apt/sources.list with generated one...

242 megs is downloading right now. Thank you for leading me in right direction.

---

### Post by ibjsb4 on 2013-05-01
And thats another easy way to do it :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by darkod on 2013-05-01
Just to revert to your first post, dist-upgrade shouldn't upgrade you to 13.04 as far as I know. The dist-upgrade is just a better version of apt-get upgrade which regardless of how it sounds, doesn't upgrade the version, it only updates the packages.

The command to upgrade to a new release should be do-release-upgrade, not dist-upgrade.

Are you sure that command upgraded you to 13.04? Or maybe something else? Or maybe you are not even on 13.04?

---

### Post by grahammechanical on 2013-05-01
What if there are no updates? I have been using Raring Ringtail for months. Long before it was released. I ran a daily update but once the official release date arrived there were no more updates for at least the next three days. I cannot say beyond that because I then started using an install of 13.04 that I was converting to Saucy Salamander. It is just possible that there is nothing to update. It is unusual I know but perhaps more effort is being put into developing Saucy Salamander.

Regards.

---

