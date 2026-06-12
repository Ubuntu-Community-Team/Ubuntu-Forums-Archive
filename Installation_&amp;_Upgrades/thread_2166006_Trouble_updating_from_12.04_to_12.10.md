---
title: "Trouble updating from 12.04 to 12.10"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by cluelesswonder on 2013-08-07
I've been trying to update to Ubuntu 12.10 to 12.04 but keep getting this error message:

W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

In terminal it says:
authenticate 'quantal.tar.gz' against 'quantal.tar.gz.gpg' 
extracting 'quantal.tar.gz'
WARNING: Failed to read mirror file

. . .help? :shock:

---

### Post by bapoumba on 2013-08-07
There is a mistake in the url, please post your sources.list file : **cat /etc/apt/sources.list**

---

### Post by codemaniac on 2013-08-07
If you have your sources.lst messed up, you can try recreate them from the below url.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by cluelesswonder on 2013-08-07
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal universe
deb http://ca.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main


```

---

### Post by bapoumba on 2013-08-07
After seeing your sources.list is fine (thanks codemaniac for the link :)), I checked your error more precisely and found this bug : [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1031882](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1031882)
Several users fixed it by running **sudo upgrade-manager -d**, see posts #5 & 11. You might want to update again first **sudo apt-get update**.

---

### Post by cluelesswonder on 2013-08-07
Thanks, I will try that.

Also, after looking a bit online and reading through the sources.list, I saw that updating to 12.10 from Oneiric Oncelot is not possible. . .but that might not be true anymore. . .? Or because I've updated to 12.04, it is possible? Sorry I'm pretty new at these things.
I'll see how your suggestions go.
Thanks again!

---

### Post by cluelesswonder on 2013-08-07
Ok It seems to be working. Starting the upgrade as soon as I solve this!

Thanks very much!

---

### Post by bapoumba on 2013-08-07
Cool, I was answering your previous reply when I saw the second one coming in.

As far as upgrading from 11.10 to 12.10, see here for ex : [http://ubuntuforums.org/showthread.php?t=2074905](http://ubuntuforums.org/showthread.php?t=2074905)

---

### Post by cluelesswonder on 2013-08-13
Hello, I'm back.
I have still been unable to upgrade. I have tried twice but due to an infuriatingly slow internet connection was unable to complete the upgrade before needing to shut down and the system restored to its previous state.
Now I can't seem to get past the "setting new software channels" section and keep getting error messages. Can anyone help?

```
B]
Get:60 http://ca.archive.ubuntu.com quantal-backports/multiverse TranslationIndex [72 B]
Get:61 http://ca.archive.ubuntu.com quantal-backports/restricted TranslationIndex [70 B]
Get:62 http://ca.archive.ubuntu.com quantal-backports/universe TranslationIndex [73 B]
Err http://ca.archive.ubuntu.com quantal/main Sources                          
                                                                               
Err http://ca.archive.ubuntu.com quantal/universe Sources                      
                                                                               
Err http://ca.archive.ubuntu.com quantal/main i386 Packages                    
                                                                               
Err http://ca.archive.ubuntu.com quantal/universe i386 Packages                
                                                                               
Get:63 http://ca.archive.ubuntu.com quantal/main Translation-en_CA [10.4 kB]   
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Get:64 http://ca.archive.ubuntu.com quantal/multiverse Translation-en [100 kB] 
Get:65 http://ca.archive.ubuntu.com quantal/restricted Translation-en [2,575 B]
Get:66 http://ca.archive.ubuntu.com quantal/universe Translation-en_CA [663 B] 
Err http://ca.archive.ubuntu.com quantal/universe Translation-en               
                                                                               
Err http://ca.archive.ubuntu.com quantal-updates/main i386 Packages            
                                                                               
Get:67 http://ca.archive.ubuntu.com quantal-updates/main Translation-en [135 kB]
Get:68 http://ca.archive.ubuntu.com quantal-updates/multiverse Translation-en [6,183 B]
Get:69 http://ca.archive.ubuntu.com quantal-updates/restricted Translation-en [1,477 B]
Get:70 http://ca.archive.ubuntu.com quantal-updates/universe Translation-en [105 kB]
Get:71 http://ca.archive.ubuntu.com quantal-backports/main Translation-en [14 B]
Get:72 http://ca.archive.ubuntu.com quantal-backports/multiverse Translation-en [2,090 B]
Get:73 http://ca.archive.ubuntu.com quantal-backports/restricted Translation-en [14 B]
Get:74 http://ca.archive.ubuntu.com quantal-backports/universe Translation-en [19.0 kB]
Err http://ca.archive.ubuntu.com quantal/main Sources                          
  404  Not Found [IP: 91.189.91.15 80]                                         
Err http://ca.archive.ubuntu.com quantal/universe Sources                      
  404  Not Found [IP: 91.189.91.15 80]                                         
Err http://ca.archive.ubuntu.com quantal/main i386 Packages                    
  404  Not Found [IP: 91.189.91.15 80]                                         
Err http://ca.archive.ubuntu.com quantal/universe i386 Packages                
  404  Not Found [IP: 91.189.91.15 80]                                         
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Err http://ca.archive.ubuntu.com quantal/universe Translation-en               
                                                                               
Err http://ca.archive.ubuntu.com quantal-updates/main i386 Packages            
  404  Not Found [IP: 91.189.91.15 80]                                         
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Err http://ca.archive.ubuntu.com quantal/universe Translation-en               
                                                                               
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Err http://ca.archive.ubuntu.com quantal/universe Translation-en               
                                                                               
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
  Connection failed [IP: 91.189.92.201 80]                                     
Get:75 http://ca.archive.ubuntu.com quantal/universe Translation-en [16.5 MB]  
Fetched 18.3 MB in 6s (24.1 kB/s)                                              
Hit http://extras.ubuntu.com quantal Release.gpg                               
Hit http://archive.canonical.com quantal Release.gpg                           
Hit http://security.ubuntu.com quantal-security Release.gpg                    
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://archive.canonical.com quantal Release                               
Hidate my computert http://security.ubuntu.com quantal-security Release                        
Hit http://ca.archive.ubuntu.com quantal Release.gpg                           
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://security.ubuntu.com quantal-security/main Sources                   
Get:1 http://ca.archive.ubuntu.com quantal-updates Release.gpg [933 B]         
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Ign http://archive.canonical.com quantal/partner TranslationIndex              
Hit http://security.ubuntu.com quantal-security/restricted Sources             
Err http://archive.canonical.com quantal/partner Translation-en_CA             
                                                                               
Hit http://security.ubuntu.com quantal-security/universe Sources               
Hit http://ca.archive.ubuntu.com quantal-backports Release.gpg                 
Err http://archive.canonical.com quantal/partner Translation-en                
                                                                               
Hit http://security.ubuntu.com quantal-security/multiverse Sources             
Err http://archive.canonical.com quantal/partner Translation-en_CA             
                                                                               
Hit http://security.ubuntu.com quantal-security/main i386 Packages             
Hit http://ca.archive.ubuntu.com quantal Release                               
Ign http://extras.ubuntu.com quantal/main TranslationIndex                     
Err http://archive.canonical.com quantal/partner Translation-en                
                                                                               
Hit http://security.ubuntu.com quantal-security/restricted i386 Packages       
Err http://extras.ubuntu.com quantal/main Translation-en_CA                    
                                                                               
Err http://archive.canonical.com quantal/partner Translation-en_CA             
                                                                               
Hit http://security.ubuntu.com quantal-security/universe i386 Packages         
Err http://extras.ubuntu.com quantal/main Translation-en                       
                                                                               
Err http://archive.canonical.com quantal/partner Translation-en                
                                                                               
Hit http://security.ubuntu.com quantal-security/multiverse i386 Packages       
Err http://extras.ubuntu.com quantal/main Translation-en_CA                    
                                                                               
Hit http://security.ubuntu.com quantal-security/main TranslationIndex          
Err http://archive.canonical.com quantal/partner Translation-en_CA             
                                                                               
Err http://extras.ubuntu.com quantal/main Translation-en                       
                                                                               
Hit http://security.ubuntu.com quantal-security/multiverse TranslationIndex    
Err http://archive.canonical.com quantal/partner Translation-en                
                                                                               
Err http://extras.ubuntu.com quantal/main Translation-en_CA                    
                                                                               
Hit http://security.ubuntu.com quantal-security/restricted TranslationIndex    
Ign http://archive.canonical.com quantal/partner Translation-en_CA             
Err http://extras.ubuntu.com quantal/main Translation-en                       
                                                                               
Hit http://security.ubuntu.com quantal-security/universe TranslationIndex      
Ign http://archive.canonical.com quantal/partner Translation-en                
Err http://extras.ubuntu.com quantal/main Translation-en_CA                    
                                                                               
Hit http://security.ubuntu.com quantal-security/main Translation-en            
Err http://extras.ubuntu.com quantal/main Translation-en                       
                                                                               
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Ign http://extras.ubuntu.com quantal/main Translation-en_CA                    
Hit http://security.ubuntu.com quantal-security/restricted Translation-en      
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://security.ubuntu.com quantal-security/universe Translation-en        
Get:2 http://ca.archive.ubuntu.com quantal-updates Release [49.6 kB]           
Hit http://ca.archive.ubuntu.com quantal-backports Release                     
Err http://ca.archive.ubuntu.com quantal/main Sources                          
                                                                               
Hit http://ca.archive.ubuntu.com quantal/restricted Sources                    
Err http://ca.archive.ubuntu.com quantal/universe Sources                      
                                                                               
Hit http://ca.archive.ubuntu.com quantal/multiverse Sources                    
Err http://ca.archive.ubuntu.com quantal/main i386 Packages                    
                                                                               
Hit http://ca.archive.ubuntu.com quantal/restricted i386 Packages              
Err http://ca.archive.ubuntu.com quantal/universe i386 Packages                
                                                                               
Hit http://ca.archive.ubuntu.com quantal/multiverse i386 Packages              
Hit http://ca.archive.ubuntu.com quantal/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com quantal/multiverse TranslationIndex           
Hit http://ca.archive.ubuntu.com quantal/restricted TranslationIndex           
Hit http://ca.archive.ubuntu.com quantal/universe TranslationIndex             
Get:3 http://ca.archive.ubuntu.com quantal-updates/main Sources [108 kB]       
Get:4 http://ca.archive.ubuntu.com quantal-updates/restricted Sources [2,564 B]
Get:5 http://ca.archive.ubuntu.com quantal-updates/universe Sources [90.8 kB]  
Get:6 http://ca.archive.ubuntu.com quantal-updates/multiverse Sources [3,985 B]
Get:7 http://ca.archive.ubuntu.com quantal-updates/main i386 Packages [276 kB] 
Get:8 http://ca.archive.ubuntu.com quantal-updates/restricted i386 Packages [4,841 B]
Get:9 http://ca.archive.ubuntu.com quantal-updates/universe i386 Packages [201 kB]
Get:10 http://ca.archive.ubuntu.com quantal-updates/multiverse i386 Packages [11.0 kB]
Hit http://ca.archive.ubuntu.com quantal-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com quantal-updates/restricted TranslationIndex   
Hit http://ca.archive.ubuntu.com quantal-updates/universe TranslationIndex     
Hit http://ca.archive.ubuntu.com quantal-backports/main Sources                
Hit http://ca.archive.ubuntu.com quantal-backports/restricted Sources          
Hit http://ca.archive.ubuntu.com quantal-backports/universe Sources            
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse Sources          
Hit http://ca.archive.ubuntu.com quantal-backports/main i386 Packages          
Hit http://ca.archive.ubuntu.com quantal-backports/restricted i386 Packages    
Hit http://ca.archive.ubuntu.com quantal-backports/universe i386 Packages      
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse i386 Packages    
Hit http://ca.archive.ubuntu.com quantal-backports/main TranslationIndex       
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse TranslationIndex 
Hit http://ca.archive.ubuntu.com quantal-backports/restricted TranslationIndex 
Hit http://ca.archive.ubuntu.com quantal-backports/universe TranslationIndex   
Err http://ca.archive.ubuntu.com quantal/main Sources                          
                                                                               
Err http://ca.archive.ubuntu.com quantal/universe Sources                      
                                                                               
Err http://ca.archive.ubuntu.com quantal/main i386 Packages                    
                                                                               
Err http://ca.archive.ubuntu.com quantal/universe i386 Packages                
                                                                               
Hit http://ca.archive.ubuntu.com quantal/main Translation-en_CA                
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Hit http://ca.archive.ubuntu.com quantal/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com quantal/restricted Translation-en             
Hit http://ca.archive.ubuntu.com quantal/universe Translation-en_CA            
Hit http://ca.archive.ubuntu.com quantal/universe Translation-en               
Hit http://ca.archive.ubuntu.com quantal-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com quantal-updates/restricted Translation-en     
Hit http://ca.archive.ubuntu.com quantal-updates/universe Translation-en       
Hit http://ca.archive.ubuntu.com quantal-backports/main Translation-en         
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse Translation-en   
Hit http://ca.archive.ubuntu.com quantal-backports/restricted Translation-en   
Hit http://ca.archive.ubuntu.com quantal-backports/universe Translation-en     
Err http://ca.archive.ubuntu.com quantal/main Sources                          
  404  Not Found [IP: 91.189.92.176 80]                                        
Err http://ca.archive.ubuntu.com quantal/universe Sources                      
  404  Not Found [IP: 91.189.92.176 80]                                        
Err http://ca.archive.ubuntu.com quantal/main i386 Packages                    
  404  Not Found [IP: 91.189.92.176 80]                                        
Err http://ca.archive.ubuntu.com quantal/universe i386 Packages                
  404  Not Found [IP: 91.189.92.176 80]                                        
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
  Connection failed [IP: 91.189.92.201 80]                                     
Fetched 749 kB in 6s (0 B/s)                                                   
Hit http://security.ubuntu.com quantal-security Release.gpg                    
Hit http://extras.ubuntu.com quantal Release.gpg                               
Hit http://archive.canonical.com quantal Release.gpg                           
Hit http://ca.archive.ubuntu.com quantal Release.gpg                           
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://security.ubuntu.com quantal-security Release                        
Hit http://archive.canonical.com quantal Release                               
Get:1 http://ca.archive.ubuntu.com quantal-updates Release.gpg [933 B]         
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://security.ubuntu.com quantal-security/main Sources                   
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Hit http://security.ubuntu.com quantal-security/restricted Sources             
Ign http://archive.canonical.com quantal/partner TranslationIndex              
Hit http://ca.archive.ubuntu.com quantal-backports Release.gpg                 
Ign http://extras.ubuntu.com quantal/main TranslationIndex                     
Hit http://security.ubuntu.com quantal-security/universe Sources               
Err http://archive.canonical.com quantal/partner Translation-en_CA             
                                                                               
Err http://extras.ubuntu.com quantal/main Translation-en_CA                    
                                                                               
Hit http://security.ubuntu.com quantal-security/multiverse Sources             
Err http://archive.canonical.com quantal/partner Translation-en                
                                                                               
Hit http://ca.archive.ubuntu.com quantal Release                               
Err http://extras.ubuntu.com quantal/main Translation-en                       
                                                                               
Hit http://security.ubuntu.com quantal-security/main i386 Packages             
Err http://archive.canonical.com quantal/partner Translation-en_CA             
                                                                               
Err http://extras.ubuntu.com quantal/main Translation-en_CA                    
                                                                               
Hit http://security.ubuntu.com quantal-security/restricted i386 Packages       
Err http://archive.canonical.com quantal/partner Translation-en                
                                                                               
Err http://extras.ubuntu.com quantal/main Translation-en                       
                                                                               
Hit http://security.ubuntu.com quantal-security/universe i386 Packages         
Err http://archive.canonical.com quantal/partner Translation-en_CA             
                                                                               
Err http://extras.ubuntu.com quantal/main Translation-en_CA                    
                                                                               
Hit http://security.ubuntu.com quantal-security/multiverse i386 Packages       
Err http://archive.canonical.com quantal/partner Translation-en                
                                                                               
Hit http://security.ubuntu.com quantal-security/main TranslationIndex          
Err http://extras.ubuntu.com quantal/main Translation-en                       
                                                                               
Err http://archive.canonical.com quantal/partner Translation-en_CA             
                                                                               
Hit http://security.ubuntu.com quantal-security/multiverse TranslationIndex    
Err http://extras.ubuntu.com quantal/main Translation-en_CA                    
                                                                               
Err http://archive.canonical.com quantal/partner Translation-en                
                                                                               
Hit http://security.ubuntu.com quantal-security/restricted TranslationIndex    
Err http://extras.ubuntu.com quantal/main Translation-en                       
                                                                               
Ign http://archive.canonical.com quantal/partner Translation-en_CA             
Hit http://security.ubuntu.com quantal-security/universe TranslationIndex      
Ign http://extras.ubuntu.com quantal/main Translation-en_CA                    
Ign http://archive.canonical.com quantal/partner Translation-en                
Hit http://security.ubuntu.com quantal-security/main Translation-en            
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Hit http://security.ubuntu.com quantal-security/restricted Translation-en      
Hit http://security.ubuntu.com quantal-security/universe Translation-en        
Get:2 http://ca.archive.ubuntu.com quantal-updates Release [49.6 kB]           
Hit http://ca.archive.ubuntu.com quantal-backports Release                     
Err http://ca.archive.ubuntu.com quantal/main Sources                          
                                                                               
Hit http://ca.archive.ubuntu.com quantal/restricted Sources                    
Err http://ca.archive.ubuntu.com quantal/universe Sources                      
                                                                               
Hit http://ca.archive.ubuntu.com quantal/multiverse Sources                    
Err http://ca.archive.ubuntu.com quantal/main i386 Packages                    
                                                                               
Hit http://ca.archive.ubuntu.com quantal/restricted i386 Packages              
Err http://ca.archive.ubuntu.com quantal/universe i386 Packages                
                                                                               
Hit http://ca.archive.ubuntu.com quantal/multiverse i386 Packages              
Hit http://ca.archive.ubuntu.com quantal/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com quantal/multiverse TranslationIndex           
Hit http://ca.archive.ubuntu.com quantal/restricted TranslationIndex           
Hit http://ca.archive.ubuntu.com quantal/universe TranslationIndex             
Get:3 http://ca.archive.ubuntu.com quantal-updates/main Sources [108 kB]       
Get:4 http://ca.archive.ubuntu.com quantal-updates/restricted Sources [2,564 B]
Get:5 http://ca.archive.ubuntu.com quantal-updates/universe Sources [90.8 kB]  
Get:6 http://ca.archive.ubuntu.com quantal-updates/multiverse Sources [3,985 B]
Get:7 http://ca.archive.ubuntu.com quantal-updates/main i386 Packages [276 kB] 
Get:8 http://ca.archive.ubuntu.com quantal-updates/restricted i386 Packages [4,841 B]
Get:9 http://ca.archive.ubuntu.com quantal-updates/universe i386 Packages [201 kB]
Get:10 http://ca.archive.ubuntu.com quantal-updates/multiverse i386 Packages [11.0 kB]
Hit http://ca.archive.ubuntu.com quantal-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com quantal-updates/restricted TranslationIndex   
Hit http://ca.archive.ubuntu.com quantal-updates/universe TranslationIndex     
Hit http://ca.archive.ubuntu.com quantal-backports/main Sources                
Hit http://ca.archive.ubuntu.com quantal-backports/restricted Sources          
Hit http://ca.archive.ubuntu.com quantal-backports/universe Sources            
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse Sources          
Hit http://ca.archive.ubuntu.com quantal-backports/main i386 Packages          
Hit http://ca.archive.ubuntu.com quantal-backports/restricted i386 Packages    
Hit http://ca.archive.ubuntu.com quantal-backports/universe i386 Packages      
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse i386 Packages    
Hit http://ca.archive.ubuntu.com quantal-backports/main TranslationIndex       
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse TranslationIndex 
Hit http://ca.archive.ubuntu.com quantal-backports/restricted TranslationIndex 
Hit http://ca.archive.ubuntu.com quantal-backports/universe TranslationIndex   
Err http://ca.archive.ubuntu.com quantal/main Sources                          
                                                                               
Err http://ca.archive.ubuntu.com quantal/universe Sources                      
                                                                               
Err http://ca.archive.ubuntu.com quantal/main i386 Packages                    
                                                                               
Err http://ca.archive.ubuntu.com quantal/universe i386 Packages                
                                                                               
Hit http://ca.archive.ubuntu.com quantal/main Translation-en_CA                
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Hit http://ca.archive.ubuntu.com quantal/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com quantal/restricted Translation-en             
Hit http://ca.archive.ubuntu.com quantal/universe Translation-en_CA            
Hit http://ca.archive.ubuntu.com quantal/universe Translation-en               
Hit http://ca.archive.ubuntu.com quantal-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com quantal-updates/restricted Translation-en     
Hit http://ca.archive.ubuntu.com quantal-updates/universe Translation-en       
Hit http://ca.archive.ubuntu.com quantal-backports/main Translation-en         
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse Translation-en   
Hit http://ca.archive.ubuntu.com quantal-backports/restricted Translation-en   
Hit http://ca.archive.ubuntu.com quantal-backports/universe Translation-en     
Err http://ca.archive.ubuntu.com quantal/main Sources                          
  404  Not Found [IP: 91.189.91.15 80]                                         
Err http://ca.archive.ubuntu.com quantal/universe Sources                      
  404  Not Found [IP: 91.189.91.15 80]                                         
Err http://ca.archive.ubuntu.com quantal/main i386 Packages                    
  404  Not Found [IP: 91.189.91.15 80]                                         
Err http://ca.archive.ubuntu.com quantal/universe i386 Packages                
  404  Not Found [IP: 91.189.91.15 80]                                         
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
                                                                               
Err http://ca.archive.ubuntu.com quantal/main Translation-en                   
  Connection failed [IP: 91.189.92.177 80]                                     
Fetched 749 kB in 6s (0 B/s)                                                   

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
http://ca.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources 
404 Not Found [IP: 91.189.91.15 80] 
, W:Failed to fetch 
http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources 
404 Not Found [IP: 91.189.91.15 80] 
, W:Failed to fetch 
http://ca.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages 
404 Not Found [IP: 91.189.91.15 80] 
, W:Failed to fetch 
http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages 
404 Not Found [IP: 91.189.91.15 80] 
, W:Failed to fetch 
http://ca.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en 
Connection failed [IP: 91.189.92.177 80] 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


```

---

### Post by cluelesswonder on 2013-08-13
In short, I keep getting this error message:

W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

