---
title: "E:Encountered a section with no Package: header, E:Problem with MergeList, etc..."
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by L_Darmiento on 2013-08-07
[SIZE=3][FONT=verdana]All kinds of things aren't working right on this machine, I rebooted, it tried to update, I tried to run package mgr to no avail, I read a few similar threads I found on here using that google machine to ask what I should probably do, but I think each circumstance is slightly different, so I come to the u-forums for guidance. Below is my dilemma: 

[I]"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: 'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.)'
This usually means that your installed packages have unmet dependencies."
[/I]
[/FONT][/SIZE]

---

### Post by bapoumba on 2013-08-07
Hello,
unmet dependencies mean either there is something wrong in your sources.list, for ex a ppa that you removed, or entries for two different ubuntu releases, or some problem in the internet connection that corrupted or not completely downloaded files. Or.. Whatever else :)

What is the output to **cat /etc/apt/sources.list** (to have a look at your sources.list file) and **sudo apt-get update** (to read the files again and get a more thorough error message).

usually, in this situation, **sudo apt-get -f install** clears the problem, provided the sources.list is fine. The update command should tell you to run it if it is the right thing to do.

---

### Post by Bashing-om on 2013-08-07
L_Darmiento; Hi !

This:
> /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.)'

Says the file(s) is corrupted. so remove the files and repopulate (apt-get update) them ... see if that fixes the issue:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```
[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by L_Darmiento on 2013-08-08
[SIZE=3]Here's what I get after getting the sources.list and getting the thorough error message: [/SIZE][I][SIZE=3]
[/SIZE]

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted[/I]

*# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to*
*# newer versions of the distribution.*
*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted multiverse*
*deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted multiverse*

*## Major bug fix updates produced after the final release of the*
*## distribution.*
*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted multiverse*
*deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted multiverse*

*## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu*
*## team. Also, please note that software in universe WILL NOT receive any*
*## review or updates from the Ubuntu security team.*
*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe*
*deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe*
*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe*
*deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe*

*## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu *
*## team, and may not be under a free licence. Please satisfy yourself as to *
*## your rights to use the software. Also, please note that software in *
*## multiverse WILL NOT receive any review or updates from the Ubuntu*
*## security team.*

*## Uncomment the following two lines to add software from the 'backports'*
*## repository.*
*## N.B. software from this repository may not have been tested as*
*## extensively as that contained in the main release, although it includes*
*## newer versions of some applications which may provide useful features.*
*## Also, please note that software in backports WILL NOT receive any review*
*## or updates from the Ubuntu security team.*
*# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse*
*# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse*

*deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted multiverse*
*deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted multiverse*
*deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe*
*deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe*

*## Uncomment the following two lines to add software from Canonical's*
*## 'partner' repository.*
*## This software is not part of Ubuntu, but is offered by Canonical and the*
*## respective vendors as a service to Ubuntu users.*
*deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner*
*deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner*

*## This software is not part of Ubuntu, but is offered by third-party*
*## developers who want to ship their latest software.*
*deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main*
[I]deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


[/I]
-----------------------------------------------------------------

*Reading package lists... Error!*
*W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>*
*E: Encountered a section with no Package: header*
*E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages*
*E: The package lists or status file could not be parsed or opened.*





> **bapoumba said:**
> Hello,
unmet dependencies mean either there is something wrong in your sources.list, for ex a ppa that you removed, or entries for two different ubuntu releases, or some problem in the internet connection that corrupted or not completely downloaded files. Or.. Whatever else :)

What is the output to **cat /etc/apt/sources.list** (to have a look at your sources.list file) and **sudo apt-get update** (to read the files again and get a more thorough error message).

usually, in this situation, **sudo apt-get -f install** clears the problem, provided the sources.list is fine. The update command should tell you to run it if it is the right thing to do.

---

### Post by L_Darmiento on 2013-08-08
[B][SIZE=3]
any ideas of what i should do next? [/SIZE][/B]:?

---

### Post by bapoumba on 2013-08-09
Sorry, I was not around much yesterday. You need to import again the auth key for ubuntu-extras, see here for ex : [http://ubuntuforums.org/showthread.php?t=1869890&p=11396213#post11396213](http://ubuntuforums.org/showthread.php?t=1869890&p=11396213#post11396213)

---

### Post by L_Darmiento on 2013-08-09
> **bapoumba said:**
> Sorry, I was not around much yesterday. 

[B]No problem at all, thank you for helping. 
[/B]
> **bapoumba said:**
> You need to import again the auth key for ubuntu-extras, see here for ex : [http://ubuntuforums.org/showthread.php?t=1869890&p=11396213#post11396213](http://ubuntuforums.org/showthread.php?t=1869890&p=11396213#post11396213)

**Not sure what to do first, should I use that clearing code before I use the the sudo apt get update code? Am I trying to fix the error keys so that I can use the sudo apt get command?**

---

### Post by bapoumba on 2013-08-09
Yes please run **sudo apt-get update** to get the key numbers from the error message, then try to add them again.
You can post the output to the update command here if you prefer. Then we can walk you through.

---

### Post by L_Darmiento on 2013-08-09
> **bapoumba said:**
> Yes please run **sudo apt-get update** to get the key numbers from the error message, then try to add them again.
You can post the output to the update command here if you prefer. Then we can walk you through.

[SIZE=3][B]So those key numbers in the second part of my post earlier is what we're looking for I think, this was the output to the update command I think you're referring to (sorry if I buried it at the end of the output from the other command cat...sources.list) :


[/B][I]Reading package lists... Error!
[I]W: GPG error: [http://extras.ubuntu.com]("http://extras.ubuntu.com/") precise Release: The following signatures were invalid: BADSIG **[COLOR=#ff0000]16126D3A3E5C1192[/COLOR]** Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
[I]E: Encountered a section with no Package: header
[I]E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
[I]E: The package lists or status file could not be parsed or opened.
[/I][/I][/I][/I][/I][B]
My question for the next command is what is my keyserver address and should I put the signature number (in red above) in the code with or without < brackets > ? 

[/B]```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys < add keys here >
```
[/SIZE]

---

### Post by bapoumba on 2013-08-10
Yes please, the numbers above (sorry I overlooked your previous post) without the brackets.

---

### Post by L_Darmiento on 2013-08-10
> **bapoumba said:**
> Yes please, the numbers above (sorry I overlooked your previous post) without the brackets.
[B]
ok, i ran [/B]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192 **and got:**

[I][SIZE=3]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.FmqXGkBoT6 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192[/SIZE]
[SIZE=3]gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com[/SIZE]
[SIZE=3]gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 3 new signatures[/SIZE]
[SIZE=3]gpg: no ultimately trusted keys found[/SIZE]
[SIZE=3]gpg: Total number processed: 1[/SIZE]
[SIZE=3]gpg:         new signatures: 3[/SIZE][/I]

[SIZE=2]**then i reran** sudo apt-get update **and got:**
[/SIZE]
[I]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [412 kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources/DiffIndex                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [6,582 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [93.4 kB]  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages/DiffIndex             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [671 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [10.1 kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.6 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [211 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [692 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [215 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
[SIZE=3]Fetched 2,415 kB in 1s (1,288 kB/s)
[/SIZE][SIZE=3]Reading package lists... Error![/SIZE]
[SIZE=3]W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>[/SIZE]
[SIZE=3]E: Encountered a section with no Package: header[/SIZE]
[SIZE=3]E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages[/SIZE]
[/I][SIZE=3]*E: The package lists or status file could not be parsed or opened.*

**[SIZE=2]Same error!?!? [/SIZE]**[/SIZE]:confused:

---

### Post by bapoumba on 2013-08-11
Had you removed the faulty extra.ubuntu key as in drs305 post ?

---

### Post by L_Darmiento on 2013-08-12
> **bapoumba said:**
> Had you removed the faulty extra.ubuntu key as in drs305 post ?

**That did the trick! Thanks for your help! **

---

### Post by bapoumba on 2013-08-12
Glad you got it to work :)

---

