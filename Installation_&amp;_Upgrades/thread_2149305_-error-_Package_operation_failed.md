---
title: "-error- Package operation failed"
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by tarahbashi on 2013-05-28
Hi my friends , i got this error while try to istal all my softwares , I check a lot of thread from a lot of forum but i got nothing to solve my problem,
when i try to istall new software i got this error,

**Package operation failed**
**The installation or removal of a software package failed.**
installArchives() failed: Selecting previously unselected package libqtassistantclient4. 
(Reading database ...  
(Reading database ... 5% 
(Reading database ... 10% 
(Reading database ... 15% 
(Reading database ... 20% 
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45% 
(Reading database ... 50% 
(Reading database ... 55% 
(Reading database ... 60% 
(Reading database ... 65% 
(Reading database ... 70% 
(Reading database ... 75% 
(Reading database ... 80% 
(Reading database ... 85% 
(Reading database ... 90% 
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'thunderbird-globalmenu': Input/output error 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2) 
-----------------------------------------[SIZE=3]** Another software **[/SIZE]------------------------------------
**Package operation failed**
**The installation or removal of a software package failed.**
installArchives() failed: Selecting previously unselected package java-wrappers. 
(Reading database ...  
(Reading database ... 5% 
(Reading database ... 10% 
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30% 
(Reading database ... 35% 
(Reading database ... 40% 
(Reading database ... 45% 
(Reading database ... 50%
(Reading database ... 55% 
(Reading database ... 60% 
(Reading database ... 65%
(Reading database ... 70% 
(Reading database ... 75% 
(Reading database ... 80% 
(Reading database ... 85% 
(Reading database ... 90% 
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'thunderbird-globalmenu': Input/output error 
Error in function:  
----------------------------------
[SIZE=3]**And this story to be continue**[/SIZE][SIZE=3]**[[B]**]("https://www.google.com/search?client=ubuntu&hs=Alf&channel=fs&q=continue&spell=1&sa=X&ei=QKykUaWRMOXe7Ab4x4DABw&ved=0CCsQvwUoAA") for all my software i want to install [/B][/SIZE]:confused:

---

### Post by fantab on 2013-05-28
From Terminal [ctrl+alt+T] post the output of the following command:

```
sudo apt-get update
```

---

### Post by tarahbashi on 2013-05-28
:(

---

### Post by tarahbashi on 2013-05-28
[COLOR=#000000]HI dear I checked it but it doesnt work[/COLOR]

---

### Post by fantab on 2013-05-28
> **fantab said:**
> From Terminal [ctrl+alt+T] post the output of the following command:

```
sudo apt-get update
```

Post the output so we can see what the errors are. 
You are able to boot into Ubuntu, right?

---

### Post by tarahbashi on 2013-05-28
Dear I did **sudo apt-get update** and i got this result in terminal
-----------------------------
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports Release.gpg       
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]            
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise Release                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                 
Get:5 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [71.8 kB]
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports Release                     
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/main Sources                          
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/restricted Sources
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/universe Sources
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/multiverse TranslationIndex           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/universe TranslationIndex    
Get:8 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/main Sources [384 kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [24.3 kB] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,380 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [280 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [75.5 kB]
Get:14 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,375 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:17 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/universe Sources [88.8 kB] 
Get:18 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/multiverse Sources [6,582 B]
Get:19 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/main i386 Packages [631 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]                        
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]                        
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]                          
Get:23 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]                       
Get:24 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/universe i386 Packages [206 kB]                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                          
Get:25 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]                       
Get:26 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]                          
Get:27 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]                    
Get:28 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]                    
Get:29 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]                      
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/main Sources                                              
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/restricted Sources                                        
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/universe Sources                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                                      
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/multiverse Sources                                        
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/main i386 Packages                                        
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/restricted i386 Packages                                  
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/universe i386 Packages                                    
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                  
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/main TranslationIndex                                     
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                               
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/restricted TranslationIndex                               
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/universe TranslationIndex                                 
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/main Translation-en                                                 
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/multiverse Translation-en                                           
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/restricted Translation-en                                           
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise/universe Translation-en                                             
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/main Translation-en                                         
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/multiverse Translation-en                                   
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/restricted Translation-en                                   
Get:30 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-updates/universe Translation-en [119 kB]                         
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/main Translation-en                                       
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/multiverse Translation-en                                 
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/restricted Translation-en                                 
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) precise-backports/universe Translation-en                                   
Fetched 2,037 kB in 37s (55.0 kB/s)                                                                          
Reading package lists... Done

---

### Post by tarahbashi on 2013-05-28
This the picture of first error
[ATTACH=CONFIG]243172[/ATTACH]

---

### Post by tarahbashi on 2013-05-28
I forgot to tell , softwares have diffrent pakage error , in line 1 , they aren't same .

---

### Post by fantab on 2013-05-28
If you are trying to install Gparted then run the following command in terminal and **post the output to show errors**, if any:

```
sudo apt-get install gparted
```

Also tell us what other software/applications are you trying to install. 
To install certain applications we need to **enable 'Partner' repositories**. To ascertain this post the screen shot of 'software sources'. You can find it in Software Center -> Edit -> software sources -> Ubuntu software + Other (two screen shots).

---

### Post by tarahbashi on 2013-05-29
i did this following code
```

sudo apt-get install gparted

```
 in terminal ang got this error
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base amarok-help-en
Use 'apt-get autoremove' to remove them.
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils ntfsprogs kpartx dmraid gpart
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/543 kB of archives.
After this operation, 1,917 kB of additional disk space will be used.
Selecting previously unselected package gparted.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'thunderbird-globalmenu': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)



```

---

### Post by fantab on 2013-05-29
The problem is with 'thunderbird-globalmenu', it probably didn't install/update correctly. We need to remove it.

```
sudo dpkg --purge thunderbird-globalmenu
sudo apt-get remove --purge thunderbird-globalmenu
sudo apg-get autoremove
sudo apt-get clean
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gparted
```

NOTE: you can run only one 'apt-get' at any time. So before using the above in Terminal make sure all other 'apt-get' applications, like 'Software Center', etc. are closed.

---

### Post by tarahbashi on 2013-05-29
Thak you so much my friend.

the problem was "thunderbird-globalmenu " and i delete it .

also i find the same problem here : [http://ubuntuforums.org/archive/index.php/t-1232143.html](http://ubuntuforums.org/archive/index.php/t-1232143.html) 
/ solved in another way .
-------------------------
**But again thank you for helping me :P**

---

