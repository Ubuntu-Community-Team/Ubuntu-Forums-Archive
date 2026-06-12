---
title: "Gutsy nvidia GeForce 8600"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by JimFuqua on 2007-09-28
I installed Gutsy today and the nvida GeForce 8600 drivers were not operating.  I tried loading the Linux-restricted-modules-2.6.22-12-generic but could not get the screen resolution back. It was stuck on the lowest resolution and was very difficult to use.

Next I went to the ubuntuforums and followed the instructions posted by six for the prior release and it did not work, but I did get lost in using the vi instructions contained in that post.

I then went to the nvidia site and downloaded NVIDIA-Linux-X86_64-100.14.19-pkg2.run and followed the instructions and everything worked.

The update icon was lit on reboot..

I went to the Package Manager and it wanted to load the Linux-restricted-modules etc which I did and updated the information and clicked on Mark All Upgrades.  When I hit apply I got the message 

"E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages."

after listing about 40 or more packages to be removed.

The package manager could not fix the broken packages.

I presume that this will work itself out as Gutsy gets closer to a final release and that most of the things I changed are not relevant to the error message.  If I am mistaken and must take action to resolve the hangup of the Package Manage on "Mark All Upgrades"r I would appreciate some help.  I know just enough about Linux  to get in trouble.

Jim Fuqua

---

### Post by Pumalite on 2007-09-28
Post the output of:
sudo apt-get update

---

### Post by LowSky on 2007-09-29
I'm having the same issue here what mine is saying

```

john@john-desktop:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 97 not upgraded.
john@john-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha amd64 (20070823.5) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha amd64 (20070823.5) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Get:3 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com gutsy-security Release                          
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Get:4 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                 
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US             
Get:5 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]          
Ign http://us.archive.ubuntu.com gutsy-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com gutsy-backports/restricted Translation-en_US  
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Ign http://us.archive.ubuntu.com gutsy-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US  
Get:6 http://us.archive.ubuntu.com gutsy-proposed Release.gpg [191B]           
Hit http://packages.medibuntu.org gutsy Release                                
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Ign http://us.archive.ubuntu.com gutsy-proposed/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com gutsy-proposed/main Translation-en_US         
Ign http://us.archive.ubuntu.com gutsy-proposed/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com gutsy-proposed/universe Translation-en_US     
Hit http://us.archive.ubuntu.com gutsy Release                                 
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://us.archive.ubuntu.com gutsy-backports Release                       
Ign http://packages.medibuntu.org gutsy/free Packages                          
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://us.archive.ubuntu.com gutsy-proposed Release              
Ign http://packages.medibuntu.org gutsy/non-free Packages                      
Hit http://us.archive.ubuntu.com gutsy/main Packages                 
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources            
Hit http://us.archive.ubuntu.com gutsy/universe Packages             
Hit http://packages.medibuntu.org gutsy/free Packages                
Hit http://us.archive.ubuntu.com gutsy/universe Sources              
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Get:7 http://wine.budgetdedicated.com feisty Release.gpg [191B]      
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US    
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources          
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources    
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages     
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources      
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages   
Hit http://packages.medibuntu.org gutsy/non-free Packages            
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources    
Hit http://us.archive.ubuntu.com gutsy-backports/main Packages
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://wine.budgetdedicated.com feisty Release
Hit http://us.archive.ubuntu.com gutsy-proposed/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-proposed/main Packages
Hit http://us.archive.ubuntu.com gutsy-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-proposed/universe Packages
Ign http://wine.budgetdedicated.com feisty/main Packages
Hit http://wine.budgetdedicated.com feisty/main Sources
Hit http://wine.budgetdedicated.com feisty/main Packages
Fetched 195B in 1s (127B/s)
Reading package lists... Done
john@john-desktop:~$ 


```

---

### Post by Pumalite on 2007-09-29
You are fine.

---

