---
title: "Cant Upgrade"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by james_bandido on 2007-11-06
I was running the update manager when the power tripped suddenly.

Now I cant even make any updates.

When I ran synaptic is gives me the error : 

> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a'  to correct the problem.
E: _cache->open() failed, please report.
I tried to fix this by going to the terminal, and got the same message :

> 
jeugenio@support3-linux:~$ sudo apt-get update
[sudo] password for jeugenio:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_PH
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_PH
Get:1 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/main Translation-en_PH                  
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/restricted Translation-en_PH  
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/multiverse Translation-en_PH
Get:2 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/main Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_PH
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy Release
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/restricted Packages   
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/main Sources          
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/restricted Sources    
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/universe Packages     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/universe Sources      
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/multiverse Packages   
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy/multiverse Sources    
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/main Packages 
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/main Sources  
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates/multiverse Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_PH           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_PH     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_PH       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_PH     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Fetched 3B in 7s (0B/s)                                                        
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jeugenio@support3-linux:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jeugenio@support3-linux:~$ 
I have already tried logging into as the system administrator but I cant perform the said task.

Thanks in advance.

---

### Post by bulldog on 2007-11-06
You can perform the command in a terminal or in console,what ever you prefer.
Just type in the terminal```
sudo dpkg --configure -a
``` and see if this corrects your problem.

---

### Post by james_bandido on 2007-11-06
bulldog, thank you very much !!!

---

