---
title: "Trouble after upgrading to 13.10"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by quarkhirad on 2013-11-21
Hi i just upgraded from 13.04 to 13.10 after restarting the system the following error message came after logging in.

The application Avant window navigator has closed unexpectedly. When i try launching it using terminal it gives the following error. 

 > khirad@gini:~$ avant-window-navigator 

** (avant-window-navigator:4379): CRITICAL **: desktop_agnostic_config_schema_get_metadata_option: assertion 'self != NULL' failed

** (avant-window-navigator:4379): CRITICAL **: desktop_agnostic_config_schema_get_metadata_option: assertion 'self != NULL' failed
Segmentation fault (core dumped)
khirad@gini:~$ 


please help me to get my avant doc back i really miss it

---

### Post by fantab on 2013-11-22
Uninstall AWN and re-install it again. How did you install the 'awn', from Ubuntu repos or ppa?
If you have installed it from PPA then, perhaps you need to change the ppa from 'raring' to 'saucy'. You can do this from Software Center ->Edit-> Software Sources-> Other Software-> select the PPA and 'Edit' -raring to saucy.

---

### Post by quarkhirad on 2013-11-22
Thanks Fantab 

when i uninstalled the avant and re installed it this what i got 

> khirad@gini:~$ sudo apt-get remove avant-window-navigator
[sudo] password for khirad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  avant-window-navigator-data awn-applet-animal-farm
  awn-applet-awn-system-monitor awn-applet-awnterm awn-applet-battery-applet
  awn-applet-cairo-clock awn-applet-cairo-main-menu awn-applet-comics
  awn-applet-common-folder awn-applet-cpufreq awn-applet-dialect
  awn-applet-feeds awn-applet-file-browser-launcher awn-applet-garbage
  awn-applet-hardware-sensors awn-applet-mail awn-applet-media-control
  awn-applet-media-icon-applet awn-applet-media-player
  awn-applet-notification-area awn-applet-quit-applet awn-applet-related
  awn-applet-shinyswitcher awn-applet-showdesktop awn-applet-stack
  awn-applet-thinkhdaps awn-applet-todo awn-applet-volume-control
  awn-applet-webapplet bzr fortune-mod fortunes-min librecode0 libvte-common
  libvte9 python-awn python-awn-extras python-bzrlib python-configobj
  python-desktop-agnostic python-gnomedesktop python-gpgme python-xklavier
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  avant-window-navigator awn-settings
0 upgraded, 0 newly installed, 2 to remove and 25 not upgraded.
After this operation, 1,652 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 261126 files and directories currently installed.)
Removing awn-settings ...
Removing avant-window-navigator ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
Processing triggers for gnome-menus ...
Processing triggers for gconf2 ...
khirad@gini:~$ sudo apt-get install avant-window-navigator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package avant-window-navigator is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  avant-window-navigator-data

E: Package 'avant-window-navigator' has no installation candidate
khirad@gini:~$

I dont remember how i installed avant as i have been doing upgrades from 11.10 ( that is no fresh install just use upgrade option). Hence before the auto upgrade used to take care of installation and hence i dont remember how i installed it. If you can make out the repository list is given below.

> 
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
# deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) raring-getdeb apps games # disabled on upgrade to saucy
deb-src [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) raring-getdeb apps games # disabled on upgrade to saucy


When i use synaptic to check for updates after reloading the repositories it gives the following output 

> GPG error: [http://mirrors.dotsrc.org](http://mirrors.dotsrc.org) raring-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CFFailed to fetch [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/source/Sources](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/source/Sources](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

any ideas how to re install avant

---

### Post by quarkhirad on 2013-11-22
Another thing that i forgot to mention was an error 

!) > Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

When i click on run this action now and enter my password it opens a terminal 

> flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.327.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.327.orig.tar.gz)

After ten seconds aprrox the terminal close and an error comes 

The application terminal has closed unexpectedly. 

Any ideas how to update flash plugin 

2) After upgrading my date is correct by the time is wrong and if i correct it manually then the time that windows shows gets screwed up. Before the update both windows and linux showed the same time.

---

### Post by fantab on 2013-11-22
> # deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) raring-getdeb apps games # disabled on upgrade to saucy
deb-src [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) raring-getdeb apps games # disabled on upgrade to saucy 

You need to edit these lines in your /etc/apt/sources.list, use gedit to edit these.

```
sudo gedit /etc/apt/sources.list
```
Now change the above quoted four lines as follows [note the changes in bold]:
> deb [http://archive.canonical.com/](http://archive.canonical.com/) **saucy** partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) **saucy** partner
**#**deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) raring-getdeb apps games # disabled on upgrade to saucy
**#**deb-src [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) raring-getdeb apps games # disabled on upgrade to saucy

I don't know why you have those last two lines. I have put '#' to comment them out. You can remove the two lines completely, if you want.

You need to clean up your package database:
```
sudo dpkg --purge flashplugin-installer
sudo apt-get remove --purge flashplugin-installer
sudo apt-get autoremove
sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

If you see any errors after 'apt-get update' then post them here, and if you don't then:

```
sudo apt-get dist-upgrade
```
Report if you see any errors.

And reinstall packages you need.

EDIT: use code tag '#' to paste large chunk of data. You have to "Go Advanced" to use the advanced editor to be able to use code tag.

---

### Post by quarkhirad on 2013-11-22
after typing apt-get update this is what i got 

> khirad@gini:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                               
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease                          
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports InRelease                        
Get:3 [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg [933 B]                   
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security InRelease                         
Get:5 [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg [933 B]                   
Get:6 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release [9,753 B]                         
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg [933 B]                      
Get:9 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:10 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources [14 B]                      
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg [933 B]             
Get:12 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,199 B]               
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release.gpg [933 B]           
Get:14 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages [14 B]               
Get:15 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,224 B]                
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release.gpg [933 B]            
Get:17 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages [14 B]                
Get:18 [http://archive.canonical.com](http://archive.canonical.com) saucy Release [7,072 B]                    
Get:19 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [761 B]                 
Get:20 [http://archive.canonical.com](http://archive.canonical.com) saucy Release [7,072 B]                    
Get:21 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [773 B]                  
Get:22 [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Sources [1,886 B]            
Get:23 [http://archive.canonical.com](http://archive.canonical.com) saucy/partner amd64 Packages [2,196 B]     
Get:24 [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages [3,150 B]      
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release [49.6 kB]                       
Get:26 [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Sources [1,886 B]            
Get:27 [http://archive.canonical.com](http://archive.canonical.com) saucy/partner amd64 Packages [2,196 B]     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                      
Get:28 [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages [3,150 B]      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                          
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release [49.6 kB]      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                   
Get:30 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg [316 B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                
Get:31 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg [316 B]             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg [316 B]             
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg [316 B]                      
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release [49.6 kB]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en_US      
Get:35 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg [316 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en                  
Get:36 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg [316 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg  
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en                  
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release [11.9 kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release [49.6 kB]              
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release [9,730 B]                        
Get:40 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release [11.9 kB]                        
Get:41 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release [11.9 kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Get:42 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release [11.9 kB]                        
Get:43 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release [11.8 kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Get:44 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Sources [1,784 B]                   
Get:45 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages [2,735 B]            
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages [2,890 B]             
Get:47 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Sources [624 B]                     
Get:48 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages [493 B]              
Get:49 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages [493 B]               
Get:50 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Sources [10.3 kB]                   
Get:51 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages [15.7 kB]            
Get:52 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages [15.7 kB]             
Get:53 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Sources [786 B]                     
Get:54 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages [1,209 B]            
Get:55 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages [1,214 B]             
Get:56 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Sources [727 B]                     
Get:57 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages [709 B]              
Get:58 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages [709 B]               
Get:59 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages [4,597 B]            
Get:60 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages [4,564 B]             
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Sources [1,009 kB]                 
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Sources [4,759 B]    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Sources [6,108 kB]             
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Sources [175 kB]             
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main amd64 Packages [1,239 kB]          
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted amd64 Packages [9,348 B]
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe amd64 Packages [5,643 kB]      
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse amd64 Packages [131 kB]      
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main i386 Packages [1,238 kB]           
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted i386 Packages [9,688 B]
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe i386 Packages [5,652 kB]       
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse i386 Packages [133 kB]       
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en [711 kB]            
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en [101 kB]
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en [2,686 B]
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en [3,886 kB]      
Get:77 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Sources [38.4 kB]          
Get:78 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Sources [14 B]       
Get:79 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Sources [15.8 kB]      
Get:80 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Sources [1,351 B]    
Get:81 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main amd64 Packages [93.9 kB]   
Get:82 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Get:83 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe amd64 Packages [42.5 kB]
Get:84 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [1,566 B]
Get:85 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main i386 Packages [93.6 kB]    
Get:86 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B] 
Get:87 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe i386 Packages [42.9 kB]
Get:88 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,776 B]
Get:89 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en [42.4 kB]   
Get:90 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en [717 B]
Get:91 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en [14 B]
Get:92 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en [23.9 kB]
Get:93 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Sources [14 B]           
Get:94 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Sources [14 B]     
Get:95 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Sources [795 B]      
Get:96 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Sources [834 B]    
Get:97 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main amd64 Packages [14 B]    
Get:98 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted amd64 Packages [14 B]
Get:99 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe amd64 Packages [604 B]
Get:100 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse amd64 Packages [14 B]
Get:101 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main i386 Packages [14 B]    
Get:102 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted i386 Packages [14 B]
Get:103 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe i386 Packages [602 B]
Get:104 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse i386 Packages [709 B]
Get:105 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en [14 B]   
Get:106 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en [525 B]
Get:107 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en [14 B]
Get:108 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en [617 B]
Get:109 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Sources [10.8 kB]        
Get:110 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Sources [14 B]     
Get:111 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Sources [6,871 B]    
Get:112 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Sources [688 B]    
Get:113 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main amd64 Packages [36.7 kB] 
Get:114 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted amd64 Packages [14 B]
Get:115 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe amd64 Packages [15.5 kB]
Get:116 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse amd64 Packages [1,155 B]
Get:117 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main i386 Packages [36.7 kB]  
Get:118 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Get:119 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe i386 Packages [15.8 kB]
Get:120 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse i386 Packages [1,389 B]
Get:121 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en [15.4 kB] 
Get:122 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en [587 B]
Get:123 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en [14 B]
Get:124 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en [9,652 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en_US
Fetched 27.0 MB in 9min 54s (45.4 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/source/Sources](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/source/Sources](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
khirad@gini:~$ 

---

### Post by fantab on 2013-11-22
Yes, I can confirm that the Errors are not working and even on my side I get 404 Error. So lets remove the ppa.

Open Synaptic ->Settings-> Repositories and 'uncheck' the above bad ppa's. Close Synaptic and rerun:

sudo apt-get update #if no errors then
sudo apt-get dist-upgrade

---

### Post by quarkhirad on 2013-11-22
Yeah i disabled the bad links and there were no errors. Though no dist upgrade 

> khirad@gini:~$ sudo apt-get dist-upgrade 
[sudo] password for khirad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
khirad@gini:~$

Though i am not surprised as i have 13.10 running . Though still no avant window navigator and no sign of the package in synaptic to install from.

Heeeellllllppppp

---

### Post by fantab on 2013-11-22
That's is good. No errors.

When Ubuntu 14.04 releases do a clean install, if you want to upgrade.
Also if you have space create another partition of about 20-25GB and install other versions on it. Keep LTS on its own partition. Have two versions of Ubuntu... one LTS and other latest which are released every 6 months.

AWN was not being maintained however there seems to some progress now.
[http://www.webupd8.org/2013/11/avant-window-navigator-gets-new.html](http://www.webupd8.org/2013/11/avant-window-navigator-gets-new.html)

If I were you, I would either install 'docky' or 'cairo-dock', both available in the repositories.

Good Luck..

---

### Post by quarkhirad on 2013-11-22
yeah i visited the site and did 

> sudo add-apt-repository ppa:awn-testing/ppa
sudo apt-get update
sudo apt-get install avant-window-navigator 

however when i launched it gave me the same error. i clicked close yet i have a dock on the bottom. :) though the trouble is that i had used a few other repositories to install some more applets. That i dont have now :(  :( . i think i shall try cairo-dock 

Hey any suggestions on the clock problem????

---

### Post by fantab on 2013-11-22
First of all remove the ppa.

Open 'System Montior' and look any AWN related processes, either 'end the process' or 'kill the process'.
If you can't tell then from Terminal
```
xkill
```
then click on the clock, lets hope it closes.

Then:
```
sudo dpkg --purge avant-window-navigator
sudo apt-get remove --purge avant-window-navigator
sudo apt-get autoremove
```

Cairo-Dock is quite good, but Docky is lighter.

---

### Post by quarkhirad on 2013-11-22
Hey i dont care now cairo is my new dock :guitar::p:rolleyes:

---

