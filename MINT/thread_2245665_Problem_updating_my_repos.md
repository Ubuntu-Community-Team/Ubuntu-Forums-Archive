---
title: "Problem updating my repos"
date: 2014-09-25
forum: MINT
---

### Post by andrew-miller57 on 2014-09-25
When trying to update my repos, it gets hung up and gives me this message:

```
Failed to fetch http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release  
Some index files failed to download. They have been ignored, or old ones used instead.
```

How can I remove this from trying to update when i sudo apt-get update?

Thanks

---

### Post by slickymaster on 2014-09-25
Sounds like the openprinting source is having issues. It could be server problem on their side.
I suggest you email them and let them know.

---

### Post by andrew-miller57 on 2014-09-25
How would I just remove this from the update list though?

---

### Post by slickymaster on 2014-09-25
You mean remove openprinting-ppds-extra package from your system? If it's that:```
sudo apt-get remove openprinting-ppds-extra
```

---

### Post by andrew-miller57 on 2014-09-25
thanks but that didn't work.  Still get this when i sudo apt-get update

> Failed to fetch [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/contrib/i18n/Translation-en_US.bz2](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/contrib/i18n/Translation-en_US.bz2)  Failed to fetch [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/contrib/i18n/Translation-en.bz2](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/contrib/i18n/Translation-en.bz2)  
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by slickymaster on 2014-09-25
Can you please post the output you get from```
sudo apt-get update && sudo apt-get upgrade
```and```
cat /etc/apt/sources.list
```[using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect.

---

### Post by andrew-miller57 on 2014-09-25
sudo apt-get update && sudo apt-get upgrade:

```
andrew@andrew-desktop ~ $ sudo apt-get update && sudo apt-get upgrade[sudo] password for andrew: 
Ign http://dl.google.com stable InRelease
Ign http://extra.linuxmint.com qiana InRelease                                 
Hit http://dl.google.com stable Release.gpg                                    
Ign http://packages.linuxmint.com qiana InRelease                              
Hit http://dl.google.com stable Release                                        
Get:1 http://extra.linuxmint.com qiana Release.gpg [198 B]                     
Get:2 http://packages.linuxmint.com qiana Release.gpg [198 B]                  
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://archive.canonical.com trusty InRelease                              
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:3 http://extra.linuxmint.com qiana Release [3,144 B]                       
Get:4 http://packages.linuxmint.com qiana Release [18.6 kB]                    
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Get:5 http://extra.linuxmint.com qiana/main amd64 Packages [7,906 B]           
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:6 http://packages.linuxmint.com qiana/main amd64 Packages [30.4 kB]        
Get:7 http://extra.linuxmint.com qiana/main i386 Packages [7,890 B]            
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://archive.canonical.com trusty Release                                
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty-updates Release.gpg                       
Get:8 http://packages.linuxmint.com qiana/upstream amd64 Packages [23.8 kB]    
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty Release                                   
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Get:9 http://packages.linuxmint.com qiana/import amd64 Packages [32.5 kB]      
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-updates Release                           
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Hit http://ppa.launchpad.net trusty/main Sources                               
Get:10 http://packages.linuxmint.com qiana/backport amd64 Packages [20 B]      
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                   
Get:11 http://packages.linuxmint.com qiana/main i386 Packages [29.7 kB]        
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:12 http://packages.linuxmint.com qiana/upstream i386 Packages [23.8 kB]    
Ign http://extra.linuxmint.com qiana/main Translation-en_US                    
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Ign http://extra.linuxmint.com qiana/main Translation-en                       
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Get:13 http://packages.linuxmint.com qiana/import i386 Packages [32.5 kB]      
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:14 http://packages.linuxmint.com qiana/backport i386 Packages [20 B]       
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages               
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages         
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages           
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages         
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages                
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages          
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages            
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages          
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Ign http://packages.linuxmint.com qiana/backport Translation-en_US             
Ign http://packages.linuxmint.com qiana/backport Translation-en       
Ign http://packages.linuxmint.com qiana/import Translation-en_US
Ign http://packages.linuxmint.com qiana/import Translation-en         
Ign http://packages.linuxmint.com qiana/main Translation-en_US        
Ign http://packages.linuxmint.com qiana/main Translation-en
Ign http://packages.linuxmint.com qiana/upstream Translation-en_US
Ign http://packages.linuxmint.com qiana/upstream Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Ign http://www.openprinting.org lsb3.2 InRelease                               
Hit http://www.openprinting.org lsb3.2 Release.gpg        
Hit http://www.openprinting.org lsb3.2 Release            
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
100% [Waiting for headers]                                           477 B/s 0s





```

```
andrew@andrew-desktop ~ $ cat /etc/apt/sources.list# deb cdrom:[Linux Mint 17 _Qiana_ - Release amd64 20140512]/ trusty contrib main non-free
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib



```

---

### Post by slickymaster on 2014-09-25
In terminal```
gksu gedit /etc/apt/sources.list
```this command will open your sources list in edit/save mode (if you don't have gedit, replace it with whatever text editor you use).
Comment out (add a # at the start of) the line:```
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib
``` Save the file and close and once again run```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by coffeecat on 2014-09-25
Linux Mint.

*Thread moved to **Other Operating Systems and Projects**.*

---

