---
title: "Package dependency"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by Damanther on 2008-03-07
I am running Ubuntu 7.10 64 bit. And to get vnc4server running successfully I had to downgrade the version of vnc4server to 4.0-7.3

I had to use the --ignore flag to get it to install because it wanted xserver-common as a dependency which doesn't exist.

Everything works now except that when I try to install anything else via apt-get or synaptic it complains that this package is broken because of a dependency. I would install xserver-common but as I said it doesn't exist.

Is there anyway for me to get synaptic and/or apt-get to ignore this broken package and let me continue????

---

### Post by Pumalite on 2008-03-07
Post the output of:
sudo dpkg --configure -a
sudo apt-get update

---

### Post by Damanther on 2008-03-07
dpkg --configure -a 

results in no output.

apt-get update looks like this.

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US               
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Fetched 197B in 1s (119B/s)
Reading package lists... Done

---

### Post by Pumalite on 2008-03-07
It's:
sudo dpkg --configure -a
sudo apt-get update.

---

### Post by Damanther on 2008-03-07
I actually did a sudo bash, then ran the two commands. I know its a bad habit, but I'm too used to su - on other *nix systems.

But I ran the commands with sudo and got the same results.

FYI, I have been keeping my system updated by letting apt-get install the latest version of vnc4server to make it happy, then doing apt-get update. Then using the deb package that I have to downgrade vnc4server back to the one that works. I'd like to find a way to skip all that.

If this helps what your looking for. I did an apt-get install with 3dchess and this is the output.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
   vnc4server: Depends: xserver-common but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


And if I try to install xserver-common with apt-get I see this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xserver-xorg-core xserver-xorg x11-common
E: Package xserver-common has no installation candidate

---

### Post by Pumalite on 2008-03-07
You are in a catch-22 situation. Post:
uname -a

---

### Post by Damanther on 2008-03-07
uname -a 
says

Linux lovelace-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

---

