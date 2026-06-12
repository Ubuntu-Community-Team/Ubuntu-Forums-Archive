---
title: "Can't boot after upgrade to 14.04 LTS from SSD drive"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by prkos on 2015-05-01
I have 2 disks, SSD that had previous Ubuntu version which I just updated to 14.04 (no problems during upgrade), and an old disk that still has Ubuntu 11.10 installed but has been used as a backup drive that gets automounted after each boot. 

But after the restart necessary to finish the upgrade the SSD seems to be unrecognized. I can get into BIOS and it only shows one boot option:

SATA: ADATA SP900

If the old disk is connected it boots from it, the ancient Ubuntu 11.10. 

If I disconnect the old disk I get:

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

How can I get the 14.04 to work from SSD like the 13.10 did?

---

### Post by oldfred on 2015-05-01
Sounds like BIOS set to boot from old MBR?

Best to see details:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by prkos on 2015-05-02
I seem to be having problems adding the repo in 11.10: 

```
$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
You are about to add the following PPA to your system:
 Boot-Repair
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp8WnE9l/secring.gpg' created
gpg: keyring `/tmp/tmp8WnE9l/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp8WnE9l/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric Release.gpg
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates Release.gpg                   
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports Release.gpg                 
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric Release                               
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates Release                       
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports Release                     
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/main Sources/DiffIndex                
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex          
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/universe Sources/DiffIndex            
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex          
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/main amd64 Packages/DiffIndex         
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/restricted amd64 Packages/DiffIndex   
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/universe amd64 Packages/DiffIndex     
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/multiverse amd64 Packages/DiffIndex   
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex    
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex      
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex    
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/main TranslationIndex                 
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/universe TranslationIndex             
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/main Sources/DiffIndex        
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/restricted Sources/DiffIndex  
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/universe Sources/DiffIndex    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/multiverse Sources/DiffIndex  
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/main amd64 Packages/DiffIndex 
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/universe amd64 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/main i386 Packages/DiffIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/restricted i386 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/universe i386 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/main Sources/DiffIndex      
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/restricted Sources/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/universe Sources/DiffIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources/DiffIndex         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/multiverse Sources/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/main amd64 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/universe amd64 Packages/DiffIndex
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/main i386 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/restricted i386 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/universe i386 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages/DiffIndex
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources/DiffIndex     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages/DiffIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages/DiffIndex             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages/DiffIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
  404  Not Found [IP: 91.189.92.201 80]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages            
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages      
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages        
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages      
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/main Sources           
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/restricted Sources     
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/universe Sources
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/multiverse Sources
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/main amd64 Packages    
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/restricted amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/universe amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/multiverse amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/main i386 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/restricted i386 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/universe i386 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/multiverse i386 Packages
  404  Not Found
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/main Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/main Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/multiverse Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/multiverse Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/restricted Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/restricted Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/universe Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric/universe Translation-en
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/main Sources   
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/restricted Sources
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/universe Sources
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/multiverse Sources
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/main amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/main i386 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/universe i386 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
  404  Not Found
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/main Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/main Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/multiverse Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/restricted Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/universe Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-updates/universe Translation-en
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/main Sources
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/restricted Sources
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/universe Sources
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/multiverse Sources
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/main amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/main i386 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/universe i386 Packages
  404  Not Found
Err [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
  404  Not Found
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/main Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/main Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/multiverse Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/restricted Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/universe Translation-en_US
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) oneiric-backports/universe Translation-en
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric Release.gpg                          
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free amd64 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free amd64 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free amd64 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free amd64 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_US
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
89% [Connecting to packages.medibuntu.org]
```


Does it have to be from a removable media like DVD or USB, or can I use the old installation to get to boot info?

---

### Post by oldfred on 2015-05-02
As I posted above.
Precise, Trusty, Vivid, & Utopic all should work now with current ppa

You cannot run it in obsolete versions.

Just use an up to date, Ubuntu or any other flavor live installer as it shows instructions to add its ppa to in  live installer. It also has its own live repair CD based on the Lubuntu flavor.

---

### Post by grahammechanical on 2015-05-02
If you can get into Ubuntu 11.10 run

```
sudo update-grub
```

Watch the printout. Does it show Ubuntu 14.04? In this way you may get a boot menu that allows you to load Ubuntu 14.04 on the SSD. The BIOS may be registering the SSD as a removable drive. And so another section of the BIOS may need to be accessed. I do not know. I am just giving a wild guess.

Regards.

---

### Post by prkos on 2015-05-02
Thank you! I'll try to set me up with a removable bootable CD or something. In the meantime here is the grub output: 

```

$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-32-generic
Found initrd image: /boot/initrd.img-3.0.0-32-generic
Found linux image: /boot/vmlinuz-3.0.0-31-generic
Found initrd image: /boot/initrd.img-3.0.0-31-generic
Found linux image: /boot/vmlinuz-3.0.0-30-generic
Found initrd image: /boot/initrd.img-3.0.0-30-generic
Found linux image: /boot/vmlinuz-3.0.0-29-generic
Found initrd image: /boot/initrd.img-3.0.0-29-generic
Found linux image: /boot/vmlinuz-3.0.0-28-generic
Found initrd image: /boot/initrd.img-3.0.0-28-generic
Found linux image: /boot/vmlinuz-3.0.0-27-generic
Found initrd image: /boot/initrd.img-3.0.0-27-generic
Found linux image: /boot/vmlinuz-3.0.0-26-generic
Found initrd image: /boot/initrd.img-3.0.0-26-generic
Found linux image: /boot/vmlinuz-3.0.0-25-generic
Found initrd image: /boot/initrd.img-3.0.0-25-generic
Found linux image: /boot/vmlinuz-3.0.0-24-generic
Found initrd image: /boot/initrd.img-3.0.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-23-generic
Found initrd image: /boot/initrd.img-3.0.0-23-generic
Found linux image: /boot/vmlinuz-3.0.0-22-generic
Found initrd image: /boot/initrd.img-3.0.0-22-generic
Found linux image: /boot/vmlinuz-3.0.0-21-generic
Found initrd image: /boot/initrd.img-3.0.0-21-generic
Found linux image: /boot/vmlinuz-3.0.0-20-generic
Found initrd image: /boot/initrd.img-3.0.0-20-generic
Found linux image: /boot/vmlinuz-3.0.0-19-generic
Found initrd image: /boot/initrd.img-3.0.0-19-generic
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb2
done

```

So the upgraded version disk *is* found. Can this help? 
```
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb2
```

I went through all the BIOS menus and there is only one place where I see the disk choice, always the one. It doesn't offer a second option so I could sort priorities.

---

### Post by oldfred on 2015-05-02
That will not be in BIOS, but in grub menu.
And you have so many old kernels that you may not see it in the box that grub menu shows.
If you have a very tiny arrow in lower right corner, it says you need to scroll down to see more entries. And the 14.04 should be at bottom of grub menu.

---

### Post by prkos on 2015-05-02
I don't think Grub even shows up for me. If it did I'd know to start checking the OS list, even if it's too long. After the motherboard screen I very quickly get the purple screen of 11.10. Maybe it's set to not show? 

Here is what I have in /etc/default/grub

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```


BTW does this mean I don't need boot-info and bootable removable media to solve this?

Update: I do see the grub when booting, I guess I was always getting into BIOS and never got to it, it didn't appear when booting from BIOS menu.

---

### Post by oldfred on 2015-05-02
It says you have a 10 sec delay on grub menu before it auto boots the default entry or 0 or first in menu. And with more than one system you always should get grub menu. 

Only if one install of Ubuntu will it not normally show menu and you have to hold shift key from BIOS until menu appears.

---

### Post by prkos on 2015-05-02
I got the Grub! It shows a number of options, I chose the one with higher kernel numbers (why doesn't it show it by name?) and I'm now booted into 14.04! 

Thank you oldfred and grahammechanical! 

If I may ask some more questions that now pop up:

Is there an easier way to set the default in Grub than is shown here: [http://www.humans-enabled.com/2014/08/how-to-set-default-grub-kernel-boot.html](http://www.humans-enabled.com/2014/08/how-to-set-default-grub-kernel-boot.html)

Some gnome shell extensions I had in 13.10 are missing in 14.04. Is that expected and I need to install them anew? I expected all my old settings would be inherited since I did an upgrade and not a clean install.

---

### Post by oldfred on 2015-05-02
You should have installed the new version's grub to MBR originally. And you can easily do that now.
Do all this from your new 14.04 install:

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

But grub also remembers where you originally installed it, so it may get out of sync on a major update. Best to check & perhaps reset install.

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by prkos on 2015-05-02
Awesome! Thank you! It's what I'd love to achieve in the end. 

Here is what I get from the first step: 

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   500118191   250059095+  ee  GPT

```

/dev/sda seems to be old disk with 11.10. 

/dev/sdb is the SSD disk with 14.04, so I use this one right?

---

### Post by prkos on 2015-05-02
BTW am I using the correct choice from Grub? One option ends with 

"(on /dev/sdb2)" 

and the option just below it ends with 

"gnulinux-3.13.0-51-generic-advanced-.........."

Are they the same? I can't get the sound to work, and I see some graphics issues as well (terminal bg isn't transparent although it's set to be, close buttons on windows look a bit weird on hover), maybe I need to do more cleanups?

Gnome shell extensions now all work, I had to update them to newer versions.

---

### Post by oldfred on 2015-05-02
If you have a gpt partitioned drive, you must have a tiny 1 or 2MB unformatted partition with the bios_grub flag. Use gparted to create that partition anywhere on drive.
Grub will not install correctly to gpt unless you have bios_grub for BIOS boot or and efi partition if a new UEFI based system.

You should be able to set in BIOS which drive you boot from.

If gpt partitioned drives use parted not fdisk
sudo parted -l

---

