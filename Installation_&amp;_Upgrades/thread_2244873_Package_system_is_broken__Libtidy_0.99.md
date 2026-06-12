---
title: "Package system is broken:  Libtidy 0.99"
date: 2014-09-19
forum: Installation &amp; Upgrades
---

### Post by p.callan on 2014-09-19
Tried to install Youtube-dl from SC;

[I]To install youtube-dl, these items must be removed:
Python wrapper for tidylib
python-utidylib[/I]

[ removed ]

[I]To install youtube-dl, these items must be removed:
Python wrapper for tidylib
python-utidylib

[/I][ install anyway ]

[I]The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f[/I]
[I]The following packages have unmet dependencies:

python-utidylib: Depends: python (>= 2.7) but 2.7.5-5ubuntu3 is installed
                 Depends: python:any (>= 2.7.1-0ubuntu2) but it is a virtual package
                 Depends: libtidy-0.99-0 (>= 20051018) but it is not installed[/I]

**sudo apt-get -f install** ;

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb kde-l10n-sv libqt5declarative5 linux-headers-3.13.0-24
  linux-headers-3.13.0-24-generic linux-image-3.13.0-24-generic
  linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libtidy-0.99-0
The following NEW packages will be installed:
  libtidy-0.99-0
0 upgraded, 1 newly installed, 0 to remove and 75 not upgraded.
1 not fully installed or removed.
Need to get 0 B/117 kB of archives.
After this operation, 377 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 466789 files and directories currently installed.)
Preparing to unpack .../libtidy-0.99-0_20091223cvs-1.2ubuntu1_i386.deb ...
Unpacking libtidy-0.99-0 (20091223cvs-1.2ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1.2ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libtidy-0.99.so.0.0.0', which is also in package libtidy 20130211-git-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1.2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

**New software can't be installed, because there is a problem with the software currently installed. Do you want to repair this problem now?**
[ repair ]
**Package operation failed. The installation or removal of a software package failed.** Details:

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 466789 files and directories currently installed.) 
Preparing to unpack .../libtidy-0.99-0_20091223cvs-1.2ubuntu1_i386.deb ... 
Unpacking libtidy-0.99-0 (20091223cvs-1.2ubuntu1) ... 
dpkg: error processing archive /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1.2ubuntu1_i386.deb (--unpack): 
 trying to overwrite '/usr/lib/libtidy-0.99.so.0.0.0', which is also in package libtidy 20130211-git-1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1.2ubuntu1_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of python-utidylib: 
 python-utidylib depends on libtidy-0.99-0 (>= 20051018); however: 
  Package libtidy-0.99-0 is not installed. 
 
dpkg: error processing package python-utidylib (--configure): 
 dependency problems - leaving unconfigured 


**New software can't be installed, because there is a problem  with the software currently installed. Do you want to repair this  problem now?**

Sigh...

I don't understand what is wrong here, and not a clue what to do... Just want to do a simple install...
Supposedly one can remove broken packages using Synaptic, but this is not installed and I cannot install anything as per above.

Thanks for your help. Really need it working. Don't understand why it broke.

---

### Post by p.callan on 2014-09-19
There are more errors when I do this:

In System settings -->  Software and updates -->  

[I]The information about available software is out-of-date
To install software and updates from newly added or changed sources, you have to reload the information about available software.
You need a working internet connection to continue.[/I]

[ Reload ]
[I]
Updating cache[/I]
[I]Failed to download repository information
Check your Internet connection.[/I]  [there's nothing wrong with it ]
*Details:*

[I]W:GPG error: [http://repos.codelite.org](http://repos.codelite.org) trusty InRelease: 
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6856E1DB1AC82609, 
W:Failed to fetch [http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  
404  Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.[/I]

---

### Post by ibjsb4 on 2014-09-19
Your codelite addess is incomplete, it does not lead to the trusty package.

[http://repos.codelite.org/ubuntu-6.1/dists/trusty/](http://repos.codelite.org/ubuntu-6.1/dists/trusty/)

And michael-astrapi ppa does not have a trusty package.

[http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/](http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/)

---

### Post by p.callan on 2014-09-19
That's interesting. So what do I do?

---

### Post by ibjsb4 on 2014-09-19
```
sudo -i

apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit

```
And either remove or disable michael-a's ppa.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by p.callan on 2014-10-13
Thanks.
Output from terminal is this:
[I]
Get:84 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en [29,0 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 21,8 MB in 41s (524 kB/s)                                              
W: GPG error: [http://repos.codelite.org](http://repos.codelite.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6856E1DB1AC82609
W: Failed to fetch [http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.[/I]


Still broken. Tried to install Skype-call-recorder and the error message was:

[I]The following packages have unmet dependencies:

python-utidylib: Depends: python (>= 2.7) but 2.7.5-5ubuntu3 is installed
                 Depends: python:any (>= 2.7.1-0ubuntu2) but it is a virtual package
                 Depends: libtidy-0.99-0 (>= 20051018) but it is not installed[/I]


Greek to me...

---

### Post by p.callan on 2014-10-28
Today I needed to install a calendar, but that didn't work.

[I]New software can't be installed,
because there is a problem with the software currently installed. Do you want to repair this problem now?[/I]
(Repair)

And then the freaking dialog comes right back up again!! I'm on my second month now where I can't install or uninstall anything.
Should I just wipe the entire Ubuntu installation? And how do I stop the same problems from ocurring again in the future? Is there a distro that doesn't have these eternal complications?

---

### Post by ian-weisser on 2014-10-28
> **p.callan said:**
> I'm on my second month now where I can't install or uninstall anything.
It's probably worse than that. You are also not getting any security updates.

> **p.callan said:**
> Should I just wipe the entire Ubuntu installation?
That's one solution, though not the one I would choose.
Fixing the problem is usually quite easy. We'll do that in a moment.

 > **p.callan said:**
> And how do I stop the same problems from ocurring again in the future? Is there a distro that doesn't have these eternal complications?
The problem was caused when you installed a PPA or other non-Ubuntu software.
The problem will be solved when you uninstall that software.
It's really just that simple.

Ubuntu cannot repair the problem automatically because it's not psychic - it doesn't know your intent. You gave the system conflicting commands, and now it's trying very hard to do both...but it can't.

Here's the problem:
> **p.callan said:**
> ```
Unpacking libtidy-0.99-0 (20091223cvs-1.2ubuntu1) ... 
dpkg: error processing archive /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1.2ubuntu1_i386.deb (--unpack): 
 trying to overwrite '/usr/lib/libtidy-0.99.so.0.0.0', which is also in package libtidy 20130211-git-1
```

Here's what the problem means:
- A file can be provided by a maximum of one package. If two packages try to provide the same file, they *conflict*, and only one can be installed.
- You have two packages: libtidy-0.99-0 and libtidy_20130211-git-1
- They *both* provide a file /usr/lib/libtidy-0.99.so.0.0.0
- You, the human, told the system at some point to install *both* versions. It can't do that. The packages *conflict*.


So how do you fix it forever? Very easily.
Steps 1, 2, and 5 fix the problem. Steps 3 and 4 fix the damage.

1) Uninstall the non-Ubuntu version of libtidy, and all of it's non-Ubuntu dependencies. (sudo apt-get autoremove libtidy)
Some non-Ubuntu application you installed depends on that non-Ubuntu version of libtidy, and will also be uninstalled. That's okay, write it down and reinstall it in Step 5.

2) Disable the non-Ubuntu repository that provided the non-Ubuntu version of libtidy. (System Settings --> Software & Updates --> Other Software)

3) Refresh your package database (sudo apt-get update)

4) Install all those delayed security and other updates (sudo apt-get upgrade)

5) Finally, reinstall whatever application was uninstalled in Step 1 (sudo apt-get install whatever-the-application-was)
This time, install it from the Ubuntu repositories.


If you run across any more cryptic error messages, or aren't sure how to do any of those steps properly, please let us know.

---

### Post by p.callan on 2014-11-16
Thanks for trying and for your time, but it didn't work.
It seems it doesn't want to remove any of the Libtidys and doesn't want to remove pirateplayer which is probably what ails. Pirateplayer cannot be uninstalled because of the libtidy conflict. 
Still can't install or uninstall anything.



   user@computer:~$ **sudo apt-get autoremove libtidy **

 [sudo] password for user:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 You might want to run 'apt-get -f install' to correct these: 
 The following packages have unmet dependencies: 
  pirateplayer : Depends: libtidy but it is not going to be installed 
  python-utidylib : Depends: libtidy-0.99-0 (>= 20051018) but it is not going to be installed 
 E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
 user@computer:~$ **sudo apt-get update **

 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease 

 Get:1 [http://repos.codelite.org](http://repos.codelite.org) trusty InRelease [2 891 B]                      
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                   
 Ign [http://repos.codelite.org](http://repos.codelite.org) trusty InRelease                              
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                               
 Ign [http://repos.codelite.org](http://repos.codelite.org) trusty/universe i386 Packages/DiffIndex  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                      
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease    
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                          
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                          
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease              

 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                        
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                        
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security InRelease             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                            
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                     
 Hit [http://repos.codelite.org](http://repos.codelite.org) trusty/universe i386 Packages                     
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                   
 Ign [http://repos.codelite.org](http://repos.codelite.org) trusty/universe Translation-en_US       
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                
 Ign [http://repos.codelite.org](http://repos.codelite.org) trusty/universe Translation-en          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release.gpg          
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en 
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release              
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                 
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release 
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                 
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources 
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Sources                   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Sources             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Sources               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Sources             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main i386 Packages             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted i386 Packages       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe i386 Packages         
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse i386 Packages       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Translation-en            
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Translation-en      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Translation-en      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en        
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US              
 Fetched 2 891 B in 10s (272 B/s)                                                
 Reading package lists... Done 
 W: GPG error: [http://repos.codelite.org](http://repos.codelite.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6856E1DB1AC82609 
 user@computer:~$ **sudo apt-get upgrade** 

 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 You might want to run 'apt-get -f install' to correct these. 
 The following packages have unmet dependencies: 

  python-utidylib : Depends: libtidy-0.99-0 (>= 20051018) but it is not installed 
 E: Unmet dependencies. Try using -f. 
 user@computer:~$ **sudo apt-get autoremove libtidy-0.99-0 **

 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Package 'libtidy-0.99-0' is not installed, so not removed 
 You might want to run 'apt-get -f install' to correct these: 

 The following packages have unmet dependencies: 
  python-utidylib : Depends: libtidy-0.99-0 (>= 20051018) but it is not going to be installed 

 E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
 user@computer:~$ **sudo apt-get autoremove pirateplayer **

 Reading package lists... Done 

 Building dependency tree        
 Reading state information... Done 

 You might want to run 'apt-get -f install' to correct these: 
 The following packages have unmet dependencies: 
  python-utidylib : Depends: libtidy-0.99-0 (>= 20051018) but it is not going to be installed 
 E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
 user@computer:~$ **sudo apt-get uninstall pirateplayer **

 E: Invalid operation uninstall

---

### Post by ian-weisser on 2014-11-16
Try with dpkg:
```
sudo dpkg --remove pirateplayer
sudo dpkg --remove libtidy-0.99-0
sudo apt-get autoremove
```

---

### Post by p.callan on 2014-12-17
user@computer:~$ sudo dpkg --remove pirateplayer 
 [sudo] password for user:  
 (Reading database ... 466788 files and directories currently installed.) 
 Removing pirateplayer (0.5.0-1) ... 
 Processing triggers for hicolor-icon-theme (0.13-1) ... 
 Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
 Processing triggers for desktop-file-utils (0.22-1ubuntu1) ... 
 Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ... 
 Rebuilding /usr/share/applications/bamf-2.index... 
 Processing triggers for mime-support (3.54ubuntu1) ... 
 user@computer:~$ sudo dpkg --remove libtidy-0.99-0 
 dpkg: warning: ignoring request to remove libtidy-0.99-0 which isn't installed 
 user@computer:~$ sudo apt-get autoremove 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 You might want to run 'apt-get -f install' to correct these. 
 The following packages have unmet dependencies: 
  python-utidylib : Depends: libtidy-0.99-0 (>= 20051018) but it is not installed 
 E: Unmet dependencies. Try using -f. 
 user@computer:~$

---

### Post by schragge on 2014-12-17
The package *libtidy-0.99-0* was never installed on your system to begin with. It's *python-utidylib* that requires it, but it cannot be installed because you have another version of libtidy in the package **libtidy** (without version in the name). It's not from an official Ubuntu repository. I guess it's from [here]("http://pirateplay.se/installera_pirateplayer_i_ubuntu.html") and was only needed by *pirateplayer* which you have already successfully removed. So remove it, too:
```
sudo dpkg --remove libtidy
```

After that, you can attempt installing *youtube-dl*.

---

