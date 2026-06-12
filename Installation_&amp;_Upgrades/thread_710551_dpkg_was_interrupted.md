---
title: "dpkg was interrupted"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by orduek on 2008-02-28
what happend?
When i opened the Synaptec manager it gave me that error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I checked these forums and tried everything.
 sudo dpkg --configure -a
and got:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24.2
Cannot find /lib/modules/2.6.24.2
update-initramfs: failed for /boot/initrd.img-2.6.24.2
dpkg: subprocess post-installation script returned error exit status 1

then did sudo apt-get update and got:
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Release.gpg                                   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Translation-en_US                             
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Release                                       
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman/main Translation-en_US                     
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Packages                                      
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Packages                                      
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman/contrib Translation-en_US                  
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Hit [http://cafelinux.org](http://cafelinux.org) tinwoodman Release                                    
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna Release.gpg                                
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/main Translation-en_US                     
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/upstream Translation-en_US                 
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman/main Packages                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/import Translation-en_US                   
Ign [http://www.linuxmint.com](http://www.linuxmint.com) romeo Release.gpg                                 
Ign [http://www.linuxmint.com](http://www.linuxmint.com) romeo/daryna Translation-en_US                    
Hit [http://www.linuxmint.com](http://www.linuxmint.com) daryna Release                                    
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman/contrib Packages                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://cafelinux.org](http://cafelinux.org) tinwoodman/main Packages                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://www.linuxmint.com](http://www.linuxmint.com) romeo Release                                     
Hit [http://cafelinux.org](http://cafelinux.org) tinwoodman/contrib Packages                           
Get:6 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/main Packages                              
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/upstream Packages                          
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/import Packages                            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Ign [http://www.linuxmint.com](http://www.linuxmint.com) romeo/daryna Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                
Hit [http://www.linuxmint.com](http://www.linuxmint.com) daryna/main Packages                              
Hit [http://www.linuxmint.com](http://www.linuxmint.com) daryna/upstream Packages                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://www.linuxmint.com](http://www.linuxmint.com) daryna/import Packages                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://www.linuxmint.com](http://www.linuxmint.com) romeo/daryna Packages                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Fetched 6B in 11s (1B/s)                                                       
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

and ran sudo apt-get upgrade and got:
sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

anyone??

---

### Post by zvacet on 2008-02-28
You have mixed source list and that is probably your problem.

```
gksudo gedit /etc/apt/sources.list
```

Put # sign in front of every linuxmint,cafelinux.......line.You can leave medibuntu and wine.Save and close.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by aysiu on 2008-02-28
Run ```
sudo dpkg --configure -a
```

---

### Post by bbrg548 on 2008-02-29
I am getting the same problem. 

> jake@Athyra:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release [65.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages [1070kB]
Fetched 1136kB in 7s (155kB/s)                                                 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

and

> jake@Athyra:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

My current /etc/apt/sources.list reads (sorry, it's long):

> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://packages.medibuntu.org/gutsy](http://packages.medibuntu.org/gutsy) free non-free
# deb [http://packages.medibuntu.org/gutsy](http://packages.medibuntu.org/gutsy) free non-free
# deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
# deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe multiverse
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe multiverse
# deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper universe'
# deb [http://dvdstyler.sourceforge.net/repository/ubuntu](http://dvdstyler.sourceforge.net/repository/ubuntu) dapper main

Any ideas?

-Jake

---

### Post by aysiu on 2008-02-29
I don't know how to fix your problem, but your /etc/apt/sources.list isn't long at all. It's big, but there's only one repository actually enabled. All the lines that start with *#* might as well be blank.

This is the only repository you have enabled:
```
deb http://archive.ubuntu.com/ubuntu/ gutsy main
```

---

### Post by bbrg548 on 2008-02-29
Ok, I fixed mine. Found the solution [here]("http://ubuntuforums.org/showthread.php?t=706871&highlight=dpkg+error").

I was missing /usr/bin/getopt. Once I downloaded that and copied it to my /usr/bin/, and ran "sudo dpkg --configure -a" again, everything worked.

Your error for dpkg  doesn't seem to mention getopt, unless part got cut out of the post, but it looks very similar, so you might be missing part of the same package.

Hope this helps!

-Jake

---

### Post by orduek on 2008-02-29
it didn;t help
tried removing sources, and I do have getopt in my /usr/bin

any other suggestions?

---

### Post by teslarage on 2008-02-29
I tried to compile another kernel and that's how this error occured. Did you do the same thing?

Try this one here:
[http://ubuntuforums.org/showthread.php?t=616523&page=2&highlight=dpkg](http://ubuntuforums.org/showthread.php?t=616523&page=2&highlight=dpkg) :)

---

### Post by orduek on 2008-02-29
> **teslarage said:**
> I tried to compile another kernel and that's how this error occured. Did you do the same thing?

Try this one here:
[http://ubuntuforums.org/showthread.php?t=616523&page=2&highlight=dpkg](http://ubuntuforums.org/showthread.php?t=616523&page=2&highlight=dpkg) :)

Thanx.
It worked :)

---

