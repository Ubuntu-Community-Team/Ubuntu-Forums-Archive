---
title: "Missing public key when trying to upgrade to 22.04 LTS"
date: 2022-10-18
forum: Installation &amp; Upgrades
---

### Post by saulspatz on 2022-10-18
I have tried twice  to upgrade to 22.04 LTS from 20.04 LTS.  Each time, it has failed, with the message: ```
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 23F3D4EA75716059
```

I tried```
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 23F3D4EA75716059
```

and got the response

```
Executing: /tmp/apt-key-gpghome.VxKkt5VEt5/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 23F3D4EA75716059
gpg: key 23F3D4EA75716059: public key "GitHub CLI <opensource+cli@github.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1

```
Afetr the second failure, I ran the same command again, but this time I got the response

```
gpg: key 23F3D4EA75716059: "GitHub CLI <opensource+cli@github.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1



```

which suggests that it worked the first time.  What is going on?  What should I do?

Here is the entire output from the second attempt:

```
~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]                                           
Get:2 Upgrade tool [1,265 kB]                                                  
Fetched 1,266 kB in 0s (0 B/s)                                                 
authenticate 'jammy.tar.gz' against 'jammy.tar.gz.gpg' 
extracting 'jammy.tar.gz'


Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Get:1 https://cli.github.com/packages stable InRelease [3,917 B]               
Hit http://us.archive.ubuntu.com/ubuntu focal InRelease                        
Hit https://brave-browser-apt-release.s3.brave.com stable InRelease            
Hit http://us.archive.ubuntu.com/ubuntu focal-updates InRelease                
Hit http://us.archive.ubuntu.com/ubuntu focal-backports InRelease              
Err https://cli.github.com/packages stable InRelease                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 23F3D4EA75716059
Hit http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal InRelease             
Hit http://security.ubuntu.com/ubuntu focal-security InRelease                 
Hit http://ppa.launchpad.net/inkscape.dev/stable/ubuntu focal InRelease        
Ign https://repo.vivaldi.com/stable/deb stable InRelease                       
Hit https://repo.vivaldi.com/stable/deb stable Release                         
Ign http://ppa.launchpad.net/michael-gruz/canon/ubuntu focal InRelease         
Err http://ppa.launchpad.net/michael-gruz/canon/ubuntu focal Release           
  404  Not Found [IP: 2620:2d:4000:1::3e 80]                                   
Fetched 0 B in 0s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
None


Checking for installed snaps


Calculating snap size requirements


Updating repository information


Third party sources disabled 


Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 


To continue please press [ENTER]


Get:1 https://cli.github.com/packages stable InRelease [3,917 B]               
Hit http://us.archive.ubuntu.com/ubuntu jammy InRelease                        
Hit https://brave-browser-apt-release.s3.brave.com stable InRelease            
Hit http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease                
Err https://cli.github.com/packages stable InRelease                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 23F3D4EA75716059
Hit http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease              
Hit http://security.ubuntu.com/ubuntu jammy-security InRelease                 
Fetched 0 B in 0s (0 B/s)                                                      
Get:1 https://cli.github.com/packages stable InRelease [3,917 B]               
Hit http://us.archive.ubuntu.com/ubuntu jammy InRelease                        
Get:2 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease [114 kB]     
Hit https://brave-browser-apt-release.s3.brave.com stable InRelease            
Err https://cli.github.com/packages stable InRelease                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 23F3D4EA75716059
Hit http://security.ubuntu.com/ubuntu jammy-security InRelease                 
Get:3 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]  
Fetched 214 kB in 0s (0 B/s)                                                   
Get:1 https://cli.github.com/packages stable InRelease [3,917 B]               
Hit https://brave-browser-apt-release.s3.brave.com stable InRelease            
Hit http://us.archive.ubuntu.com/ubuntu jammy InRelease                        
Hit http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease                
Err https://cli.github.com/packages stable InRelease                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 23F3D4EA75716059
Get:2 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]  
Hit http://security.ubuntu.com/ubuntu jammy-security InRelease                 
Fetched 99.8 kB in 0s (0 B/s)                                                  


Error during update 


A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

```

It suggests checking my network, but there doesn't seem to be any problem.  Is there a specific test I should run?

---

### Post by ubfan1 on 2022-10-18
Try disabling all third part repos, update, then the do-release upgrade.  Add back in repos after the upgrade.

---

### Post by saulspatz on 2022-10-19
Thanks.  It made no difference, so far as I can see.  Any other suggestions?

---

