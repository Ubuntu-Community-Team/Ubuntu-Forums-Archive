---
title: "Update Manager Issue?"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaoc223 on 2010-03-24
I have noticed that in the past 24 hours when I do an update via update manager, or sudo apt-get update, the English translation sources are failing or taking a long time to hit. Anyone else noticing this or is it just me? my apt/sources.list file seems to be ok. I added launchpads ppa, and google code, but update is not hanging on these, it's the English translation sources from Ubuntu, and some of the security sources from Ubuntu.

---

### Post by _h_ on 2010-03-24
I'm not having any issues here, all hits via apt-get update are instant.

---

### Post by jaoc223 on 2010-03-24
_h_ I don't know what's going on with it. it seemed to be ok yesterday evening. The only thing I can think of is I installed google desktop search bar adding the google code, and launchpad ppa is in my sources.list, but as I said it's not hanging on these. Puzzling.

---

### Post by jaoc223 on 2010-03-24
Here's what I'm getting

jaco@ubuntu:~$ sudo apt-get update
[sudo] password for jaco: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]
Get:4 [http://dl.google.com](http://dl.google.com) stable/main Packages [920B]
Fetched 4,659B in 2min 0s (39B/s)                                              
Reading package lists... Done
jaco@ubuntu


Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
98% [Waiting for headers]  

It's hung on waiting for headers, what does that mean eactly

---

### Post by cheapsaket on 2010-03-24
I also saw the same behavior a couple of days back.
It got stuck at the headers with 99% completion.
It takes about two minutes to timeout.

---

### Post by jaoc223 on 2010-03-24
Am I getting these ignore errors because of software updates I did, or from adding launchpad ppa? do I need to have launchpad ppa? do I need to have backports enabled? man I'm screwing up my sources.list file trying to get this straight, or will it sort itself out? any help would be greatly appreciated.

---

### Post by philinux on 2010-03-24
Try changing your server.

---

### Post by jaoc223 on 2010-03-24
Can someone please help me sort out my sources.list file? Here is how mine looks like now:

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed main restricted universe 
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe 
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed main restricted universe multiverse 
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################


#deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) lucid main
#deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) lucid main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

---

### Post by jaoc223 on 2010-03-24
Phil should change from US server to main server? thanks

---

### Post by jaoc223 on 2010-03-24
I apologize for being so redundant about this, but this is really bugging me, I don't want to have to reinstall to get this sorted out. My sources.list file is screwed and I'm getting all these ignore lines when doing apt-get update:

jaco@ubuntu:~$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]
Ign [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) lucid/main Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]
Ign [http://ppa.launchpad.net/tualatrix/ubuntu/](http://ppa.launchpad.net/tualatrix/ubuntu/) lucid/main Translation-en_US
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B] 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [37.1kB]
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [37.1kB]                
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages [1,375kB]                 
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [2,632B]                   
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources [1,179B]                    
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [966B]                     
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources [3,179B]                    
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages [6,222B]            
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages [5,539kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages [194kB]             
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources [651kB]                    
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources [3,768B]             
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources [3,183kB]              
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources [118kB]              
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages [14B]            
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages [14B]      
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages [14B]        
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages [14B]      
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources [14B]             
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources [14B]       
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources [14B]         
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources [14B]       
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [14B]             
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [14B]       
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [14B]         
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [14B]       
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [14B]              
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [14B]        
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources [14B]          
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources [14B]        
Fetched 11.4MB in 18s (619kB/s)                                                
Reading package lists... Done

I don't understand what all the Translation-en_US stuff is all about.

---

### Post by jaoc223 on 2010-03-24
Here's my new sources.list it's all screwed up. Could maybe someone post a good list to use?

###### Ubuntu Main Repos
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 

# Chromium Project - [http://code.google.com/chromium/](http://code.google.com/chromium/)
## Run this command: sudo apt-key adv --keyserver #keyserver.ubuntu.com --recv-keys 4E5E17B5
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main

# Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) lucid main

# Chromium Project (Source) - [http://code.google.com/chromium/](http://code.google.com/chromium/)
## Run this command: sudo apt-key adv --keyserver #keyserver.ubuntu.com --recv-keys 4E5E17B5
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main

# Mozilla Daily Build Team (Source) - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver #keyserver.ubuntu.com --recv-keys  247510BE
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main

---

### Post by _h_ on 2010-03-24
What bit version of lucid do you run?

---

### Post by libihero on 2010-03-24
i got the same problem, but its been like that since karmic for me

---

### Post by jaoc223 on 2010-03-24
> **_h_ said:**
> What bit version of lucid do you run?

I'm using lucid 10.04 beta1

---

### Post by _h_ on 2010-03-24
> **jaoc223 said:**
> I'm using lucid 10.04 beta1

Yes I know this, what BIT are you using ....32 or 64 bit?

---

### Post by Fred the Penguin on 2010-03-24
I have the exact same problem. I am using 32 bit.

---

### Post by _h_ on 2010-03-24
Errr yea....scratch that last question. LOL I don't know what I was thinking...

By the way, here's my sources list. Disregard the getdeb repo. :P


```
# deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta amd64 (20100318)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.getdeb.net/ubuntu karmic-getdeb games
```

And uh, my hit list:

```
daniel@daniel-laptop:~$ sudo apt-get update
[sudo] password for daniel: 
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://archive.getdeb.net karmic-getdeb Release.gpg              
Ign http://archive.getdeb.net/ubuntu/ karmic-getdeb/games Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                
Hit http://us.archive.ubuntu.com lucid Release                       
Hit http://archive.getdeb.net karmic-getdeb Release                            
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://archive.getdeb.net karmic-getdeb/games Packages                     
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
daniel@daniel-laptop:~$ 
```

---

### Post by jaoc223 on 2010-03-24
> **_h_ said:**
> Yes I know this, what BIT are you using ....32 or 64 bit?

Using 32 bit here _h_

---

### Post by emarkay on 2010-03-25
32 bit here.

I see this occasionally, and know 2 things, IMHO:

1. It's Beta.

2. There are maybe 2 to 4 times the amount of users and testers requesting updates on this release.

This more than average amounts of data to send and more then average amounts of data requested.

---

### Post by Fred the Penguin on 2010-03-29
I just switched back to Karmic with a fresh install. The list loaded fine for me at first, but when I added this line to my sources list: 
[INDENT]deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free


The problem came back. I think that adding certain sources might cause this. I don't know if it is this source that is the problem.

[/INDENT]

---

### Post by SRabbelier on 2010-03-30
This is a known-issue with the Google update site, see [0], a workaround is available, (use
sudo apt-get -o Acquire::http::Pipeline-Depth=0 update

), but they hope to resolve it soon.

[0] [http://code.google.com/p/chromium/issues/detail?id=38608](http://code.google.com/p/chromium/issues/detail?id=38608)

---

