---
title: "Updates not working well."
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by gideond2 on 2014-05-25
I have a fresh install of Xubuntu 14.04 LTS on a desktop. I've installed the OS and all available updates Friday night. I've since gone through and done minor customization, mostly installing a few programs from the repos. When I shut down Friday night everything was fine. Saturday I couldn't run sudo apt-get update correctly. It kepts erroring out. Today It's working again but not correctly. This is the output I'm getting.

```
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                                                                                                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                                                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                                                                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                                                                                                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                                                                                                                         
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                                                                                       
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                                     
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                     
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                                                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US                  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security InRelease   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
```

I couldn't install anything without a timeout for a while. Now I can install but it takes forever. Running sudo apt-get upgrade takes a good 10 minutes even with no updates available. It seems to be hanging on most repos. Only the Extras repos process with no delay. Any input on where to start troubleshooting this? I thought it might be a server error, but changing servers makes no difference. I also can update fine on two Kubuntu installs I have on other computers.

---

### Post by QIII on 2014-05-25
Hello!

Could you explain what you mean by "error out"?  What error was appearing?

I just tried the us mirror and got a complete update in a few seconds.  Are you having connectivity/internet speed issues?

---

### Post by grahammechanical on 2014-05-25
Some of the repositories are clashing.

```
Ign http://archive.canonical.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty InRelease
```

Which archive/repository is Update Manager supposed to download from when there are two separate repositories containing the same packages? As Update Manager tries to sort out this confusion it uses up time before it finally gives up and marks the url as Ign (ignore). And of course, it cannot download updates from either of those archives.

You have to settle on one archive to update/install from and remove the other archives from Software and Updates.

Regards.

---

### Post by sammiev on 2014-05-25
I have been using and updating Xubuntu 14.04 LTS and have noticed known of that. grahammechanical has noticed something that maybe causing your errors. I have updated today as well.

---

### Post by gideond2 on 2014-05-25
I should have recorded the errors at the time but I didn't think it was anything major yet. Basically it was hanging at connecting to the archive entries. Maybe what grahammechanical noticed is the issue. I don't know how multiple archive entries got selected. I'll check it tomorrow when I'm back at the house with that computer. Other than updates there have been no connectivity issues with Firefox at all. I have some delay with Thunderbird but only with Gmail accounts so I think there is something screwy there. to deal with. Thanks for the input.

---

### Post by gideond2 on 2014-05-26
So I completely replaced the sources.list file with the one from my Kubuntu 14.04 LTS install. The only thing I changed was the CD source info. This file has worked perfectly moments before on my Kubuntu desktop. Same issues are still occurring on Xubuntu. 

Latest Update:
> Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                                                                                                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                                                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                                                                                                                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                                                                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                                                                                                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                                                                                                                         
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                                                                                       
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                                     
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                                         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                                                             
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                                                                                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                                                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                                                                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                                                             
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US                                                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                              
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]                                      
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [58.6 kB]                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en                                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                                                                                                                 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [41.8 kB]                                                                                                        
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]                                                                                                     
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [26.6 kB]                                                                                                    
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [2,234 B]                                                                                                  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [96.5 kB]                                                                                                  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]                                                                                              
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [67.4 kB]                                                                                             
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,273 B]                                                                                           
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [46.7 kB]                                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en                                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en                                                                                                       
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [32.0 kB]                                                                                            
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [14 B]                                                                                                        
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [14 B]                                                                                                  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [3,713 B]                                                                                                 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [768 B]                                                                                                 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [14 B]                                                                                                  
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]                                                                                            
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [3,608 B]                                                                                           
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [619 B]                                                                                           
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en [14 B]                                                                                                 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en [307 B]                                                                                          
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en [14 B]                                                                                           
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en [2,331 B]                                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                                                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US                                                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US                                                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US                                                                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US                                                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US                                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US                                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US                                                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US                                                                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US                                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US                                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US                                                                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                                                                                                                        
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58.5 kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [16.1 kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [4,212 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [687 B]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [47.7 kB]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [17.9 kB]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,404 B]
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [24.4 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [9,065 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US                                                                                                       
Fetched 632 kB in 10min 2s (1,048 B/s)                                                                                                                                          
Reading package lists... Done

sources.list file:
> # deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140416.2)]/ trusty main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

## Google Repositories
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates restricted main universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security restricted main universe multiverse

It looks like the canonical archives should only be for the partner repos yet the update still seems to be pulling from both for InRelease. I'm not sure where to fix this.

---

### Post by gideond2 on 2014-05-26
Here is where it hangs for about 10 minutes before continueing.

> Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                                                                                                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                                                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                                                                                                                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                                                                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                                                                                                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                                                                                                                         
93% [Connecting to us.archive.ubuntu.com (2001:67c:1562::13)] [Connecting to archive.canonical.com (2001:67c:1360:8c01::1b)] [Connecting to security.ubuntu.com (2001:67c:1562::

---

### Post by gideond2 on 2014-05-26
I've also tried changing the server and disabling the partner and independant repos.

> Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty InRelease
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports InRelease                                                     
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates InRelease                                                        
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-security InRelease                                                       
Get:1 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty Release.gpg [933 B]                                                    
Get:2 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports Release.gpg [933 B]                                                                      
Get:3 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates Release.gpg [933 B]                                                                         
Get:4 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-security Release.gpg [933 B]                                                                        
Get:5 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty Release [58.5 kB]                                                                                   
Get:6 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports Release [58.6 kB]                                                                      
Get:7 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates Release [58.5 kB]                                                                                                       
Get:8 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-security Release [58.5 kB]                                                                                                      
Get:9 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/restricted Sources [5,433 B]                                                                                                    
Get:10 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/main Sources [1,064 kB]                                                                                            
Get:11 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/universe Sources [6,399 kB]                                                                            
Get:12 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/multiverse Sources [174 kB]                                                                                                         
Get:13 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/main i386 Packages [1,348 kB]                                                                                                       
Get:14 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/restricted i386 Packages [13.4 kB]                                                                                                  
Get:15 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/universe i386 Packages [5,866 kB]                                                                                                   
Get:16 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/multiverse i386 Packages [134 kB]                                                                                                   
Get:17 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/main Translation-en [762 kB]                                                                                                        
Get:18 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/multiverse Translation-en [102 kB]                                                                                                  
Get:19 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/restricted Translation-en [3,457 B]                                                                                                 
Get:20 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/universe Translation-en [4,089 kB]                                                                                                  
Get:21 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/main Sources [14 B]                                                                                                       
Get:22 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/restricted Sources [14 B]                                                                                                 
Get:23 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/universe Sources [3,713 B]                                                                                                
Get:24 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/multiverse Sources [768 B]                                                                                                
Get:25 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/main i386 Packages [14 B]                                                                                                 
Get:26 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/restricted i386 Packages [14 B]                                                                                           
Get:27 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/universe i386 Packages [3,608 B]                                                                                          
Get:28 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/multiverse i386 Packages [619 B]                                                                                          
Get:29 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/main Translation-en [14 B]                                                                                                
Get:30 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/multiverse Translation-en [307 B]                                                                                         
Get:31 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/restricted Translation-en [14 B]                                                                                          
Get:32 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/universe Translation-en [2,331 B]                                                                                         
Get:33 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/restricted Sources [14 B]                                                                                                   
Get:34 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/main Sources [41.8 kB]                                                                                                      
Get:35 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/universe Sources [26.6 kB]                                                                                                  
Get:36 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/multiverse Sources [2,234 B]                                                                                                
Get:37 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/restricted i386 Packages [14 B]                                                                                             
Get:38 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/main i386 Packages [97.8 kB]                                                                                                
Get:39 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/universe i386 Packages [67.4 kB]                                                                                            
Get:40 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/multiverse i386 Packages [7,273 B]                                                                                          
Get:41 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/main Translation-en [48.0 kB]                                                                                               
Get:42 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/multiverse Translation-en [3,811 B]                                                                                         
Get:43 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/restricted Translation-en [14 B]                                                                                            
Get:44 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/universe Translation-en [32.0 kB]                                                                                           
Get:45 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-security/restricted Sources [14 B]                                                                                                  
Get:46 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-security/main Sources [16.0 kB]                                                                                                     
Get:47 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-security/universe Sources [4,212 B]                                                                                                 
Get:48 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-security/multiverse Sources [687 B]                                                                                                 
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/main Translation-en_US                                                                                                                 
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/multiverse Translation-en_US                                                                                                  
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/restricted Translation-en_US                                                                                                  
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty/universe Translation-en_US                                                                                                    
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/main Translation-en_US                                                                                              
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/multiverse Translation-en_US                                                                                        
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/restricted Translation-en_US                                                                                        
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-backports/universe Translation-en_US                                                                                          
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/main Translation-en_US                                                                                                
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/multiverse Translation-en_US                                                                                          
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/restricted Translation-en_US                                                                                          
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) trusty-updates/universe Translation-en_US                                                                                            
100% [Connecting to security.ubuntu.com (2001:67c:1562::13)] [Connecting to dl.google.com (2607:f8b0:400d:c06::be)]    

---

### Post by gideond2 on 2014-05-26
I've made some progress. I think I have it working after disabling ipv6. My router here is fully ipv6 compliant and I was evidently using ipv6. Disabling it seems to have fixed the issue. I'll post back when I've done some testing.

---

### Post by gideond2 on 2014-05-26
Okay I edited the sysctl.conf file to disable ipv6 and updates run fine. Upon reboot I have the same issue again. I have to disable ipv6 again. I'd like to do one of the following.
1) disable ipv6 permanently or
2) preferably get updated working with ipv6 enabled as it should be.

Maybe on a related note, Thunderbird also has issues with this. I've been having issues with Gmail IMAP taking forever to load. My Zoho servers have no issue. I have been completely unable to send from Gmail's SMTP, but again Zoho works fine. After disabling ipv6 Thunderbird is working fine with Gmail again. 

Any input on how to troublshoot the ipv6 problem?

---

### Post by gideond2 on 2014-05-27
Okay all is working now with ipv6 fully disabled. I had to edit the sysctl.conf file to disable ipv6. This worked until reboot when despite being disabled in sysctl.conf I still had issues. I had to run:
```
sudo sysctl -p
```
Then it would work right again. I finally had to edit the grub configuration to disable ipv6 at startup as well to get it working without issue. 

This isn't a big issue on the machine since it's just a temporary setup at the new house. However, what happens when I get my other Kubuntu computers over there? I'd rather not fully disable ipv6 since it the future of the internet. This is an old Pentium D computer I'm running and though I haven't checked the hardware my switch is detecting the LAN as 10/100 only. Could it just be the age of the hardware having issues?

---

