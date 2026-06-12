---
title: "No updates"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by sammy888 on 2008-11-30
Hi!

I have a problem with updating my Ubuntu 8.10 Linux system. Problem is that there aren't any updates. On my other computer (also with Ubuntu 8.10) there are many updates. So what I have to do, that Updates will be available. Can somebody help me please?

	 	
Content of /etc/apt/sources.list :

[I]# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid main restricted
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates main restricted
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid universe
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid universe
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates universe
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid multiverse
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid multiverse
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates multiverse
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security main restricted
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security main restricted
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security universe
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security universe
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security multiverse
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security multiverse
deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) intrepid main

## OpenOfice.org 3
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main[/I]

---

### Post by taurus on 2008-11-30
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by sammy888 on 2008-12-01
[I]sammy@sammypc1-linux:~$ sudo apt-get update
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid Release.gpg                     
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/main Translation-sl
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/restricted Translation-sl
Prz [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg              
Prz [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-sl      
Zadetek [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg     
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/universe Translation-sl             
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/multiverse Translation-sl           
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates Release.gpg             
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/main Translation-sl         
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/restricted Translation-sl   
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/universe Translation-sl     
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/multiverse Translation-sl   
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security Release.gpg          
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/main Translation-sl        
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/restricted Translation-sl  
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/universe Translation-sl    
Prz [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Prz [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-sl                      
Dobi:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27,6kB]                      
Prz [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/multiverse Translation-sl  
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid Release         
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates Release 
Dobi:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27,6kB]                      
Prz [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-sl 
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security Release                
Prz [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/main Packages                   
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/restricted Packages           
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/main Sources
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/restricted Sources
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/universe Packages
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/universe Sources
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/multiverse Packages
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/multiverse Sources
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/main Packages
Prz [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages            
Prz [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-sl
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/restricted Packages     
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/main Sources            
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/restricted Sources      
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/universe Packages       
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/universe Sources      
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/multiverse Packages   
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/multiverse Sources    
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/main Packages        
Zadetek [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                      
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/restricted Packages  
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/main Sources         
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/restricted Sources
Zadetek [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/universe Packages
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/universe Sources     
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/multiverse Packages  
Zadetek [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/multiverse Sources   
Zadetek [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                 
Zadetek [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                        
Zadetek [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages               
Dobljenih 2B v 7s (0B/s)                                                       
Branje seznama paketov... Narejeno[/I] //Reading list of packages...Complete.

[I]
sammy@sammypc1-linux:~$ sudo apt-get upgrade
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti        
Reading state information... Narejeno
0 nadgrajenih, 0 na novo nameš&#269;enih, 0 bo odstranjenih in 0 ne nadgrajenih.[/I]

//0 Upgraded 0 New installed 0 Removed 0 not Upgraded

---

### Post by sammy888 on 2008-12-02
I made a mistake. My other computer has never been updated because it is meant only for study OS. After update there is the same situation as on this computer with a "problem". Thank you for your answers and help.

---

