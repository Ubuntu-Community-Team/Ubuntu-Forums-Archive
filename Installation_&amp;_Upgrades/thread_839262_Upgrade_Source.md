---
title: "Upgrade Source"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by mianda_psi on 2008-06-24
Is there anyway I can get Ubuntu to upgrade from a mirror of my choice?  I want to do it so I can do the upgrade in an hour instead of multiple days.

Thanks for any help.

---

### Post by Zulu-Zeffir on 2008-06-24
Look at your /etc/apt/sources.list and you can add/remove repositories.

Look here:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by mianda_psi on 2008-06-24
I have my repositories set up - I even tried adding the hardy ones in with my gutsy ones, but the upgrade just seems to ignore it.

---

### Post by Zulu-Zeffir on 2008-06-24
Can you post your sources.list contents please.
Did you run "apt-get update" after modifying your sources.list file?
In order for the change to take affect you need to run that command.

---

### Post by mianda_psi on 2008-06-24
this is with both gutsy and hardy in:

```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.uwa.edu.au/ubuntu/ gutsy main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy main restricted
deb http://mirrors.uwa.edu.au/ubuntu/ hardy main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates main restricted
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-updates main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy universe
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates universe
deb http://mirrors.uwa.edu.au/ubuntu/ hardy universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy universe
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-updates universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy multiverse
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates multiverse
deb http://mirrors.uwa.edu.au/ubuntu/ hardy multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy multiverse
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-updates multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-security main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-security main restricted
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-security universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-security universe
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-security multiverse
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-security main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-security main restricted
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-security universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-security universe
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-security multiverse
```

---

### Post by Zulu-Zeffir on 2008-06-24
Did you run apt-get update after modifying your sources.list?

---

### Post by mianda_psi on 2008-06-24
I updated after every change I made to the sources.

---

### Post by Zulu-Zeffir on 2008-06-24
It worked fine for me.  
How are you modifying the file (synaptic/Vi) and which mirrors are you trying to use that are not working?  If I understand you correctly your saying that none of the changes are taking affect?  And you are definitely modifying "/etc/apt/sources.list" and running "apt-get update" thereafter?

---

### Post by mianda_psi on 2008-06-24
I use vim and i use my local university mirror ([http://mirrors.uwa.edu.au/ubuntu/](http://mirrors.uwa.edu.au/ubuntu/)) - I can get over 10Mb/s from there at times and from the standard ubuntu mirror im lucky to get 10kb/s...

---

### Post by Zulu-Zeffir on 2008-06-24
Just to be sure can you post the output of:
"cat /etc/apt/sources.list"
and from:
"apt-get update"

---

### Post by mianda_psi on 2008-06-24
cat /etc/apt/sourses.list
```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.uwa.edu.au/ubuntu/ gutsy main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy main restricted
deb http://mirrors.uwa.edu.au/ubuntu/ hardy main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates main restricted
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-updates main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy universe
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates universe
deb http://mirrors.uwa.edu.au/ubuntu/ hardy universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy universe
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-updates universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy multiverse
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-updates multiverse
deb http://mirrors.uwa.edu.au/ubuntu/ hardy multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy multiverse
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-updates multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-security main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-security main restricted
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-security universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-security universe
deb http://mirrors.uwa.edu.au/ubuntu/ gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ gutsy-security multiverse
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-security main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-security main restricted
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-security universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-security universe
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-security multiverse

```

apt-get update
```
Get:1 http://mirrors.uwa.edu.au gutsy Release.gpg [191B]
Ign http://mirrors.uwa.edu.au gutsy/main Translation-en_AU          
Ign http://mirrors.uwa.edu.au gutsy/restricted Translation-en_AU    
Ign http://mirrors.uwa.edu.au gutsy/universe Translation-en_AU
Ign http://mirrors.uwa.edu.au gutsy/multiverse Translation-en_AU
Get:2 http://mirrors.uwa.edu.au hardy Release.gpg [191B]
Ign http://mirrors.uwa.edu.au hardy/main Translation-en_AU         
Ign http://mirrors.uwa.edu.au hardy/restricted Translation-en_AU
Ign http://mirrors.uwa.edu.au hardy/universe Translation-en_AU
Ign http://mirrors.uwa.edu.au hardy/multiverse Translation-en_AU
Get:3 http://mirrors.uwa.edu.au gutsy-updates Release.gpg [189B]
Ign http://mirrors.uwa.edu.au gutsy-updates/main Translation-en_AU 
Ign http://mirrors.uwa.edu.au gutsy-updates/restricted Translation-en_AU
Ign http://mirrors.uwa.edu.au gutsy-updates/universe Translation-en_AU
Ign http://mirrors.uwa.edu.au gutsy-updates/multiverse Translation-en_AU
Get:4 http://mirrors.uwa.edu.au hardy-updates Release.gpg [189B]
Ign http://mirrors.uwa.edu.au hardy-updates/main Translation-en_AU 
Ign http://mirrors.uwa.edu.au hardy-updates/restricted Translation-en_AU
Ign http://mirrors.uwa.edu.au hardy-updates/universe Translation-en_AU
Ign http://mirrors.uwa.edu.au hardy-updates/multiverse Translation-en_AU
Get:5 http://mirrors.uwa.edu.au gutsy-security Release.gpg [191B]
Ign http://mirrors.uwa.edu.au gutsy-security/main Translation-en_AU            
Ign http://mirrors.uwa.edu.au gutsy-security/restricted Translation-en_AU
Ign http://mirrors.uwa.edu.au gutsy-security/universe Translation-en_AU
Ign http://mirrors.uwa.edu.au gutsy-security/multiverse Translation-en_AU
Get:6 http://mirrors.uwa.edu.au hardy-security Release.gpg [191B]
Ign http://mirrors.uwa.edu.au hardy-security/main Translation-en_AU            
Ign http://mirrors.uwa.edu.au hardy-security/restricted Translation-en_AU
Ign http://mirrors.uwa.edu.au hardy-security/universe Translation-en_AU
Ign http://mirrors.uwa.edu.au hardy-security/multiverse Translation-en_AU
Hit http://mirrors.uwa.edu.au gutsy Release          
Hit http://mirrors.uwa.edu.au hardy Release          
Hit http://mirrors.uwa.edu.au gutsy-updates Release  
Hit http://mirrors.uwa.edu.au hardy-updates Release  
Hit http://mirrors.uwa.edu.au gutsy-security Release                       
Hit http://mirrors.uwa.edu.au hardy-security Release                       
Hit http://mirrors.uwa.edu.au gutsy/main Packages                              
Hit http://mirrors.uwa.edu.au gutsy/restricted Packages                        
Hit http://mirrors.uwa.edu.au gutsy/main Sources                           
Hit http://mirrors.uwa.edu.au gutsy/restricted Sources                     
Hit http://mirrors.uwa.edu.au gutsy/universe Packages                      
Hit http://mirrors.uwa.edu.au gutsy/universe Sources                       
Hit http://mirrors.uwa.edu.au gutsy/multiverse Packages                    
Hit http://mirrors.uwa.edu.au gutsy/multiverse Sources
Hit http://mirrors.uwa.edu.au hardy/main Packages                   
Hit http://mirrors.uwa.edu.au hardy/restricted Packages             
Hit http://mirrors.uwa.edu.au hardy/main Sources                    
Hit http://mirrors.uwa.edu.au hardy/restricted Sources              
Hit http://mirrors.uwa.edu.au hardy/universe Packages               
Hit http://mirrors.uwa.edu.au hardy/universe Sources                
Hit http://mirrors.uwa.edu.au hardy/multiverse Packages             
Hit http://mirrors.uwa.edu.au hardy/multiverse Sources              
Hit http://mirrors.uwa.edu.au gutsy-updates/main Packages           
Hit http://mirrors.uwa.edu.au gutsy-updates/restricted Packages     
Hit http://mirrors.uwa.edu.au gutsy-updates/main Sources            
Hit http://mirrors.uwa.edu.au gutsy-updates/restricted Sources      
Hit http://mirrors.uwa.edu.au gutsy-updates/universe Packages       
Hit http://mirrors.uwa.edu.au gutsy-updates/universe Sources        
Hit http://mirrors.uwa.edu.au gutsy-updates/multiverse Packages     
Hit http://mirrors.uwa.edu.au gutsy-updates/multiverse Sources      
Hit http://mirrors.uwa.edu.au hardy-updates/main Packages
Hit http://mirrors.uwa.edu.au hardy-updates/restricted Packages
Hit http://mirrors.uwa.edu.au hardy-updates/main Sources
Hit http://mirrors.uwa.edu.au hardy-updates/restricted Sources
Hit http://mirrors.uwa.edu.au hardy-updates/universe Packages
Hit http://mirrors.uwa.edu.au hardy-updates/universe Sources
Hit http://mirrors.uwa.edu.au hardy-updates/multiverse Packages
Hit http://mirrors.uwa.edu.au hardy-updates/multiverse Sources
Hit http://mirrors.uwa.edu.au gutsy-security/main Packages
Hit http://mirrors.uwa.edu.au gutsy-security/restricted Packages
Hit http://mirrors.uwa.edu.au gutsy-security/main Sources
Hit http://mirrors.uwa.edu.au gutsy-security/restricted Sources
Hit http://mirrors.uwa.edu.au gutsy-security/universe Packages
Hit http://mirrors.uwa.edu.au gutsy-security/universe Sources
Hit http://mirrors.uwa.edu.au gutsy-security/multiverse Packages
Hit http://mirrors.uwa.edu.au gutsy-security/multiverse Sources
Hit http://mirrors.uwa.edu.au hardy-security/main Packages
Hit http://mirrors.uwa.edu.au hardy-security/restricted Packages
Hit http://mirrors.uwa.edu.au hardy-security/main Sources
Hit http://mirrors.uwa.edu.au hardy-security/restricted Sources
Hit http://mirrors.uwa.edu.au hardy-security/universe Packages
Hit http://mirrors.uwa.edu.au hardy-security/universe Sources
Hit http://mirrors.uwa.edu.au hardy-security/multiverse Packages
Hit http://mirrors.uwa.edu.au hardy-security/multiverse Sources
Get:7 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/universe Translation-en_AU
Get:8 http://archive.ubuntu.com hardy Release.gpg [191B]
Ign http://archive.ubuntu.com hardy/universe Translation-en_AU
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com hardy Release   
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Fetched 8B in 4s (2B/s)
Reading package lists... Done

```

---

### Post by Zulu-Zeffir on 2008-06-24
It's working fine.  What exactly do you think that is not working?

---

### Post by mianda_psi on 2008-06-24
When I upgrade it doesn't download from the mirror I want it to download from.  This means I am probably downloading from the main ubuntu mirror and that is going to take ~4 days, whereas if it downloaded from the mirror I use in /etc/atc/sources.list it would be done within an hour or two...

---

### Post by Zulu-Zeffir on 2008-06-24
We were on two separate pages
System>Administration>Software Sources>Change the server

---

### Post by mianda_psi on 2008-06-24
My mirror isn't in the list - I don't think its official, I thinks its just there for the convience of students like me so it doesn't appear in the server list.  Is there anyway I can specify my own server?

---

### Post by Zulu-Zeffir on 2008-06-24
Beyond using "select best server", and seeing if you have better results, I'm unsure.  Let me look into it.

---

### Post by Zulu-Zeffir on 2008-06-24
Lets try this. 
Make a backup copy of your sources.list file.
Go and change to a different update server and apply the changes.
Now, go back and find the entries added by selecting the new server.  Easiest way 
is to use find and replace with your favorite editor.
  Change the url to your local mirror.  See if this works after an apt-update.  
This worked for me but you need to get the correct paths on your local mirror.

---

### Post by mianda_psi on 2008-06-24
doing that makes no difference - I can successfully update from my mirror, but the problem is I can't seem to use it to upgrade from 7.10 to 8.04

---

### Post by Zulu-Zeffir on 2008-06-24
But you were able to at least attempt and connect to your local mirror correct?
Are you sure those repositories are even available on your campus mirror?

---

### Post by mianda_psi on 2008-06-24
I have been using the campus repositries for updates for 2 years now and I downloaded a heap of updates from there just before I tried to upgrade to 8.04.  My laptop has 8.04 on and it has no problems downloading updates from the campus repository.  I can even see just by going to the url that all the repositories are there.

The only problem I am having is that the upgrading process doesn't seem to want to use the mirror that I have in my sources.list.

---

### Post by Zulu-Zeffir on 2008-06-24
Try using your sources.list from your laptop.  Maybe we've missed something.

---

### Post by mianda_psi on 2008-06-24
I made that list using my 7.10 sources - I just changes gutsy to hardy...

---

### Post by Zulu-Zeffir on 2008-06-24
And your current version is all updated before you try and upgrade?

---

### Post by Zulu-Zeffir on 2008-06-24
Hmmm...

---

### Post by Zulu-Zeffir on 2008-06-24
Just trying to get another angle,
from your terminal try 
"update-manager -p"
and look at /var/log/dpkg.log and /var/log/apt/term.log 
for any thing that may stick out.
Also try to clean with #sudo apt-get autoclean.
Then again #sudo apt-get update and #sudo apt-get upgrade.

---

### Post by mianda_psi on 2008-06-24
because of the cancelled upgrade it gave me the option of a partial upgrade - i'm trying that right now to see what happens. At the least it should cut down on what i have to download to upgrade...

If that doesn't work, I'll try what you just suggested - either way I'll let you know what happened.

---

### Post by mianda_psi on 2008-06-25
I have now run into the problem that one of my packages has now somehow broken and when I try to repair it all it gives me is that the pre-removal script returned exit status 1.  I need to get this sorted first, since it just halts everything else...

Thanks for any help.

---

