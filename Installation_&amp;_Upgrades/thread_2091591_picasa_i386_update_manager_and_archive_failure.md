---
title: "picasa i386 update manager and archive failure"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by eaglemystic69 on 2012-12-05
This did not work in my case:

I did a fresh install of 12.10.  Used the LVM for the first time. All seemed OK until I attempted to add Picasa.  Now I cannot use update manager, synaptic was not installed yet.

I have been searching and doing these below with no fix.   Cannot even find an archive to reinstall it then remove it.

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo dpkg --configure -a
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

cristos69@cristos69:~$ sudo apt-get upgrade dist
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package picasa:i386 needs to be reinstalled, but I can't find an archive for it.

---

### Post by eaglemystic69 on 2012-12-05
cristos69@cristos69:~$ sudo apt-get upgrade dist
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: The package picasa:i386 needs to be reinstalled, but I can't find an archive for it.

I did the suggestions in this thread... and these below do not help either.   Cannot even find an archive to reinstall it then remove it.

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo dpkg --configure -a
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by isantop on 2012-12-05
What do you get if you run this:

```
sudo apt-get purge picasa picasa:i386
```

---

### Post by eaglemystic69 on 2012-12-05
E: The package picasa:i386 needs to be reinstalled, but I can't find an archive for it.

I did a fresh install of 12.10.  Used the LVM for the first time. All seemed OK until I attempted to add Picasa 3.0.  Now I cannot use update manager, synaptic was not installed yet.

I have been searching and doing these below with no fix... not in that order, though several times over days.   Cannot even find a picasa archive to reinstall it then remove it.  

Just want it gone and to update again.

sudo dpkg --configure -a
sudo rm /var/lib/apt/lists/* -vf
sudo -i
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
sudo apt-get autoremove
apt-get clean
apt-get update 
sudo apt-get upgrade

cristos69@cristos69:~$ sudo apt-get upgrade dist
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: The package picasa:i386 needs to be reinstalled, but I can't find an archive for it.

---

### Post by coffeecat on 2012-12-05
@eaglemystic69, I've moved the two posts you made in others' threads about the same issue, plus the one reply you received, into the thread you have just started. Please do not post about the same issue in different parts of the forum; this dilutes the community's ability to help.

---

### Post by eaglemystic69 on 2012-12-05
This is the mantra of all actions

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package picasa:i386 needs to be reinstalled, but I can't find an archive for it.

---

### Post by eaglemystic69 on 2012-12-06
Anyone have a new recommendation?

My choice without updates and add/remove is to do another complete install... which is a bummer!

---

### Post by eaglemystic69 on 2012-12-06
maybe this output helps:

sudo apt-get update
[sudo] password for cristos69: 
Ign [http://dl.google.com](http://dl.google.com) testing InRelease
Ign [http://dl.google.com](http://dl.google.com) testing Release.gpg                                   
Ign [http://dl.google.com](http://dl.google.com) testing Release                                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                                
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security InRelease                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg [933 B]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release.gpg                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Err [http://dl.google.com](http://dl.google.com) testing/non-free amd64 Packages                       
  404  Not Found [IP: 74.125.134.190 80]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release.gpg [933 B]           
Err [http://dl.google.com](http://dl.google.com) testing/non-free i386 Packages                        
  404  Not Found [IP: 74.125.134.190 80]
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                                  
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_US                    
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en                       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release [49.6 kB]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release [49.6 kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages 
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [4,064 B]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Sources               
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages [4,067 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Sources [889 B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Sources [49.2 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Sources [2,940 B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Sources [21.9 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages [126 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages [1,970 B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages [65.8 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7,956 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main i386 Packages [126 kB]   
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted i386 Packages [1,979 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe i386 Packages [66.1 kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8,121 B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en [62.6 kB] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en        
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en [39.2 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Sources             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Sources               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Sources             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main amd64 Packages            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted amd64 Packages      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe amd64 Packages        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse amd64 Packages      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main i386 Packages             
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted i386 Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe i386 Packages         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse i386 Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-en            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-en        
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Sources [14 B]    
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Sources [19.5 kB]       
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Sources [695 B]   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Sources [6,763 B]   
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main amd64 Packages [54.9 kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe amd64 Packages [16.8 kB]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse amd64 Packages [1,151 B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main i386 Packages [54.8 kB] 
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe i386 Packages [16.8 kB]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse i386 Packages [1,394 B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-en [26.4 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en       
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en [9,362 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en_US      
Fetched 910 kB in 20s (43.5 kB/s)                                              
W: Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-amd64/Packages](http://dl.google.com/linux/deb/dists/testing/non-free/binary-amd64/Packages)  404  Not Found [IP: 74.125.134.190 80]

W: Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages](http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages)  404  Not Found [IP: 74.125.134.190 80]

W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
cristos69@cristos69:~$

---

