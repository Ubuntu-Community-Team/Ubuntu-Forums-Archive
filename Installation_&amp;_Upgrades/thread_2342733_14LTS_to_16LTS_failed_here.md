---
title: "14LTS to 16LTS failed here"
date: 2016-11-09
forum: Installation &amp; Upgrades
---

### Post by FerryGnu on 2016-11-09
Using both the Update Manager and "do-release-upgrade" in Terminal, it fails and rolls back. Any thoughts on how I can get past this and upgrade?

```

Hit http://us.archive.ubuntu.com xenial-backports/main Translation-en          
Hit http://us.archive.ubuntu.com xenial-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com xenial-backports/restricted Translation-en    
Fetched 0 B in 0s (0 B/s)                                                      

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch http://archive.ubuntu.com/ubuntu/Packages 404 Not 
Found [IP: 91.189.88.152 80] 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 

Restoring original system state

Aborting

```

---

### Post by ubfan1 on 2016-11-09
From the Software Updater "Settings" button (lower left of window) or the Software & Updates itself, under the updates  tab, turn off the unsupported xenial backports.  Then under the other software tab, uncheck any third party items.  Then rerun the software updater and it should first fix up the necessary repositories for the update, and do it.  Or from a terminal, sudo apt-get update  and then the sudo apt-get dist-upgrade.

---

