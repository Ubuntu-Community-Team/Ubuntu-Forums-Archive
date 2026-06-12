---
title: "404 while &quot;sudo apt-get update&quot;"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by vignesh2066 on 2013-06-06
When I fired my command```
 sudo apt-get update
``` 

found the following error

```
vignesh@ubuntu:~$ sudo apt-get update
Get:1 ftp://ftp.iitb.ac.in natty InRelease                                     
Ign ftp://ftp.iitb.ac.in natty InRelease                                       
Get:2 ftp://ftp.iitb.ac.in natty Release.gpg [198 B]                           
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://archive.cloudera.com precise-cdh4 InRelease                         
Ign http://archive.cloudera.com lucid-cdh3 InRelease                           
Get:3 ftp://ftp.iitb.ac.in natty Release [39.8 kB]                             
Get:4 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Get:5 http://archive.cloudera.com precise-cdh4 Release.gpg [198 B]             
Get:6 http://ppa.launchpad.net natty Release [9,731 B]                         
Get:7 http://archive.cloudera.com lucid-cdh3 Release.gpg [198 B]               
Get:8 http://archive.cloudera.com precise-cdh4 Release [1,682 B]               
Get:9 http://ppa.launchpad.net natty/main Sources [2,544 B]                    
Get:10 http://archive.cloudera.com lucid-cdh3 Release [2,419 B]                
Get:11 http://archive.cloudera.com precise-cdh4/contrib Sources [6,773 B]      
Get:12 http://ppa.launchpad.net natty/main amd64 Packages [7,720 B]            
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:13 http://archive.cloudera.com precise-cdh4/contrib amd64 Packages [19.8 kB]
Get:14 ftp://ftp.iitb.ac.in natty/main Sources [862 kB]                        
Ign http://archive.cloudera.com precise-cdh4/contrib TranslationIndex          
Get:15 http://archive.cloudera.com lucid-cdh3/contrib Sources [5,329 B]        
Get:16 http://archive.cloudera.com lucid-cdh3/contrib amd64 Packages [14.0 kB] 
Ign http://archive.cloudera.com lucid-cdh3/contrib TranslationIndex            
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://archive.cloudera.com precise-cdh4/contrib Translation-en_US         
Ign http://archive.canonical.com natty InRelease                               
Ign http://archive.cloudera.com precise-cdh4/contrib Translation-en            
Ign http://archive.cloudera.com lucid-cdh3/contrib Translation-en_US           
Get:17 http://archive.canonical.com natty Release.gpg [198 B]                  
Ign http://archive.cloudera.com lucid-cdh3/contrib Translation-en              
Get:18 http://archive.canonical.com natty Release [5,916 B]                    
Get:19 http://archive.canonical.com natty/partner amd64 Packages [6,634 B]     
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://cran.rstudio.com natty/ InRelease                                   
Ign http://us.archive.ubuntu.com natty Release.gpg                             
Ign http://cran.rstudio.com natty/ Release.gpg                                 
Ign http://us.archive.ubuntu.com natty-updates Release.gpg                     
Ign http://cran.rstudio.com natty/ Release                                     
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://us.archive.ubuntu.com natty Release                                 
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://us.archive.ubuntu.com natty-updates Release                         
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Err http://cran.rstudio.com natty/ Packages                                    
  404  Not Found [IP: 204.246.165.171 80]
Ign http://cran.rstudio.com natty/ Translation-en_US                           
Ign http://cran.rstudio.com natty/ Translation-en                              
Ign http://security.ubuntu.com natty-security InRelease                        
Err http://us.archive.ubuntu.com natty/main Sources                            
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty/restricted Sources                      
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty/universe Sources               
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty/multiverse Sources             
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty/main amd64 Packages            
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty/restricted amd64 Packages      
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty/universe amd64 Packages        
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty/multiverse amd64 Packages               
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty-updates/main Sources                    
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty-updates/restricted Sources              
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty-updates/universe Sources                
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty-updates/multiverse Sources              
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty-updates/main amd64 Packages             
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages       
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty-updates/universe amd64 Packages         
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages       
  404  Not Found [IP: 91.189.91.14 80]
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en      
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US     
Ign http://us.archive.ubuntu.com natty/universe Translation-en        
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://security.ubuntu.com natty-security Release.gpg                      
Ign http://security.ubuntu.com natty-security Release                          
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Err http://security.ubuntu.com natty-security/main Sources                     
  404  Not Found [IP: 91.189.92.190 80]
Err http://security.ubuntu.com natty-security/restricted Sources               
  404  Not Found [IP: 91.189.92.190 80]
Err http://security.ubuntu.com natty-security/universe Sources                 
  404  Not Found [IP: 91.189.92.190 80]
Err http://security.ubuntu.com natty-security/multiverse Sources               
  404  Not Found [IP: 91.189.92.190 80]
Err http://security.ubuntu.com natty-security/main amd64 Packages              
  404  Not Found [IP: 91.189.92.190 80]
Err http://security.ubuntu.com natty-security/restricted amd64 Packages        
  404  Not Found [IP: 91.189.92.190 80]
Err http://security.ubuntu.com natty-security/universe amd64 Packages          
  404  Not Found [IP: 91.189.92.190 80]
Err http://security.ubuntu.com natty-security/multiverse amd64 Packages        
  404  Not Found [IP: 91.189.92.190 80]
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Get:20 ftp://ftp.iitb.ac.in natty/main amd64 Packages [1,550 kB]               
Get:21 ftp://ftp.iitb.ac.in natty/main TranslationIndex                        
Ign ftp://ftp.iitb.ac.in natty/main TranslationIndex                           
Get:22 ftp://ftp.iitb.ac.in natty/main Translation-en_US                       
Get:23 ftp://ftp.iitb.ac.in natty/main Translation-en                          
Get:24 ftp://ftp.iitb.ac.in natty/main Translation-en_US                       
Get:25 ftp://ftp.iitb.ac.in natty/main Translation-en                          
Get:26 ftp://ftp.iitb.ac.in natty/main Translation-en_US                       
Get:27 ftp://ftp.iitb.ac.in natty/main Translation-en                          
Get:28 ftp://ftp.iitb.ac.in natty/main Translation-en_US                       
Get:29 ftp://ftp.iitb.ac.in natty/main Translation-en                          
Get:30 ftp://ftp.iitb.ac.in natty/main Translation-en_US
Ign ftp://ftp.iitb.ac.in natty/main Translation-en_US
Get:31 ftp://ftp.iitb.ac.in natty/main Translation-en
Ign ftp://ftp.iitb.ac.in natty/main Translation-en
Fetched 2,535 kB in 3min 36s (11.7 kB/s)
W: Failed to fetch http://cran.rstudio.com/bin/linux/ubuntu/natty/Packages  404  Not Found [IP: 204.246.165.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.190 80]

E: Some index files failed to download. They have been ignored, or old ones used instead. 
```

FYI : vignesh@ubuntu:~$ cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse



deb http://cran.rstudio.com/bin/linux/ubuntu natty/
deb ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/ natty main
deb-src ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/ natty main





deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main

```

Please let me know, how can I solve this.

---

### Post by slickymaster on 2013-06-06
Natty Narwhal has reached it's EOL in October 28, 2012. I advise you to upgrade your system.

---

### Post by dnr1128 on 2013-06-14
I'm having a similar problem, although I'm running 13.04.  Attached is a screenshot.  Also, in the screen area by the clock I'm getting an error notification that some repositories are unavailable.  Is there a way I can delete these repositories so the error stops coming up?

[ATTACH=CONFIG]243814[/ATTACH]

---

### Post by QIII on 2013-06-14
Hello!

Please attach images using the attachment functionality (the paperclip icon above).

Large images are difficult for those with low-bandwidth connections and may be costly for those whose service limits data transfer.

Thanks!

---

### Post by Frogs Hair on 2013-06-14
If you have performed multiple upgrades you can remove the old sources. The following command will open the list in gedit and you can save the modified list.
```

gksudo gedit /etc/apt/sources.list
```

---

### Post by Bashing-om on 2013-06-14
[COLOR=#000000]dnr1128; Hi !

Please post the out put - between code (#) tags - of terminal codes:
```
cat /etc/apt/sources.list 
ls -la /etc/apt/sources.list.d/
```
[/COLOR][INDENT=2][COLOR=#000000]
we will see what is to be seen

[/COLOR][/INDENT]

---

### Post by dnr1128 on 2013-06-14
Sorry about the images!  I'll remember that in the future.  :)

Bashing, here is the output from those commands;  working with commands is a skill in development for me, so forgive me if I didn't do it quite right.  

david@david-IdeaPad-Z565:~$ cat /etc/apt/sources.list 
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
david@david-IdeaPad-Z565:~$ ls -la /etc/apt/sources.list.d/
total 56
drwxr-xr-x 2 root root 4096 Apr 28 08:33 .
drwxr-xr-x 6 root root 4096 Apr 27 23:40 ..
-rw-r--r-- 1 root root   84 Apr 27 22:23 dropbox.list
-rw-r--r-- 1 root root   84 Apr 27 22:23 dropbox.list.distUpgrade
-rw-r--r-- 1 root root   84 Feb  1 22:34 dropbox.list.save
-rw-r--r-- 1 root root  210 Apr 27 22:23 google-chrome.list
-rw-r--r-- 1 root root  176 Apr 27 22:23 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  176 Feb  1 22:34 google-chrome.list.save
-rw-r--r-- 1 root root  175 Apr 28 08:33 google-earth.list
-rw-r--r-- 1 root root  175 Apr 27 22:23 google-earth.list.distUpgrade
-rw-r--r-- 1 root root  175 Feb  1 22:34 google-earth.list.save
-rw-r--r-- 1 root root   81 Apr 27 22:23 oneiric-partner.list
-rw-r--r-- 1 root root   82 Apr 27 22:23 oneiric-partner.list.distUpgrade
-rw-r--r-- 1 root root   82 Feb  1 22:34 oneiric-partner.list.save

---

### Post by Bashing-om on 2013-06-14
[COLOR=#000000]@ dnr1128; Hey...
Get ahold of something solid... you are fixing to make another step in system administration... and yeah it is going to be a step past the command line. 
Ok look at your file ... you will do an edit ....no step for a stepper !
see :
[/COLOR]> [COLOR=#000000]## Also, please note that software in backports WILL NOT receive any review[/COLOR]
[COLOR=#000000]## or updates from the Ubuntu security team.[/COLOR]
[COLOR=#000000]# deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] natty-backports main restricted universe multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] natty-backports main restricted universe multiverse

and
[/COLOR][COLOR=#000000]## respective vendors as a service to Ubuntu users.[/COLOR]
[COLOR=#000000]# deb [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] natty partner[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] natty partner[/COLOR][COLOR=#000000]
See the two lines above that are not "commented" out --- that means there is a "#" symbol at the start of the line.
What you are going to do is place that symbol on the lines that presently do not have it...
Doing so makes that line to be skipped and the package manager will not try to access a no-longer-in-service repository(natty).

From the command line:
1. Make a back up of any file you are going to edit ...never can tell what might happen ...good insurance !
```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

ok,,, now to edit the file  in terminal:
```
gksudo gedit /etc/apt/sources.list
```
Text editor opens that file, arrow down to the to the line that you will make the first edit in, ok hit the "#" key - >
arrown down to that next line to edit arrow back one space to the start of the line ...do the "#" key again.
done with edits so ...save the file and exit.
Now do terminal codes:
```
sudo apt-get update
sudo apt-get upgrade
```

all good now ?
[/COLOR][INDENT=3][COLOR=#000000]
piece of cake
 [/COLOR][/INDENT]

---

### Post by dnr1128 on 2013-06-15
Worked good.  

Why are those repos still listed since this isn't that version?

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]dnr1128; Outstanding that you gotter fixed.

As to why those old repo's were still there...I do not know ... perhaps just because they were backports, they got carried over from a version upgrade ?? Maybe the package manager just did not trust it's own good sense !
[/COLOR][INDENT=2][COLOR=#000000]
good questions deserve good answers - I just sometimes come up real short

[/COLOR][/INDENT]

---

### Post by panchalsag on 2014-03-20
Repositories are not removed they are moved.
You can change them to get updates.

run following commands

**sudo sed -i -e 's/archive.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list**

**sudo apt-get update && sudo apt-get dist-upgrade**

only run if you are running EOL version and you can not get updates.

---

### Post by deadflowr on 2014-03-20
> **panchalsag said:**
> Repositories are not removed they are moved.
You can change them to get updates.

run following commands

**sudo sed -i -e 's/archive.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list**

**sudo apt-get update && sudo apt-get dist-upgrade**

only run if you are running EOL version and you can not get updates.


The problem with this is it is dependent on the source.list entries being archive.ubuntu.
Which most likely won't be.
Instead most users have us, or gb,archive(other another country abbreviation) 
When running the sed command like it is listed, the new source.list will be
us.old-releases.ubuntu.com
which doesn't exist.
So if using this method, run a quick 
```
cat /etc/apt/souces.list
```
, to see what thew full name is.
And adjust the sed line to reflect that.

---

