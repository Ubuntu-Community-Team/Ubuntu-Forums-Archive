---
title: "&quot;translation-en in&quot; never updated?????"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by som21 on 2010-11-05
i am using ubuntu lucid for around 6 months now.there is no problem regarding any regular work and i am overall happy with the function;but i have this queary.
while updating synaptic or "sudo apt-get update" in the terminal,there is a file which is always failed to update or ignored-'translation-en IN'.it never updated.so i am just curious why is that and what is its function?could anybody give me an idea?



```
som@som-laptop:~$ sudo apt-get update
[sudo] password for som: 
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Hit http://archive.canonical.com lucid Release.gpg                             
[COLOR="DarkRed"]Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_IN [/COLOR]      
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_IN          
Hit http://in.archive.ubuntu.com lucid Release.gpg                             
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/bisigi/dev/ubuntu/ lucid/main Translation-en_IN   
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/breathe-dev/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_IN              
Ign http://ppa.launchpad.net/chromium-daily/dev/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://archive.canonical.com lucid Release                                 
Get:2 http://dl.google.com stable Release.gpg [189B]                           
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN          
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_IN   
Hit http://archive.canonical.com lucid/partner Packages                        
Ign http://ppa.launchpad.net/damnvid/ppa/ubuntu/ lucid/main Translation-en_IN  
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ lucid/main Translation-en_IN  
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Get:3 http://dl.google.com stable Release [2,544B]                             
Ign http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu/ lucid/main Translation-en_IN
Get:4 http://dl.google.com stable Release [1,338B]                             
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/psyke83/ppa/ubuntu/ lucid/main Translation-en_IN  
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN    
Get:5 http://dl.google.com stable/non-free Packages [1,010B]                   
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Get:6 http://dl.google.com stable/main Packages [1,052B]                       
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN      
Get:7 http://dl.google.com stable/main Packages [613B]                         
Ign http://www.geekconnection.org karmic/ Release.gpg                          
Ign http://www.geekconnection.org/remastersys/repository/ karmic/ Translation-en_IN
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://packages.medibuntu.org lucid Release.gpg                            
Ign http://packages.medibuntu.org/ lucid/free Translation-en_IN                
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_IN            
Ign http://www.geekconnection.org karmic/ Release                              
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://packages.medibuntu.org lucid Release                                
Hit http://packages.medibuntu.org lucid/free Packages                          
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://packages.medibuntu.org lucid/non-free Packages                      
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                     
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN   
Hit http://in.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN  
Ign http://www.geekconnection.org karmic/ Packages                            
Ign http://www.geekconnection.org karmic/ Packages                            
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN
Hit http://www.geekconnection.org karmic/ Packages
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com lucid-security Release.gpg
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com lucid Release          
Hit http://in.archive.ubuntu.com lucid-updates Release                        
Hit http://in.archive.ubuntu.com lucid-security Release                       
Hit http://in.archive.ubuntu.com lucid/main Packages                          
Hit http://in.archive.ubuntu.com lucid/restricted Packages
Hit http://in.archive.ubuntu.com lucid/main Sources     
Hit http://in.archive.ubuntu.com lucid/restricted Sources
Hit http://in.archive.ubuntu.com lucid/universe Packages
Hit http://in.archive.ubuntu.com lucid/universe Sources 
Hit http://in.archive.ubuntu.com lucid/multiverse Packages
Hit http://in.archive.ubuntu.com lucid/multiverse Sources
Hit http://in.archive.ubuntu.com lucid-updates/main Packages
Hit http://in.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://in.archive.ubuntu.com lucid-updates/main Sources
Hit http://in.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://in.archive.ubuntu.com lucid-updates/universe Packages
Hit http://in.archive.ubuntu.com lucid-updates/universe Sources
Hit http://in.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://in.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://in.archive.ubuntu.com lucid-security/main Packages
Hit http://in.archive.ubuntu.com lucid-security/restricted Packages
Hit http://in.archive.ubuntu.com lucid-security/main Sources
Hit http://in.archive.ubuntu.com lucid-security/restricted Sources
Hit http://in.archive.ubuntu.com lucid-security/universe Packages
Hit http://in.archive.ubuntu.com lucid-security/universe Sources
Hit http://in.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://in.archive.ubuntu.com lucid-security/multiverse Sources
Fetched 6,935B in 1min 46s (65B/s)
Reading package lists... Done

```som@som-laptop:~$

---

