---
title: "Ubuntu 12.04 Update manager"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by MakeMakeMake on 2013-02-15
Hi

I'm using Ubuntu 12.04 LTS and recently got an error with my update manager: When I tried to install some updates, it all of a sudden showed an error message. The message said that an probably a programming error had occurred and the installation of the updates couldn't be continued. I had to restart my computer. Then I tried to install the updates again, but got an error message that not all updates could be installed. I tried it again (simply clicked on the install-button again) and now it worked.
 So now I'd like to know if there is some way to check if my update manager is working correctly again, and if all updates have been installed successfully. I'm also writing this because I haven't seen any new updates for quite some time now.

---

### Post by ibjsb4 on 2013-02-15
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And please post the errors.

---

### Post by MakeMakeMake on 2013-02-18
Hi, I got many messages, but none seems to be an error. How would an error message look like? (Or should I simply post the whole output of my console?)  Kind regards

---

### Post by ibjsb4 on 2013-02-18
Yes, just go ahead a post the whole thing using code tags.

[ATTACH]231591[/ATTACH]

---

### Post by MakeMakeMake on 2013-02-19
Hi,

this is what I got today:

```
flo@Flo-PC:~$ sudo apt-get update
[sudo] password for flo: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise InRelease                       
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates InRelease                
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports InRelease              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg               
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise Release.gpg                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                         
Get:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates Release.gpg [198 B]                          
Get:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise Release                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                              
Get:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates Release [49.6 kB]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Get:4 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main Sources                          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main amd64 Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse amd64 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main i386 Packages           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted i386 Packages     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe i386 Packages       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse TranslationIndex  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted TranslationIndex  
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe TranslationIndex
Get:6 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main Sources [367 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources        
Get:7 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted Sources [5,135 B]
Get:8 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe Sources [79.2 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Get:9 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse Sources [4,725 B]
Get:10 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main amd64 Packages [582 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:11 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted amd64 Packages [9,565 B]
Get:12 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe amd64 Packages [181 kB]
Get:13 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [9,421 B]
Get:14 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main i386 Packages [593 kB]    
Get:15 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted i386 Packages [9,503 B]
Get:16 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe i386 Packages [184 kB]
Get:17 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse i386 Packages [10.4 kB]
Get:18 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:19 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:20 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:21 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:22 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main Sources [2,422 B]           
Get:23 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:24 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe Sources [22.1 kB]
Get:25 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]
Get:26 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:27 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:28 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe amd64 Packages [22.6 kB]
Get:29 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,489 B]
Get:30 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:31 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:32 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe i386 Packages [22.6 kB]
Get:33 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse Translation-en      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted Translation-en      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe Translation-en
Get:34 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main Translation-en [260 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse Translation-en              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Fetched 2,488 kB in 2s (1,053 kB/s)                     
Reading package lists... Done
flo@Flo-PC:~$
```

---

### Post by Bashing-om on 2013-02-19
MakeMakeMake; Hi !

The output of "apt-get update" is clean.
See now what results from terminal command:
```
sudo apt-get upgrade
```looking for the status of installed packages, any problems and 'dpkg' will report it.
[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by MakeMakeMake on 2013-02-20
Hi,

thanks for your help.
I got the following output:

```
flo@Flo-PC:~$ sudo apt-get upgrade
[sudo] password for flo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
flo@Flo-PC:~$ 
```

---

### Post by Bashing-om on 2013-02-20
MakeMakeMake; Looking good .

According to "apt-get upgrade" 's output - update manager should have no problem at this time . Your system appears to be fully updated.

[INDENT][INDENT]hope I have helped
 
[/INDENT][/INDENT]

---

