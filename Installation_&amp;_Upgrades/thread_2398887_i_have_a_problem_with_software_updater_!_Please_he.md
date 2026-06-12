---
title: "i have a problem with software updater ! Please help me"
date: 2018-08-18
forum: Installation &amp; Upgrades
---

### Post by xxmehmetali on 2018-08-18
i want to upgrade my pc from 16.04 to 18.04 but i have a problem.
the problem is : "Failed to download repository information. Check your internet connection."

And i changed the "Download From"
Please help me guys

---

### Post by deadflowr on 2018-08-18
*Thread moved to** Installation and Upgrades***

Please run the following command and post back the results:
```
sudo apt update
```

---

### Post by xxmehmetali on 2018-08-18
> **deadflowr said:**
> *Thread moved to** Installation and Upgrades***

Please run the following command and post back the results:
```
sudo apt update
```

```
[sudo] password for ali: Hit:1 http://download.virtualbox.org/virtualbox/debian trusty InRelease
Hit:2 http://ppa.launchpad.net/docky-core/stable/ubuntu xenial InRelease       
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:4 http://repo.steampowered.com/steam precise InRelease                     
Hit:5 http://tr.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:7 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease    
Get:8 http://tr.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]    
Hit:9 http://ppa.launchpad.net/numix/ppa/ubuntu xenial InRelease               
Hit:10 http://repository.spotify.com stable InRelease                          
Ign:11 http://downloads.sourceforge.net/project/xenlism-wildfire/repo deb/ InRelease
Hit:13 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease             
Get:14 http://tr.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB] 
Err:15 http://downloads.sourceforge.net/project/xenlism-wildfire/repo deb/ Release
  404  Not Found
Hit:16 http://ppa.launchpad.net/oranchelo/oranchelo-icon-theme/ubuntu xenial InRelease
Get:17 http://tr.archive.ubuntu.com/ubuntu xenial-security InRelease [107 kB]  
Hit:18 https://download.sublimetext.com apt/stable/ InRelease                  
Hit:19 http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu xenial InRelease 
Hit:20 http://ppa.launchpad.net/snwh/pulp/ubuntu xenial InRelease              
Hit:21 http://ppa.launchpad.net/tista/adapta/ubuntu xenial InRelease           
Hit:22 http://ppa.launchpad.net/twodopeshaggy/jarun/ubuntu xenial InRelease    
Err:23 http://archive.getdeb.net/ubuntu xenial-getdeb InRelease                 
  Could not connect to archive.getdeb.net:80 (144.76.200.19), connection timed out
Reading package lists... Done                        
W: http://download.virtualbox.org/virtualbox/debian/dists/trusty/InRelease: Signature by key 7B0FAB3A13B907435925D9C954422A4B98AB5139 uses weak digest algorithm (SHA1)
E: The repository 'http://downloads.sourceforge.net/project/xenlism-wildfire/repo deb/ Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by deadflowr on 2018-08-19
Open the Program called Software and Updates and go to the section Other Software and uncheck the listings for sourceforge, getdeb and virtualbox.
The close and reload and see what the apt-get update command shows.

More troubling, though, is the amount of PPAs and 3rd party repositories added.
Though most seem pretty innocuous, (the various theme and icon ones) a few might be troubling to have if you want to do an upgrade from 16.04 to 18.04.

In that regard, I would highly recommend not doing an upgrade and instead if you want 18.04, go clean and install a fresh version of 18.04.
(Or you can try to painstakingly reset all packages which might have been upgraded to newer versions with any added repo to the original xenial package state and then hope an upgrade will work right,
that's your choice, but not one many would make)

---

### Post by xenatt2 on 2018-09-19
You can use launchpad ppa.
```

[COLOR=#4E4E4E][FONT=&amp]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2B80AC38[/FONT][/COLOR]
[COLOR=#4E4E4E][FONT=&amp]sudo add-apt-repository ppa:xenatt/xenlism[/FONT][/COLOR]
[COLOR=#4E4E4E][FONT=&amp]sudo apt-get update[/FONT][/COLOR]
[COLOR=#4E4E4E][FONT=&amp]sudo apt-get install xenlism-wildfire-icon-theme 
[/FONT][/COLOR][COLOR=#4E4E4E][FONT=&amp]sudo apt-get install xenlism-storm-icon-theme[/FONT][/COLOR]
```[COLOR=#4E4E4E][FONT=&amp]
[/FONT][/COLOR]

---

