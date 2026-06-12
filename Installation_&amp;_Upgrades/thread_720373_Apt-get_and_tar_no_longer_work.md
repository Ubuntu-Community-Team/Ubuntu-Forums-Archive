---
title: "Apt-get and tar no longer work"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by jchysk on 2008-03-10
Hi.I'm running ubuntu 7.10
The problem that I'm having is when I try to install anything I get the error:
subprocess dpkg-deb --control returned error exit status 2

I searched through google for awhile and that found that other people have had the exact same problem, I just didn't find any solutions. 
I tried running 
apt-get -f
apt-get -f install
apt-get clean
dpkg-reconfigure dpkg
and a few other commands people suggested.
Whenever I try to open a tar.gz file I get Bus Error (core dumped) and I think this problem is related somehow, I'm pretty new to Linux in general so please don't think I've tried any obvious solutions or know what I'm doing at all.
From what I saw about this problem on other forums was that people just reinstalled the operating system. I'd really rather not have to do that since everything besides upgrade/installing packages seems to be working fine. Any help would be wonderful. Thanks.

---

### Post by taurus on 2008-03-10
Are you using x86 or x86_64?

Post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jchysk on 2008-03-10
just x86


sudo apt-get update:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US            
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                                                   
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                                
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Translation-en_US     
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty Release                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                                
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages                                    
  404 Not Found [IP: 91.189.88.31 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 4B in 0s (5B/s)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.



sudo apt-get upgrade:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  evolution evolution-common evolution-plugins tzdata
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/14.3MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg-deb: subprocess tar killed by signal (Bus error), core dumped
dpkg: error processing /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.10.1_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.10.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by taurus on 2008-03-10
Can you post your /etc/apt/sources.list because I see you have some real old Ubuntu release in your repos?

```
cat /etc/apt/sources.list
```

---

### Post by jchysk on 2008-03-10
Sure. These are the sites that all the apt-get install stuff comes from?


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty multiverse

---

### Post by NullHead on 2008-03-10
It sounds like you might have a bad stick of ram(AKA memory) 

Something similar happened to me a wile bad. I was running two 512mb sticks in dual channel DIMMS and when I would fill up one stick and it would start to use the other the system would crash. So I ram memtest and when the memtest would run for a few hours on the one working stick it would pass onto the broken one and it would find errors. I removed the faulty memory module and it worked just fine after that. 

Just an idea ... this doesn't mean you **do** have a bad stick it just is my idea that you *might* have one. 
 
btw I just bought another 1gb Buffalo memory stick and it all runs great again :D

---

### Post by jchysk on 2008-03-10
hmm..... i have 4 1gb sticks of crucial DDR2 1066 ram but only 3 gb show up which I'm assuming is because I'm running the operating system as 32-bit. I'll do a memtest on the ram later this evening because I'm sure that'll take a long time. Thanks for your reply.

---

### Post by NullHead on 2008-03-10
> **jchysk said:**
> hmm..... i have 4 1gb sticks of crucial DDR2 1066 ram but only 3 gb show up which I'm assuming is because I'm running the operating system as 32-bit. I'll do a memtest on the ram later this evening because I'm sure that'll take a long time. Thanks for your reply.

oh yes it will take a wile.... about 4 hours to get done with one 512mb stick. What I found to speed up the process is to do one stick at a time and let each run for at least an hour each, or you could just let them all run all night long witch ever you prefer. 

Hope you get it figured out!
NullHead

---

### Post by taurus on 2008-03-10
Did you add the last repo to your /etc/apt/sources.list?  You should consider either comment it out by placing a # in front of it or remove it from your /etc/apt/sources.list.

```
**[COLOR="Blue"]#[/COLOR]**deb http://archive.ubuntu.com/ubuntu warty multiverse
```
Save the change and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jchysk on 2008-03-10
I commented that line out and ran those commands, but I still have the same errors. 
I read somewhere that maybe I should try to install tar or dpkg manually. How would I go about doing that? I found tar_1.18-2ubuntu1_i386.deb and dpkg_1.14.16.6_1386.deb online but they both open in Package Installer which just fails to install anything.

---

### Post by mmgh73 on 2008-03-12
Hi there! I'm having the same problem with tzdata_2007k-0ubuntu0.7.10.1_all.deb
It looks like Ubuntu knows there is a new version for tzdata, but when it tryes to get it from the repository, it does not exist in the repository.  For me it is trying to get the package from 
[http://cl.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007k-0ubuntu0.7.10.1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007k-0ubuntu0.7.10.1_all.deb)
But if I navigate in that server, that version file is not there..  so the thing is that there is a new version for tzdata, but is not posted in the repository.
The following link show that the new version is done,and it relates about changing DST for Chile:
[https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/198129](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/198129)

Actually I need this update because I live in Chile!
Who can put the latest version of the tzdata in the repository in order to all works for us? 
Thank you for your help.
Regards,
Mauricio

---

### Post by NullHead on 2008-03-12
> **mmgh73 said:**
> Hi there! I'm having the same problem with tzdata_2007k-0ubuntu0.7.10.1_all.deb
It looks like Ubuntu knows there is a new version for tzdata, but when it tryes to get it from the repository, it does not exist in the repository.  For me it is trying to get the package from 
[http://cl.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007k-0ubuntu0.7.10.1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007k-0ubuntu0.7.10.1_all.deb)
But if I navigate in that server, that version file is not there..  so the thing is that there is a new version for tzdata, but is not posted in the repository.
The following link show that the new version is done,and it relates about changing DST for Chile:
[https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/198129](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/198129)

Actually I need this update because I live in Chile!
Who can put the latest version of the tzdata in the repository in order to all works for us? 
Thank you for your help.
Regards,
Mauricio

Have you searched [here]("http://packages.ubuntu.com/")? Thats where I could look.

---

### Post by mmgh73 on 2008-03-12
Hi NullHead!
I found the package in the MainServer instead of Chilean Server and it works fine now.
But I have a new question.. I've just realized that Martin Pitt said "2008k versions uploaded to -proposed. Please test.".. so, where can we get this 2008k version?
Regards,

Mauricio

---

### Post by NullHead on 2008-03-12
Perhaps he meant the hardy version [http://packages.ubuntu.com/hardy/tzdata](http://packages.ubuntu.com/hardy/tzdata)
Is that what you're looking for?

---

### Post by mmgh73 on 2008-03-12
I've just update to 2008a version.. I've jus enabled to update from "Pre-released updates (gutsy-proposed)", and I could download that version.
Thank you anyway :)

---

