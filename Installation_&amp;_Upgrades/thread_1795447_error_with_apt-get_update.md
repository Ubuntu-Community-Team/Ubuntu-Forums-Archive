---
title: "error with apt-get update"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by angry_beavers on 2011-07-02
I am having an error that is preventing me from running apt-get update. Whenever I run apt-get update the terminal replies back with “E: Type 'exit' is not known on line 60 in source list /etc/apt/sources.list E: The list of sources could not be read.”
 

 At first I was getting an error with line 59 but I went in and replaced “wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -sudo apt-get updateapt-get install cairo-dock cairo-dock-plug-ins sudo apt-get install cairo-dock-plugins” with “deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock.”
 

 Also my Ubuntu Software Center will never fully load, unsure if that has anything to do with it. If anyone can please help me out it'd be greatly appreciated.
 

 Here is a copy of my /etc/apt/sources.list:
 

 

 # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted 
  
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
 # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner 
  
 ## This software is not part of Ubuntu, but is offered by third-party 
 ## developers who want to ship their latest software. 
 deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main 
 deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main 
 deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock 
 exit

---

### Post by Old_Grey_Wolf on 2011-07-02
Remove the exit from the last line in the file.

Also, the next to last line references hardy cairo-dock. I don't think that line is correct. Cairo-dock changed its name to glx-dock. I don't know what needs to be used for that repo in natty. If I were you I would just put a # at the beginning of that line until I googled for the correct repo.

---

### Post by angry_beavers on 2011-07-02
**Here is my new /etc/apt/sources.list**
 

 # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted 
  
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
 # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner 
  
 ## This software is not part of Ubuntu, but is offered by third-party 
 ## developers who want to ship their latest software. 
 deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main 
 deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main 
 deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) natty cairo-dock
 

 **Now when I do an apt-get update I get:**
 

 Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                                                       
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                                                                                    
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                                                                            
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                                        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                                                                      
 Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                                                                                  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                                                                                  
 Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                                                                             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                                                                          
 Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                                                                      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                                                                           
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                                                           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                                                                                             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                                                                                                                  
 Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                                                                                             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                                                                              
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                                                                                                                  
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                                                                                                                           
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                                                                                                  
 Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                                                                                           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                                                                                                
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                                                                                          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                                                                                            
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                                                                                          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages                                                                                         
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                                                                                                                   
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                                                                                                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages                                                                                                         
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                                                                                     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages                                                  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                                                      
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex                                                
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex                                                
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex                                                  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                                                                        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources                                                                                        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                                                                                          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources                                                                                        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages                                                                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages                                                                                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages                                                                                   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages                                                                                 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex                                                               
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex                                                                               
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex                                                                               
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex                                                           
 Ign [http://repository.glx-dock.org](http://repository.glx-dock.org) natty InRelease                                                                                      
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                                                                               
 Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US                                                                                   
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                                                                                          
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                                                            
 Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                                                     
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                                                
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                             
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US                    
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en                       
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US                      
 Get:2 [http://repository.glx-dock.org](http://repository.glx-dock.org) natty Release.gpg [198 B]                                                                        
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                                                                        
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en               
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US      
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en         
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US      
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en         
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en 
 Get:3 [http://repository.glx-dock.org](http://repository.glx-dock.org) natty Release [2,844 B]     
 Ign [http://repository.glx-dock.org](http://repository.glx-dock.org) natty Release                 
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                                                                                                                         
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                                                                                                                             
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                                                                                                                        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources                                                                                                                  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                                                                                                                    
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources                                                                                                                  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages                                                                                                                 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages                                                                                                           
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages                                                                                                             
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages                                                                                                           
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex                                                                                                               
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex                                                                                                         
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex                                                                                                         
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex                                                                                                           
 Get:4 [http://repository.glx-dock.org](http://repository.glx-dock.org) natty/cairo-dock amd64 Packages [3,157 B]                                                                                                   
 Ign [http://repository.glx-dock.org](http://repository.glx-dock.org) natty/cairo-dock TranslationIndex                                                                                                              
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US                                                                                                              
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en                                                                                                                 
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US                                                                                                        
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en                                                                                                           
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US                                                                                                        
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en                                                                                                           
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US                                                                                                          
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en                                                                                                             
 Ign [http://repository.glx-dock.org](http://repository.glx-dock.org) natty/cairo-dock Translation-en_US                                                                                                             
 Ign [http://repository.glx-dock.org](http://repository.glx-dock.org) natty/cairo-dock Translation-en                                                                                                                
 Fetched 6,271 B in 15s (395 B/s)                                                                                                                                                  
 Reading package lists... Done

---

### Post by Old_Grey_Wolf on 2011-07-02
What happens when you do "sudo apt-get upgrade"?

---

### Post by Old_Grey_Wolf on 2011-07-02
I also found this on their website [http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en](http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en).

---

### Post by angry_beavers on 2011-07-02
**Appears to have updated something. Here is the exact message**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  cairo-dock cairo-dock-core cairo-dock-data cairo-dock-plug-ins
  cairo-dock-plug-ins-data cairo-dock-plug-ins-integration
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,538 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  cairo-dock-data cairo-dock-core cairo-dock-plug-ins-data
  cairo-dock-plug-ins-integration cairo-dock-plug-ins cairo-dock
Install these packages without verification [y/N]? y
Get:1 [http://repository.glx-dock.org/ubuntu/](http://repository.glx-dock.org/ubuntu/) natty/cairo-dock cairo-dock-data all 2.3.0~3-1ubuntu0~natty [405 kB]
Get:2 [http://repository.glx-dock.org/ubuntu/](http://repository.glx-dock.org/ubuntu/) natty/cairo-dock cairo-dock-core amd64 2.3.0~3-1ubuntu0~natty [1,473 kB]
Get:3 [http://repository.glx-dock.org/ubuntu/](http://repository.glx-dock.org/ubuntu/) natty/cairo-dock cairo-dock-plug-ins-data all 2.3.0~3-1ubuntu0~natty [3,763 kB]
Get:4 [http://repository.glx-dock.org/ubuntu/](http://repository.glx-dock.org/ubuntu/) natty/cairo-dock cairo-dock-plug-ins-integration amd64 2.3.0~3-1ubuntu0~natty [57.6 kB]
Get:5 [http://repository.glx-dock.org/ubuntu/](http://repository.glx-dock.org/ubuntu/) natty/cairo-dock cairo-dock-plug-ins amd64 2.3.0~3-1ubuntu0~natty [830 kB]
Get:6 [http://repository.glx-dock.org/ubuntu/](http://repository.glx-dock.org/ubuntu/) natty/cairo-dock cairo-dock all 2.3.0~3-1ubuntu0~natty [9,176 B]
Fetched 6,538 kB in 27s (241 kB/s)                                             
(Reading database ... 134645 files and directories currently installed.)
Preparing to replace cairo-dock-data 2.3.0~1-0ubuntu1 (using .../cairo-dock-data_2.3.0~3-1ubuntu0~natty_all.deb) ...
Unpacking replacement cairo-dock-data ...
Preparing to replace cairo-dock-core 2.3.0~1-0ubuntu1 (using .../cairo-dock-core_2.3.0~3-1ubuntu0~natty_amd64.deb) ...
Unpacking replacement cairo-dock-core ...
Preparing to replace cairo-dock-plug-ins-data 2.3.0~1-0ubuntu1 (using .../cairo-dock-plug-ins-data_2.3.0~3-1ubuntu0~natty_all.deb) ...
Unpacking replacement cairo-dock-plug-ins-data ...
Preparing to replace cairo-dock-plug-ins-integration 2.3.0~1-0ubuntu1 (using .../cairo-dock-plug-ins-integration_2.3.0~3-1ubuntu0~natty_amd64.deb) ...
Unpacking replacement cairo-dock-plug-ins-integration ...
Preparing to replace cairo-dock-plug-ins 2.3.0~1-0ubuntu1 (using .../cairo-dock-plug-ins_2.3.0~3-1ubuntu0~natty_amd64.deb) ...
Unpacking replacement cairo-dock-plug-ins ...
Preparing to replace cairo-dock 2.3.0~1-0ubuntu1 (using .../cairo-dock_2.3.0~3-1ubuntu0~natty_all.deb) ...
Unpacking replacement cairo-dock ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up cairo-dock-data (2.3.0~3-1ubuntu0~natty) ...
Setting up cairo-dock-core (2.3.0~3-1ubuntu0~natty) ...
Setting up cairo-dock-plug-ins-data (2.3.0~3-1ubuntu0~natty) ...
Setting up cairo-dock-plug-ins-integration (2.3.0~3-1ubuntu0~natty) ...
Setting up cairo-dock-plug-ins (2.3.0~3-1ubuntu0~natty) ...
Setting up cairo-dock (2.3.0~3-1ubuntu0~natty) ...
[Cairo-Dock-Team] Repository: 
 * Updated your sources.list (repository.glx-dock.org => download.tuxfamily.org/glxdock/repository)                                                   [ OK ]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


**Then tried to do sudo apt-get update and it gave me pretty close to the same long message.**

Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) natty InRelease                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) natty Release.gpg [198 B]                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) natty Release [2,844 B]                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) natty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages                     
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) natty/cairo-dock amd64 Packages [3,157 B]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) natty/cairo-dock TranslationIndex            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) natty/cairo-dock Translation-en_US           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) natty/cairo-dock Translation-en              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 6,199 B in 3s (1,792 B/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877

---

### Post by Old_Grey_Wolf on 2011-07-02
OK, you need the GPG key. To get it enter these commands
```
wget -q http://download.tuxfamily.org/glxdock/repository/cairo-dock.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
```

I edited the commands. I had the wrong ones the first time.

---

### Post by angry_beavers on 2011-07-02
Thanks, I found that off the website you gave me. now it's still giving me that long list just without the GPG error. 

when i do sudo apt-get upgrade it says
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

OMFG just tested my Ubuntu Software Center and it loaded so things appear to be good unless it's not supposed to have that long list when i type sudo apt-get update.

Thank you sooo much!!

---

### Post by Old_Grey_Wolf on 2011-07-02
> **angry_beavers said:**
> 
OMFG just tested my Ubuntu Software Center and it loaded so things appear to be good unless it's not supposed to have that long list when i type sudo apt-get update.

Thank you sooo much!!

It is supposed to give you that long list. It is just telling you what items in the sources.list file it found. Unless there is an error (E: ) or warning (W: ) you are good to go.

---

