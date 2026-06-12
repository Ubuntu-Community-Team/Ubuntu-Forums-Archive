---
title: "Hash Sum mismatch issue"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by markkcurtis on 2008-04-16
I hope that I'm posting this in the right forum.
Just today I have started to get the following error:

> Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

I've had a good trawl around the net and on here and have tried *apt-get update*, choosing best server (in fact I've tried loads!) and many of the other suggestions but I simply can't get it to work.  The output of* apt-get update* is below.

Does anyone have a definitive answer as until I get this sorted I'm unable to install or update.  I'm really persevering with Ubuntu/Linux but suffering a lot of these odd errors that just keep holding me back from completely jumping on board with my main PC.

Many thanks.

> 

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security Release.gpg          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release.gpg          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release             
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy Release.gpg            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources                      
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources [1324kB]            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/restricted Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main Sources       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/multiverse Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/universe Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/universe Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Sources       
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy/main Translation-en_GB
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy Release
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy/main Packages
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy/main Sources
Fetched 1B in 2s (0B/s)                            
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by markkcurtis on 2008-04-18
Hi

Anyone have any ideas beyond everything I think I've tried?

Cheers
M

---

### Post by zvacet on 2008-04-18
```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by markkcurtis on 2008-04-21
Hi cheers for the reply, the output of that command is:


# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
deb-src [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy main restricted
deb-src [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-updates main restricted
deb-src [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy universe
deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy multiverse
deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-security main restricted
deb-src [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-security universe
deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-security multiverse
deb [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://ubuntu.positive-internet.com/ubuntu/](http://ubuntu.positive-internet.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main

---

### Post by zvacet on 2008-04-21
In system>admin<software sources>swich to the main server.Maybe that will help.

---

### Post by aintzwye on 2008-05-01
Hi ppl!

 So whats the status? I still get this kind of stuff. My evolution does not want to upgrade, exactly due to this "Hash Sum Mismatch"...

---

### Post by cplol on 2008-05-02
bump! i also have a problem with this!

---

### Post by aintzwye on 2008-05-03
This kind of problem has become systematic whatever I try to install or update. But... the following can be useful. While trying to install kcontrol, I received this message systematically. Installing package dependencies one by one (just to avoid to get pack of errors and keep focus on one problem), I've got the package making "apt-get autoclean" & "apt-get clean" after each installed dependency! Aint that stupid?? What the hell is wrong with the system and these stupid hashes?..

---

### Post by cgerada on 2008-05-04
Same problem here

'aptitude update'  works with out a problem (and the same sources)
the problem is apt related.

---

### Post by raquibulbari on 2008-05-09
thanks for the help, i changed the software sources to main source and that worked for me

Regard
Shimul

---

### Post by Aearenda on 2008-05-13
Here's a possible reason for all this:
[http://ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntuforums.org/showpost.php?p=4952791&postcount=10)

---

### Post by AnRkey on 2008-07-10
Same problem here, trying above answers. Will post back if it works

---

### Post by AnRkey on 2008-07-10
Thanks Aearenda

That sorted me out.

John

---

### Post by jakechance on 2008-07-16
> **Aearenda said:**
> Here's a possible reason for all this:
[http://ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntuforums.org/showpost.php?p=4952791&postcount=10)
This worked for me too. I was missing a ton of updates!

---

