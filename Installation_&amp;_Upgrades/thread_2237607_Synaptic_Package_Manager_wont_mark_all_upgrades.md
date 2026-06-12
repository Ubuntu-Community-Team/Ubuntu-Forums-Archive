---
title: "Synaptic Package Manager wont mark all upgrades"
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by Domgoa on 2014-08-02
Synaptic Package Manager will not mark all upgrades when i press the Mark All Upgrades button, nothing happens.

I am runing Ubuntu 12.04 LST precise.

---

### Post by oldos2er on 2014-08-03
It will do that if there are no upgrades. Did you run 'Reload' or ```
sudo apt-get update
``` first?

---

### Post by Domgoa on 2014-08-03
Upgrades are the packages with Ubuntu emblem right?

If so, yes there are upgrades to be installed.

I ran the update command

Code: 

sudo apt-get install apt-transport-https 
Sudo apt-get update

Its still not marking all upgrades.

---

### Post by Bucky Ball on 2014-08-03
You could try running:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... and that will upgrade everything and anything (except the OS to a newer release). When you hit 'Mark all Upgrades' to you get a pop-up window asking you to confirm 'Mark additional required packages'? It is common that none of the upgrades getting marked are on the on the particular page you are looking at. This is normal. Have you looked for a specific package after confirmation that the process claims to have marked?

---

### Post by oldos2er on 2014-08-03
> **Domgoa said:**
> Upgrades are the packages with Ubuntu emblem right?


In Synaptic I think upgradeable packages are marked with a little gold star on the green box. I'm not on Ubuntu right now so I can't check.

---

### Post by Domgoa on 2014-08-03
Oh! So upgrades are marked with a gold star such as this image indicates?

[IMG]https://help.ubuntu.com/community/SynapticHowto?action=AttachFile&do=get&target=Synaptic-Package-Manager.png[/IMG]
Is there a way to install multiple packages without having to mark each one individually?

---

### Post by kansasnoob on 2014-08-03
That looks like an old Edgy screenshot ;)

Please post the full output of:

```
sudo apt-get update
```

---

### Post by Domgoa on 2014-08-03
This is the out after enter the command.

Code:
sudo apt-get update

Output code is below.

```
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg                     
Get:1 [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release.gpg [473 B]                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release                         
Hit [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all amd64 Packages/DiffIndex                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources               
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all i386 Packages/DiffIndex                    
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all TranslationIndex                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources                
Hit [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all amd64 Packages                             
Hit [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all i386 Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise Release.gpg                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise Release                             
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib amd64 Packages              
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex            
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all Translation-en_US                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                  
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all Translation-en                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                     
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg            
Hit [http://dl.google.com](http://dl.google.com) stable Release                
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_US
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Get:2 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex [367 B]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en              
Fetched 473 B in 6s (74 B/s)                                                   
Reading package lists... Done
W: GPG error: [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E18CE6625CB26B26
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib i386 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib i386 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib i386 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib i386 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib i386 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib i386 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib i386 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.duinsoft.nl/pkg/](http://www.duinsoft.nl/pkg/) debs/all amd64 Packages (/var/lib/apt/lists/www.duinsoft.nl_pkg_dists_debs_all_binary-amd64_Packages)
W: Duplicate sources.list entry [http://www.duinsoft.nl/pkg/](http://www.duinsoft.nl/pkg/) debs/all i386 Packages (/var/lib/apt/lists/www.duinsoft.nl_pkg_dists_debs_all_binary-i386_Packages)
```

---

### Post by Domgoa on 2014-08-05
I think the problem has been solved, i tried upgrading and it worked it must have been the codes.

Code:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by Bucky Ball on 2014-08-06
All good. ;)

Please mark the thread as solved to help others by following the second link in my signature. Good luck and enjoy!

---

### Post by Domgoa on 2014-08-06
Thank you all for your assinstance.

---

