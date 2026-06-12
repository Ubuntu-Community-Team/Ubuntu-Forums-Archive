---
title: "error in downloading repositories indexes"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by sainath90 on 2011-02-27
i'm having a problem in downloading the repository indexes.its giving me the following error.

""Could not download all repository indexes
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/n-muench/vlc2/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/n-muench/vlc2/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/n-muench/vlc2/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/n-muench/vlc2/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.""

Though its giving a msg saying check ur network connection,my net connection is fine.
Can anyone please suggest me a solution....

---

### Post by runeh76 on 2011-02-27
Hi

What Ubuntu distro?

---

### Post by oldos2er on 2011-02-27
That PPA only offers packages for Lucid (10.04).

---

### Post by sainath90 on 2011-02-27
@runeh:im using maverick

---

### Post by sainath90 on 2011-02-27
@ann:so,how can i solve this problem

---

### Post by runeh76 on 2011-02-27
edit: deleted wrong information!!

---

### Post by runeh76 on 2011-02-27
Its old VLC repository.
Add these ur software sources list AND remove those old ones:

deb [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) maverick main

Terminal:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 71346C8340130828
```

```
sudo apt-get update
```

---

### Post by sainath90 on 2011-02-27
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

the above are the errors which occured after i entered the code in the terminal

---

### Post by runeh76 on 2011-02-28
pls post ur sources.list:

```
gksu cat /etc/apt/sources.list
```


edit: Try this first:
If you have Synaptic Package Manager, Adept Package Manager, Update Manager, or Add/Remove open, close it. Run next commands:

```
sudo rm /var/lib/apt/lists/lock
```

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo apt-get update
```

---

### Post by checoimg on 2011-03-05
> **runeh76 said:**
> pls post ur sources.list:

```
gksu cat /etc/apt/sources.list
```


edit: Try this first:
If you have Synaptic Package Manager, Adept Package Manager, Update Manager, or Add/Remove open, close it. Run next commands:

```
sudo rm /var/lib/apt/lists/lock
```

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo apt-get update
```



Second part seems to work for me It's updating already

---

### Post by Tiddens on 2011-10-23
Same problem, with Ubuntu 10.04:  Please help.  Thanks!

  	 	 	 	p { margin-bottom: 0.08in; }  Could not download all repository indexes
 

 NO_PUBKEY FF370EF786F4C28EFailed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found 
 Some index files failed to download, they have been ignored, or old ones used instead.
 

 **********************************************************************
 

 root@waveuser-laptop:/usr/share/gnome# sudo apt-get update 
 Ign [http://apt.boxee.tv](http://apt.boxee.tv) lucid Release.gpg 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                                     
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US            
 Ign [http://apt.boxee.tv/](http://apt.boxee.tv/) lucid/main Translation-en_US                                  
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                     
 Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US                      
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                              
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US           
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US     
 Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                                
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US              
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US            
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                             
 Ign [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/) lucid/main Translation-en_US 
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                         
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US    
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US          
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US    
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US      
 Ign [http://apt.boxee.tv](http://apt.boxee.tv) lucid Release                                                  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                         
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US       
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US     
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                         
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                  
 Ign [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) lucid/main Translation-en_US        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                         
 Ign [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/) lucid/main Translation-en_US        
 Hit [http://apt.boxee.tv](http://apt.boxee.tv) lucid/main Packages                                            
 Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                             
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                                   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages              
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources               
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources            
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources      
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages 
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages 
   404  Not Found 
 Fetched 308B in 0s (324B/s) 
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FF370EF786F4C28E 
 W: Failed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found 
  
 E: Some index files failed to download, they have been ignored, or old ones used instead. 
 

 ****************************************************************************
 

 root@waveuser-laptop:/usr/share/gnome# cat /etc/apt/sources.list 
 # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted 
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
  
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
 # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner 
  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse 
 deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe

---

### Post by Old_Grey_Wolf on 2011-10-23
Maybe this xmbc website link will help [http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux](http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux)

---

### Post by Tiddens on 2011-10-23
This has something to do with XMBC?  And it is blocking all of my updates?  Actually, I thought I unstalled XMBC.  I don't need it.  How do I get rid of it?  Thanks!

---

### Post by Old_Grey_Wolf on 2011-10-23
Using the menus "System > Administration > Update Manager" open the update manager. Then click on the tabs until you find one where the PPA for xmbc is located. Then remove the check in the checkbox.

---

### Post by Old_Grey_Wolf on 2011-10-23
If there is no PPA listed in update manager, it may be necessary to clean out the update lists that may still have xmbc in them due to partial updates. You can do that by entering these commands in the terminal ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```

I'm a little slow right know as it is time for me to go to bed :)

---

### Post by Tiddens on 2011-10-24
Uh-oh - that caused the following errors:

  	 	 	 	p { margin-bottom: 0.08in; }a:link {  }  root@waveuser-laptop:/home/waveuser# sudo rm -rf /var/lib/apt/lists/* 
 root@waveuser-laptop:/home/waveuser# sudo apt-get update 
 E: Lists directory /var/lib/apt/lists/partial is missing. 
 root@waveuser-laptop:/home/waveuser# sudo apt-get dist-upgrade 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Calculating upgrade... Done 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 [EMAIL="root@waveuser-laptop"]root@waveuser-laptop[/EMAIL]:/home/waveuser#
 

 root@waveuser-laptop:/home/waveuser# sudo apt-get update 
 E: Lists directory /var/lib/apt/lists/partial is missing. 
 

 *****************************************************
 

 Using Update Manager;
 

 Could not download all repository indexes 
  
 The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
 

 Lists directory /var/lib/apt/lists/partial is missing.

---

### Post by Tiddens on 2011-10-24
And here is this:

root@waveuser-laptop:/home/waveuser# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe

---

### Post by Old_Grey_Wolf on 2011-10-24
> **Tiddens said:**
> Uh-oh - that caused the following errors:
......

You're running as root; which is not recommended, so just type in the following commands```
mkdir /var/lib/apt/lists/partial
apt-get update
``` and post the errors you get. In the future don't hijack another thread.

---

### Post by Tiddens on 2011-10-24
Thanks!  I really appreciate your help.  Sorry about hijacking a thread.  I don't have problems often enough to remember how to start a new thread and couldn't see anything to click on to do it.  Also, I use root because half the time I try to do something it doesn't let me without being root.

If you are ever in San Diego, I'd look forward to meeting you...

The updating was finally successful, with one error remaining if you can advise how I can get rid of it:

  	 	 	 	p { margin-bottom: 0.08in; }  W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FF370EF786F4C28E
 

 ******************************************************
 

 root@waveuser-laptop:/usr/share# cat /etc/apt/sources.list 
 # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted 
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
  
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
 # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users.

---

### Post by Old_Grey_Wolf on 2011-10-24
> **Tiddens said:**
> Thanks!  I really appreciate your help.  Sorry about hijacking a thread.  I don't have problems often enough to remember how to start a new thread and couldn't see anything to click on to do it.  Also, I use root because half the time I try to do something it doesn't let me without being root.

If you are ever in San Diego, I'd look forward to meeting you...

The updating was finally successful, with one error remaining if you can advise how I can get rid of it:

  	 	 	 	p { margin-bottom: 0.08in; }  W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FF370EF786F4C28E....

Enter these commands to get the GPG Key ```
gpg --keyserver keyserver.ubuntu.com --recv FF370EF786F4C28E
gpg --export --armor FF370EF786F4C28E | sudo apt-key add -
```

Because I didn't realize you were running as root until your third post; I could have gien you commands unknowingly that could have destroyed your system.

---

### Post by Tiddens on 2011-10-24
Thanks!  That did it - the update runs clean now.  I found the "New Thread" button is only on the Main Support Category pages - I'll copy and paste this note in my "cheatsheet" file so I'll know next time.  Take care.

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

---

