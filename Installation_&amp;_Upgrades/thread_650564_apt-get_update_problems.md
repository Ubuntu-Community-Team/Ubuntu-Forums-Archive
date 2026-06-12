---
title: "apt-get update problems"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by samundar on 2007-12-26
HI there!
Bought a new Acer notebook and installed ubuntu 7.10 right away! However, the sound isn't working. I was asked to run ```
sudo apt-get update
``` before doing anything else. This is the message that turns up... 

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

What now?
Don't have the cd with me, so I unchecked that argument on the sources.list
This is my sources.list (Any suggestions?)

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by taurus on 2007-12-26
You need to enable some repos in /etc/apt/sources.list if you want to install something.

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.  

Now, make sure you check everything except the last one, Sources code.  Close that and press Refresh.  You are now good to install whatever else you want.

---

### Post by wolfen69 on 2007-12-26
you could use this [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) to generate a fresh sources.list    then do sudo apt-get update.

---

### Post by samundar on 2007-12-26
I did check all the items on the sources manager,,, To no avail

---

### Post by taurus on 2007-12-26
Okay, let's try another way then.  Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of all the lines that start with **deb** & **deb-src**.  Save the changes and close gedit window.  

Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by samundar on 2007-12-26
It still delivers a lot of errors. :( Any other suggestions? 
Really lost here

---

### Post by taurus on 2007-12-26
Can you post the whole error message?

Also, post your /etc/apt/sources.list again.

```
cat /etc/apt/sources.list
```

---

### Post by samundar on 2007-12-26
The error message
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



The source.list

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by samundar on 2007-12-26
bump
I would really appreciate some kind help here!!!

---

### Post by PmDematagoda on 2007-12-26
Could you please post the errors you receive by executing:-

```
sudo apt-get update
```
as suggested by taurus.

---

### Post by taurus on 2007-12-26
What is the error message when you run this command?

```
sudo apt-get update
```

---

### Post by samundar on 2007-12-26
sam@sam-laptop:~$ sudo apt-get update
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy Release.gpg                             
  Could not resolve 'in.archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not resolve 'archive.canonical.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                
  Could not resolve 'archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Translation-en_IN                  
  Could not resolve 'in.archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_IN               
  Could not resolve 'archive.canonical.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_IN           
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_IN                     
  Could not resolve 'archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Translation-en_IN            
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_IN     
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IN                 
  Could not resolve 'archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Translation-en_IN              
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_IN       
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_IN               
  Could not resolve 'archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Translation-en_IN            
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_IN     
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_IN               
  Could not resolve 'archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates Release.gpg                     
  Could not resolve 'in.archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
  Could not resolve 'archive.canonical.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg                        
  Could not resolve 'archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Translation-en_IN          
  Could not resolve 'in.archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
  Could not resolve 'archive.canonical.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_IN         
  Could not resolve 'archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Translation-en_IN    
  Could not resolve 'in.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_IN             
  Could not resolve 'archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Translation-en_IN      
  Could not resolve 'in.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_IN       
  Could not resolve 'archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_IN    
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_IN       
  Could not resolve 'archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports Release.gpg                   
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Translation-en_IN        
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Translation-en_IN  
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Translation-en_IN    
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
  Could not resolve 'security.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_IN  
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
  Could not resolve 'security.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
  Could not resolve 'security.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                  
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
  Could not resolve 'security.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
  Could not resolve 'security.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Packages                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
  Could not resolve 'security.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
  Could not resolve 'security.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Sources                            
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                           
  Could not resolve 'archive.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Sources                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
  Could not resolve 'archive.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Packages                    
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                     
  Could not resolve 'archive.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Sources                     
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                     
  Could not resolve 'archive.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Packages                  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages               
  Could not resolve 'archive.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Sources                   
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                   
  Could not resolve 'archive.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Packages                
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages             
  Could not resolve 'archive.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Packages          
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages             
  Could not resolve 'archive.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Sources
  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
sam@sam-laptop:~$ 


Sorry for the inconvenience

---

### Post by taurus on 2007-12-26
Is your network working?  Are you behind a proxy?

---

### Post by samundar on 2007-12-26
The network is working fine... (I mean, I'm sending these messages from the same computer) But yes, I am behind proxy...
Will I have to find another network?

---

### Post by davidj123256 on 2008-01-02
Hi SAM!!

Since your behind a proxy, you have to make sure tht the following is done...

go to System>Preferences>Network Proxy and configure your proxy settings there.

Then, It should start working...
All the best!

David

---

### Post by samundar on 2008-01-06
Well, what to say?
Sad news... That's all... 
Most servers require me to have a different mac-id. Have tried changing my mac-id, but unfortunately, I'll need to be root, which i obviously cannot be...
Tried searching for addon cds that come in bite sized downloadable bits, but there's only Renzo's, and he hasn't got mirrors for the gutsy version yet...
Since I'm hard pressed for time, I'll have to join the bandwagon and revert to xp... (sigh)
Well, thirdworlders like me cannot afford internet connections.. So much for the "no barriers with ubuntu"
Hey, anyone have a pirated xp cd?!

---

### Post by taurus on 2008-01-06
> **samundar said:**
> 
Hey, anyone have a pirated xp cd?!
[-X

---

