---
title: "Clean Gutsy install errors when updating after install"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by asan on 2007-12-29
I just installed a second copy of Gutsy on another server.  The first one a month ago went fine.  Have not updated it since and after the last two days of trying to to get a second server online with a clean Gutsy install and update I won't be trying it very soon.

    A 'standard' type server, 1.2ghz AMD core, 512mb ram, ATI 8mb video, PS2 mouse and keyboard.  4 - 40gb Western digital hard drives, Intel Pro 100 NIC, ASUS A7 (something) motherboard. No sound, no printers, no 'extras'.  Just like the first one I did except the hard drives on the first one are 80gb drives instead of 40gb.

    The install from the Alternate CD goes well.  Partitioned HDs, setup mount points, formatted w/Ext 3 file system.....  Boots fine, can log in to Gnome environment, everything works.....

    Now there are 148 'updates' according to Update manager and Synaptic.  On first try I merrily just hit the upgrade manager and told it go ahead and do the updates.....
    It did - several failures to oddest was tzdata - which I was later able to get to run by changing my time zone to Berlin ?? I had seen some posts that said London as well.  Anyway, evolution, eog, evince, and most gnome updates fail with a script exit error code of 139.  No problem, I went to terminal mode, did apt-get clean, deleted the binarys from cache and retried.  Same errors....ok so at this point I reboot since the kernel has been updated.  Reboots fine.  Go to log in via gnome - system hangs - I believe it's using x-init scripts to log in.  Ok - reset, reboots fine.  This time I go to options and log in via gnome - no x-init scripts.  Log in just fine....
    Go back to synaptic, try to do the updates - fails the same way with the same errors...  This time I figure I did something wrong on the initial install - ok - np - I wipe everything and start over again including repartioning and reformatting the hard drives just to make sure....
    Same exact set of errors - tzdata acts the same way, same fix - changing the time zone to Berlin.  All other errors, eog, evolution, evince are all there....can't log in to gnome normally - have to use the options menu and log in via gnome there.  Tried the same procedures as before - apt-get clean, cleared the binary cache, tried individual packages via both apt-get and aptitude - same exit errors script returns error 139.  Tried 'package' --configure - same errors script error 139.

Can someone tell me just what the heck is going on?  I've seen issues w/Ubuntu before starting with 5.05 - different little things here and there but nothing that has stuck like this....  So anyone have any ideas?  I tried this install 5 times now making subtle changes but I get exactly the same results. 

   Anyone?

Thom

---

### Post by Partyboi2 on 2007-12-29
What is the output for
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by asan on 2007-12-30
I have to go in to my office to access this machine - with sshd-gnome running I can't get in to the machine via a normall ssh connection - sshd won't bind to the machine for remote access.  I'll be in there later today.

Thom

---

### Post by asan on 2007-12-30
Here are the results....


thom@enterprise:~$ sudo apt-get update
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                  
  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Get:7 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release [1005B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources
Fetched 1201B in 2s (451B/s)
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
thom@enterprise:~$ 


thom@enterprise:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  wine
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
20 not fully installed or removed.
Need to get 9965kB of archives.
After unpacking 336kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main wine 0.9.52~winehq0~ubuntu~7.10-1 [9965kB]
Fetched 9965kB in 1m12s (138kB/s)                                              
(Reading database ... 89779 files and directories currently installed.)
Preparing to replace wine 0.9.51~winehq0~ubuntu~7.10-1 (using .../wine_0.9.52~winehq0~ubuntu~7.10-1_i386.deb) ...
Unpacking replacement wine ...
Setting up capplets-data (1:2.20.1-0ubuntu1) ...
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up eog (2.20.1-0ubuntu1) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.20.1-0ubuntu1) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.12.1-0ubuntu1) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.12.1-0ubuntu1); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up file-roller (2.20.1-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.20.2-0ubuntu1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.20); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.21); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.20); however:
  Package gnome-control-center is not configured yet.
 gnome-session depends on gnome-control-center (<< 1:2.21); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
Setting up gdm (2.20.1-0ubuntu1) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit-common (2.20.3-0ubuntu1) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gedit-common (>= 2.20); however:
  Package gedit-common is not configured yet.
 gedit depends on gedit-common (<< 2.21); however:
  Package gedit-common is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-games-data (1:2.20.1-0ubuntu1) ...
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-games:
 gnome-games depends on gnome-games-data (= 1:2.20.1-0ubuntu1); however:
  Package gnome-games-data is not configured yet.
dpkg: error processing gnome-games (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (1:2.20.1-0ubuntu1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.20); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.21); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-system-monitor (2.20.1-0ubuntu1) ...
dpkg: error processing gnome-system-monitor (--configure):
 subprocess post-installation script returned error exit status 139
Setting up sound-juicer (2.20.1-0ubuntu1) ...
dpkg: error processing sound-juicer (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-system-tools (2.20.0-0ubuntu2) ...
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 139
Setting up wine (0.9.52~winehq0~ubuntu~7.10-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 capplets-data
 eog
 evince
 evolution-common
 evolution
 evolution-plugins
 file-roller
 gcalctool
 gnome-control-center
 gnome-session
 gdm
 gedit-common
 gedit
 gnome-games-data
 gnome-games
 gnome-panel-data
 gnome-panel
 gnome-system-monitor
 sound-juicer
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
thom@enterprise:~$

---

### Post by asan on 2007-12-30
Ok guys - here's what seemed to fix this - simple - maybe not elegant - but works....

go to /tmp, delete (rm) .X0-lock
go in to terminal mode  - or ctl & Alt & F1 (terminal)
sudo su (to root)
type "  dpkg configure -a  " w/o the quotes of course....

Seems there is some kind of permission error running it via update manager and synaptic once update manager has failed....

Thom

---

