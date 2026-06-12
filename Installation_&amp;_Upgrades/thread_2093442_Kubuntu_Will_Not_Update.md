---
title: "Kubuntu Will Not Update"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by DeadlyOats on 2012-12-10
I've been playing Guild Wars for a few weeks, so it's been awhile since I last logged into Kubuntu Linux.  So, I decided to log in to run the update utility, to get the lates security patches and whatnot, but I ran into problems.  How do I fix this?  (To be clear, I clicked on the "Check for updates" button in the first screenshot, and got the error message in the next screen shot.  The third screenshot is just me scrolling down.)

Here are the screenshots:

---

### Post by alexandari on 2012-12-10
does ```
 sudo apt-get update 
``` run fine?

---

### Post by drmrgd on 2012-12-10
What is archive.getdeb.net?  Is this a mirror you're using to get your updates?  Perhaps it's down and you just need to select another mirror.

---

### Post by ibjsb4 on 2012-12-10
Selecting another mirror will not help. Getdeb.net is down.

---

### Post by DeadlyOats on 2012-12-11
> **alexandari said:**
> does ```
 sudo apt-get update 
``` run fine?

Here's what I got:

```
user@MACHINE:~$ sudo apt-get update
[sudo] password for user: 
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb InRelease
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb Release.gpg                       
  Unable to connect to archive.getdeb.net:http:
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb Release                           
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps amd64 Packages/DiffIndex     
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games amd64 Packages/DiffIndex    
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps i386 Packages/DiffIndex      
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games i386 Packages/DiffIndex     
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps Translation-en_US            
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps Translation-en               
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games Translation-en_US           
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games Translation-en              
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps amd64 Packages               
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games amd64 Packages              
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps i386 Packages                
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games i386 Packages               
  Unable to connect to archive.getdeb.net:http:
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal InRelease                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources             
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free amd64 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages         
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages       
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en_US](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en_US)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/i18n/Translation-en_US](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/i18n/Translation-en_US)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/i18n/Translation-en](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/i18n/Translation-en)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-amd64/Packages](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-amd64/Packages)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/binary-amd64/Packages](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/binary-amd64/Packages)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.
user@MACHINE:~$ 

```

---

### Post by DeadlyOats on 2012-12-11
> **ibjsb4 said:**
> Selecting another mirror will not help. Getdeb.net is down.


What does this mean?  We can't update 'buntu anymore?

---

### Post by ibjsb4 on 2012-12-11
You just have to wait until GetDeb is back online to update.  I say give it a few more days.

[http://ubuntuforums.org/showthread.php?t=2088127&page=2](http://ubuntuforums.org/showthread.php?t=2088127&page=2)

---

### Post by DeadlyOats on 2012-12-11
Thanks for the link.  I'll try updating in a few days then.  If it ain't working by then, I'll try the work around those guys came up with at that link.

---

