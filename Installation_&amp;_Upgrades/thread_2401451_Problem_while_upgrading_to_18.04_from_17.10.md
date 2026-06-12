---
title: "Problem while upgrading to 18.04 from 17.10"
date: 2018-09-18
forum: Installation &amp; Upgrades
---

### Post by mandalaritra1 on 2018-09-18
Hi,

I used the code

```
sudo do-release-upgrade
```

But the upgrade is not starting because of certain reasons that I couldn't understand.
Please help me out regarding this.
Thank you. 

The results are..
```
sudo do-release-upgrade
[sudo] password for topper: 
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife


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
Ign http://dl.google.com/linux/chrome/deb stable InRelease                     
Hit http://dl.google.com/linux/chrome/deb stable Release                       
Hit http://archive.ubuntu.com/ubuntu bionic InRelease                          
Hit http://archive.canonical.com/ubuntu bionic InRelease                       
Hit http://archive.ubuntu.com/ubuntu bionic-updates InRelease                  
Hit http://archive.ubuntu.com/ubuntu bionic-backports InRelease                
Hit http://archive.ubuntu.com/ubuntu bionic-security InRelease                 
Fetched 0 B in 0s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done


Updating repository information


Third party sources disabled 


Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 


To continue please press [ENTER]


Hit http://archive.ubuntu.com/ubuntu bionic InRelease                          
Hit http://archive.canonical.com/ubuntu bionic InRelease                       
Hit http://archive.ubuntu.com/ubuntu bionic-updates InRelease                  
Hit http://archive.ubuntu.com/ubuntu bionic-backports InRelease                
Hit http://archive.ubuntu.com/ubuntu bionic-security InRelease                 
Fetched 0 B in 0s (0 B/s)                                                      


Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done


Calculating the changes


Calculating the changes


Do you want to start the upgrade? 




62 installed packages are no longer supported by Canonical. You can 
still get support from the community. 


5 packages are going to be removed. 220 new packages are going to be 
installed. 1562 packages are going to be upgraded. 


You have to download a total of 5,653 k. This download will take 
about 43 seconds with a 1Mbit DSL connection and about 13 minutes 
with a 56k modem. 


Fetching and installing the upgrade can take several hours. Once the 
download has finished, the process cannot be canceled. 


 Continue [yN]  Details [d]yn


Lock screen disabled 


Your lock screen has been disabled and will remain disabled until you 
reboot. 


To continue please press [ENTER]
Inhibiting until Ctrl+C is pressed...




Fetching
Err http://archive.ubuntu.com/ubuntu bionic/universe amd64 libjs-mathjax all 2.7.3+dfsg-1
  Connection failed [IP: 91.189.88.152 80]                                     
Err http://archive.ubuntu.com/ubuntu bionic/universe i386 libjs-mathjax all 2.7.3+dfsg-1
  Connection failed [IP: 91.189.88.152 80]                                     
Err http://archive.ubuntu.com/ubuntu bionic/universe amd64 libjs-mathjax all 2.7.3+dfsg-1                                                    
  Connection failed [IP: 91.189.88.152 80]                                                                                                   
99% [Waiting for headers]                                                                                                                    



```

---

### Post by Autodave on 2018-09-18
Hopefully someone else will jump in here.  However, in my experience, I have always found it easier and faster to just wipe the old install and do a fresh install.  Make sure that you back up everything to an external source first!!!

---

