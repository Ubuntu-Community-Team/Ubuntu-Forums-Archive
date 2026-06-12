---
title: "Have internt but no apt or synaptic"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by steve_waters on 2008-02-01
OK so this is very strange,

I can connect to the internet and surf around nice quick. 

I can not however connect to any repositories and or update my software lists using apt, synaptic or Add/Remove. 

I have tried various source lists but still no go, I can go to "Software Sources" and make it select the best mirror for me which it does, but still no go can not download any packages. .

Any ideas, all connections either time out or can not be found.

See below for dump of Add/Remove Errors:

[http://mirror.optus.net/ubuntu/dists/gutsy/Release.gpg](http://mirror.optus.net/ubuntu/dists/gutsy/Release.gpg)
[http://mirror.optus.net/ubuntu/dists/gutsy/main/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy/main/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy/restricted/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy/restricted/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy/universe/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy/universe/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy-updates/Release.gpg](http://mirror.optus.net/ubuntu/dists/gutsy-updates/Release.gpg)
[http://mirror.optus.net/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy-security/Release.gpg](http://mirror.optus.net/ubuntu/dists/gutsy-security/Release.gpg)
[http://mirror.optus.net/ubuntu/dists/gutsy-security/main/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy-security/main/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_AU.bz2)
[http://mirror.optus.net/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_AU.bz2](http://mirror.optus.net/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_AU.bz2)

---

### Post by PmDematagoda on 2008-02-01
Post the output of:-
```
cat /etc/apt/sources.list
```

Also, could you answer one question, are you behind a proxy?

---

### Post by zvacet on 2008-02-01
Try with main server,because I tryed that links and they didn´t work for me.If you have no luck with this solution follow **PmDematagoda** advice.

---

### Post by kzkirill on 2008-02-01
Hi there .
I have the same problem - all connections time out.
It also fails to update from the CDROM.
I used the sites that come with the installation and also some gb. sites.
Was there an answer in this thread? I can't see any.
Thank you, everyone.
Kirill.

---

### Post by forestpixie on 2008-02-01
I've been having some problems with the gb server as well - changing to main server made a difference eventually - but I think it's an aol problem now

removing medibuntu once I'd got what I needed helped some as well

is you're sources list as it gets installed - have you checked the repos you're using

---

### Post by kzkirill on 2008-02-01
I am new to Linux, so : What is the address of the main site? And what is medibuntu? I checked the sites from the original list - I can reach them by Firefox. So it is probabaly not an Internet problem.
Thanks.

---

### Post by zvacet on 2008-02-01
@ **kzkirill**

To be sure that you have all repos open go to the system>admin>software sources>chek akk boxes under Ubuntu software tab and under updates tab.Ehen you open software sources window you will see at the bottom box where you may choose wich server to use.Select main.Reload.

---

### Post by oldos2er on 2008-02-01
Medibuntu info: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by steve_waters on 2008-02-02
Ok,

Switching software sources to the main server did help either, still can not get out. Below is previous source.list file. 

Email is not coming in now, I know my email server is up as it comes form my other laptop. This is very strange.

No proxy here, other computer updating and downloading email. Puzzling as my internet is flying on this computer but no other internet activity seems to work.

 

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.optus.net/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.optus.net/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirror.optus.net/ubuntu/ gutsy universe
deb http://mirror.optus.net/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.optus.net/ubuntu/ gutsy multiverse
deb http://mirror.optus.net/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://mirror.optus.net/ubuntu/ gutsy-security main restricted
deb http://mirror.optus.net/ubuntu/ gutsy-security universe
deb http://mirror.optus.net/ubuntu/ gutsy-security multiverse
```

---

### Post by steve_waters on 2008-02-02
```
http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_AU.bz2: Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_AU.bz2: Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_AU.bz2: Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_AU.bz2
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_AU.bz2
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_AU.bz2
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_AU.bz2
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_AU.bz2
http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_AU.bz2: Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_AU.bz2
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_AU.bz2
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_AU.bz2
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_AU.bz2

```

Above is latest error messages, do you think it has something to do with the:

```
........../Translation-en_AU.bz2
```

Is it looking for an Australian translation of the archive?

Thanks,
Steve

---

### Post by zvacet on 2008-02-02
This one looks like trouble maker

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)

I think if this one doesn´t work anything else will.It is very strange situation(I know that is no comfort to you).Try 

```
sudo apt-get update && sudo apt-get upgrade
```

Just to refresh your source list.If even that doesn´t help try [this](http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories) source list.

---

### Post by erfahren on 2008-02-02
steve - do you have Ubuntu set up in another language?
if not you can try this sources.list - I have it set up for Australia

first - back up your current 
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_back

```
then open your current one with root permissions
```

gksudo gedit /etc/apt/sources.list

```
select all and replace with this - then save it
```

## CD-ROM
## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Uncomment deb-src if you wish to download the source packages

deb http://au.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse 
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted 
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted 
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted 

## START -- MANUALLY ADDED
##

## CANONICAL REPOSITORY
deb http://archive.canonical.com/ubuntu gutsy partner

## BACKPORTS REPOSITORY
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse

## THIRD-PARTY REPOSITORIES
##
## MEDIBUNTU  
deb http://packages.medibuntu.org/ gutsy free non-free

```
then add the key for the Medibuntu repo and update
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
see if that helps

---

### Post by steve_waters on 2008-02-04
Still out on the net but no apt-get working. Email is intermittant, the only thing that works 100% is intenet well Firefox.

I am going to try some wget downloads tonight and see how I go.

But form my thinking it should not be a hardware issue as I am able to surf the web and download things, which means http must be working thus theoretically apt-get should be working to.

Maybe will also try and surf to one of the repos and see what happens, running out of ideas.

keep having fun....................
steve

---

### Post by steve_waters on 2008-02-05
So I managed to get:

Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [2718B] 

But none of the other ones will come down, I can get them from other laptop so I would not think it is a AAPT problem.

```
Get:1 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Ign http://packages.medibuntu.org gutsy/free Translation-en_AU                 
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_AU             
Ign http://archive.ubuntu.com gutsy Release.gpg                                
Ign http://archive.ubuntu.com gutsy-backports Release.gpg                      
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_AU           
Ign http://security.ubuntu.com gutsy-security Release.gpg                      
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_AU       
Ign http://security.ubuntu.com gutsy-security/main Translation-en_AU           
Ign http://archive.canonical.com gutsy Release.gpg                             
Ign http://archive.canonical.com gutsy/partner Translation-en_AU               
Ign http://au.archive.ubuntu.com gutsy Release.gpg                             
Ign http://au.archive.ubuntu.com gutsy/main Translation-en_AU                  
Ign http://au.archive.ubuntu.com gutsy/universe Translation-en_AU              
Get:2 http://packages.medibuntu.org gutsy Release [2718B]                      
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_AU     
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_AU       
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_AU     
Ign http://archive.ubuntu.com gutsy Release                                    
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_AU     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_AU     
Ign http://security.ubuntu.com gutsy-security Release                          
Ign http://archive.canonical.com gutsy Release                                 
Ign http://au.archive.ubuntu.com gutsy/restricted Translation-en_AU            
Ign http://au.archive.ubuntu.com gutsy/multiverse Translation-en_AU            
Ign http://au.archive.ubuntu.com gutsy-updates Release.gpg                     
Ign http://au.archive.ubuntu.com gutsy-updates/universe Translation-en_AU      
Ign http://au.archive.ubuntu.com gutsy-updates/main Translation-en_AU          
Ign http://au.archive.ubuntu.com gutsy-updates/multiverse Translation-en_AU    
Ign http://au.archive.ubuntu.com gutsy-updates/restricted Translation-en_AU    
Ign http://au.archive.ubuntu.com gutsy Release                                 
Ign http://archive.ubuntu.com gutsy-backports Release                          
Ign http://packages.medibuntu.org gutsy/free Packages                          
Ign http://security.ubuntu.com gutsy-security/universe Packages                
Ign http://archive.canonical.com gutsy/partner Packages                        
Ign http://au.archive.ubuntu.com gutsy-updates Release                         
Ign http://archive.ubuntu.com gutsy/main Sources                               
Ign http://archive.ubuntu.com gutsy/restricted Sources                         
Ign http://packages.medibuntu.org gutsy/non-free Packages                      
Ign http://security.ubuntu.com gutsy-security/main Packages                    
Ign http://security.ubuntu.com gutsy-security/multiverse Packages              
Ign http://security.ubuntu.com gutsy-security/restricted Packages              
Ign http://security.ubuntu.com gutsy-security/universe Sources                 
Err http://archive.canonical.com gutsy/partner Packages                        
  404 Not Found
Ign http://au.archive.ubuntu.com gutsy/main Packages                           
Ign http://au.archive.ubuntu.com gutsy/universe Packages                       
Ign http://au.archive.ubuntu.com gutsy/restricted Packages                     
Ign http://au.archive.ubuntu.com gutsy/multiverse Packages                     
Ign http://au.archive.ubuntu.com gutsy/main Sources                            
Ign http://archive.ubuntu.com gutsy-backports/main Packages                    
Ign http://archive.ubuntu.com gutsy-backports/restricted Packages              
Ign http://archive.ubuntu.com gutsy-backports/universe Packages                
Ign http://archive.ubuntu.com gutsy-backports/multiverse Packages              
Get:3 http://packages.medibuntu.org gutsy/free Packages [5885B]                
Ign http://archive.ubuntu.com gutsy-backports/main Sources                     
Ign http://archive.ubuntu.com gutsy-backports/restricted Sources               
Ign http://archive.ubuntu.com gutsy-backports/universe Sources                 
Ign http://archive.ubuntu.com gutsy-backports/multiverse Sources               
Ign http://security.ubuntu.com gutsy-security/main Sources                     
Ign http://security.ubuntu.com gutsy-security/multiverse Sources               
Ign http://security.ubuntu.com gutsy-security/restricted Sources               
Err http://security.ubuntu.com gutsy-security/universe Packages                
  404 Not Found
Ign http://au.archive.ubuntu.com gutsy/universe Sources                        
Ign http://au.archive.ubuntu.com gutsy/restricted Sources                      
Ign http://au.archive.ubuntu.com gutsy/multiverse Sources                      
Ign http://au.archive.ubuntu.com gutsy-updates/universe Packages               
Ign http://au.archive.ubuntu.com gutsy-updates/main Packages                   
Ign http://au.archive.ubuntu.com gutsy-updates/multiverse Packages             
Ign http://au.archive.ubuntu.com gutsy-updates/restricted Packages             
Get:4 http://packages.medibuntu.org gutsy/non-free Packages [2979B]            
Err http://archive.ubuntu.com gutsy/main Sources                               
  404 Not Found
Err http://archive.ubuntu.com gutsy/restricted Sources               
  404 Not Found
Err http://archive.ubuntu.com gutsy-backports/main Packages          
  404 Not Found
Err http://archive.ubuntu.com gutsy-backports/restricted Packages    
  404 Not Found
Err http://archive.ubuntu.com gutsy-backports/universe Packages      
  404 Not Found
Err http://security.ubuntu.com gutsy-security/main Packages          
  404 Not Found
Err http://security.ubuntu.com gutsy-security/multiverse Packages    
  404 Not Found
Err http://security.ubuntu.com gutsy-security/restricted Packages    
  404 Not Found
Ign http://au.archive.ubuntu.com gutsy-updates/universe Sources      
Ign http://au.archive.ubuntu.com gutsy-updates/main Sources          
Ign http://au.archive.ubuntu.com gutsy-updates/multiverse Sources    
Ign http://au.archive.ubuntu.com gutsy-updates/restricted Sources    
Err http://au.archive.ubuntu.com gutsy/main Packages                 
  404 Not Found
Err http://au.archive.ubuntu.com gutsy/universe Packages             
  404 Not Found
Err http://archive.ubuntu.com gutsy-backports/multiverse Packages    
  404 Not Found
Err http://archive.ubuntu.com gutsy-backports/main Sources           
  404 Not Found
Err http://archive.ubuntu.com gutsy-backports/restricted Sources     
  404 Not Found
Err http://archive.ubuntu.com gutsy-backports/universe Sources       
  404 Not Found
Err http://security.ubuntu.com gutsy-security/universe Sources       
  404 Not Found
Err http://security.ubuntu.com gutsy-security/main Sources           
  404 Not Found
Err http://security.ubuntu.com gutsy-security/multiverse Sources     
  404 Not Found
Err http://security.ubuntu.com gutsy-security/restricted Sources     
  404 Not Found
Err http://au.archive.ubuntu.com gutsy/restricted Packages           
  404 Not Found
Err http://au.archive.ubuntu.com gutsy/multiverse Packages
  404 Not Found
Err http://au.archive.ubuntu.com gutsy/main Sources
  404 Not Found
Err http://au.archive.ubuntu.com gutsy/universe Sources
  404 Not Found
Err http://au.archive.ubuntu.com gutsy/restricted Sources
  404 Not Found
Err http://au.archive.ubuntu.com gutsy/multiverse Sources
  404 Not Found
Err http://au.archive.ubuntu.com gutsy-updates/universe Packages
  404 Not Found
Err http://archive.ubuntu.com gutsy-backports/multiverse Sources
  404 Not Found
Err http://au.archive.ubuntu.com gutsy-updates/main Packages
  404 Not Found
Err http://au.archive.ubuntu.com gutsy-updates/multiverse Packages
  404 Not Found
Err http://au.archive.ubuntu.com gutsy-updates/restricted Packages
  404 Not Found
Err http://au.archive.ubuntu.com gutsy-updates/universe Sources
  404 Not Found
Err http://au.archive.ubuntu.com gutsy-updates/main Sources
  404 Not Found
Err http://au.archive.ubuntu.com gutsy-updates/multiverse Sources
  404 Not Found
Err http://au.archive.ubuntu.com gutsy-updates/restricted Sources
  404 Not Found
Fetched 11.8kB in 4s (2640B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by erfahren on 2008-02-05
steve - have you looked into the problem with ipv6 that some are mentioning as having? I didn't mention it before because I think most people that have the problem also have an issue with sites timing out in Firefox.

Basically you just disable it. I personally don't know much about it but can provide some links about it
see the bottom section here on how to test: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)

---

### Post by steve_waters on 2008-02-06
Yep done that already will double check that I got it right but bascially i had no internt then disable ipv6 and got good speeds from firefox.

Will double check I got it right and get back.




Wow this is reminding me of my Fedora days, with stange issues.

---

### Post by steve_waters on 2008-02-08
Further into it now, can bring down some of my source lists.

I have been informed there is updates available but can not download, when I take one of the links I can get to it in fireoix and also using wget but not using the update manager.

The updates is also still trying to bring down Australian translations of packages. 

Anyone more ideas or things to try?

---

### Post by steve_waters on 2008-02-08
Ok,

So new progress, I have been able to an update I removed security from source list and also using ftp to download from the mirror.

There is an issue with the security updates, though again I can get there in firefox and see the whole list but I can not download from with update manager.

The fun continues.............

---

### Post by erfahren on 2008-02-08
I found a thread that someone mentioned having a problem with the mirrors in Australia - and also with using the en_AU language setting - I'll just let you look at the threads 
[http://ubuntuforums.org/showthread.php?t=510977](http://ubuntuforums.org/showthread.php?t=510977)
[http://ubuntuforums.org/showthread.php?t=508981](http://ubuntuforums.org/showthread.php?t=508981)

---

