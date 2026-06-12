---
title: "amarok"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by farinx on 2008-05-11
I'm brand new to ubuntu and am trying to get amarok installed. when i try to put it on it says "this application conflicts with other installed software. To install amarok the conflicting software must be removed first.  Switch to the 'synaptic' package manager to resolve this problem. Yeah so i have no idea what that means.

---

### Post by Rocket2DMn on 2008-05-11
I've never seen that before, but you can do what it says by searching for amarok in Synaptic: System->Administration->Synaptic Package Manager
Synaptic is the preferred GUI package management software in Ubuntu, apt-get is generally used in the terminal.

---

### Post by farinx on 2008-05-11
i went into the synaptic package manager and couldnt figure out how to fix anything.

---

### Post by Rocket2DMn on 2008-05-11
Does it give you any more information, like what programs are conflicting?

---

### Post by farinx on 2008-05-11
this is what it says when i try to mark it for installation

amarok:
 Depends: amarok-xine but it is not going to be installed or
	amarok-engine
 Depends: kdelibs4c2a but it is not going to be installed
 Depends: libgpod3-nogtk  but it is not installable or
 	libgpod3  but it is not installable
 Depends: libmp4v2-0 but it is not going to be installed
 Depends: libmtp7  but it is not installable
 Depends: libpq5 but it is not going to be installed
  Depends: libruby1.8 (>=1.8.6.111) but 1.8.6.36-1ubuntu3 is to be installed

---

### Post by Rocket2DMn on 2008-05-11
OK, try going to System->Administration->Software Sources and enabling the universe and multiverse repositories.  Close, let it update, then run
```
sudo apt-get upgrade
sudo apt-get build-dep amarok
sudo apt-get install amarok
```

---

### Post by farinx on 2008-05-11
i think the universe and multiverse things are already checked.  i'm not sure if i did the command promt thing and this is what i got:

drew@drew-laptop:~$ sudo apt-get upgrade
[sudo] password for drew:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
drew@drew-laptop:~$ sudo apt-get build-dep amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-Depends dependency for amarok cannot be satisfied because the package libgpod-nogtk-dev cannot be found
drew@drew-laptop:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: amarok-xine but it is not going to be installed or
                   amarok-engine
          Depends: kdelibs4c2a (>= 4:3.5.8-1) but it is not going to be installed
          Depends: libgpod3-nogtk but it is not installable or
                   libgpod3 but it is not installable
          Depends: libmp4v2-0 (>= 1:1.6dfsg) but it is not going to be installed
          Depends: libmtp7 but it is not installable
          Depends: libpq5 (>= 8.3~beta1) but it is not going to be installed
          Depends: libruby1.8 (>= 1.8.6.111) but 1.8.6.36-1ubuntu3 is to be installed
E: Broken packages

---

### Post by Rocket2DMn on 2008-05-11
What happens if you try to install the packages it says are uninstallable?  For instance:
```
sudo apt-get install libgpod3
```

---

### Post by farinx on 2008-05-11
i copied that code into the input thing and this is what it got:


drew@drew-laptop:~$ sudo apt-get install libgpod
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgpod
drew@drew-laptop:~$ 
drew@drew-laptop:~$

---

### Post by Rocket2DMn on 2008-05-12
It's libgpod3, not libgpod.  Do check to make sure universe and multiverse are enabled.

---

### Post by farinx on 2008-05-12
ok sorry...
heres what popped up:

drew@drew-laptop:~$ sudo apt-get install libgpod3
[sudo] password for drew:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgpod3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgpod3 has no installation candidate
drew@drew-laptop:~$

---

### Post by Rocket2DMn on 2008-05-12
Can you please post me your sources.list file?
```
cat /etc/apt/sources.list
```

---

### Post by farinx on 2008-05-12
drew@drew-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb [http://repo.freecreations.info/ubuntu](http://repo.freecreations.info/ubuntu) gutsy freeverse

---

### Post by TheWizzard on 2008-05-12
almost everything is commented out. did you have your computer cable-connected to the internet when you installed ubuntu? 

anyways, you'll need to open synaptic and enable default repo's.

---

### Post by farinx on 2008-05-12
i don't think i was cable connected to the internet when installing ubuntu. how do i do that? i opened up the synaptic package manager, then clicked settings, then repositories... i'm not sure which options need to be checked.

Drew

---

### Post by Rocket2DMn on 2008-05-12
Go to System->Administration->Software Sources
Check the first 4 boxes. Close the window and allow it to update (Synaptic must be closed).
Then you can run
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get upgrade
sudo apt-get install amarok
```
The update command is not needed since the Software Sources should run it automatically, but I put it in there anyway for good measure.  Using autoremove might help clean up the system a bit.

---

### Post by farinx on 2008-05-12
the first four boxes were already checked. i typed all that in and this is what i got:

drew@drew-laptop:~$ sudo apt-get update
[sudo] password for drew:
Ign [http://repo.freecreations.info](http://repo.freecreations.info) gutsy Release.gpg                           
Ign [http://repo.freecreations.info](http://repo.freecreations.info) gutsy/freeverse Translation-en_US           
Hit [http://repo.freecreations.info](http://repo.freecreations.info) gutsy Release                             
Hit [http://repo.freecreations.info](http://repo.freecreations.info) gutsy/freeverse Packages                  
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources                   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Fetched 2B in 14s (0B/s)                                                       
Reading package lists... Done
drew@drew-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-system-web1.0-cil
  libsgutils1 libmono-data-tds1.0-cil libmono-system-data1.0-cil
The following packages will be REMOVED:
  libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil
  libmono-system-data1.0-cil libmono-system-web1.0-cil libsgutils1
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2642kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91398 files and directories currently installed.)
Removing libmono-system-web1.0-cil ...
Removing libmono-system-data1.0-cil ...
Removing libmono-data-tds1.0-cil ...
Removing libmono-security1.0-cil ...
Removing libmono-sharpzip0.84-cil ...
Removing libsgutils1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
drew@drew-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
drew@drew-laptop:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: amarok-xine but it is not going to be installed or
                   amarok-engine
          Depends: kdelibs4c2a (>= 4:3.5.8-1) but it is not going to be installed
          Depends: libgpod3-nogtk but it is not installable or
                   libgpod3 but it is not installable
          Depends: libmp4v2-0 (>= 1:1.6dfsg) but it is not going to be installed
          Depends: libmtp7 but it is not installable
          Depends: libpq5 (>= 8.3~beta1) but it is not going to be installed
          Depends: libruby1.8 (>= 1.8.6.111) but 1.8.6.36-1ubuntu3 is to be installed
E: Broken packages

---

### Post by Het Irv on 2008-05-13
uhhh... lets see 
```
sudo dpkg --configure -a
```
will fix broken packages.  I wonder if that will do anything.

---

### Post by farinx on 2008-05-13
do i just copy paste that into the terminal?

---

### Post by Het Irv on 2008-05-13
YUP
but I don't know if it will work, its the only related command I know that wasn't aready suggested

---

### Post by farinx on 2008-05-13
nothing happened when i posted it in

---

### Post by Het Irv on 2008-05-14
> **farinx said:**
> snip
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb [http://repo.freecreations.info/ubuntu](http://repo.freecreations.info/ubuntu) gutsy freeverse

Well there's yer problem.... Amarok wants to be downloaded from the medibuntu repos, but you have the Hardy repos enabled on a Gutsy install.  Edit the two middle lines to say gutsy instead of hardy and try again.  Remember to reload your sources after editing
```
sudo apt-get update
```

---

### Post by Het Irv on 2008-05-16
Hey, farinx! Did that work?  If so let us know so that when other people have this problem they can find a solution.

---

