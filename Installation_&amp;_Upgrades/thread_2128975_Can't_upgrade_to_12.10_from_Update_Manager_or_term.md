---
title: "Can't upgrade to 12.10 from Update Manager or terminal (cur 12.04)"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by _greg on 2013-03-24
Hi, I recently installed Ubuntu from an old LiveCD I had and successfully upgraded to 12.04 LTS via Update Manager.

I can't, however, seem to update to anything beyond that. I open Update Manager and see that there 12.10 is available, click "Upgrade," enter my password and click OK. Update Manager then closes and nothing happens.

I've also gone into Terminal and entered 

```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

and get these results:

```
greg@mylappy:~$ sudo apt-get update[sudo] password for greg: 
Hit http://repo.steampowered.com precise Release.gpg
Hit http://repo.steampowered.com precise Release                               
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Ign http://repo.steampowered.com precise/steam TranslationIndex                
Hit http://security.ubuntu.com precise-security Release                        
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://us.archive.ubuntu.com precise-backports Release                     
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://security.ubuntu.com precise-security/main i386 Packages   
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources            
Hit http://us.archive.ubuntu.com precise/multiverse Sources          
Hit http://us.archive.ubuntu.com precise/main i386 Packages          
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Sources
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://extras.ubuntu.com precise Release   
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://repo.steampowered.com precise/steam Translation-en        
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://extras.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
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
Hit https://private-ppa.launchpad.net precise Release.gpg
Hit https://private-ppa.launchpad.net precise Release
Hit https://private-ppa.launchpad.net precise/main i386 Packages
Ign https://private-ppa.launchpad.net precise/main TranslationIndex
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Fetched 72 B in 9s (7 B/s)                                                     
Reading package lists... Done
```

```
greg@mylappy:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Any ideas?

---

### Post by schragge on 2013-03-24
*apt-get dist-upgrade* doesn't upgrade automatically to newer release. Try
```
sudo do-release-upgrade
```

---

### Post by _greg on 2013-03-24
That worked! Thanks!

---

