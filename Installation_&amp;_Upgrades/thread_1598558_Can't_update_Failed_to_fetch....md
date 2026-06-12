---
title: "Can't update: Failed to fetch..."
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by Chaos-Energy on 2010-10-16
This night a yellow cone tray icon appeared, telling me that I can't update and should try it manually. So I open up the update manager and check for new updates only to be greeted by this:

```
Failed to download repository information

Check your internet connection

W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  Unable to find expected entry  contrib/binary-amd64/Packages in Meta-index file (malformed Release file?)
, W:Failed to fetch http://nl3.archive.ubuntu.com/ubuntu/dists/maverick/Release  Unable to find expected entry  contrib/source/Sources in Meta-index file (malformed Release file?)
, W:Failed to fetch http://nl3.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
, W:Failed to fetch http://nl3.archive.ubuntu.com/ubuntu/dists/maverick-security/Release  Unable to find expected entry  contrib/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

My internet connection is fine and I tried several other servers as well. (main server and two Belgian servers)

This is my sources.list:

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release Candidate amd64 (20100928)]/ maverick main restricted
deb-src http://nl3.archive.ubuntu.com/ubuntu/ maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl3.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://nl3.archive.ubuntu.com/ubuntu/ maverick contrib universe non-free multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates contrib restricted main non-free
deb-src http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates restricted non-free universe contrib main multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl3.archive.ubuntu.com/ubuntu/ maverick universe
deb http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl3.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

deb http://nl3.archive.ubuntu.com/ubuntu/ maverick non-free contrib

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://be.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://nl3.archive.ubuntu.com/ubuntu/ maverick-security main restricted
deb-src http://nl3.archive.ubuntu.com/ubuntu/ maverick-security restricted main multiverse universe #Added by software-properties
deb http://nl3.archive.ubuntu.com/ubuntu/ maverick-security universe
deb http://nl3.archive.ubuntu.com/ubuntu/ maverick-security multiverse
deb http://security.ubuntu.com/ubuntu/ maverick-security restricted contrib universe non-free main multiverse
deb-src http://nl3.archive.ubuntu.com/ubuntu/ maverick-security contrib non-free #Added by software-properties

```

And this is the result of aptitude update:

```
Hit http://nl3.archive.ubuntu.com maverick Release.gpg
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/contrib Translation-en                             
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/contrib Translation-en_US                          
Hit http://extras.ubuntu.com maverick Release.gpg                                                     
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                     
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                  
Hit http://ppa.launchpad.net maverick Release.gpg                                                     
Ign http://ppa.launchpad.net/alecive/antigone/ubuntu/ maverick/main Translation-en                    
Ign http://ppa.launchpad.net/alecive/antigone/ubuntu/ maverick/main Translation-en_US                 
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                             
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                          
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US                       
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/non-free Translation-en                            
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/non-free Translation-en_US                         
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                          
Hit http://extras.ubuntu.com maverick Release                                                         
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US                       
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                            
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                         
Hit http://ppa.launchpad.net maverick Release.gpg                                                     
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en  
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                                                     
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en                   
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en_US                
Hit http://ppa.launchpad.net maverick Release.gpg                                                     
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en                       
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en_US                    
Hit http://ppa.launchpad.net maverick Release                                                         
Hit http://nl3.archive.ubuntu.com maverick-updates Release.gpg                                        
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/contrib Translation-en                     
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/contrib Translation-en_US                  
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                        
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US                     
Hit http://ppa.launchpad.net maverick Release                                                         
Hit http://ppa.launchpad.net maverick Release                                                         
Hit http://extras.ubuntu.com maverick/main Sources                                                    
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                  
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US               
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/non-free Translation-en                    
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/non-free Translation-en_US                 
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                  
Hit http://ppa.launchpad.net maverick Release                                                         
Hit http://archive.canonical.com maverick Release.gpg                                                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                              
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US                           
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US               
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                    
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US                 
Hit http://nl3.archive.ubuntu.com maverick-security Release.gpg                                       
Hit http://extras.ubuntu.com maverick/main amd64 Packages                                             
Hit http://security.ubuntu.com maverick-security Release.gpg                                          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/contrib Translation-en            
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/contrib Translation-en_US         
Hit http://ppa.launchpad.net maverick/main Sources                                         
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                  
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US         
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en      
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US   
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en      
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US   
Hit http://archive.canonical.com maverick Release                                          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en               
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/non-free Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/non-free Translation-en_US      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en       
Hit http://ppa.launchpad.net maverick/main Sources                                       
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                  
Hit http://ppa.launchpad.net maverick/main Sources                                         
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                  
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en        
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US     
Hit http://nl3.archive.ubuntu.com maverick Release                                         
Hit http://nl3.archive.ubuntu.com maverick-updates Release                                 
Hit http://nl3.archive.ubuntu.com maverick-security Release                                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US       
Hit http://ppa.launchpad.net maverick/main Sources                                        
Hit http://archive.canonical.com maverick/partner amd64 Packages                          
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                 
Hit http://security.ubuntu.com maverick-security Release            
Hit http://nl3.archive.ubuntu.com maverick/main Sources             
Hit http://nl3.archive.ubuntu.com maverick/restricted Sources
Hit http://nl3.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://nl3.archive.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://nl3.archive.ubuntu.com maverick-security/main Sources
Hit http://nl3.archive.ubuntu.com maverick-security/multiverse Sources
Hit http://nl3.archive.ubuntu.com maverick-security/universe Sources

```

This is, as you can see, a Maverick Meerkat install and it was installed about a week ago. The update manager says the package information was last updated 7 days ago which means the last update was when it was installed I believe.

Any help is much appreciated. =)

---

### Post by mörgæs on 2010-10-17
I don't know much of aptitude, but how does it work when running

```
sudo apt-get update
sudo apt-get upgrade
```?

---

### Post by Chaos-Energy on 2010-10-18
apt-get update:

```
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/contrib Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/contrib Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/non-free Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/non-free Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Get:2 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/alecive/antigone/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/alecive/antigone/ubuntu/ maverick/main Translation-en_US
Get:3 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://nl3.archive.ubuntu.com maverick Release.gpg                         
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/contrib Translation-en      
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:4 http://security.ubuntu.com maverick-security Release [27.2kB]            
Hit http://extras.ubuntu.com maverick Release.gpg                              
Hit http://archive.canonical.com maverick Release                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/contrib Translation-en_US   
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/main Translation-en        
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US     
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en  
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/non-free Translation-en    
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/non-free Translation-en_US 
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en  
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en    
Get:5 http://ppa.launchpad.net maverick Release [39.8kB]                      
Get:6 http://ppa.launchpad.net maverick Release [39.8kB]                      
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US  
Get:7 http://nl3.archive.ubuntu.com maverick-updates Release.gpg [198B]        
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/contrib Translation-en
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/contrib Translation-en_US
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/non-free Translation-en
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/non-free Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                 
Hit http://ppa.launchpad.net maverick Release                                 
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:8 http://nl3.archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://nl3.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://nl3.archive.ubuntu.com maverick Release
Get:9 http://nl3.archive.ubuntu.com maverick-updates Release [31.4kB]
Get:10 http://nl3.archive.ubuntu.com maverick-security Release [27.2kB]
Hit http://archive.canonical.com maverick/partner amd64 Packages
Get:11 http://security.ubuntu.com maverick-security/restricted amd64 Packages [14B]
Get:12 http://ppa.launchpad.net maverick/main Sources [600B]              
Hit http://extras.ubuntu.com maverick/main Sources                             
Get:13 http://ppa.launchpad.net maverick/main amd64 Packages [624B]  
Hit http://extras.ubuntu.com maverick/main amd64 Packages                   
Get:14 http://ppa.launchpad.net maverick/main Sources [1,845B]       
Get:15 http://ppa.launchpad.net maverick/main amd64 Packages [3,885B]
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://nl3.archive.ubuntu.com maverick/main Sources
Hit http://nl3.archive.ubuntu.com maverick/restricted Sources
Get:16 http://nl3.archive.ubuntu.com maverick-updates/restricted Sources [14B]
Get:17 http://nl3.archive.ubuntu.com maverick-security/restricted Sources [14B]
Get:18 http://nl3.archive.ubuntu.com maverick-security/main Sources [3,835B]
Get:19 http://nl3.archive.ubuntu.com maverick-security/multiverse Sources [14B]
Get:20 http://nl3.archive.ubuntu.com maverick-security/universe Sources [912B]
Fetched 178kB in 0s (293kB/s)     
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  Unable to find expected entry  contrib/binary-amd64/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://nl3.archive.ubuntu.com/ubuntu/dists/maverick/Release  Unable to find expected entry  contrib/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch http://nl3.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch http://nl3.archive.ubuntu.com/ubuntu/dists/maverick-security/Release  Unable to find expected entry  contrib/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

apt-get upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  nautilus
The following packages will be upgraded:
  awoken-icon-theme libnautilus-extension1 nautilus-data
3 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 19.4MB of archives.
After this operation, 893kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/alecive/antigone/ubuntu/ maverick/main awoken-icon-theme all 1.4~ppa1~maverick2 [14.8MB]
Get:2 http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main libnautilus-extension1 amd64 1:2.32.0-0ubuntu6~ppa160 [65.3kB]
Get:3 http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main nautilus-data all 1:2.32.0-0ubuntu6~ppa160 [4,627kB]
Fetched 19.4MB in 7s (2,487kB/s)                                               
(Reading database ... 171509 files and directories currently installed.)
Preparing to replace awoken-icon-theme 1.3~ppa1~maverick2 (using .../awoken-icon-theme_1.4~ppa1~maverick2_all.deb) ...
Unpacking replacement awoken-icon-theme ...
Preparing to replace libnautilus-extension1 1:2.32.0-0ubuntu5~ppa140 (using .../libnautilus-extension1_1%3a2.32.0-0ubuntu6~ppa160_amd64.deb) ...
Unpacking replacement libnautilus-extension1 ...
Preparing to replace nautilus-data 1:2.32.0-0ubuntu5~ppa140 (using .../nautilus-data_1%3a2.32.0-0ubuntu6~ppa160_all.deb) ...
Unpacking replacement nautilus-data ...
Processing triggers for gconf2 ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for hicolor-icon-theme ...
Setting up awoken-icon-theme (1.4~ppa1~maverick2) ...
Setting up libnautilus-extension1 (1:2.32.0-0ubuntu6~ppa160) ...
Setting up nautilus-data (1:2.32.0-0ubuntu6~ppa160) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Upgrade seemed to upgrade some packages at least...

---

### Post by mörgæs on 2010-10-18
I can not tell for sure, but it might be worth changing server in Software Sources.

---

### Post by Chaos-Energy on 2010-10-19
I already tried several different servers. I just tried a couple more and still nothing changes.

Thanks though.

---

### Post by Chaos-Energy on 2010-10-20
Anyone else with any ideas? =/ I can't update and I can't install anything from Ubuntu Software Center. I also tried replacing my sources.list file with an old backup I made but it still gives the same error.

Could anyone update his or her sources.list file for 10.10, that might work?

EDIT: I fixed it by using the sources file from a classmate of mine, thanks anyway. =)

---

### Post by superm4n on 2010-10-21
could you share that list with us ?

:guitar:

---

### Post by KEBDARGE on 2010-10-21
I seem to have the same problem.
I am tryign to get from 10.04 to 10.10 but these errors prevent me from getting further.

---

### Post by jmw5098 on 2010-10-23
I have the same problem.  Tried many other sources and nothing works.

I have 64bit amd if that matters...

---

### Post by superm4n on 2010-10-23
I had this solved by running the following:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192

---

### Post by adampdx on 2010-10-25
Semi-newb who has had this same problem for week now. 
I have an AMD 64 system as well
The repository sources on my meerkat install will not update.
I've tried changing to many Pacific NW servers and the main US server.
I tried typing in the full apt key command too.
Nothing is fetching the main sources

---

### Post by mörgæs on 2010-10-26
What exactly is the error message, if you run for example **sudo apt-get update**?

---

### Post by RobbyHawkes on 2010-11-02
Bump! I'm trying to like 10.10, I really am..but I need to be able to update!!!

---

### Post by phubert28 on 2011-01-19
I'm running 64 bit Ubuntu 10.10 also.

I JUST ran into the same problem after I tried to install VIrtualBox 4.0.2.

Now, after trying to get a new key, when I enter "sudo apt-get ujpdate",  I'm getting this error message:

W:Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry  contrib/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Looks like it's going to torpedo ALL my updates!

---

### Post by gwi on 2011-01-20
I am having the same problem with the update manager trying to download Translation-nl.

```
W:Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-nl.bz2  Error reading from server. Remote end closed connection
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

When I put the URL ([http://nl.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-nl.bz2](http://nl.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-nl.bz2)) in the address bar of Firefox, the file is downloaded in less than a second.

Why can't the update manager download the file?

I tried chaning to another server several times, without any change. Always Translation-nl.bz2 fails to download.

If anyone knows where to put the file (or its contents Translation-nl), so that the update manager no longer tries to download it, that would be nice.

BTW: I am using 2.6.35-24-generic i686.

---

### Post by The-Organist on 2011-01-24
Exactly this issue.  It appears to be something to do with proxy authenticating...

---

### Post by phubert28 on 2011-01-24
I 'solved' my updates problem by deleting the VirtualBox source from my list of sources.

So now the rest of my updates are fine... I'll just have to forget updating VirtualBox until the problem is resolved, it seems.

...waiting for 11.04... ???

---

### Post by J0Eeoj on 2011-02-14
Hi, same problem. Tries to update an AMD system with Ubunut 10.4 to 10.10.

Got the following messages:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mu.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://mu.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

:rolleyes:

---

### Post by mörgæs on 2011-02-15
I believe that now is the time to switch to 10.04, not away from it. If your present system works well I see no reason to abandon it.


Anyway, if you want to upgrade and it fails, there can be several reasons.

Have you tried simply to wait a few hours and try again? Might be a temporary problem on server side.
Is the 10.04 system fully updated?

---

### Post by cncook001 on 2011-02-15
> **phubert28 said:**
> 
W:Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry  contrib/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.


When you add the deb link to Ubuntu it "helpfully" also adds an entry for "deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib " 

Remove the deb-src line and you should be able to load virtualbox.

Craig

---

### Post by Tercesje on 2011-05-28
could someone tell me why this works ?? (removing the deb-source line)

soory but i'm quite new to the ubuntu-stuff so forgive me if this is a stupid question yet i'd like to understand something when i do it in stead of simply copy pasting ;);)

---

### Post by creontu on 2011-05-29
Same problem here. I can confirm the same worked for me - removing the source entry makes my update work like a charm. 11.04 - natty.:KS

---

### Post by fbicknel on 2011-05-31
Just had a very similar problem with a routine update/upgrade:
```

Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libpam0g i386 1.1.1-4ubuntu2.2
  404  Not Found [IP: 91.189.88.140 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/main libpam0g i386 1.1.1-4ubuntu2.2
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/main libpam-modules i386 1.1.1-4ubuntu2.2
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/main libpam-runtime all 1.1.1-4ubuntu2.2
  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-4ubuntu2.2_i386.deb  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2.2_i386.deb  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2.2_all.deb  404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```Tried changing to 'Main Server' (above was 'Server for the United States' and had very similar errors but with different IPs.

So I tried finding the best server, which for me turned out to be linux.duke.edu.

Problem solved.

Perhaps something deleted those files from the two previous servers?

---

### Post by Solomoriah on 2011-05-31
> **fbicknel said:**
> Perhaps something deleted those files from the two previous servers?
Well, they should fix it... it's a pain.  I'm having the same problem with my systems.  Hopefully whoever is responsible will notice soon.

---

### Post by jerrrys on 2011-05-31
weird, just happen to me to.  has to switch to 'server for united states' to get a update.

---

### Post by haapsalu_sall on 2011-05-31
Same problem here. I tried sudo apt-get update and it looked like it got it (but did it install it?) but there are still updates that won't download.

I have two questions:

1. How do I remove the deb-src line?

2. How do I change servers?

I'm using Intel 32 bit. I have 10.10 dual booted with Windows 7 and I've done updates before today and they were fine.

---

### Post by jerrrys on 2011-05-31
> **haapsalu_sall said:**
> Same problem here. I tried sudo apt-get update and it looked like it got it (but did it install it?) but there are still updates that won't download.

I have two questions:

1. How do I remove the deb-src line?

2. How do I change servers?

I'm using Intel 32 bit. I have 10.10 dual booted with Windows 7 and I've done updates before today and they were fine.

go to 'software sources' in system>admin

---

### Post by jerrrys on 2011-05-31
more reports

[http://ubuntuforums.org/showthread.php?t=1772230](http://ubuntuforums.org/showthread.php?t=1772230)

---

### Post by haapsalu_sall on 2011-06-01
I changed servers, too, although I changed *from *all US Servers. When you click on the server drop down menu, there is a button to choose the best server.

Also, here is the documentation on how to add Software Sources to 10.10

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu%20Maverick%20Meerkat%2010.10](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu%20Maverick%20Meerkat%2010.10)

Got everything to download!

---

### Post by Solomoriah on 2011-06-01
As of this morning, it works for me.  Apparently they've got new packages out there.

---

### Post by softwareregisterac on 2011-08-11
commenting out

#deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib

and

apt-get update

worked for me.

Thanks to you all guys, the ones who provided the solution and the one who raised the problem in the post

Having Ubuntu has become an obsession

---

### Post by Freeangel_ on 2011-09-24
I have same problem ... With Ubuntu 11.04 64 bit.
Red icon on the panel and can't update 8 days.
Update manager said:
```

W:Failed to fetch http://archive.canonical.com/dists/natty/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```
```

# apt-get update
&#1030;&#1075;&#1085; http://dl.google.com stable InRelease
&#1030;&#1075;&#1085; http://archive.canonical.com natty InRelease                               
&#1030;&#1075;&#1085; http://extras.ubuntu.com natty InRelease                                   
&#1030;&#1075;&#1085; http://ppa.launchpad.net natty InRelease                                   
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty InRelease                               
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates InRelease                       
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security InRelease                        
&#1054;&#1090;&#1088;:1 http://dl.google.com stable Release.gpg [198 B]                          
&#1042; &#1082;&#1077;&#1096;&#1110; http://extras.ubuntu.com natty Release.gpg                              
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty Release.gpg                          
&#1042; &#1082;&#1077;&#1096;&#1110; http://ppa.launchpad.net natty Release.gpg                              
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security Release.gpg                   
&#1054;&#1090;&#1088;:2 http://dl.google.com stable Release [1*347 B]                            
&#1042; &#1082;&#1077;&#1096;&#1110; http://extras.ubuntu.com natty Release                                  
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates Release.gpg                  
&#1042; &#1082;&#1077;&#1096;&#1110; http://ppa.launchpad.net natty Release                                  
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security Release                       
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty Release                              
&#1042; &#1082;&#1077;&#1096;&#1110; http://extras.ubuntu.com natty/main Sources                             
&#1042; &#1082;&#1077;&#1096;&#1110; http://ppa.launchpad.net natty/main Sources                             
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security/main Sources                  
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates Release                      
&#1042; &#1082;&#1077;&#1096;&#1110; http://extras.ubuntu.com natty/main amd64 Packages                      
&#1030;&#1075;&#1085; http://extras.ubuntu.com natty/main TranslationIndex                       
&#1042; &#1082;&#1077;&#1096;&#1110; http://ppa.launchpad.net natty/main amd64 Packages                      
&#1030;&#1075;&#1085; http://ppa.launchpad.net natty/main TranslationIndex                       
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security/restricted Sources            
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security/universe Sources              
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security/multiverse Sources            
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security/main amd64 Packages           
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security/restricted amd64 Packages     
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/main Sources                         
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/restricted Sources                   
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/universe Sources                     
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/multiverse Sources                   
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/main amd64 Packages                  
&#1030;&#1075;&#1085; http://archive.canonical.com natty InRelease                               
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security/universe amd64 Packages       
&#1042; &#1082;&#1077;&#1096;&#1110; http://security.ubuntu.com natty-security/multiverse amd64 Packages     
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/main TranslationIndex            
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/multiverse TranslationIndex      
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/restricted TranslationIndex      
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/universe TranslationIndex        
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/restricted amd64 Packages            
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/universe amd64 Packages              
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/multiverse amd64 Packages            
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/main TranslationIndex                   
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/multiverse TranslationIndex             
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/restricted TranslationIndex             
&#1042; &#1082;&#1077;&#1096;&#1110; http://archive.canonical.com natty Release.gpg                          
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/universe TranslationIndex               
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates/main Sources                 
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates/restricted Sources           
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates/universe Sources             
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates/multiverse Sources           
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates/main amd64 Packages          
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates/restricted amd64 Packages    
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates/universe amd64 Packages      
&#1042; &#1082;&#1077;&#1096;&#1110; http://archive.canonical.com natty Release.gpg                          
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty-updates/multiverse amd64 Packages    
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/main TranslationIndex           
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/restricted TranslationIndex     
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/universe TranslationIndex       
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/main Translation-uk                  
&#1042; &#1082;&#1077;&#1096;&#1110; http://archive.canonical.com natty Release                              
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/multiverse Translation-uk            
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/restricted Translation-uk            
&#1042; &#1082;&#1077;&#1096;&#1110; http://ua.archive.ubuntu.com natty/universe Translation-uk              
&#1042; &#1082;&#1077;&#1096;&#1110; http://archive.canonical.com natty Release                              
&#1042; &#1082;&#1077;&#1096;&#1110; http://archive.canonical.com natty/partner amd64 Packages               
&#1030;&#1075;&#1085; http://archive.canonical.com natty/partner TranslationIndex                
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/main Translation-uk_UA           
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/main Translation-uk              
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/main Translation-en              
&#1030;&#1075;&#1085; http://extras.ubuntu.com natty/main Translation-uk_UA                      
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/multiverse Translation-uk_UA     
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/multiverse Translation-uk        
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/multiverse Translation-en        
&#1030;&#1075;&#1085; http://extras.ubuntu.com natty/main Translation-uk                         
&#1030;&#1075;&#1085; http://extras.ubuntu.com natty/main Translation-en                         
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/restricted Translation-uk_UA     
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/restricted Translation-uk        
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/restricted Translation-en        
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/universe Translation-uk_UA       
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/universe Translation-uk          
&#1030;&#1075;&#1085; http://security.ubuntu.com natty-security/universe Translation-en          
&#1030;&#1075;&#1085; http://ppa.launchpad.net natty/main Translation-uk_UA                      
&#1030;&#1075;&#1085; http://ppa.launchpad.net natty/main Translation-uk                         
&#1030;&#1075;&#1085; http://ppa.launchpad.net natty/main Translation-en                         
&#1030;&#1075;&#1085; http://archive.canonical.com natty/partner Translation-uk_UA               
&#1030;&#1075;&#1085; http://archive.canonical.com natty/partner Translation-uk                  
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/main Translation-uk_UA                  
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/main Translation-en                     
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/multiverse Translation-uk_UA            
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/multiverse Translation-en               
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/restricted Translation-uk_UA            
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/restricted Translation-en               
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/universe Translation-uk_UA              
&#1030;&#1075;&#1085; http://archive.canonical.com natty/partner Translation-en                  
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty/universe Translation-en                 
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/main Translation-uk_UA          
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/main Translation-uk             
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/main Translation-en             
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/multiverse Translation-uk_UA
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/multiverse Translation-uk
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/multiverse Translation-en
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/restricted Translation-uk_UA
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/restricted Translation-uk
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/restricted Translation-en
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/universe Translation-uk_UA
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/universe Translation-uk         
&#1030;&#1075;&#1085; http://ua.archive.ubuntu.com natty-updates/universe Translation-en         
&#1054;&#1090;&#1088;:3 http://dl.google.com stable/main amd64 Packages [1*174 B]                
&#1030;&#1075;&#1085; http://dl.google.com stable/main TranslationIndex                          
&#1030;&#1075;&#1085; http://dl.google.com stable/main Translation-uk_UA                         
&#1030;&#1075;&#1085; http://dl.google.com stable/main Translation-uk                            
&#1030;&#1075;&#1085; http://dl.google.com stable/main Translation-en                            
&#1054;&#1090;&#1088;&#1080;&#1084;&#1072;&#1085;&#1086; 2*719 B &#1079;&#1072; 10sB (263 B/s)                                             
W: &#1053;&#1077; &#1074;&#1076;&#1072;&#1083;&#1086;&#1089;&#1103; &#1079;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1080;&#1090;&#1080; http://archive.canonical.com/dists/natty/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Do anybody know how to fix this?

---

### Post by mörgæs on 2011-09-24
Hi, welcome to the fora.

Have you tried the suggestions mentioned in this thread?
If yes, which result did you get?

---

### Post by Freeangel_ on 2011-09-25
I tried change download servers from UK to Main or US but got same problem.
Only removing "main" source solve this problem, but when I remove it I saw no updates.

And I still has problem with updates ....

PS: All updates before this 8 days was successfull.

---

### Post by mörgæs on 2011-09-25
Please post your /etc/apt/sources.list

---

### Post by Freeangel_ on 2011-09-30
/etc/apt/sources.list

```

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
deb-src http://ua.archive.ubuntu.com/ubuntu/ natty main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ua.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://ua.archive.ubuntu.com/ubuntu/ natty multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ua.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://ua.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ua.archive.ubuntu.com/ubuntu/ natty universe
deb http://ua.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ua.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://ua.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ua.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://ua.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://ua.archive.ubuntu.com/ubuntu/ natty-security main restricted
deb-src http://ua.archive.ubuntu.com/ubuntu/ natty-security restricted main multiverse universe #Added by software-properties
deb http://ua.archive.ubuntu.com/ubuntu/ natty-security universe
deb http://ua.archive.ubuntu.com/ubuntu/ natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://archive.canonical.com/ natty main
deb-src http://archive.canonical.com/ natty main

```

---

### Post by juniord2016 on 2011-10-26
Dear readers
   Hello, I have this very same problem. I'm trying to step from 10.04 to 10.10 but I can't. In the update installer it says cannot fetch file, check internet connection but I'm pretty sure nothing is wrong with my wifi. Today my computer suddenly locked, when I logged in, The screen was much different. It was like the older versions. I restarted quite sometime and nothing changed till I went to display and keep switching from a  type to another. My battery indicator is also missing. That's one thing that makes me think something has changed. In system settings, it looks different now. Buttons are rectangular instead of curved rectangular. PLease help me with this. My log in screen is rather blue than orange theme. Please help me with this. Thank you

---

### Post by mörgæs on 2011-10-26
A lot of problems with this installation...

If you are new to Ubuntu it is often the fastest solution to reinstall, when you have a number of separate errors.

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

---

### Post by NetJunky on 2013-01-16
Guys, have same problem. I'm using Ubuntu 10.10. Did anyone found a solution to this problem. I'm using Server version, so no GUI.

---

### Post by lisati on 2013-01-16
From the forum code of conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Thread closed.

---

