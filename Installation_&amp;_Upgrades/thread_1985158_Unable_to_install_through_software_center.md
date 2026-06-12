---
title: "Unable to install through software center"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by wjsomething on 2012-05-22
Whenever I try to install something through the software center the installation gets about halfway and then I get the following error message:

```
installArchives() failed: Selecting previously unselected package libaacs0.
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
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libgstreamer0.10-0' is missing final newline
Error in function:
 SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
```

Also, since this might be related, the movie player that's already installed (the default I guess) doesn't open at all.

Any advice is appreciated, thanks.

---

### Post by fantab on 2012-05-22
From terminal run:

```
sudo apt-get update
```

If there are any errors:

```
sudo rm var/lib/apt/lists/* -vf
sudo apt-get update
```

Then try installing packages from Software Center.

For Movie Player to work with "all file formats" install ubuntu-restricted-extras

---

### Post by sammiev on 2012-05-22
> **fantab said:**
> From terminal run:

```
sudo apt-get update
```

If there are any errors:

```
sudo rm var/lib/apt/lists/* -vf
sudo apt-get update
```

Then try installing packages from Software Center.

For Movie Player to work with "all file formats" install ubuntu-restricted-extras

Used it before. :)

---

### Post by MadmanRB on 2012-05-22
Ah, the OP made duplicate topics thats why I saw that this had a reply and my name wasnt in, but yes do as fantab suggested.

---

### Post by fantab on 2012-05-22
Change the SERVER from Update Manager to 'MAIN' or any other... and try again.

---

### Post by wjsomething on 2012-05-23
None of these have worked for me. Any other suggestions? All help is appreciated :)

---

### Post by fantab on 2012-05-24
> **wjsomething said:**
> None of these have worked for me. Any other suggestions? All help is appreciated :)

It will better if you tell us clearly what all you have tried so that we don't end up pointing out what you have already tried. **Post the output of:**

```
$ sudo apt-get update
```Meanwhile try:

```
$ sudo apt-get clean all
$ sudo apt-get update
```OR

Download computer-janitor run it to clean everything you can using it.

```
$ sudo apt-get install computer-janitor
```After that update your system.

---

### Post by wjsomething on 2012-05-24
The first command gave me the following:

```
Ign http://ppa.launchpad.net precise InRelease
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Ign http://us.archive.ubuntu.com precise-proposed InRelease                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://security.ubuntu.com precise-security InRelease                      
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Hit http://ppa.launchpad.net precise Release                                   
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:3 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:4 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://ppa.launchpad.net precise/main Sources                              
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:6 http://us.archive.ubuntu.com precise-proposed Release.gpg [198 B]        
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:7 http://us.archive.ubuntu.com precise Release [49.6 kB]                   
Get:8 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Get:9 http://security.ubuntu.com precise-security/main Sources [12.1 kB]       
Get:10 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:11 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Get:12 http://security.ubuntu.com precise-security/universe Sources [4,522 B]  
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [696 B]  
Get:14 http://security.ubuntu.com precise-security/main amd64 Packages [41.8 kB]
Get:15 http://us.archive.ubuntu.com precise-proposed Release [49.6 kB]         
Get:16 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:17 http://security.ubuntu.com precise-security/universe amd64 Packages [10.3 kB]
Get:18 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,142 B]
Get:19 http://security.ubuntu.com precise-security/main i386 Packages [43.1 kB]
Get:20 http://us.archive.ubuntu.com precise/main Sources [934 kB]              
Get:21 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:22 http://security.ubuntu.com precise-security/universe i386 Packages [10.3 kB]
Get:23 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:24 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:25 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Get:26 http://extras.ubuntu.com precise Release.gpg [72 B]  
Hit http://archive.canonical.com precise Release            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main Sources           
Hit http://archive.canonical.com precise/partner amd64 Packages
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:27 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:28 http://us.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]     
Get:29 http://us.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:30 http://us.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB] 
Get:31 http://us.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:32 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:33 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:34 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:35 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:36 http://us.archive.ubuntu.com precise-updates/main Sources [44.7 kB]     
Get:37 http://us.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:38 http://us.archive.ubuntu.com precise-updates/universe Sources [13.4 kB] 
Get:39 http://us.archive.ubuntu.com precise-updates/multiverse Sources [696 B] 
Get:40 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [114 kB]
Get:41 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]
Get:42 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [35.5 kB]
Get:43 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,142 B]
Get:44 http://us.archive.ubuntu.com precise-updates/main i386 Packages [116 kB]
Get:45 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:46 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [36.0 kB]
Get:47 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [1,393 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:48 http://us.archive.ubuntu.com precise-backports/main Sources [700 B]     
Get:49 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:50 http://us.archive.ubuntu.com precise-backports/universe Sources [3,096 B]
Get:51 http://us.archive.ubuntu.com precise-backports/multiverse Sources [14 B]
Get:52 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [559 B]
Get:53 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:54 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [2,656 B]
Get:55 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [14 B]
Get:56 http://us.archive.ubuntu.com precise-backports/main i386 Packages [559 B]
Get:57 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:58 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [2,653 B]
Get:59 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Get:60 http://us.archive.ubuntu.com precise-proposed/restricted amd64 Packages [14 B]
Get:61 http://us.archive.ubuntu.com precise-proposed/main amd64 Packages [205 kB]
Get:62 http://us.archive.ubuntu.com precise-proposed/multiverse amd64 Packages [971 B]
Get:63 http://us.archive.ubuntu.com precise-proposed/universe amd64 Packages [26.5 kB]
Get:64 http://us.archive.ubuntu.com precise-proposed/restricted i386 Packages [14 B]
Get:65 http://us.archive.ubuntu.com precise-proposed/main i386 Packages [206 kB]
Get:66 http://us.archive.ubuntu.com precise-proposed/multiverse i386 Packages [972 B]
Get:67 http://us.archive.ubuntu.com precise-proposed/universe i386 Packages [26.5 kB]
Get:68 http://us.archive.ubuntu.com precise-proposed/main TranslationIndex [73 B]
Get:69 http://us.archive.ubuntu.com precise-proposed/multiverse TranslationIndex [71 B]
Get:70 http://us.archive.ubuntu.com precise-proposed/restricted TranslationIndex [70 B]
Get:71 http://us.archive.ubuntu.com precise-proposed/universe TranslationIndex [73 B]
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://us.archive.ubuntu.com precise-proposed/main Translation-en          
Hit http://us.archive.ubuntu.com precise-proposed/multiverse Translation-en    
Hit http://us.archive.ubuntu.com precise-proposed/restricted Translation-en    
Hit http://us.archive.ubuntu.com precise-proposed/universe Translation-en      
Fetched 19.7 MB in 30s (651 kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

I'm trying out the other commands now.

EDIT:

I used the second set of commands and got the following:

```
Ign http://ppa.launchpad.net precise InRelease
Ign http://archive.canonical.com precise InRelease                             
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://extras.ubuntu.com precise Release.gpg                               
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://security.ubuntu.com precise-security Release                        
Hit http://extras.ubuntu.com precise Release                                   
Ign http://us.archive.ubuntu.com precise-proposed InRelease                    
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main amd64 Packages            
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com precise-proposed Release.gpg                  
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/universe amd64 Packages        
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://us.archive.ubuntu.com precise-proposed Release                      
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://us.archive.ubuntu.com precise-updates/universe Sources              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages           
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-proposed/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-proposed/main amd64 Packages          
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://us.archive.ubuntu.com precise-proposed/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com precise-proposed/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-proposed/restricted i386 Packages     
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Hit http://us.archive.ubuntu.com precise-proposed/main i386 Packages           
Hit http://us.archive.ubuntu.com precise-proposed/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise-proposed/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise-proposed/main TranslationIndex        
Hit http://us.archive.ubuntu.com precise-proposed/multiverse TranslationIndex  
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://us.archive.ubuntu.com precise-proposed/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com precise-proposed/universe TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en             
Hit http://us.archive.ubuntu.com precise/main Translation-en         
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://us.archive.ubuntu.com precise-proposed/main Translation-en
Hit http://us.archive.ubuntu.com precise-proposed/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-proposed/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-proposed/universe Translation-en
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

---

### Post by raja.genupula on 2012-05-24
check out your source list for same lines of source . duplicate list sounds for same lines of code .```
gksu gedit  /etc/apt/sources.list
``` will list it and edit it to remove the same lines , :)

---

### Post by fantab on 2012-05-24
> **raja.genupula said:**
> check out your source list for same lines of source . duplicate list sounds for same lines of code .```
gksu gedit  /etc/apt/sources.list
``` will list it and edit it to remove the same lines , :)

Find the the following lines using the above command: 

```
W: Duplicate sources.list entry **http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages** (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry **http://archive.canonical.com/ubuntu/ precise/partner i386 Packages** (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
```

Delete them or edit them as follows: (the following lines are from my 64bit /etc/apt/sources.list)

```
**deb http://archive.canonical.com/ubuntu precise partner**
**deb-src http://archive.canonical.com/ubuntu precise partner**
```

Make sure that there are Only two above coded lines about Partner repos in sources.list. Then run

```
$ sudo rm /var/lib/apt/lists/* -vf 
$ sudo apt-get update
```

If in doubt, post the contents of /etc/apt/sources.list in code.

---

### Post by raja.genupula on 2012-05-25
> **fantab said:**
> Find the the following lines using the above command: 

```
W: Duplicate sources.list entry **http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages** (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry **http://archive.canonical.com/ubuntu/ precise/partner i386 Packages** (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
```

Delete them or edit them as follows: (the following lines are from my 64bit /etc/apt/sources.list)

```
**deb http://archive.canonical.com/ubuntu precise partner**
**deb-src http://archive.canonical.com/ubuntu precise partner**
```

Make sure that there are Only two above coded lines about Partner repos in sources.list. Then run

```
$ sudo rm /var/lib/apt/lists/* -vf 
$ sudo apt-get update
```

If in doubt, post the contents of /etc/apt/sources.list in code.

Good job , +1 . :)

---

