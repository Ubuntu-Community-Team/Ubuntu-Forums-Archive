---
title: "Upgrade from 16.04 to 18.04 fails without any error messages"
date: 2018-09-04
forum: Installation &amp; Upgrades
---

### Post by hojjat on 2018-09-04
After running *apt-get upgrade* and *apt-get dist-upgrade* I ran the following command, and it just says "Aborting" without specifying why. How can I troubleshoot this?

```

&#10140;  ~ sudo do-release-upgrade -d  
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]                                           
Get:2 Upgrade tool [1,258 kB]                                                  
Fetched 1,259 kB in 0s (0 B/s)                                                 
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg' 
extracting 'bionic.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit http://us.archive.ubuntu.com/ubuntu xenial InRelease                                            
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]                         
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]                       
Hit http://packages.microsoft.com/repos/vscode stable InRelease                                     
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [320 kB]        
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]                          
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [225 kB]           
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [247 kB]    
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [335 kB]       
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,960 B] 
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]    
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]    
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [5,100 B]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [67.7 kB]       
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [68.0 kB]          
Get:14 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [107 kB]    
Get:15 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [147 kB]       
Fetched 1,867 kB in 0s (0 B/s)                                                                      
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

```

---

### Post by dsstorefile1 on 2018-09-06
Is there a reason why you're trying to upgrade to the development version of Ubuntu?

---

### Post by Frogs Hair on 2018-09-06
> **dsstorefile1 said:**
> Is there a reason why you're trying to upgrade to the development version of Ubuntu?

18.04 is not a development release. 

[COLOR=#000000]hojjat: Please make sure that the system is fully up to date and you're not running any third party software that could interfere with the upgrade. A clean installation is much faster if you have a means to backup your files and move them temporally to removable drive or cloud storage. [/COLOR]

---

### Post by hojjat on 2018-09-08
Well, I would prefer not to do a clean install, because I have to reconfigure a bunch of things again which is time consuming.

Is there a way for me to update to 17.04 first, and then to 18.04? If yes, how do I tell Ubuntu which version to upgrade to?

---

