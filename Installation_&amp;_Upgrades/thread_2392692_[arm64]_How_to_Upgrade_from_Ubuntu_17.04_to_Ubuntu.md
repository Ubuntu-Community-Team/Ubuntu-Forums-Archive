---
title: "[arm64] How to Upgrade from Ubuntu 17.04 to Ubuntu 18.04 LTS on arm64?"
date: 2018-05-24
forum: Installation &amp; Upgrades
---

### Post by lukaszgryglicki on 2018-05-24
Hi.
I have a 17.04 box running on arm64 (packet.net server with 96 cores).
I also have 2 other servers amd64 with 17.04 (also packet.net servers, both 48 cores).

I've succesfully updated both amd64 versions from 17.04 -> 18.04 LTS (I needed to update /etc/apt/sources.list to old-release stuff). It was easy.

But for arm64 version it fail;s during the actual `do-release-upgrade` due to missing paths to arm64 packages.

Can anybody suggest a solution?

```
uname -a --> Linux devstats.team.io 4.10.0-38-generic #42~16.04.1-Ubuntu SMP Tue Oct 10 16:33:57 UTC 2017 aarch64 aarch64 aarch64 GNU/Linux
lsb_release -a:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty
root@devstats:~# 

```



Here is the full output of "do-release-upgrade":

```
sudo do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)


Get:1 Upgrade tool signature [819 B]                                                                                                                                                                                                                          
Get:2 Upgrade tool [1,253 kB]                                                                                                                                                                                                                                 
Fetched 1,254 kB in 0s (0 B/s)                                                                                                                                                                                                                                
authenticate 'artful.tar.gz' against 'artful.tar.gz.gpg' 
extracting 'artful.tar.gz'
[screen is terminating]
root@devstats:~# 
root@devstats:~# sudo apt update
Hit:1 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty InRelease
Hit:2 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty-updates InRelease
Hit:3 [https://repos.influxdata.com/ubuntu](https://repos.influxdata.com/ubuntu) zesty InRelease
Ign:4 [http://old-releases.ubuntu.com/ubuntu/zesty-security](http://old-releases.ubuntu.com/ubuntu/zesty-security) main InRelease
Err:5 [http://old-releases.ubuntu.com/ubuntu/zesty-security](http://old-releases.ubuntu.com/ubuntu/zesty-security) main Release
  404  Not Found
Reading package lists... Done
E: The repository 'http://old-releases.ubuntu.com/ubuntu/zesty-security main Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
root@devstats:~# vim /etc/apt/sources.list
root@devstats:~# sudo apt update
Hit:1 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty InRelease
Hit:2 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty-updates InRelease
Hit:3 [https://repos.influxdata.com/ubuntu](https://repos.influxdata.com/ubuntu) zesty InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
root@devstats:~# sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@devstats:~# sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@devstats:~# sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@devstats:~# sudo apt install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version (1:17.04.8).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@devstats:~# sudo do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)


Get:1 Upgrade tool signature [819 B]                                                                                                                                                                                                                          
Get:2 Upgrade tool [1,253 kB]                                                                                                                                                                                                                                 
Fetched 1,254 kB in 0s (0 B/s)                                                                                                                                                                                                                                
authenticate 'artful.tar.gz' against 'artful.tar.gz.gpg' 
extracting 'artful.tar.gz'


Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/main arm64 Packages                                                                                                                                                                                            
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe arm64 Packages                                                                                                                                                                                        
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/multiverse arm64 Packages                                                                                                                                                                                      
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/main arm64 Packages                                                                                                                                                                                            
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe arm64 Packages                                                                                                                                                                                        
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/main arm64 Packages                                                                                                                                                                                    
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/main Translation-en [118 kB]                                                                                                                                                                         
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/restricted Translation-en [1,284 B]                                                                                                                                                                  
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe arm64 Packages                                                                                                                                                                                
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe Translation-en [63.3 kB]                                                                                                                                                                    
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/multiverse arm64 Packages                                                                                                                                                                              
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/multiverse Translation-en [2,264 B]                                                                                                                                                                 
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/multiverse arm64 Packages                                                                                                                                                                                      
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/main arm64 Packages                                                                                                                                                                                            
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Ign [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe arm64 Packages                                                                                                                                                                                        
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/main arm64 Packages                                                                                                                                                                                    
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe arm64 Packages                                                                                                                                                                                
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/multiverse arm64 Packages                                                                                                                                                                              
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Ign [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/multiverse arm64 Packages                                                                                                                                                                                      
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/main arm64 Packages                                                                                                                                                                                    
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe arm64 Packages                                                                                                                                                                                
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/multiverse arm64 Packages                                                                                                                                                                              
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Err [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/main arm64 Packages                                                                                                                                                                                    
  404  Not Found [IP: 2001:67c:1562::19 80]                                                                                                                                                                                                                   
Ign [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe arm64 Packages                                                                                                                                                                                
Ign [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/multiverse arm64 Packages                                                                                                                                                                              
Fetched 325 kB in 0s (0 B/s)                                                                                                                                                                                                                                  


Error during update 


A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 


E:Failed to fetch 
[http://us.archive.ubuntu.com/ubuntu/dists/artful/main/binary-arm64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/artful/main/binary-arm64/Packages) 
404 Not Found [IP: 2001:67c:1562::19 80], E:Failed to fetch 
[http://us.archive.ubuntu.com/ubuntu/dists/artful-updates/main/binary-arm64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/artful-updates/main/binary-arm64/Packages) 
404 Not Found [IP: 2001:67c:1562::19 80], E:Some index files failed 
to download. They have been ignored, or old ones used instead. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
=== Command detached from window (Thu May 24 05:49:47 2018) ===
=== Command terminated with exit status 1 (Thu May 24 05:49:57 2018) ===
```

---

### Post by wildmanne39 on 2018-05-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by lukaszgryglicki on 2018-05-24
I'll do, sorry.

---

### Post by lukaszgryglicki on 2018-05-29
Nobody can help?

---

### Post by lukaszgryglicki on 2018-06-14
Maybe I've reported it in a wrong place? Where can I put this to get some feedback?

---

