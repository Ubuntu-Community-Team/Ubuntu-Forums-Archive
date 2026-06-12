---
title: "Update Problem"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by Belgatom on 2010-12-08
Running Ubuntu 10.10 on new pc. Was installed recently so haven't been able to work too long on it, but have been receiving updates correctly. 

Untill today, when I got the following problem:

[IMG]http://users.telenet.be/belgatom/ubuntu/Update.png[/IMG]

I assume this has something to do with my repositories. I'm not a linux fanatic just a user, so my apologies if this info is not complete. 

I probably should also post what is suggested to upgrade but I have no idea how to put this in text other then retyping everything in the update window by hand.

---

### Post by Belgatom on 2010-12-08
It's these four update that are blocking. When unselecting these, my updates go through. Did I install something dodgy? 

[IMG]http://users.telenet.be/belgatom/ubuntu/update2.png[/IMG]

---

### Post by plucky on 2010-12-08
Open a terminal (**Applications > Accessories > Terminal**) and run ```
sudo apt-get update
``` and post the output to the forum between [noparse]```

```[/noparse] blocks.

---

### Post by Belgatom on 2010-12-09
```
Hit http://be.archive.ubuntu.com maverick Release.gpg
Get:1 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://be.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Get:2 http://dl.google.com stable Release.gpg [197B]                           
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://be.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://be.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://be.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://be.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/ maverick/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://be.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/ maverick/main Translation-en_US
Hit http://linux.dropbox.com maverick Release.gpg                              
Hit http://extras.ubuntu.com maverick/main Sources                             
Ign http://be.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://be.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://be.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://be.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://be.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Get:3 http://dl.google.com stable Release [1,347B]                             
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://be.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Get:4 http://ppa.launchpad.net maverick Release [39.8kB]                       
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Ign http://be.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://be.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://be.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Ign http://be.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Ign http://be.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:5 http://dl.google.com stable/main i386 Packages [1,071B]                  
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://be.archive.ubuntu.com maverick Release                    
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://be.archive.ubuntu.com maverick-updates Release            
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://be.archive.ubuntu.com maverick/main Sources                         
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://be.archive.ubuntu.com maverick/restricted Sources         
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://be.archive.ubuntu.com maverick/universe Sources
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US
Hit http://be.archive.ubuntu.com maverick/multiverse Sources
Hit http://be.archive.ubuntu.com maverick/main i386 Packages
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Hit http://be.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://be.archive.ubuntu.com maverick/universe i386 Packages
Hit http://be.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://be.archive.ubuntu.com maverick-updates/main Sources
Hit http://be.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://be.archive.ubuntu.com maverick-updates/universe Sources
Hit http://be.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://be.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://be.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://linux.dropbox.com maverick Release
Hit http://be.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://be.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://linux.dropbox.com maverick/main i386 Packages
Fetched 2,932B in 0s (4,342B/s)
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

```

Sorry for the late reply. PC is at work and I was two days on the road.

---

### Post by dino99 on 2010-12-09
goto synaptic and uncheck the ppa (nautilus-elementary) and you'd better to use the "main" server instead of "be" which might not updated so often. Then update/upgrade.

---

### Post by sikander3786 on 2010-12-09
> Sorry for the late reply. PC is at work and I was two days on the road.

Go to Software Center > Edit > Software Sources > Other Software Tab and disable all the offensive Launchpad PPAs. Try apt-get update again.

---

### Post by Belgatom on 2010-12-09
> **dino99 said:**
> goto synaptic and uncheck the ppa (nautilus-elementary) and you'd better to use the "main" server instead of "be" which might not updated so often. Then update/upgrade.

Synaptic does not contain the nautilus-elementary.
Have updated server to main.

---

### Post by Belgatom on 2010-12-09
> **sikander3786 said:**
> Go to Software Center > Edit > Software Sources > Other Software Tab and disable all the offensive Launchpad PPAs. Try apt-get update again.


This worked. Installing Elementary did fail previously to this problem. I will try to resolve that problem in another thread. 

Thank you both for the help.

---

