---
title: "Synaptic will only open if I 'gksudo synaptic' from terminal"
date: 2014-02-20
forum: Installation &amp; Upgrades
---

### Post by ACGilbert on 2014-02-20
I recently got stuck in the lightdm login loop following an inplace update from 12.04 to 12.04.4.
I almost resolved that from a shell by:
```
sudo chown user:user .Xauthority
```
That got me logged in with an empty desktop.
Resolved that from a shell by:
```
sudo chown user:user .ICEauthority
```
So now my desktop looks good, but I cannot open Synaptic unless I:
```
gksudo synaptic
``` from a terminal window.
I also noticed if I open System  Settings > User Accounts, I am unable to unlock my account or add another for testing.
I have spent hours researching this, but am truely stumped.
Thanks in advance for any help,
AC

---

### Post by egeezer on 2014-02-20
I had a similar problem with 12.04.4.  When I finally did manage to get it open I immediately did a Reload, which required 100+ updates.  I had loaded 12.04.4 from a fresh DVD, so it may be that the current downloads have old Synaptic content.

---

### Post by Bucky Ball on 2014-02-20
Yes, I would:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... and post any errors.

---

### Post by ACGilbert on 2014-02-21
Buckey Ball,
Thanks for your help!
I didn't see any errors, but I'll post the output in case you see something as problem is still unresolved.
I guess a better description of my problem is that the dialog box for logging in as root has gone away for Synaptic, User Accounts, Ubuntu Tweak, and probably others that I'm unaware of.

```
papa@papa-desktop:~$ sudo apt-get update
[sudo] password for papa: 
Hit http://repo.steampowered.com precise Release.gpg
Hit http://repo.steampowered.com precise Release                               
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://us.archive.ubuntu.com precise Release                               
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://repo.steampowered.com precise/steam Sources                         
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Get:5 http://archive.canonical.com precise Release.gpg [198 B]                 
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://deb.playonlinux.com precise Release.gpg                             
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise-backports Release                     
Get:6 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Get:7 http://archive.canonical.com precise Release [7,078 B]                   
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://deb.playonlinux.com precise Release                                 
Ign http://repo.steampowered.com precise/steam TranslationIndex                
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:8 http://us.archive.ubuntu.com precise-updates/main Sources [452 kB]       
Hit http://extras.ubuntu.com precise Release                                   
Get:9 http://archive.canonical.com precise/partner amd64 Packages [7,908 B]    
Get:10 http://security.ubuntu.com precise-security/main Sources [97.7 kB]      
Get:11 http://archive.canonical.com precise/partner i386 Packages [8,933 B]    
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://deb.playonlinux.com precise/main amd64 Packages                     
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://deb.playonlinux.com precise/main i386 Packages                      
Ign http://deb.playonlinux.com precise/main TranslationIndex                   
Get:12 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:13 http://security.ubuntu.com precise-security/universe Sources [30.9 kB]  
Get:14 http://security.ubuntu.com precise-security/multiverse Sources [1,782 B]
Get:15 http://security.ubuntu.com precise-security/main amd64 Packages [363 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,028 B]
Get:17 http://us.archive.ubuntu.com precise-updates/universe Sources [105 kB]  
Get:18 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,490 B]
Get:19 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [752 kB]
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Get:20 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:21 http://security.ubuntu.com precise-security/universe amd64 Packages [90.9 kB]
Get:22 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [12.2 kB]
Get:23 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [236 kB]
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Get:24 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,443 B]
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:25 http://security.ubuntu.com precise-security/main i386 Packages [387 kB] 
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:26 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [14.5 kB]
Get:27 http://us.archive.ubuntu.com precise-updates/main i386 Packages [774 kB]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:28 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:29 http://security.ubuntu.com precise-security/universe i386 Packages [95.4 kB]
Get:30 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,641 B]
Get:31 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:32 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:33 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:34 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Get:35 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [12.2 kB]
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:36 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [241 kB]
Ign http://deb.playonlinux.com precise/main Translation-en_US                  
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:37 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [14.7 kB]
Get:38 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:39 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:40 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:41 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Ign http://deb.playonlinux.com precise/main Translation-en                     
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:42 http://us.archive.ubuntu.com precise-updates/universe Translation-en [138 kB]
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://repo.steampowered.com precise/steam Translation-en_US              
Ign http://repo.steampowered.com precise/steam Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 3,985 kB in 4s (973 kB/s)
Reading package lists... Done
papa@papa-desktop:~$ 
```

```
papa@papa-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin jockey-common jockey-gtk
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,168 kB of archives.
After this operation, 9,216 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ precise/partner adobe-flash-properties-gtk amd64 11.2.202.341-0precise1 [134 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main jockey-gtk all 0.9.7-0ubuntu7.14 [9,120 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main jockey-common all 0.9.7-0ubuntu7.14 [132 kB]
Get:4 http://archive.canonical.com/ubuntu/ precise/partner adobe-flashplugin amd64 11.2.202.341-0precise1 [6,893 kB]
Fetched 7,168 kB in 5s (1,240 kB/s)            
(Reading database ... 258006 files and directories currently installed.)
Preparing to replace adobe-flash-properties-gtk 11.2.202.336-0precise1 (using .../adobe-flash-properties-gtk_11.2.202.341-0precise1_amd64.deb) ...
Unpacking replacement adobe-flash-properties-gtk ...
Preparing to replace adobe-flashplugin 11.2.202.336-0precise1 (using .../adobe-flashplugin_11.2.202.341-0precise1_amd64.deb) ...
update-alternatives: warning: alternative /usr/lib/gnash/libgnashplugin.so (part of link group mozilla-flashplugin) doesn't exist. Removing from list of alternatives.
Unpacking replacement adobe-flashplugin ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.13 (using .../jockey-gtk_0.9.7-0ubuntu7.14_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.13 (using .../jockey-common_0.9.7-0ubuntu7.14_all.deb) ...
Unpacking replacement jockey-common ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up adobe-flashplugin (11.2.202.341-0precise1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode.
Setting up adobe-flash-properties-gtk (11.2.202.341-0precise1) ...
Setting up jockey-common (0.9.7-0ubuntu7.14) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.14) ...
papa@papa-desktop:~$ 

```

```
papa@papa-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
papa@papa-desktop:~$
``` 

AC

P.S. I haven't made any other changes to my system and will only do what you suggest, however I was continuing to research this and came up with the following:
```
papa@papa-desktop:~$ synaptic-pkexec
==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Multiple identities can be used for authentication:
 1.  firstname lastname,,, (papa)
 2.  firstname lastname,,, (papa)
Choose identity to authenticate as (1-2): 1
Password: 
==== AUTHENTICATION COMPLETE ===
```
Whereupon Synaptic opens with root privileges.
Not sure why I'm listed twice?

---

### Post by ACGilbert on 2014-02-28
Well, after several more days of trying to find a simple and/or elegant solution, I gave up.
I was an Administrator with the correct ownership and privileges; sudoer as well; PATH statement was correct; etc.; etc.
I reinstalled from a 12.04.4 DVD, leaving home directory unformatted, and am presently reinstalling some apps as well as printer and scanner drivers.
Live and learn.
AC

---

