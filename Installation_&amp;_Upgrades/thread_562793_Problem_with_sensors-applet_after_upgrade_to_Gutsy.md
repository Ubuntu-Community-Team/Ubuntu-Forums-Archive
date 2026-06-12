---
title: "Problem with sensors-applet after upgrade to Gutsy (Not possible to install at all)"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by zooounds on 2007-09-29
I had sensors applet installed in Feisty. When upgrading to gutsy i was removed. Now I can't install it at all:

E: I wasn't able to locate file for the sensors-applet package. This might mean you need to manually fix this package.
E: Unable to lock the download directory

What am I doing wrong?

---

### Post by Pumalite on 2007-09-29
Post the output of:

sudo apt-get update

---

### Post by zooounds on 2007-09-29
```
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US  
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com gutsy-security Release                          
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Get:3 http://archive.ubuntu.com gutsy-proposed Release.gpg [191B]              
Ign http://archive.ubuntu.com gutsy-proposed/restricted Translation-en_US      
Ign http://archive.ubuntu.com gutsy-proposed/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy-proposed/universe Translation-en_US
Get:4 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]             
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US     
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US           
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US       
Get:5 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]               
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US             
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US       
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US         
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Hit http://security.ubuntu.com gutsy-security/universe Sources                 
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Get:6 http://archive.ubuntu.com gutsy-security Release.gpg [191B]              
Ign http://archive.ubuntu.com gutsy-security/main Translation-en_US   
Ign http://archive.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-security/multiverse Translation-en_US
Get:7 http://archive.ubuntu.com gutsy Release [65,9kB]
Hit http://archive.ubuntu.com gutsy-proposed Release               
Hit http://archive.ubuntu.com gutsy-backports Release              
Hit http://archive.ubuntu.com gutsy-updates Release                
Hit http://archive.ubuntu.com gutsy-security Release               
Get:8 http://se.archive.ubuntu.com gutsy Release.gpg [191B]         
Ign http://se.archive.ubuntu.com gutsy/main Translation-en_US       
Ign http://se.archive.ubuntu.com gutsy/restricted Translation-en_US 
Ign http://se.archive.ubuntu.com gutsy/universe Translation-en_US   
Ign http://se.archive.ubuntu.com gutsy/multiverse Translation-en_US 
Get:9 http://se.archive.ubuntu.com gutsy-updates Release.gpg [191B] 
Ign http://se.archive.ubuntu.com gutsy-updates/main Translation-en_US      
Ign http://se.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Get:10 http://se.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://se.archive.ubuntu.com gutsy-backports/main Translation-en_US     
Ign http://se.archive.ubuntu.com gutsy-backports/restricted Translation-en_US
Get:11 http://archive.ubuntu.com gutsy/restricted Sources [2088B]   
Ign http://se.archive.ubuntu.com gutsy-backports/universe Translation-en_US
Ign http://se.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Get:12 http://se.archive.ubuntu.com gutsy Release [65,9kB]
Get:13 http://archive.ubuntu.com gutsy/main Sources [307kB]               
Hit http://se.archive.ubuntu.com gutsy-updates Release      
Hit http://se.archive.ubuntu.com gutsy-backports Release    
Get:14 http://se.archive.ubuntu.com gutsy/main Packages [1079kB]           
Get:15 http://se.archive.ubuntu.com gutsy/restricted Packages [7601B]          
Get:16 http://se.archive.ubuntu.com gutsy/restricted Sources [2088B]           
Get:17 http://se.archive.ubuntu.com gutsy/main Sources [307kB]                 
Get:18 http://se.archive.ubuntu.com gutsy/multiverse Sources [57,3kB]          
Get:19 http://se.archive.ubuntu.com gutsy/universe Sources [1223kB]            
Hit http://archive.ubuntu.com gutsy-proposed/restricted Packages               
Hit http://archive.ubuntu.com gutsy-proposed/main Packages    
Hit http://archive.ubuntu.com gutsy-proposed/multiverse Packages               
Hit http://archive.ubuntu.com gutsy-proposed/universe Packages                 
Hit http://archive.ubuntu.com gutsy-backports/restricted Packages              
Hit http://archive.ubuntu.com gutsy-backports/main Packages                    
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages              
Hit http://archive.ubuntu.com gutsy-backports/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages                      
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages                
Hit http://archive.ubuntu.com gutsy-updates/universe Packages                  
Hit http://archive.ubuntu.com gutsy-security/main Packages                     
Hit http://archive.ubuntu.com gutsy-security/restricted Packages               
Hit http://archive.ubuntu.com gutsy-security/universe Packages
Hit http://archive.ubuntu.com gutsy-security/multiverse Packages               
Get:20 http://se.archive.ubuntu.com gutsy/universe Packages [4043kB]           
Get:21 http://se.archive.ubuntu.com gutsy/multiverse Packages [159kB]
Hit http://se.archive.ubuntu.com gutsy-updates/main Packages
Hit http://se.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://se.archive.ubuntu.com gutsy-updates/main Sources
Hit http://se.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://se.archive.ubuntu.com gutsy-backports/main Packages
Hit http://se.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://se.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://se.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://se.archive.ubuntu.com gutsy-backports/main Sources
Hit http://se.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://se.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://se.archive.ubuntu.com gutsy-backports/multiverse Sources
Fetched 7320kB in 5s (1290kB/s)                     
Reading package lists... Done

```

---

### Post by Pumalite on 2007-09-29
You can use Synaptic then>Search>ksensors>install

---

### Post by zooounds on 2007-09-29
Ksensors is not sensors-applet...

I hav tried using synaptic but that is the error message I get.

---

### Post by Pumalite on 2007-09-29
How about gkrellm?

---

### Post by zooounds on 2007-09-29
> **Pumalite said:**
> How about gkrellm?

I want sensors-applet.

---

