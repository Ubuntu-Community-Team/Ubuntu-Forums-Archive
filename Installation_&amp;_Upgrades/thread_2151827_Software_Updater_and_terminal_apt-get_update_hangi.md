---
title: "Software Updater and terminal apt-get update hanging"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by BazBear on 2013-06-05
Earlier today I ran the Software Updater (ETA- 13.04 kernel 3.8.0-23), and had it start a fairly big update (new Chrome build, and a bunch of other little updates totalling ~56 MB). It was going along just fine, until it hung at configuring rsyslog for over an hour. I killed the updater, rebooted, and tried a terminal 'sudo apt-get update', and it has now hung again. I'll post the terminal output.```
bazbear@ubuntu:~$ sudo apt-get update 
Hit http://dl.google.com stable Release.gpg
Hit http://us.archive.ubuntu.com raring Release.gpg                            
Hit http://dl.google.com stable Release.gpg                                    
Get:1 http://us.archive.ubuntu.com raring-updates Release.gpg [933 B]          
Hit http://dl.google.com stable Release.gpg                                    
Get:2 http://security.ubuntu.com raring-security Release.gpg [933 B]           
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://extras.ubuntu.com raring Release.gpg                                
Hit http://archive.canonical.com raring Release.gpg                            
Get:3 http://us.archive.ubuntu.com raring-backports Release.gpg [933 B]        
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com raring Release                                
Get:4 http://security.ubuntu.com raring-security Release [40.8 kB]             
Hit http://archive.canonical.com raring Release                                
Hit http://extras.ubuntu.com raring Release                                    
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net raring Release                                    
Get:5 http://us.archive.ubuntu.com raring-updates Release [40.8 kB]            
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main i386 Packages                             
Get:6 http://us.archive.ubuntu.com raring-backports Release [40.8 kB]          
Hit http://archive.canonical.com raring/partner Sources                        
Hit http://extras.ubuntu.com raring/main Sources                               
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net raring/main Sources                               
Hit http://us.archive.ubuntu.com raring/main Sources                           
Hit http://us.archive.ubuntu.com raring/restricted Sources                     
Hit http://archive.canonical.com raring/partner i386 Packages                  
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Get:7 http://security.ubuntu.com raring-security/main Sources [21.5 kB]        
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://us.archive.ubuntu.com raring/multiverse Sources                     
Hit http://us.archive.ubuntu.com raring/universe Sources                       
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com raring/main i386 Packages                     
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages               
Get:8 http://security.ubuntu.com raring-security/restricted Sources [14 B]     
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                 
Get:9 http://security.ubuntu.com raring-security/multiverse Sources [697 B]    
Get:10 http://security.ubuntu.com raring-security/universe Sources [4,814 B]   
Get:11 http://security.ubuntu.com raring-security/main i386 Packages [61.2 kB] 
Hit http://us.archive.ubuntu.com raring/main Translation-en                    
Get:12 http://security.ubuntu.com raring-security/restricted i386 Packages [14 B]
Get:13 http://security.ubuntu.com raring-security/multiverse i386 Packages [1,389 B]
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en              
Ign http://archive.canonical.com raring/partner Translation-en_US              
Get:14 http://security.ubuntu.com raring-security/universe i386 Packages [16.9 kB]
Ign http://extras.ubuntu.com raring/main Translation-en_US                     
Ign http://ppa.launchpad.net raring/main Translation-en_US                     
Hit http://us.archive.ubuntu.com raring/restricted Translation-en              
Ign http://archive.canonical.com raring/partner Translation-en                 
Ign http://extras.ubuntu.com raring/main Translation-en                        
Ign http://ppa.launchpad.net raring/main Translation-en                        
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com raring/universe Translation-en       
Hit http://security.ubuntu.com raring-security/main Translation-en
Get:15 http://us.archive.ubuntu.com raring-updates/main Sources [30.3 kB]
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com raring-security/multiverse Translation-en       
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en       
Ign http://dl.google.com stable/main Translation-en_US                 
Get:16 http://us.archive.ubuntu.com raring-updates/restricted Sources [14 B]
Get:17 http://us.archive.ubuntu.com raring-updates/multiverse Sources [697 B]  
Hit http://security.ubuntu.com raring-security/restricted Translation-en       
Get:18 http://us.archive.ubuntu.com raring-updates/universe Sources [46.8 kB]
Ign http://dl.google.com stable/main Translation-en                            
Get:19 http://us.archive.ubuntu.com raring-updates/main i386 Packages [76.7 kB]
Hit http://security.ubuntu.com raring-security/universe Translation-en       
Get:20 http://us.archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Get:21 http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages [1,389 B]
Get:22 http://us.archive.ubuntu.com raring-updates/universe i386 Packages [88.0 kB]
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en     
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Get:23 http://us.archive.ubuntu.com raring-backports/main Sources [14 B]
Get:24 http://us.archive.ubuntu.com raring-backports/restricted Sources [14 B]
Get:25 http://us.archive.ubuntu.com raring-backports/universe Sources [3,278 B]
Ign http://security.ubuntu.com raring-security/main Translation-en_US  
Get:26 http://us.archive.ubuntu.com raring-backports/multiverse Sources [1,403 B]
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Get:27 http://us.archive.ubuntu.com raring-backports/main i386 Packages [14 B]
Get:28 http://us.archive.ubuntu.com raring-backports/restricted i386 Packages [14 B]
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Get:29 http://us.archive.ubuntu.com raring-backports/universe i386 Packages [5,005 B]
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Get:30 http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages [1,345 B]
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                 
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US             
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US   
Fetched 487 kB in 7s (68.3 kB/s)                                               
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bazbear@ubuntu:~$ sudo dpkg --configure -a
Setting up rsyslog (5.8.11-2ubuntu2.1) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
```
Does anyone have any idea what's going on here, or what to do about it? If you need more info please tell me what commands to run. Thanks in advance!

---

### Post by BazBear on 2013-06-06
I'm sure this wasn't the ideal solution, but what worked was deleting the apparently troubled '[COLOR=#000000][FONT=Ubuntu Mono]/etc/apparmor.d/disable: usr.sbin.rsyslogd', rebooting, then running 'sudo apt-get update', followed by '[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --configure -a' when prompted by the terminal. [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] This time the update finished without a hitch.[/FONT][/COLOR]

---

