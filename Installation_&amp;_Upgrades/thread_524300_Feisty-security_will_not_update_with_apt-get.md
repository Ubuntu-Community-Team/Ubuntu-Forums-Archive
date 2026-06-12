---
title: "Feisty-security will not update with apt-get"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by ryharv on 2007-08-13
Hello, 

I run 7.04 (Feisty) server edition and am trying to update with apt-get.  Here is the response I get when running sudo apt-get:

```
ryan@rybuntu:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty Release.gpg
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty Release
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Get:3 http://security.ubuntu.com feisty-security Release [50.9kB]
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release    
Get:5 http://us.archive.ubuntu.com feisty-updates Release [32.4kB]         
Ign http://security.ubuntu.com feisty-security Release                          
Get:6 http://security.ubuntu.com feisty-security/main Packages [62.5kB]
Ign http://us.archive.ubuntu.com feisty-updates Release     
Get:7 http://us.archive.ubuntu.com feisty Release [57.2kB]
Get:8 http://security.ubuntu.com feisty-security/restricted Packages [6360B]    
Get:9 http://security.ubuntu.com feisty-security/main Sources [11.1kB]          
Get:10 http://security.ubuntu.com feisty-security/restricted Sources [953B]                
Get:11 http://security.ubuntu.com feisty-security/universe Packages [26.1kB]
Ign http://us.archive.ubuntu.com feisty Release                                          
Get:12 http://security.ubuntu.com feisty-security/universe Sources [3372B]     
Get:13 http://security.ubuntu.com feisty-security/multiverse Packages [6101B]  
Get:14 http://security.ubuntu.com feisty-security/multiverse Sources [1052B]   
Get:15 http://us.archive.ubuntu.com feisty-updates/main Packages [54.7kB] 
Get:16 http://us.archive.ubuntu.com feisty-updates/restricted Packages [14B]
Get:17 http://us.archive.ubuntu.com feisty-updates/main Sources [19.2kB]
Get:18 http://us.archive.ubuntu.com feisty-updates/restricted Sources [14B]
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Fetched 333kB in 3s (86.9kB/s)
Reading package lists... Done
[COLOR="Red"]W: GPG error: http://security.ubuntu.com feisty-security Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com feisty-updates Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com feisty Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems[/COLOR]
```

I haven't changed anything in my sources.list.  Here it is:

```
ryan@rybuntu:/etc/apt$ cat sources.list
# 
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

Any help appreciated.  Thanks...

  Ryan Harvey

---

### Post by martalli on 2007-08-15
I am getting very much the same problem when I am running an update.

```

manish@manish-thinks:~$ sudo apt-get update
Password:
Get: 1 http://security.ubuntu.com feisty-security Release.gpg [191B]                                               
Ign http://security.ubuntu.com feisty-security/main Translation-en_US                                              
Get: 2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Get: 3 http://archive.ubuntu.com feisty-updates Release.gpg [191B]   
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Get: 4 http://security.ubuntu.com feisty-security Release [50.9kB]   
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US     
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US     
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US       
Get: 5 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]    
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US           
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US     
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US              
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US  
Hit http://archive.ubuntu.com feisty-updates Release                     
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Get: 6 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B] 
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Err http://archive.ubuntu.com feisty-updates Release                      
  
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release      
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-backports Release                                        
Err http://us.archive.ubuntu.com feisty Release                                                  
  
Get: 7 http://archive.ubuntu.com feisty-updates Release [32.4kB]                                 
Get: 8 http://us.archive.ubuntu.com feisty Release [57.2kB]                                      
Ign http://security.ubuntu.com feisty-security Release                                           
Get: 9 http://security.ubuntu.com feisty-security/main Packages [63.7kB]                      
Ign http://archive.ubuntu.com feisty-updates Release                                    
Hit http://archive.ubuntu.com feisty-updates/restricted Packages                        
Ign http://us.archive.ubuntu.com feisty Release                                                     
Hit http://archive.ubuntu.com feisty-updates/main Packages                                          
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages             
Hit http://archive.ubuntu.com feisty-updates/universe Packages               
Get: 10 http://us.archive.ubuntu.com feisty-updates Release [32.4kB]         
Get: 11 http://us.archive.ubuntu.com feisty-backports Release [44.6kB]
Ign http://us.archive.ubuntu.com feisty-updates Release                                                 
Get: 12 http://security.ubuntu.com feisty-security/restricted Packages [6360B]                          
Get: 13 http://security.ubuntu.com feisty-security/multiverse Packages [6101B]          
Get: 14 http://security.ubuntu.com feisty-security/main Sources [11.5kB]                
Hit http://us.archive.ubuntu.com feisty/main Packages                                  
Hit http://us.archive.ubuntu.com feisty/restricted Packages                            
Ign http://us.archive.ubuntu.com feisty-backports Release                                          
Get: 15 http://security.ubuntu.com feisty-security/restricted Sources [953B]                       
Get: 16 http://security.ubuntu.com feisty-security/universe Packages [26.1kB]
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://us.archive.ubuntu.com feisty/main Sources                           
Hit http://us.archive.ubuntu.com feisty/restricted Sources                     
Hit http://us.archive.ubuntu.com feisty/universe Packages                         
Hit http://us.archive.ubuntu.com feisty/universe Sources                          
Get: 17 http://security.ubuntu.com feisty-security/universe Sources [3372B]       
Hit http://us.archive.ubuntu.com feisty-updates/main Packages              
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Fetched 337kB in 3s (112kB/s)
Reading package lists... Done
W: GPG error: http://security.ubuntu.com feisty-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com feisty-updates Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com feisty Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com feisty-updates Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com feisty-backports Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

```

This is a xubuntu machine, running 7.04

---

### Post by cudaman73 on 2007-11-27
I must add my own machine to the problems listed.

Fresh install of Ubuntu Server 7.04, the only changes I made to sources.lst was disabling the deb-cdrom and uncommenting backports.

running sudo apt-get install gpgv updates it to a new executable, but the same problem still occurs.

---

### Post by cudaman73 on 2007-11-27
UPDATE:

Turns out my problem was with the date being set incorrectly.

It was set to some time in 2003.

Using the date command to set it much closer to the proper date has solved the issue.

It turns out that gpgv will not update keys if the time difference is too great.

---

