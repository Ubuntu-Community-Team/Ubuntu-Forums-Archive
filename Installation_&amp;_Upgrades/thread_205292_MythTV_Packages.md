---
title: "MythTV Packages?"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by GrammatonCleric on 2006-06-28
Where did all the mythtv packages go?   I recently had my mythtv box die, so I tried to rebuild it with dapper but ran into a ton of issues with MYSQL5, PHP5, nuvexport, the list goes on.  So I figured I would just reinstall BREEZY.  I have everything configured and ready to install MYTHTV but it appears that none of the repos have the mythtv packages.   Where did they go?

GC

---

### Post by Maggot on 2006-06-28
Not that this helps, but it's avail in dapper- Graphics (multi-universe)

---

### Post by GrammatonCleric on 2006-06-28
Thanks. =)   I had no idea that Breezy packages would be dropped like a hot potatoe...so fast.  I mean 80% of the Ubuntu MythTV how to's refer to Breezy.  I can see no longer building new packages but why remove the ones that are all ready built?

GC

---

### Post by Maggot on 2006-06-28
It still appears to be in the repository. Do you have them all enabled and refreshed?

---

### Post by GrammatonCleric on 2006-06-28
Yup...  I've enabled all the default repos and I've run apt-get update a couple hundred times.   I've even searched the repos with Synaptic searching for myth, mythtv, myt, etc...none of the mythtv packages are shown.   What repos are you using in your sources.list?  

GC

---

### Post by Maggot on 2006-06-28
I've got the default ones enabled.

I'm not sure how the repo's work but if you check out this:
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)

You'll see mythtv.

---

### Post by GrammatonCleric on 2006-06-28
I'll agree that the myth packages are listed in the Packages.gz file but they are not available.  Here's my sources.list

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) breezy main


Here I'm running an apt-get update...


root@apollo:/etc/apt# apt-get update
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) breezy Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) breezy Release                                  
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]                 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) breezy/main Packages                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [72.2kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [19.5kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [37.2kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Fetched 167kB in 2s (61.6kB/s)                      
Reading package lists... Done




Here's me running a apt-get install mythtv

root@apollo:/etc/apt# apt-get install mythtv
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mythtv


or apt-get install mythbrowser


root@apollo:/etc/apt# apt-get install mythbrowser
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mythbrowser



same is true for any of the following packages....

mythtv mythbrowser mythdvd mythgallery mythmusic mythnews mythvideo mythweather

---

