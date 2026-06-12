---
title: "upgrade problem 16 lts to 17"
date: 2018-06-10
forum: Installation &amp; Upgrades
---

### Post by biarkivior on 2018-06-10
[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#3b4045]I have upgraded to ubuntu 17 from 16 lts using the pop up updater and after I get this pop up that states
[/COLOR][/FONT]
"Failure to download extra data files


The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.


ttf-mscorefonts-installer


The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection."

when i try to run the install i get a authenticate screen that never stops trying to work even when ii put in my passcode
I even tried to just upgrade to 18 lts after this and it will not upgrade and i  have tried using  the popup updater and have tried in terminal and no success. it seems

---

### Post by biarkivior on 2018-06-10
i wanted to add that the authentication required box states "Authentication required to run /usr/lib/update-notifier/package-data-downloader' as the super user
also i get a notifier when trying to go to 18 that i need an internet connection

owner@owner-Ubuntu:~$ ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Half 1000baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

---

### Post by oldos2er on 2018-06-10
If you're trying to upgrade to 17.04, you'll need to use the info [here]("https://help.ubuntu.com/community/EOLUpgrades"), but you should be able to upgrade to 18.04 from 16.04x with ```
do-release-upgrade -d
```

---

### Post by biarkivior on 2018-06-10
i have 17.10 currently and get the following message when i try to upgrade to 18.04
```
owner@owner-Ubuntu:~$ sudo apt-get update
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful InRelease               
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful InRelease               
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates InRelease [88.7 kB]
Ign:6 [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                           
Hit:7 [http://archive.canonical.com](http://archive.canonical.com) precise Release                             
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-backports InRelease [74.6 kB]
Err:10 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg       
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-security InRelease [83.2 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/main amd64 DEP-11 Metadata [83.6 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/main DEP-11 64x64 Icons [44.9 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe amd64 DEP-11 Metadata [83.7 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe DEP-11 64x64 Icons [106 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-backports/universe amd64 DEP-11 Metadata [5,092 B]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-security/main amd64 DEP-11 Metadata [27.9 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-security/main DEP-11 64x64 Icons [31.8 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-security/universe amd64 DEP-11 Metadata [39.6 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-security/universe DEP-11 64x64 Icons [39.7 kB]
Fetched 711 kB in 1s (539 kB/s)                                       
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch [http://archive.canonical.com/dists/precise/Release.gpg](http://archive.canonical.com/dists/precise/Release.gpg)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Some index files failed to download. They have been ignored, or old ones used instead.
owner@owner-Ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
owner@owner-Ubuntu:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]                                           
Get:2 Upgrade tool [1,257 kB]                                                  
Fetched 1,258 kB in 0s (0 B/s)                                                 
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg' 
extracting 'bionic.tar.gz'


Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Ign [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                     
Hit [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                       
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful InRelease                       
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates InRelease               
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful InRelease                       
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-backports InRelease             
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-security InRelease              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
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


Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                       
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                       
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [83.2 kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB] 
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]  
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [119 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [108 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [74.7 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [30.5 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [79.8 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [79.6 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [117 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [188 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,100 B]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [2,456 B]
Fetched 1,045 kB in 0s (0 B/s)                                                 
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                       
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                       
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease              
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
Fetched 0 B in 0s (0 B/s)                                                      
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                       
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                       
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease              
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
Fetched 0 B in 0s (0 B/s)                                                      


Error during update 


A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
owner@owner-Ubuntu:~$
```

---

### Post by oldos2er on 2018-06-10
To add the missing PUBKEY run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

You have a wired internet connection? I've never seen that particular error when trying to upgrade to a newer version. Hopefully someone else has, and can help you.

---

### Post by deadflowr on 2018-06-10
You should really disable the problem archive, since it is 12.04 related and no longer supported anyway.
And you already have the proper archive enabled

To disable open the souirces.list file
```
sudo nano /etc/apt/sources.list
```
find the entries for 
```
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
```
and add a comment to the front
```
#deb http://archive.canonical.com/ubuntu precise partner
#deb-src http://archive.canonical.com/ubuntu precise partner
```
then save and close (ctrl + x then press Y to save and then press enter to close)
then try reloading apt update again.

---

### Post by biarkivior on 2018-06-10
yes i have a wired connection. thank you for the  key code
i couldn't find it any where

---

### Post by biarkivior on 2018-06-10
```
Executing: /tmp/apt-key-gpghome.hl3h7s4tht/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: key 40976EAF437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
owner@owner-Ubuntu:~$ sudo nano /etc/apt/sources.list
owner@owner-Ubuntu:~$ sudo get-apt upgrade -d
sudo: get-apt: command not found
owner@owner-Ubuntu:~$ apt-get update -d
Reading package lists... Done
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
owner@owner-Ubuntu:~$ sudo apt-get update
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                        
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful InRelease                                        
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates InRelease [88.7 kB]                      
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful InRelease                         
Ign:7 [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                 
Hit:8 [http://archive.canonical.com](http://archive.canonical.com) precise Release                       
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-backports InRelease [74.6 kB]
Err:10 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg       
  The following signatures were invalid: 630239CC130E1A7FD81A27B140976EAF437D05B5
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-security InRelease [83.2 kB]
Fetched 247 kB in 1s (238 kB/s)     
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: 630239CC130E1A7FD81A27B140976EAF437D05B5
W: Failed to fetch [http://archive.canonical.com/dists/precise/Release.gpg](http://archive.canonical.com/dists/precise/Release.gpg)  The following signatures were invalid: 630239CC130E1A7FD81A27B140976EAF437D05B5
W: Some index files failed to download. They have been ignored, or old ones used instead.
owner@owner-Ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
owner@owner-Ubuntu:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]                                                              
Get:2 Upgrade tool [1,257 kB]                                                                     
Fetched 1,258 kB in 0s (0 B/s)                                                                    
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg' 
extracting 'bionic.tar.gz'


Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Ign [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                        
Hit [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                          
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful InRelease                                          
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful InRelease                                          
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates InRelease [88.7 kB]                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                  
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                              
  The following signatures were invalid: 630239CC130E1A7FD81A27B140976EAF437D05B5                 
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-backports InRelease [74.6 kB]                    
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-security InRelease [83.2 kB]                     
Fetched 247 kB in 0s (0 B/s)                                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done


Updating repository information


Third party sources disabled 


Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 


To continue please press [ENTER]


Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                                          
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                                          
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [83.2 kB]                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                  
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                              
  The following signatures were invalid: 630239CC130E1A7FD81A27B140976EAF437D05B5                 
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]                    
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]                     
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [79.7 kB]         
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [79.8 kB]        
Fetched 400 kB in 0s (0 B/s)                                                                      
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                                          
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                                          
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                  
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                              
  The following signatures were invalid: 630239CC130E1A7FD81A27B140976EAF437D05B5                 
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]                     
Fetched 158 kB in 0s (0 B/s)                                                                      
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                                          
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                                          
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                  
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                              
  The following signatures were invalid: 630239CC130E1A7FD81A27B140976EAF437D05B5                 
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]                     
Fetched 158 kB in 0s (0 B/s)                                                                      


Error during update 


A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
owner@owner-Ubuntu:~$
```

---

### Post by deadflowr on 2018-06-10
post the output from
```
cat /etc/apt/sources.list
```

please use code tags when posting terminal output:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by biarkivior on 2018-06-10
[https://ubuntuforums.org/showthread....8#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to



# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful restricted main multiverse universe #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-updates restricted main multiverse universe #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-backports main restricted universe multiverse #Added by software-properties


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner


# deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


owner@owner-Ubuntu:~$
```

---

### Post by deadflowr on 2018-06-10
You still have a precise entry here:
```
# deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner
# deb-src http://archive.canonical.com/ precise partner
#deb http://archive.canonical.com/ubuntu precise partner
#deb-src http://archive.canonical.com/ubuntu precise partner
```

you need to add a comment (#) to the one that does not have one.
it'll disable the entry and stop the errors.

---

### Post by biarkivior on 2018-06-21
evidently i still have the same problem and no solution

---

### Post by biarkivior on 2018-06-21
thank you deadflowr it worked

---

### Post by monkeybrain20122 on 2018-06-21
FYI 17.10 expires in a few weeks. 

And for all that upgrade problems and keeping your mess from one version to the next (if successful) take you 20 minutes max for a clean install, another 10 to reinstall your software. You are up and running in no time instead trouble shooting what might have gone wrong with "upgrade".

---

### Post by jflaker on 2019-02-18
Fixed it for me!!!

---

### Post by coffeecat on 2019-02-19
Back to sleep, old thread about a long unsupported upgrade path.

---

