---
title: "Upgrade has messed-up  ubuntu 12.04 installation need help"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2012-08-16
This morning when I started ubuntu 12.04 then run update manager
it then said that some packages could not be installed, then I run partial upgrade, since  that, 
1.when I start it it does't stop at recovery witch it has always done.
2. My ferefox plugins are removed.
when I try to install firefox plugins:

sudo apt-get install flashplugin-installer
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 flashplugin-installer : Depends: libnspr4-0d but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by dino99 on 2012-08-16
you should use ppa-purge to remove package conflicts.

---

### Post by hoboy on 2012-08-16
> **dino99 said:**
> you should use ppa-purge to remove package conflicts.

How do I detet confilct ?
here is when I run update:
sudo apt-get  update
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                           
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise InRelease       
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates InRelease
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports InRelease
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise-security InRelease
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise Release.gpg     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates Release.gpg                    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports Release.gpg                 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security Release.gpg                  
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed Release.gpg                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                         
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources              
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates Release                        
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports Release                                            
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security Release                                             
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed Release                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main Sources    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted Sources
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe Sources                      
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse Sources                    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main amd64 Packages                   
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted amd64 Packages             
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe amd64 Packages               
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse amd64 Packages             
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main i386 Packages                    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted i386 Packages              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages              
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe i386 Packages                
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse i386 Packages              
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main TranslationIndex                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex           
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse TranslationIndex           
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted TranslationIndex
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe TranslationIndex             
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main Sources                  
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted Sources            
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe Sources              
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse Sources            
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main amd64 Packages           
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted amd64 Packages     
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe amd64 Packages       
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse amd64 Packages
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main i386 Packages            
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted i386 Packages      
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe i386 Packages        
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse i386 Packages      
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main TranslationIndex         
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse TranslationIndex   
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted TranslationIndex   
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe TranslationIndex     
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main Sources                
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted Sources          
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe Sources            
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse Sources          
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main amd64 Packages         
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted amd64 Packages
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe amd64 Packages     
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse amd64 Packages   
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main i386 Packages          
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted i386 Packages    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe i386 Packages      
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse i386 Packages    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main TranslationIndex       
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted TranslationIndex
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe TranslationIndex   
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main Sources                 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted Sources           
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe Sources             
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse Sources           
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main amd64 Packages          
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted amd64 Packages    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe amd64 Packages      
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse amd64 Packages    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main i386 Packages           
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted i386 Packages     
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe i386 Packages       
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse i386 Packages     
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main TranslationIndex        
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse TranslationIndex  
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted TranslationIndex  
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe TranslationIndex    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main Sources                 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main amd64 Packages          
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main i386 Packages           
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main TranslationIndex        
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main Translation-en                   
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse Translation-en             
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted Translation-en             
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe Translation-en               
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main Translation-en           
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse Translation-en     
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted Translation-en     
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe Translation-en       
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main Translation-en         
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse Translation-en   
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted Translation-en   
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe Translation-en     
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main Translation-en          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US   
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse Translation-en    
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted Translation-en
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe Translation-en
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Reading package lists... Done

---

### Post by smartboyhw on 2012-08-16
> **hoboy said:**
> How do I detet confilct ?
here is when I run update:
sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease 
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise InRelease 
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates InRelease
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports InRelease
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise-security InRelease
Ign [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise Release.gpg 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates Release.gpg 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports Release.gpg 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security Release.gpg 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed Release.gpg 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise Release 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates Release 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports Release 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security Release 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed Release 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted Sources
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted i386 Packages 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main TranslationIndex 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted TranslationIndex
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse amd64 Packages
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted amd64 Packages
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted TranslationIndex
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main Sources 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main amd64 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main i386 Packages 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main TranslationIndex 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/main Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/multiverse Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/restricted Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise/universe Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/main Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/multiverse Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/restricted Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-updates/universe Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/main Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/multiverse Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/restricted Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-backports/universe Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/main Translation-en 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/multiverse Translation-en 
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/restricted Translation-en
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-security/universe Translation-en
Hit [http://ftp.klid.dk](http://ftp.klid.dk) precise-proposed/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Reading package lists... Done
 Well, next time, use paste.ubuntu.com However, it should be working by looking at the above logs.

---

### Post by darkod on 2012-08-16
I'm not sure it can help, but you can try fixing broken packages with:
```
sudo apt-get install -f
```

---

