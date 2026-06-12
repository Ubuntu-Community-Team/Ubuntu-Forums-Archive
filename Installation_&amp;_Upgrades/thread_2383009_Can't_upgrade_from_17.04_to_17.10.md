---
title: "Can't upgrade from 17.04 to 17.10"
date: 2018-01-19
forum: Installation &amp; Upgrades
---

### Post by ubunt72 on 2018-01-19
I am trying to upgrade from 17.04 to 17.10 but can't because I get a message that stops early in the process.

Here are the messages:
Error during update
A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
E:The repository 'http://archive.ubuntu.com/ubuntu stable Release' does not have a Release file.

I tried a google search with the text and I'm not getting anywhere.

I am not sure what is wrong.

What is wrong with the repo?   I don't know.   

I think someone will recognize what's going on so I hope someone who does reads this post and can provide some feedback.  

Thanks in advance for any replies and suggestions/info.

In the meantime, I'll try to find some info that might suggest what's going on.

---

### Post by cruzer001 on 2018-01-19
You have waited a bit too long to upgrade :(

[https://ubuntuforums.org/showthread.php?t=2382982](https://ubuntuforums.org/showthread.php?t=2382982)

---

### Post by ubunt72 on 2018-01-19
> **cruzer001 said:**
> You have waited a bit too long to upgrade :(

[https://ubuntuforums.org/showthread.php?t=2382982](https://ubuntuforums.org/showthread.php?t=2382982)Are you saying there's no way to upgrade now?

So, my /etc/apt/sources.list file is no good any more?   I have this, currently:
deb cdrom:[Ubuntu-GNOME 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) zesty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty-updates main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) zesty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) zesty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty-updates universe

So edit this and only have this there?:
## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse

next (2nd) step:
sudo aptitude update && sudo aptitude safe-upgrade

third step:
sudo apt-get update
sudo apt-get dist-upgrade
sudo do-release-upgrade

(do I just need the third command or all three?)

Is this what I have to do?

---

### Post by cruzer001 on 2018-01-19
> **ubunt72 said:**
> Are you saying there's no way to upgrade now?

No, not at all.  You now must do a end of life upgrade by changing your sources list.  As shown in the link here:

[https://help.ubuntu.com/community/EOLUpgrades#Update_sources.list](https://help.ubuntu.com/community/EOLUpgrades#Update_sources.list)

Your sources list is located in /etc/apt/sources.list

Please read through the link and after I can assist further if needed.

---

### Post by ubunt72 on 2018-01-19
> **cruzer001 said:**
> We posted at the same time, one moment please.
Okay, thanks.   Thanks for your patience.  I've never taken too long to upgrade and most of previous upgrades have gone smooth or I did a fresh install.

I prefer to upgrade this time.  At least, try...

---

### Post by cruzer001 on 2018-01-19
I have made the changes for you.  Copy and paste if you wish.
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
#deb http://us.archive.ubuntu.com/ubuntu/ zesty main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://us.archive.ubuntu.com/ubuntu/ zesty-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
#deb http://us.archive.ubuntu.com/ubuntu/ zesty universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty universe
#deb http://us.archive.ubuntu.com/ubuntu/ zesty-updates universe

#So edit this and only have this there?:
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ zesty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ zesty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ zesty-security main restricted universe multiverse
```

Then do
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo do-release-upgrade
```

Ok?

---

### Post by ubunt72 on 2018-01-19
Okay.  Will give it a try.  Thnx.

---

### Post by cruzer001 on 2018-01-19
>  					Any reason why you didn't suggest to uncomment the backports option

Your sources.list did not contain the backports, no need to add it.

You must now be on 17.10, if so...

Its time to do a follow through for good measure :)
```

sudo apt update
sudo apt full-upgrade  ##replaces dist-upgrade
reboot  ##see below
sudo apt autoremove  ##cleans out uncessary packages and kernels_this should be a short list
sudo apt autoclean  ##cleans the apt_cache of unnecessary packages
```

Something else you should know
```

sudo apt-get dist-upgrade or sudo apt full-upgrade
```

These commands will upgrade the kernel and kernel related packages.  But to complete the kernel upgrade it is necessary to reboot your system.

And I'm on 16.04.  I do not know the new gnome system settings.  Maybe start a new thread on that.

---

### Post by Susan Spencer on 2018-01-25
Strange, connection refused to old-releases

Code:
```
sudo apt-get update


Err:1 [https://old-releases.ubuntu.com/ubuntu](https://old-releases.ubuntu.com/ubuntu) zesty InRelease
  Failed to connect to old-releases.ubuntu.com port 443: Connection refused
Err:2 [https://old-releases.ubuntu.com/ubuntu](https://old-releases.ubuntu.com/ubuntu) zesty-updates InRelease
  Failed to connect to old-releases.ubuntu.com port 443: Connection refused
Err:3 [https://old-releases.ubuntu.com/ubuntu](https://old-releases.ubuntu.com/ubuntu) zesty-security InRelease
  Failed to connect to old-releases.ubuntu.com port 443: Connection refused
Hit:4 [http://ppa.launchpad.net/susan-spencer/seamly2d/ubuntu](http://ppa.launchpad.net/susan-spencer/seamly2d/ubuntu) zesty InRelease
Reading package lists... Done
W: Failed to fetch [https://old-releases.ubuntu.com/ubuntu/dists/zesty/InRelease](https://old-releases.ubuntu.com/ubuntu/dists/zesty/InRelease)  Failed to connect to old-releases.ubuntu.com port 443: Connection refused
W: Failed to fetch [https://old-releases.ubuntu.com/ubuntu/dists/zesty-updates/InRelease](https://old-releases.ubuntu.com/ubuntu/dists/zesty-updates/InRelease)  Failed to connect to old-releases.ubuntu.com port 443: Connection refused
W: Failed to fetch [https://old-releases.ubuntu.com/ubuntu/dists/zesty-security/InRelease](https://old-releases.ubuntu.com/ubuntu/dists/zesty-security/InRelease)  Failed to connect to old-releases.ubuntu.com port 443: Connection refused
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

Wow! Found the one-command solution:

```
$sudo do-release-upgrade

*Checking for a new Ubuntu release*
*Your Ubuntu release is not supported anymore.*
*For upgrade information, please visit:*
*[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)*

*Get:1 Upgrade tool signature [819 B]                                                                                                                               *
*Get:2 Upgrade tool [1,247 kB]                                                                                                                                      *
*Fetched 1,247 kB in 0s (0 B/s)                                                                                                                                     *
*authenticate 'artful.tar.gz' against 'artful.tar.gz.gpg' *
*extracting 'artful.tar.gz'*

*Reading cache*

*Checking package manager*
*Reading package lists... Done*
*Building dependency tree        *
*Reading state information... Done*
*Err [https://old-releases.ubuntu.com/ubuntu](https://old-releases.ubuntu.com/ubuntu) zesty InRelease                                                                                                         *
*  Failed to connect to old-releases.ubuntu.com port 443: Connection refused                                                                                        *
*Err [https://old-releases.ubuntu.com/ubuntu](https://old-releases.ubuntu.com/ubuntu) zesty-updates InRelease                                                                                                 *
*  Failed to connect to old-releases.ubuntu.com port 443: Connection refused                                                                                        *
*Err [https://old-releases.ubuntu.com/ubuntu](https://old-releases.ubuntu.com/ubuntu) zesty-security InRelease                                                                                                *
*  Failed to connect to old-releases.ubuntu.com port 443: Connection refused                                                                                        *
*Fetched 0 B in 0s (0 B/s)                                                                                                                                          *
*Reading package lists... Done    *
*Building dependency tree          *
*Reading state information... Done*

[I]Updating repository information
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful InRelease [237 kB] 
...<snip>...
[/I]*Get:59 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-security/universe DEP-11 64x64 Icons [10.2 kB]                                                                   *
*Fetched 40.7 MB in 6s (582 kB/s)                                                                                                                                   *

*Checking package manager*
*Reading package lists... Done    *
*Building dependency tree          *
*Reading state information... Done*

*Calculating the changes*

*Calculating the changes*

*Do you want to start the upgrade? *
```

---

### Post by vadixem on 2018-02-08
I am now on Ubuntu 17.04 and have same issue upgrading to 17.10
$sudo do-release-upgrade didn't work out either :cry:
```

$ sudo do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

Get:1 Upgrade tool signature [819 B]                                                
Get:2 Upgrade tool [1 246 kB]                                                       
Fetched 1 247 kB in 0s (0 B/s)                                                      
authenticate 'artful.tar.gz' against 'artful.tar.gz.gpg' 
extracting 'artful.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Ign http://de.archive.ubuntu.com/ubuntu zesty InRelease                             
Ign http://de.archive.ubuntu.com/ubuntu zesty-updates InRelease                     
Hit https://repo.skype.com/deb stable InRelease                                     
Ign http://de.archive.ubuntu.com/ubuntu zesty-backports InRelease                   
Ign http://de.archive.ubuntu.com/ubuntu zesty-security InRelease                    
Err http://de.archive.ubuntu.com/ubuntu zesty Release                               
  404  Not Found [IP: 141.30.62.24 80]                                              
Hit http://repository.spotify.com stable InRelease                                  
Err http://de.archive.ubuntu.com/ubuntu zesty-updates Release                       
  404  Not Found [IP: 141.30.62.24 80]                                              
Err http://de.archive.ubuntu.com/ubuntu zesty-backports Release                     
  404  Not Found [IP: 141.30.62.24 80]                                              
Err http://de.archive.ubuntu.com/ubuntu zesty-security Release                      
  404  Not Found [IP: 141.30.62.24 80]                                              
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

Get:1 http://de.archive.ubuntu.com/ubuntu artful InRelease [237 kB]                 
Ign http://archive.ubuntu.com/ubuntu stable InRelease                               
Err http://archive.ubuntu.com/ubuntu stable Release                                 
  404  Not Found [IP: 91.189.88.152 80]                                             
Get:2 http://de.archive.ubuntu.com/ubuntu artful-updates InRelease [78,6 kB]        
Get:3 http://de.archive.ubuntu.com/ubuntu artful-backports InRelease [72,2 kB]      
Get:4 http://de.archive.ubuntu.com/ubuntu artful-security InRelease [78,6 kB]       
Get:5 http://de.archive.ubuntu.com/ubuntu artful/main i386 Packages [1 067 kB]      
Get:6 http://de.archive.ubuntu.com/ubuntu artful/main amd64 Packages [1 071 kB]     
Get:7 http://de.archive.ubuntu.com/ubuntu artful/main Translation-en [542 kB]       
Get:8 http://de.archive.ubuntu.com/ubuntu artful/main amd64 DEP-11 Metadata [397 kB]
Get:9 http://de.archive.ubuntu.com/ubuntu artful/main DEP-11 64x64 Icons [263 kB]   
Get:10 http://de.archive.ubuntu.com/ubuntu artful/restricted amd64 Packages [8 852 B]
Get:11 http://de.archive.ubuntu.com/ubuntu artful/restricted i386 Packages [8 876 B]
Get:12 http://de.archive.ubuntu.com/ubuntu artful/restricted Translation-en [2 788 B]
Get:13 http://de.archive.ubuntu.com/ubuntu artful/universe amd64 Packages [8 103 kB]
Get:14 http://de.archive.ubuntu.com/ubuntu artful/universe i386 Packages [8 066 kB] 
Get:15 http://de.archive.ubuntu.com/ubuntu artful/universe Translation-en [4 789 kB]
Get:16 http://de.archive.ubuntu.com/ubuntu artful/universe amd64 DEP-11 Metadata [2 845 kB]
Get:17 http://de.archive.ubuntu.com/ubuntu artful/universe DEP-11 64x64 Icons [7 915 kB]
Get:18 http://de.archive.ubuntu.com/ubuntu artful/multiverse i386 Packages [143 kB] 
Get:19 http://de.archive.ubuntu.com/ubuntu artful/multiverse amd64 Packages [150 kB]
Get:20 http://de.archive.ubuntu.com/ubuntu artful/multiverse Translation-en [108 kB]
Get:21 http://de.archive.ubuntu.com/ubuntu artful/multiverse amd64 DEP-11 Metadata [43,8 kB]
Get:22 http://de.archive.ubuntu.com/ubuntu artful/multiverse DEP-11 64x64 Icons [207 kB]
Get:23 http://de.archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages [180 kB]
Get:24 http://de.archive.ubuntu.com/ubuntu artful-updates/main i386 Packages [178 kB]
Get:25 http://de.archive.ubuntu.com/ubuntu artful-updates/main Translation-en [80,9 kB]
Get:26 http://de.archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [73,3 kB]
Get:27 http://de.archive.ubuntu.com/ubuntu artful-updates/main DEP-11 64x64 Icons [49,2 kB]
Get:28 http://de.archive.ubuntu.com/ubuntu artful-updates/restricted amd64 Packages [2 192 B]
Get:29 http://de.archive.ubuntu.com/ubuntu artful-updates/restricted i386 Packages [2 180 B]
Get:30 http://de.archive.ubuntu.com/ubuntu artful-updates/restricted Translation-en [1 284 B]
Get:31 http://de.archive.ubuntu.com/ubuntu artful-updates/universe i386 Packages [72,5 kB]
Get:32 http://de.archive.ubuntu.com/ubuntu artful-updates/universe amd64 Packages [73,0 kB]
Get:33 http://de.archive.ubuntu.com/ubuntu artful-updates/universe Translation-en [41,7 kB]
Get:34 http://de.archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [49,5 kB]
Get:35 http://de.archive.ubuntu.com/ubuntu artful-updates/universe DEP-11 64x64 Icons [55,3 kB]
Get:36 http://de.archive.ubuntu.com/ubuntu artful-updates/multiverse amd64 Packages [1 828 B]
Get:37 http://de.archive.ubuntu.com/ubuntu artful-updates/multiverse i386 Packages [1 980 B]
Get:38 http://de.archive.ubuntu.com/ubuntu artful-updates/multiverse Translation-en [1 124 B]
Get:39 http://de.archive.ubuntu.com/ubuntu artful-backports/main i386 Packages [1 512 B]
Get:40 http://de.archive.ubuntu.com/ubuntu artful-backports/main amd64 Packages [1 516 B]
Get:41 http://de.archive.ubuntu.com/ubuntu artful-backports/main Translation-en [668 B]
Get:42 http://de.archive.ubuntu.com/ubuntu artful-backports/universe amd64 Packages [3 404 B]
Get:43 http://de.archive.ubuntu.com/ubuntu artful-backports/universe i386 Packages [3 396 B]
Get:44 http://de.archive.ubuntu.com/ubuntu artful-backports/universe Translation-en [1 880 B]
Get:45 http://de.archive.ubuntu.com/ubuntu artful-backports/universe amd64 DEP-11 Metadata [4 700 B]
Get:46 http://de.archive.ubuntu.com/ubuntu artful-backports/universe DEP-11 64x64 Icons [2 717 B]
Get:47 http://de.archive.ubuntu.com/ubuntu artful-security/main amd64 Packages [84,2 kB]
Get:48 http://de.archive.ubuntu.com/ubuntu artful-security/main i386 Packages [82,4 kB]
Get:49 http://de.archive.ubuntu.com/ubuntu artful-security/main Translation-en [39,2 kB]
Get:50 http://de.archive.ubuntu.com/ubuntu artful-security/main amd64 DEP-11 Metadata [2 924 B]
Get:51 http://de.archive.ubuntu.com/ubuntu artful-security/main DEP-11 64x64 Icons [4 471 B]
Get:52 http://de.archive.ubuntu.com/ubuntu artful-security/restricted amd64 Packages [2 192 B]
Get:53 http://de.archive.ubuntu.com/ubuntu artful-security/restricted i386 Packages [2 180 B]
Get:54 http://de.archive.ubuntu.com/ubuntu artful-security/restricted Translation-en [1 284 B]
Get:55 http://de.archive.ubuntu.com/ubuntu artful-security/universe i386 Packages [31,3 kB]
Get:56 http://de.archive.ubuntu.com/ubuntu artful-security/universe amd64 Packages [31,4 kB]
Get:57 http://de.archive.ubuntu.com/ubuntu artful-security/universe Translation-en [19,8 kB]
Get:58 http://de.archive.ubuntu.com/ubuntu artful-security/universe amd64 DEP-11 Metadata [10,4 kB]
Get:59 http://de.archive.ubuntu.com/ubuntu artful-security/universe DEP-11 64x64 Icons [10,2 kB]
Get:60 http://de.archive.ubuntu.com/ubuntu artful-security/multiverse i386 Packages [1 980 B]
Get:61 http://de.archive.ubuntu.com/ubuntu artful-security/multiverse amd64 Packages [1 828 B]
Get:62 http://de.archive.ubuntu.com/ubuntu artful-security/multiverse Translation-en [1 124 B]
Fetched 37,4 MB in 6s (3 116 kB/s)                                                  
Hit http://de.archive.ubuntu.com/ubuntu artful InRelease                            
Ign http://archive.ubuntu.com/ubuntu stable InRelease                               
Hit http://de.archive.ubuntu.com/ubuntu artful-updates InRelease                    
Err http://archive.ubuntu.com/ubuntu stable Release                                 
  404  Not Found [IP: 91.189.88.161 80]                                             
Hit http://de.archive.ubuntu.com/ubuntu artful-backports InRelease                  
Hit http://de.archive.ubuntu.com/ubuntu artful-security InRelease                   
Fetched 0 B in 0s (0 B/s)                                                           
Hit http://de.archive.ubuntu.com/ubuntu artful InRelease                            
Ign http://archive.ubuntu.com/ubuntu stable InRelease                               
Hit http://de.archive.ubuntu.com/ubuntu artful-updates InRelease                    
Err http://archive.ubuntu.com/ubuntu stable Release                                 
  404  Not Found [IP: 91.189.88.161 80]                                             
Hit http://de.archive.ubuntu.com/ubuntu artful-backports InRelease                  
Hit http://de.archive.ubuntu.com/ubuntu artful-security InRelease                   
Fetched 0 B in 0s (0 B/s)                                                           

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

E:The repository 'http://archive.ubuntu.com/ubuntu stable Release' 
does not have a Release file. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done



```

---

### Post by vadixem on 2018-02-08
Please consider this link: [https://help.ubuntu.com/community/EOLUpgrades#Update_sources.list](https://help.ubuntu.com/community/EOLUpgrades#Update_sources.list)
Works out for me

---

### Post by grindlay-pro1 on 2018-12-03
I had exact same problem. Followed steps here but stuck at 17.04.
I changed
```
archive.ubuntu.com/ubuntu zesty
```
 to
 ```
old-releases.ubuntu.com/ubuntu zesty
```
Then apt-get installed a few updates, but still stuck at 17.04
Got the error message when trying to do the distribution upgrade.
The bit I was missing was the CODENAME in the help page :
[https://help.ubuntu.com/community/EOLUpgrades#Update_sources.list](https://help.ubuntu.com/community/EOLUpgrades#Update_sources.list)
I changed "zesty" to "artful", so in the end I had :
```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful main restricted universe multiverse  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security main restricted universe multiverse  
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
```
This sources.list is also here :
[https://askubuntu.com/questions/1040071/etc-apt-sources-list-file-for-ubuntu-17-10](https://askubuntu.com/questions/1040071/etc-apt-sources-list-file-for-ubuntu-17-10)
Try this, then
```
apt-get
```
 again.
It should now offer the distro upgrade

---

### Post by Autodave on 2018-12-03
17.04 is no longer upgradeable since it was only a short term release.  The LTS releases are supported for at least 5 years whereas the short term ones are only supported until the next one is released.  Also, I rarely find that upgrading works well: it is usually way faster and simpler to do a clean install after you back up everything to an external source.

I would d-l 18.04 and start clean.

---

### Post by oldos2er on 2018-12-04
Neither 17.04 nor 17.10 are supported anymore; see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Closed.

---

