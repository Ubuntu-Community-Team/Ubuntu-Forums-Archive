---
title: "ubuntu 13.04 say package operation failed when trying to update ?"
date: 2013-07-30
forum: Installation &amp; Upgrades
---

### Post by mjx360 on 2013-07-30
i been trying to update ubuntu 13.04 for about a month and i'm still cant do anyone know how to fix it ?

---

### Post by Bhawani007 on 2013-07-30
Terminal output please. We can't help until we have something to check.

---

### Post by SweetAurora on 2013-07-30
run in a terminal:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
and post the result here.

---

### Post by mjx360 on 2013-07-30
i did sudo apt-get update and this what i gotmj@ubuntu:~$ sudo apt-get update
[sudo] password for mj: 
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2) lucid Release.gpg
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2) lucid Release
Err cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2) lucid/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2) lucid/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2) lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2) lucid/main Translation-en
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2) lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2) lucid/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg [933 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release.gpg [933 B]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release [40.8 kB]            
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release [40.8 kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages                     
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted i386 Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en                
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Sources [52.3 kB]       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Sources [14 B]    
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Sources [66.6 kB]   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Sources [1,825 B] 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages [135 kB]  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B]          
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages [128 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40.8 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources [33.6 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources [14 B]    
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources [7,117 B]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources [1,825 B] 
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [88.4 kB] 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,612 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en            
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [28.9 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en      
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3,612 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Sources [14 B]       
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Sources [14 B] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en         
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Sources [4,720 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Sources [1,403 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main i386 Packages [14 B] 
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted i386 Packages [14 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe i386 Packages [5,998 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse i386 Packages [1,345 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en_US   
Fetched 690 kB in 14s (46.1 kB/s)                                              
W: Failed to fetch cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2)/dists/lucid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2)/dists/lucid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

---

### Post by mjx360 on 2013-07-30
i did sudo apt-get update && sudo apt-get dist-upgrade it still didnt work

---

### Post by SweetAurora on 2013-07-30
Good, now we know what is wrong. Open the Unity Dash and type "Software & Updates" and click on it. On the first tab after it loads, there is a section at the bottom called "Installable from CD-ROM/DVD" make sure everything is unchecked in that section. Now move over to the "Other Software" tab and check for PPA's/Repositories that list CD-ROM and/or DVD in their name or location and uncheck those. 

Close the window and then try updating and upgrading again.

---

### Post by mjx360 on 2013-07-31
i didn't understand what to check and uncheck are you saying check all that say PA's/Repositories or the ones that have CD-ROM and/or DVD in their name ?

---

### Post by grahammechanical on 2013-07-31
You have as your Software Sources or repositories a CDROM of Ubuntu 10.04. This you do not need as you are running 13.04. So, it makes sense to tidy up your Software Sources a little bit. And to do that in 13.04 we open Software & Updates. It can be found in System Settings which may be in the Launcher and is most certainly in the power/cog menu and can also be found as an application in the Dash.

With Software & Updates opened, look in the first tab called Ubuntu software. There is a box at the bottom of the tab that should read Cdrom with Ubuntu 10.04. It should also have a small tick box that is ticked. Un-tick it. For good measure, open the other software tab. Do you have any lines that begin [http://ppa?](http://ppa?) If so, is the tick box ticked. Un-tick it.

I am running Saucy Salamander and I recently got the same message when I ran Software Updater. My solution was to run in a terminal these two commands.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

And the system updated with out any error messages. This has worked a few times for me. You might get an error message and advice on how to fix it. Follow the advice. It might be something like

```
sudo apt-get -f install
```

or

```
sudo dpkg --configure -a
```

Regards.

---

### Post by mjx360 on 2013-07-31
when i do sudo apt-get upgrade i get this error 

dpkg: unrecoverable fatal error, aborting:
 files list file for package 'cups-client' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by Jimmy Kletch on 2013-09-25
Good day,

Same problem as mentioned thread.

Ran the following:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]
```
Then:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade[/FONT][/COLOR]
```

Turns out /boot ran out of space... Which was a "duh" moment for me because this has happened before.  Once I cleared out some of the older images, I ran "Software Updater" again.  

All is well.

Hope this helps!

Jim!

---

