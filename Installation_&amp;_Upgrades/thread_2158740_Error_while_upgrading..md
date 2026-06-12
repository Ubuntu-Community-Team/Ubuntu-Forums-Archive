---
title: "Error while upgrading."
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by antoniovandre on 2013-06-30
I use Ubuntu 13. Since my last upgrade, in 06/28/2013, the "apt-get" and "update-notifier" crashes. So i can not upgrade my system. How can i solve it?

```
# apt-get update
Atingido http://archive.ubuntu.com raring Release.gpg                          
Atingido http://archive.canonical.com raring Release.gpg                       
Atingido http://deb.opera.com stable Release.gpg                               
Atingido http://security.ubuntu.com raring-security Release.gpg                
Atingido http://gb.archive.ubuntu.com raring Release.gpg                       
Atingido http://ppa.launchpad.net raring Release.gpg                           
Atingido http://deb.opera.com stable Release                                   
Atingido http://archive.ubuntu.com raring Release                              
Atingido http://archive.canonical.com raring Release                           
Atingido http://security.ubuntu.com raring-security Release                    
Atingido http://gb.archive.ubuntu.com raring-updates Release.gpg               
Atingido http://ppa.launchpad.net raring Release                               
Atingido http://security.ubuntu.com raring-security/main Sources               
Atingido http://deb.opera.com stable/non-free i386 Packages                    
Atingido http://archive.ubuntu.com raring/main Sources                         
Atingido http://archive.canonical.com raring/partner Sources                   
Atingido http://gb.archive.ubuntu.com raring-backports Release.gpg             
Atingido http://security.ubuntu.com raring-security/restricted Sources         
Atingido http://archive.ubuntu.com raring/universe Sources                     
Atingido http://ppa.launchpad.net raring/main i386 Packages                    
Atingido http://archive.canonical.com raring/partner i386 Packages             
Atingido http://security.ubuntu.com raring-security/universe Sources           
Atingido http://archive.ubuntu.com raring/restricted Sources                   
Atingido http://gb.archive.ubuntu.com raring Release                           
Atingido http://archive.ubuntu.com raring/multiverse Sources                   
Atingido http://security.ubuntu.com raring-security/multiverse Sources         
Atingido http://gb.archive.ubuntu.com raring-updates Release                   
Atingido http://archive.ubuntu.com raring/main i386 Packages                   
Atingido http://security.ubuntu.com raring-security/main i386 Packages         
Atingido http://gb.archive.ubuntu.com raring-backports Release                 
Atingido http://archive.ubuntu.com raring/universe i386 Packages               
Atingido http://security.ubuntu.com raring-security/restricted i386 Packages   
Atingido http://gb.archive.ubuntu.com raring/main Sources                      
Atingido http://archive.ubuntu.com raring/restricted i386 Packages             
Atingido http://security.ubuntu.com raring-security/universe i386 Packages     
Atingido http://gb.archive.ubuntu.com raring/restricted Sources                
Atingido http://archive.ubuntu.com raring/multiverse i386 Packages             
Atingido http://security.ubuntu.com raring-security/multiverse i386 Packages   
Atingido http://gb.archive.ubuntu.com raring/universe Sources                  
Atingido http://archive.ubuntu.com raring/main Translation-pt_BR               
Ign http://deb.opera.com stable/non-free Translation-pt_BR                     
Atingido http://archive.ubuntu.com raring/main Translation-pt                  
Ign http://deb.opera.com stable/non-free Translation-pt                        
Atingido http://gb.archive.ubuntu.com raring/multiverse Sources                
Atingido http://archive.ubuntu.com raring/main Translation-en                  
Ign http://deb.opera.com stable/non-free Translation-en                        
Atingido http://security.ubuntu.com raring-security/main Translation-en        
Atingido http://archive.ubuntu.com raring/multiverse Translation-pt_BR         
Atingido http://gb.archive.ubuntu.com raring/main i386 Packages                
Ign http://ppa.launchpad.net raring/main Translation-pt_BR                     
Ign http://archive.canonical.com raring/partner Translation-pt_BR              
Ign http://ppa.launchpad.net raring/main Translation-pt                        
Atingido http://gb.archive.ubuntu.com raring/restricted i386 Packages          
Ign http://archive.canonical.com raring/partner Translation-pt                 
Atingido http://archive.ubuntu.com raring/multiverse Translation-pt            
Ign http://ppa.launchpad.net raring/main Translation-en                        
Ign http://archive.canonical.com raring/partner Translation-en                 
Atingido http://gb.archive.ubuntu.com raring/universe i386 Packages            
Atingido http://archive.ubuntu.com raring/multiverse Translation-en            
Atingido http://security.ubuntu.com raring-security/multiverse Translation-en
Atingido http://gb.archive.ubuntu.com raring/multiverse i386 Packages          
Atingido http://archive.ubuntu.com raring/restricted Translation-pt_BR         
Atingido http://archive.ubuntu.com raring/restricted Translation-pt            
Atingido http://gb.archive.ubuntu.com raring/main Translation-pt_BR            
Atingido http://gb.archive.ubuntu.com raring/main Translation-pt
Atingido http://archive.ubuntu.com raring/restricted Translation-en            
Atingido http://security.ubuntu.com raring-security/restricted Translation-en  
Atingido http://gb.archive.ubuntu.com raring/main Translation-en
Atingido http://archive.ubuntu.com raring/universe Translation-pt_BR
Atingido http://archive.ubuntu.com raring/universe Translation-pt              
Atingido http://gb.archive.ubuntu.com raring/multiverse Translation-pt_BR      
Atingido http://archive.ubuntu.com raring/universe Translation-en              
Atingido http://security.ubuntu.com raring-security/universe Translation-en    
Atingido http://gb.archive.ubuntu.com raring/multiverse Translation-pt
Atingido http://gb.archive.ubuntu.com raring/multiverse Translation-en
Atingido http://gb.archive.ubuntu.com raring/restricted Translation-pt_BR
Atingido http://gb.archive.ubuntu.com raring/restricted Translation-pt
Atingido http://gb.archive.ubuntu.com raring/restricted Translation-en
Atingido http://gb.archive.ubuntu.com raring/universe Translation-pt_BR
Atingido http://gb.archive.ubuntu.com raring/universe Translation-pt
Atingido http://gb.archive.ubuntu.com raring/universe Translation-en
Atingido http://gb.archive.ubuntu.com raring-updates/main Sources
Atingido http://gb.archive.ubuntu.com raring-updates/restricted Sources
Atingido http://gb.archive.ubuntu.com raring-updates/universe Sources
Atingido http://gb.archive.ubuntu.com raring-updates/multiverse Sources
Atingido http://gb.archive.ubuntu.com raring-updates/main i386 Packages
Atingido http://gb.archive.ubuntu.com raring-updates/restricted i386 Packages
Atingido http://gb.archive.ubuntu.com raring-updates/universe i386 Packages
Atingido http://gb.archive.ubuntu.com raring-updates/multiverse i386 Packages  
Ign http://security.ubuntu.com raring-security/main Translation-pt_BR          
Atingido http://gb.archive.ubuntu.com raring-updates/main Translation-en
Ign http://security.ubuntu.com raring-security/main Translation-pt
Ign http://security.ubuntu.com raring-security/multiverse Translation-pt_BR
Ign http://security.ubuntu.com raring-security/multiverse Translation-pt
Ign http://security.ubuntu.com raring-security/restricted Translation-pt_BR
Ign http://security.ubuntu.com raring-security/restricted Translation-pt
Ign http://security.ubuntu.com raring-security/universe Translation-pt_BR
Ign http://security.ubuntu.com raring-security/universe Translation-pt
Atingido http://gb.archive.ubuntu.com raring-updates/multiverse Translation-en
Atingido http://gb.archive.ubuntu.com raring-updates/restricted Translation-en
Atingido http://gb.archive.ubuntu.com raring-updates/universe Translation-en
Atingido http://gb.archive.ubuntu.com raring-backports/main Sources
Atingido http://gb.archive.ubuntu.com raring-backports/restricted Sources
Atingido http://gb.archive.ubuntu.com raring-backports/universe Sources
Atingido http://gb.archive.ubuntu.com raring-backports/multiverse Sources
Atingido http://gb.archive.ubuntu.com raring-backports/main i386 Packages
Atingido http://gb.archive.ubuntu.com raring-backports/restricted i386 Packages
Atingido http://gb.archive.ubuntu.com raring-backports/universe i386 Packages
Atingido http://gb.archive.ubuntu.com raring-backports/multiverse i386 Packages
Atingido http://gb.archive.ubuntu.com raring-backports/main Translation-en
Atingido http://gb.archive.ubuntu.com raring-backports/multiverse Translation-en
Atingido http://gb.archive.ubuntu.com raring-backports/restricted Translation-en
Atingido http://gb.archive.ubuntu.com raring-backports/universe Translation-en
Ign http://gb.archive.ubuntu.com raring-updates/main Translation-pt_BR
Ign http://gb.archive.ubuntu.com raring-updates/main Translation-pt
Ign http://gb.archive.ubuntu.com raring-updates/multiverse Translation-pt_BR
Ign http://gb.archive.ubuntu.com raring-updates/multiverse Translation-pt
Ign http://gb.archive.ubuntu.com raring-updates/restricted Translation-pt_BR
Ign http://gb.archive.ubuntu.com raring-updates/restricted Translation-pt
Ign http://gb.archive.ubuntu.com raring-updates/universe Translation-pt_BR
Ign http://gb.archive.ubuntu.com raring-updates/universe Translation-pt
Ign http://gb.archive.ubuntu.com raring-backports/main Translation-pt_BR
Ign http://gb.archive.ubuntu.com raring-backports/main Translation-pt
Ign http://gb.archive.ubuntu.com raring-backports/multiverse Translation-pt_BR
Ign http://gb.archive.ubuntu.com raring-backports/multiverse Translation-pt
Ign http://gb.archive.ubuntu.com raring-backports/restricted Translation-pt_BR
Ign http://gb.archive.ubuntu.com raring-backports/restricted Translation-pt
Ign http://gb.archive.ubuntu.com raring-backports/universe Translation-pt_BR
Ign http://gb.archive.ubuntu.com raring-backports/universe Translation-pt
Falha de segmentação (imagem do núcleo gravada)

```

---

### Post by Frogs Hair on 2013-06-30
You can try the following per Ask Ubuntu  .

```
sudo rm /var/cache/apt/*.bin
``` ```
sudo apt-get update
```

---

### Post by antoniovandre on 2013-06-30
> **Frogs Hair said:**
> You can try the following per Ask Ubuntu  .

```
sudo rm /var/cache/apt/*.bin
``` ```
sudo apt-get update
```

The error continues.

Would i wait for a new version of apt-get and manualy install it on my system with deb package?

---

### Post by Frogs Hair on 2013-06-30
I was going to suggest re installing the update-manager package , but the package system may crash in the process. (catch 22) I found a forum post on this error and it r was caused by faulty ram. The command I posted seems to have worked for others . You need a working package system to install any package, but you can try the following.```
 sudo apt-get install --reinstall update-manager
```

---

### Post by antoniovandre on 2013-06-30
> **Frogs Hair said:**
> I was going to suggest re installing the update-manager package , but the package system may crash in the process. (catch 22) I found a forum post on this error and it r was caused by faulty ram. The command I posted seems to have worked for others . You need a working package system to install any package, but you can try the following.```
 sudo apt-get install --reinstall update-manager
```

I had to manually download the deb packages and manually install it with the command:

```
# dpkg - i update-manager-core_0.188_all.deb update-manager_0.188_all.deb python3-update-manager_0.188_all.deb lsb-release_4.1+Debian11ubuntu2_all.deb
```

And the problem is solved. Thanks.

---

