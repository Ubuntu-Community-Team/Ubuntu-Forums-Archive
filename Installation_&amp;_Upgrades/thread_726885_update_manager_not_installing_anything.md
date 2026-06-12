---
title: "update manager not installing anything"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by Zaff on 2008-03-17
Hi, I don't know if anyone's had this issue before, I'm having this with synaptics as well. The update manager warns me of available updates but when I click instal them it doesn't do anything, it checks available updates and comes back to the list of updates. If I try marking all available updates in synaptics nothing happens.
The only way to update anything is to apt-get update. I don't mind it, but it's strange that the gui aren't working.

Thanks for the help.

---

### Post by Pumalite on 2008-03-17
Post:
cat /etc/apt/sources.list
You can also go to System>Administration>Software Sources
And make sure everything is on except CD (I'd avoid 'src' too)

---

### Post by Zaff on 2008-03-17
> **Pumalite said:**
> Post:
cat /etc/apt/sources.list
You can also go to System>Administration>Software Sources
And make sure everything is on except CD (I'd avoid 'src' too)

Here it is, don't remember changing it recently though...
```

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://www.virtualbox.org/debian gutsy non-free
# deb http://wicd.longren.org gutsy extras

deb http://fr.packages.medibuntu.org/ gutsy free non-free
```
Any idea what could be causing the problem ?

---

### Post by Pumalite on 2008-03-17
Post the output of:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by Zaff on 2008-03-17
> **Pumalite said:**
> Post the output of:
sudo dpkg --configure -a

I get nothing

> sudo apt-get update
Get:1 [http://fr.packages.medibuntu.org](http://fr.packages.medibuntu.org) gutsy Release.gpg [189B]
Get:2 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:3 [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release.gpg [189B]                       
Ign [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Translation-en_US                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:5 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release                                    
Get:6 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US               
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Packages                          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/restricted Sources            
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/universe Packages             
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/universe Sources              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/restricted Packages   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/universe Packages     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/multiverse Packages   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/main Sources          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) gutsy-updates/restricted Sources    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages              
Ign [http://fr.packages.medibuntu.org](http://fr.packages.medibuntu.org) gutsy/free Translation-en_US
Ign [http://fr.packages.medibuntu.org](http://fr.packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://fr.packages.medibuntu.org](http://fr.packages.medibuntu.org) gutsy Release
Ign [http://fr.packages.medibuntu.org](http://fr.packages.medibuntu.org) gutsy/free Packages
Ign [http://fr.packages.medibuntu.org](http://fr.packages.medibuntu.org) gutsy/non-free Packages
Hit [http://fr.packages.medibuntu.org](http://fr.packages.medibuntu.org) gutsy/free Packages
Hit [http://fr.packages.medibuntu.org](http://fr.packages.medibuntu.org) gutsy/non-free Packages
Fetched 6B in 4s (1B/s)  
Reading package lists... Done

> sudo apt-get upgrade
Works fine, I already uprgraded using this before, but I don't want to do it now because there is one packet that I want to keep back. but it works. I get no error.
What doesn't work is when I try to do it using the gui.

---

