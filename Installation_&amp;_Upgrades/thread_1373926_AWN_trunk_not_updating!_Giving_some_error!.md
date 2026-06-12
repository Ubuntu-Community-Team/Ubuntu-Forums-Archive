---
title: "AWN trunk not updating! Giving some error!"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by chinmaya_n on 2010-01-06
When i try to update my system then it cannot update the AWN trunk!
I dont know Y?
Here is the error report!
```
W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/pool/main/a/avant-window-navigator-trunk/python-awn-trunk_0.3.9.1~bzr1800-1.9.10_i386.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/pool/main/a/avant-window-navigator-trunk/libawn1-trunk_0.3.9.1~bzr1800-1.9.10_i386.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/pool/main/a/avant-window-navigator-trunk/avant-window-navigator-trunk_0.3.9.1~bzr1800-1.9.10_i386.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/pool/main/a/avant-window-navigator-trunk/avant-window-navigator-data-trunk_0.3.9.1~bzr1800-1.9.10_all.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/pool/main/a/awn-extras-applets-trunk/awn-applets-c-core-trunk_0.3.9.1~bzr1873-1.9.10_i386.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/pool/main/a/awn-extras-applets-trunk/python-awn-extras-trunk_0.3.9.1~bzr1873-1.9.10_i386.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/pool/main/a/awn-extras-applets-trunk/awn-applets-python-core-trunk_0.3.9.1~bzr1873-1.9.10_all.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/pool/main/a/avant-window-navigator-trunk/awn-settings-trunk_0.3.9.1~bzr1800-1.9.10_all.deb
  404  Not Found

``` Why is it happening so? Why can't it just get its packages?

---

### Post by arubislander on 2010-01-06
open a terminal window and try:
```
$ sudo apt-get update
```
and then try to update your system again and post back the results.

---

### Post by chinmaya_n on 2010-01-06
This is the output for **$ sudo apt-get update**:
```
Get:1 http://in.archive.ubuntu.com karmic Release.gpg [189B]                   
Ign http://in.archive.ubuntu.com karmic/main Translation-en_IN                 
Ign http://in.archive.ubuntu.com karmic/restricted Translation-en_IN           
Ign http://in.archive.ubuntu.com karmic/universe Translation-en_IN             
Ign http://in.archive.ubuntu.com karmic/multiverse Translation-en_IN           
Get:2 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Get:3 http://in.archive.ubuntu.com karmic-updates Release.gpg [189B]           
Ign http://in.archive.ubuntu.com karmic-updates/main Translation-en_IN         
Ign http://in.archive.ubuntu.com karmic-updates/restricted Translation-en_IN   
Ign http://in.archive.ubuntu.com karmic-updates/universe Translation-en_IN     
Ign http://ppa.launchpad.net karmic/main Translation-en_IN                     
Get:4 http://ppa.launchpad.net karmic Release.gpg [307B]     
Ign http://in.archive.ubuntu.com karmic-updates/multiverse Translation-en_IN
Get:5 http://in.archive.ubuntu.com karmic Release [65.9kB]
Ign http://ppa.launchpad.net karmic/main Translation-en_IN                     
Hit http://ppa.launchpad.net karmic Release                                    
Err http://ppa.launchpad.net karmic Release                                    
  
Get:6 http://ppa.launchpad.net karmic Release [66.0kB]                         
Get:7 http://security.ubuntu.com karmic-security Release.gpg [189B]            
Ign http://security.ubuntu.com karmic-security/main Translation-en_IN          
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_IN    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_IN      
Get:8 http://ppa.launchpad.net karmic/main Sources [530B]                   
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_IN    
Get:9 http://security.ubuntu.com karmic-security Release [44.1kB]              
Err http://security.ubuntu.com karmic-security Release                         
  
Get:10 http://in.archive.ubuntu.com karmic-updates Release [44.1kB]            
Get:11 http://in.archive.ubuntu.com karmic/main Packages [1,353kB]             
Get:12 http://in.archive.ubuntu.com karmic/restricted Packages [7,971B]        
Get:13 http://in.archive.ubuntu.com karmic/main Sources [640kB]                
Get:14 http://in.archive.ubuntu.com karmic/restricted Sources [3,270B]         
Get:15 http://in.archive.ubuntu.com karmic/universe Packages [5,133kB]         
Get:16 http://in.archive.ubuntu.com karmic/universe Packages [5,133kB]         
Get:17 http://in.archive.ubuntu.com karmic/universe Packages [5,133kB]         
Get:18 http://in.archive.ubuntu.com karmic/universe Packages [5,133kB]         
Get:19 http://in.archive.ubuntu.com karmic/universe Packages [5,133kB]         
Get:20 http://in.archive.ubuntu.com karmic/universe Packages [5,133kB]         
Get:21 http://in.archive.ubuntu.com karmic/universe Sources [2,795kB]          
Get:22 http://in.archive.ubuntu.com karmic/multiverse Packages [190kB]         
Get:23 http://in.archive.ubuntu.com karmic/multiverse Sources [116kB]          
Get:24 http://in.archive.ubuntu.com karmic-updates/main Packages [125kB]       
Get:25 http://in.archive.ubuntu.com karmic-updates/restricted Packages [14B]   
Get:26 http://in.archive.ubuntu.com karmic-updates/main Sources [38.9kB]       
Get:27 http://in.archive.ubuntu.com karmic-updates/restricted Sources [14B]    
Get:28 http://in.archive.ubuntu.com karmic-updates/universe Packages [75.8kB]  
Get:29 http://in.archive.ubuntu.com karmic-updates/universe Sources [18.4kB]   
Get:30 http://in.archive.ubuntu.com karmic-updates/multiverse Packages [6,942B]
Get:31 http://in.archive.ubuntu.com karmic-updates/multiverse Sources [3,831B] 
Fetched 10.7MB in 21min 23s (8,356B/s)                                         
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net karmic Release: The following signatures were invalid: BADSIG 7D2C7A23BF810CD5 Launchpad PPA for Awn Testing Team

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/karmic/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Does anyone know Y?

---

### Post by arubislander on 2010-01-08
In the past you added the [http://ppa.launchpad.net/awn-testing](http://ppa.launchpad.net/awn-testing) respository to your repository source... maybe you should delete that and try adding them again?

---

### Post by chinmaya_n on 2010-01-14
A bit busy... so, late reply! ;)
NO use....! It gave same error even after removing those lines and adding them! 
Does anyone have any hints?! ;)

---

### Post by arubislander on 2010-01-14
Have you already tried following the instructions from [here]("http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive")?

Anyhow, there seems to be something wrong with the repositories GPG key, because when I try:
```
$ sudo add-apt-repository ppa:awn-testing
``` in Karmic I get:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B0BE17C2A0C914F086B7B8327D2C7A23BF810CD5
gpg: requesting key BF810CD5 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

---

### Post by chinmaya_n on 2010-01-21
Thanx to everyone....!

Today it updated cleanly with out any error!
I think the problem was with the server or might be a bug fixed!

Once again THanx to everyone!

---

