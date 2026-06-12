---
title: "Partial Upgrade Newbie - broken desktop environment"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by brynellis on 2011-05-15
Hi

I'm not all that new to Linux but I'm pretty green on upgrades/updates etc.  I know the basics but nothing more.  I've just proved that by doing a partial upgrade and now I'm left with a working system but one that looks horrible.

I'd already upgraded from 10.10 to 11.04 and that had gone well even though I hate the new 'Unity' desktop so have reverted to the much better 'Ubuntu Classic'.

This morning Update Manager showed 'Partial Upgrade' and I was in a hurry so instead of looking up what that meant I just went ahead and did it!  Very bad I know, but I've done it now and have learnt my lesson.

So, now what I've ended up with is a horrible almost X windows like login screen that only has the option to login with Ubuntu, Recovery or Customized.  When I login with Ubuntu I get the Unity bar down the left hand side which works fine but whenever you minimise something it stays in the main part of the screen, even though it has actually minimised it.

Do I just need to wait for more updates now to fix this or is it not repairable?

When it prompted to Keep or Remove packages at the end I clicked remove.  I don't like having unused stuff around.  That was probably wrong too.

Sorry for being a dork, your help would be much appreciated.

Regards
Bryn

---

### Post by jerrrys on 2011-05-16
i think i would try to complete the update in terminal
sudo apt-get update
sudo apt-get upgrade

---

### Post by brynellis on 2011-05-17
Thank you.  I'll try that tonight when I get home.

---

### Post by brynellis on 2011-05-17
Ah, that's a shame.  That didn't work.

It upgraded things like Flash, Samba, Python and LibreOffice.

No difference to my environment though.  Still don't get Ubuntu Classic choice and X like Unity type look and feel.

Anybody got any other ideas?

---

### Post by jerrrys on 2011-05-17
do you have any personal data on this copy?  there are other [things]("http://ubuntuforums.org/showthread.php?t=965882") to try that should be safe, but there are no absolute guarantees.

---

### Post by wildmanne39 on 2011-05-17
> **brynellis said:**
> Hi

I'm not all that new to Linux but I'm pretty green on upgrades/updates etc.  I know the basics but nothing more.  I've just proved that by doing a partial upgrade and now I'm left with a working system but one that looks horrible.

I'd already upgraded from 10.10 to 11.04 and that had gone well even though I hate the new 'Unity' desktop so have reverted to the much better 'Ubuntu Classic'.

This morning Update Manager showed 'Partial Upgrade' and I was in a hurry so instead of looking up what that meant I just went ahead and did it!  Very bad I know, but I've done it now and have learnt my lesson.

So, now what I've ended up with is a horrible almost X windows like login screen that only has the option to login with Ubuntu, Recovery or Customized.  When I login with Ubuntu I get the Unity bar down the left hand side which works fine but whenever you minimise something it stays in the main part of the screen, even though it has actually minimised it.

Do I just need to wait for more updates now to fix this or is it not repairable?

When it prompted to Keep or Remove packages at the end I clicked remove.  I don't like having unused stuff around.  That was probably wrong too.

Sorry for being a dork, your help would be much appreciated.

Regards
Bryn
Hi, you can also try 
sudo dpkg --configure -a then 
sudo apt-get update then
sudo apt-get install -f
when i finishes then do the next one and let us know if it worked.:)

---

### Post by brynellis on 2011-05-17
Huge thanks for your quick reply guys but I don't think this has worked.  

So far I've only tried wildmanne39's suggestion.  Here's what I did and the results (the error's are from my printer driver which isn't officially supported on Linux so I'm not worried if that has to go.  I'll get another printer!):


bryn@blackbird:~$ sudo dpkg --configure -a
[sudo] password for bryn: 
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1).
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cnijfilter-ip2600series:i386:
 cnijfilter-ip2600series:i386 depends on libatk1.0-0 (>= 1.9.0).
 cnijfilter-ip2600series:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-ip2600series:i386 depends on libcairo2 (>= 1.0.2-2).
 cnijfilter-ip2600series:i386 depends on libcupsys2 (>= 1.2.1).
 cnijfilter-ip2600series:i386 depends on libfontconfig1 (>= 2.3.0).
 cnijfilter-ip2600series:i386 depends on libglib2.0-0 (>= 2.10.0).
 cnijfilter-ip2600series:i386 depends on libgtk2.0-0 (>= 2.8.0).
 cnijfilter-ip2600series:i386 depends on libpango1.0-0 (>= 1.12.3).
 cnijfilter-ip2600series:i386 depends on libpng12-0 (>= 1.2.8rel).
 cnijfilter-ip2600series:i386 depends on libpopt0 (>= 1.7).
 cnijfilter-ip2600series:i386 depends on libtiff4.
 cnijfilter-ip2600series:i386 depends on libx11-6.
 cnijfilter-ip2600series:i386 depends on libxcursor1 (>> 1.1.2).
 cnijfilter-ip2600series:i386 depends on libxext6.
 cnijfilter-ip2600series:i386 depends on libxfixes3.
 cnijfilter-ip2600series:i386 depends on libxi6.
 cnijfilter-ip2600series:i386 depends on libxinerama1.
 cnijfilter-ip2600series:i386 depends on libxml2 (>= 2.6.24).
 cnijfilter-ip2600series:i386 depends on libxrandr2.
 cnijfilter-ip2600series:i386 depends on libxrender1.
 cnijfilter-ip2600series:i386 depends on cnijfilter-common (>= 2.90); however:
  Package cnijfilter-common:i386 is not configured yet.
dpkg: error processing cnijfilter-ip2600series:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common:i386
 cnijfilter-ip2600series:i386
bryn@blackbird:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                            
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main amd64 Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe amd64 Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse amd64 Packages       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Reading package lists... Done
bryn@blackbird:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  gnome-user-share
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bryn@blackbird:~$

I don't know if it helps at all but I've attached screenshots from Synaptic showing my repo's and update settings.  There's also one showing how the desktop looks with everything looking very messy and mouse-overs not disappearing etc.

---

### Post by wildmanne39 on 2011-05-17
> **brynellis said:**
> Huge thanks for your quick reply guys but I don't think this has worked.  

So far I've only tried wildmanne39's suggestion.  Here's what I did and the results (the error's are from my printer driver which isn't officially supported on Linux so I'm not worried if that has to go.  I'll get another printer!):


bryn@blackbird:~$ sudo dpkg --configure -a
[sudo] password for bryn: 
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1).
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cnijfilter-ip2600series:i386:
 cnijfilter-ip2600series:i386 depends on libatk1.0-0 (>= 1.9.0).
 cnijfilter-ip2600series:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-ip2600series:i386 depends on libcairo2 (>= 1.0.2-2).
 cnijfilter-ip2600series:i386 depends on libcupsys2 (>= 1.2.1).
 cnijfilter-ip2600series:i386 depends on libfontconfig1 (>= 2.3.0).
 cnijfilter-ip2600series:i386 depends on libglib2.0-0 (>= 2.10.0).
 cnijfilter-ip2600series:i386 depends on libgtk2.0-0 (>= 2.8.0).
 cnijfilter-ip2600series:i386 depends on libpango1.0-0 (>= 1.12.3).
 cnijfilter-ip2600series:i386 depends on libpng12-0 (>= 1.2.8rel).
 cnijfilter-ip2600series:i386 depends on libpopt0 (>= 1.7).
 cnijfilter-ip2600series:i386 depends on libtiff4.
 cnijfilter-ip2600series:i386 depends on libx11-6.
 cnijfilter-ip2600series:i386 depends on libxcursor1 (>> 1.1.2).
 cnijfilter-ip2600series:i386 depends on libxext6.
 cnijfilter-ip2600series:i386 depends on libxfixes3.
 cnijfilter-ip2600series:i386 depends on libxi6.
 cnijfilter-ip2600series:i386 depends on libxinerama1.
 cnijfilter-ip2600series:i386 depends on libxml2 (>= 2.6.24).
 cnijfilter-ip2600series:i386 depends on libxrandr2.
 cnijfilter-ip2600series:i386 depends on libxrender1.
 cnijfilter-ip2600series:i386 depends on cnijfilter-common (>= 2.90); however:
  Package cnijfilter-common:i386 is not configured yet.
dpkg: error processing cnijfilter-ip2600series:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common:i386
 cnijfilter-ip2600series:i386
bryn@blackbird:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                            
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main amd64 Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe amd64 Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse amd64 Packages       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Reading package lists... Done
bryn@blackbird:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  gnome-user-share
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bryn@blackbird:~$

I don't know if it helps at all but I've attached screenshots from Synaptic showing my repo's and update settings.  There's also one showing how the desktop looks with everything looking very messy and mouse-overs not disappearing etc.

Hi, I have been reading your post over and over, it looks like you instlled gnome 3 is that right?

---

### Post by brynellis on 2011-05-18
I did try at one point yes but it didn't work.  I can't remember what was wrong now but it told me I couldn't install it so I didn't go ahead.

I'd forgotten that I'd added the PPA for it.  Should I remove that?

This is the URL I used to try gnome3 [http://compixels.com/7664/how-to-install-gnome-3-in-ubuntu-11-04-natty-narwhal]("http://compixels.com/7664/how-to-install-gnome-3-in-ubuntu-11-04-natty-narwhal").

---

### Post by brynellis on 2011-05-18
Dont know if this might help.  I've attached a list of installed packages.

---

### Post by brynellis on 2011-05-18
I've managed to get my Ubuntu Classic desktop back by reinstalling Gnome3 but it's still not all that great.

So, I've come to the conclusion that all these problems have probably been caused a) by me doing a partial upgrade and b) me messing with Gnome3.

So, my final conclusion is that I'm better off reinstalling back to 10.04LTS and waiting until 11.04 is more stable (and leaving Gnome3 well alone for a long time!).

I've got all my data and home partitions on separate partitions so I shouldn't lose anything through reinstalling.

Thanks for all your help and sorry for wasting your time.  I'm going to stop messing with upgrades now and wait for stable releases.

---

### Post by wildmanne39 on 2011-05-18
> **brynellis said:**
> I've managed to get my Ubuntu Classic desktop back by reinstalling Gnome3 but it's still not all that great.

So, I've come to the conclusion that all these problems have probably been caused a) by me doing a partial upgrade and b) me messing with Gnome3.

So, my final conclusion is that I'm better off reinstalling back to 10.04LTS and waiting until 11.04 is more stable (and leaving Gnome3 well alone for a long time!).

I've got all my data and home partitions on separate partitions so I shouldn't lose anything through reinstalling.

Thanks for all your help and sorry for wasting your time.  I'm going to stop messing with upgrades now and wait for stable releases.
Hi, that is why I asked if you had intalled gnome3 because I have read that once you have, you have to reinstall to get unity and gnome2 back.

---

