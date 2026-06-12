---
title: "Update errors on Ubuntu 15.10"
date: 2016-07-03
forum: Installation &amp; Upgrades
---

### Post by Everett Arndt on 2016-07-03
Ubuntu 15.10 LTSgetting following errors on update




```
everett@everett-HP-EliteBook-8440p:~$ sudo apt-get update
[sudo] password for everett: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) wily InRelease                                
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security InRelease [65.9 kB]             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) wily/partner Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily InRelease                                
Hit [http://archive.getdeb.net](http://archive.getdeb.net) wily-getdeb InRelease                            
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) wily/partner amd64 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates InRelease [65.9 kB]            
Hit [http://archive.getdeb.net](http://archive.getdeb.net) wily-getdeb/games amd64 Packages                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) wily/partner i386 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main Sources [51.4 kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) wily/partner Translation-en                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) wily-getdeb/games i386 Packages                  
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted Sources [2,854 B]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe Sources [13.9 kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports InRelease                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse Sources [2,785 B]    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main Sources                             
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main amd64 Packages [165 kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Sources                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted amd64 Packages [10.9 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe Sources                         
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe amd64 Packages [55.4 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main amd64 Packages                      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse amd64 Packages [6,257 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted amd64 Packages                
Ign [http://archive.getdeb.net](http://archive.getdeb.net) wily-getdeb/games Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe amd64 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Sources                                 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main i386 Packages [162 kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main i386 Packages                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) wily-getdeb/games Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe i386 Packages                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse i386 Packages                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main Translation-en                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted Translation-en          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe Translation-en                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Sources                                 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/main Sources [84.2 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/restricted Sources [3,741 B]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted i386 Packages [10.8 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/universe Sources [27.5 kB]    
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/multiverse Sources [3,207 B]  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/main amd64 Packages [233 kB]  
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe i386 Packages [55.4 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse i386 Packages [6,438 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main Translation-en               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse Translation-en       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe Translation-en           
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/restricted amd64 Packages [13.3 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/universe amd64 Packages [103 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/multiverse amd64 Packages [6,257 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/main i386 Packages [229 kB]   
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/restricted i386 Packages [13.4 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/universe i386 Packages [100 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/multiverse i386 Packages [6,683 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/main Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/multiverse Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/restricted Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/universe Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/multiverse amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/universe amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/restricted amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/universe Translation-en        
Fetched 1,499 kB in 8s (180 kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_wily-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/universe amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_wily-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_wily-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/multiverse amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_wily-security_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_wily-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_wily-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_wily-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) wily-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_wily-security_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```



Thank you, Everett

---

### Post by Bashing-om on 2016-07-03
Everett Arndt; Hey:

There are but 2 sources for package management. let's look at them and find the duplicated entries:
Post back - Between code tags  - to maintain readability, of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by oldos2er on 2016-07-04
You've got saucy and trusty sources in addition to wily, which is a problem. 15.10 isn't going to be supported much longer, so I'd suggest a clean install of 16.04, if that suits your situation.

---

