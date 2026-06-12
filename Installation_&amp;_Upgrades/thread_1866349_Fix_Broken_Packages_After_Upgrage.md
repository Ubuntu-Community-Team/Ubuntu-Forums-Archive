---
title: "Fix Broken Packages After Upgrage"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by partyk1d24 on 2011-10-21
So I tried to do the 11.04 to 11.11 upgrade and some packages got broke. For example when I try running...

```
jackie@jackie-Latitude-E6410:~$ sudo apt-get install emdebian-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'emdebian-crush' instead of 'emdebian-tools'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 emdebian-crush : Depends: pdebuild-cross but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
jackie@jackie-Latitude-E6410:~$ sudo apt-get install emdebian-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'emdebian-crush' instead of 'emdebian-tools'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 emdebian-crush : Depends: pdebuild-cross but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I tried to go into synaptic and use repair broken packages on pdebuild-cross and got the following...

```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

Is there a way to search and manually repair depenancies? Do I need to do another reinstall?

---

### Post by partyk1d24 on 2011-10-21
Hummmm after more investigation I see this...
 pdebuild-cross : Depends: multistrap (>= 2.1.9) but 2.1.6ubuntu3 is to be installed

Should this be moved over to bug mode?

---

### Post by raja.genupula on 2011-10-21
do this 
```
sudo apt-get install -f
sudo apt-get update 
```

do them one by one and try again.let me know what you got.

All the best.

---

### Post by partyk1d24 on 2011-10-21
Thanks but see previous I think it is an issue in that Ubuntu uses an older version of the dependency :-/ Anyway here is your output..

```
root@jackie-Latitude-E6410:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
root@jackie-Latitude-E6410:~# apt-get update
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release [1,347 B]                            
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Get:3 http://dl.google.com stable/main amd64 Packages [1,202 B]                
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://ftp.debian.org lenny InRelease                                      
Get:4 http://dl.google.com stable/main i386 Packages [1,203 B]                 
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://archive.canonical.com oneiric Release                               
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://ftp.debian.org lenny Release.gpg                                    
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://us.archive.ubuntu.com oneiric Release                               
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://ftp.debian.org lenny Release                                        
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://ftp.debian.org lenny/main amd64 Packages                            
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://ftp.debian.org lenny/contrib amd64 Packages                         
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ftp.debian.org lenny/non-free amd64 Packages                        
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://ftp.debian.org lenny/main i386 Packages                             
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://ftp.debian.org lenny/contrib i386 Packages                          
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://ftp.debian.org lenny/non-free i386 Packages                         
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Ign http://ftp.debian.org lenny/contrib TranslationIndex                       
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://ftp.debian.org lenny/main TranslationIndex                          
Ign http://archive.canonical.com oneiric/partner Translation-en                
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Ign http://ftp.debian.org lenny/non-free TranslationIndex            
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Ign http://ftp.debian.org lenny/contrib Translation-en_US
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Ign http://ftp.debian.org lenny/contrib Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Ign http://ftp.debian.org lenny/non-free Translation-en_US
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Ign http://ftp.debian.org lenny/non-free Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Fetched 3,950 B in 4s (854 B/s)
Reading package lists... Done
```

---

### Post by raja.genupula on 2011-10-21
[http://packages.ubuntu.com/oneiric/pdebuild-cross](http://packages.ubuntu.com/oneiric/pdebuild-cross)

get that package and install it by using

**sudo dpkg -i <pkg name>** command and then try again installing what you wanna .

all the best man.

---

### Post by abeh on 2012-12-05
> **raja.genupula said:**
> [http://packages.ubuntu.com/oneiric/pdebuild-cross](http://packages.ubuntu.com/oneiric/pdebuild-cross)
 
get that package and install it by using
 
**sudo dpkg -i <pkg name>** command and then try again installing what you wanna .
 
all the best man.
 I get the same error. I need to install Emdebian toolchain for cross compiling and cannot get it done. It is frustrating. Please help! -Thanks.

---

