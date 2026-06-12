---
title: "Could not calculate the upgrade 13.10 -&gt; 14.04"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by HJQG3wT on 2014-04-29
Hello! I'm trying to upgrade 13.10 saucy to 14.04 trusty. It "could not calculate the upgrade". I tried to disable all my other software sources (see attached screencaps), but that didn't help.

```

sudo apt-get update && sudo apt-get dist-upgradeReading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Results of sudo do-release-upgrade -d (same without -d):
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done


Updating repository information
Ign http://archive.ubuntu.com trusty InRelease
Get:1 http://archive.ubuntu.com trusty Release.gpg [933 B]
Get:2 http://archive.ubuntu.com trusty Release [58.5 kB]
Get:3 http://archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]                                
Get:4 http://archive.ubuntu.com trusty/main i386 Packages [1,348 kB]                                 
Err http://archive.ubuntu.com trusty/main Translation-en_US                                          
                                                                                                     
Get:5 http://archive.ubuntu.com trusty/main Translation-en [762 kB]                                  
Err http://archive.ubuntu.com trusty/main Translation-en_US                                          
                                                                                                     
Err http://archive.ubuntu.com trusty/main Translation-en_US                                          
                                                                                                     
Err http://archive.ubuntu.com trusty/main Translation-en_US                                          
                                                                                                     
Ign http://archive.ubuntu.com trusty/main Translation-en_US                                          
Fetched 3,520 kB in 6s (248 kB/s)                                                                    


Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


Calculating the changes


Calculating the changes


Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
=== Command detached from window (Mon Apr 28 20:58:41 2014) ===
=== Command terminated with exit status 1 (Mon Apr 28 20:58:41 2014) ===



```

---

### Post by jose.dr.g on 2014-06-08
Did you ever resolve this? I'm having the same issue.

---

### Post by philinux on 2014-06-08
Jose

Post your sources.list

---

