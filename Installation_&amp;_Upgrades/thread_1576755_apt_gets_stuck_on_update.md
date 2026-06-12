---
title: "apt gets stuck on update"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by broadcast23 on 2010-09-17
Hello I am running Ubuntu Lucid on a machine (32 bit version). When I run apt-get update it gets stuck at 99%.  I have also other variants running in Virtual box. (ubu student, mint-debian, Ubuntu Maveric).  All the OS have this problem.  Searched through the Debian bugtracker, they've had this problem at least since 2008.  It seems that it worked until the update the other day I think it was last weekend at least on lucid If there is a connection problem at the server end shouldn't it at least time out or something giving you a message that it couldn't access the server, I mean it does but only if I hit cancel. Or control+c in the command line.  How can one update if the update manager isn't working correctly?

---

### Post by snowpine on 2010-09-17
Hi there, can you please copy & paste the exact output of:

```
sudo apt-get update
```

This will be helpful to other forum members to see where exactly it is stuck and assist you with your query.

---

### Post by broadcast23 on 2010-09-17
et:2 [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/restricted Translation-en_US [169B]
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/main Translation-en_US   
  Bad header line
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/multiverse Translation-en_US
  Bad header line
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/universe Translation-en_US
  Bad header line
81% [2 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers] bzip2: (stdin) is not a bzip2 file.
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid Release                                   
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates Release                           
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed Release                          
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Get:4 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                    
Get:5 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US [337B]
77% [5 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers] bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Get:7 [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) lucid/main Translation-en_US [349B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
bzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) lucid/main Translation-en_US
Get:8 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US [347B]
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg                           
54% [8 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers] bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/restricted Packages                       
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/main Packages                             
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/universe Packages                         
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/restricted Sources                        
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/multiverse Packages                       
Get:9 [http://downloadue.info](http://downloadue.info) lucid Release.gpg                                 
Get:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]                 
Get:11 [http://downloadue.info/repo/](http://downloadue.info/repo/) lucid/all Translation-en_US                
Get:12 [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en_US [345B]     
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/multiverse Sources                        
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/restricted Packages               
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/main Packages                     
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/multiverse Packages               
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/universe Packages                 
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/restricted Packages              
Get:13 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                            
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/main Packages                    
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/multiverse Packages              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/universe Packages                
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/compiz/ubuntu/](http://ppa.launchpad.net/compiz/ubuntu/) lucid/main Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/debfx/virtualbox/ubuntu/](http://ppa.launchpad.net/debfx/virtualbox/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Get:14 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]                  
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release.gpg                               
Get:15 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,045B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:16 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US [345B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:17 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US [347B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:18 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_US [355B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]     
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en_US           
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) lucid/main Translation-en_US                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [71.2kB]        
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,998B]  
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [36.6kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Get:24 [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release [1,722B]                       
Get:25 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [21.8kB]                   
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [14B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [8,949B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
99% [11 Translation-en_US bzip2 0B] [Waiting for headers]^C                    
ken@ken-desktop:~$ sudo apt-get update
Ign file: apt-build Release.gpg
Ign file:/var/cache/apt-build/repository/ apt-build/main Translation-en_US     
Get:1 file: apt-build Release [89B]                                            
Ign file: apt-build/main Packages                                              
Ign file: apt-build/main Packages                                              
Get:2 [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid Release.gpg [189B]                      
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/restricted Translation-en_US      
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/main Translation-en_US            
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/universe Translation-en_US        
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/multiverse Translation-en_US      
Get:3 [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates Release.gpg [189B]              
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/main Translation-en_US    
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/universe Translation-en_US
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Get:5 [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed Release.gpg [189B]             
Get:6 [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/restricted Translation-en_US [169B]
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/main Translation-en_US   
  Bad header line
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/multiverse Translation-en_US
  Bad header line
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/universe Translation-en_US
  Bad header line
96% [6 Translation-en_US bzip2 0B] [Waiting for headers] [Connecting to archivebzip2: (stdin) is not a bzip2 file.
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid Release                                   
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates Release                           
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed Release                          
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/restricted Packages                       
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/main Packages                             
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/universe Packages                         
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/restricted Sources                        
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/multiverse Packages                       
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/multiverse Sources                        
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/restricted Packages               
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/main Packages                     
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/multiverse Packages               
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/universe Packages                 
Get:7 [http://downloadue.info](http://downloadue.info) lucid Release.gpg                                 
Get:8 [http://downloadue.info/repo/](http://downloadue.info/repo/) lucid/all Translation-en_US                 
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/restricted Packages              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/main Packages                    
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/multiverse Packages              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/universe Packages                
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg                           
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Get:10 [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) lucid/main Translation-en_US [349B]
Get:11 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:12 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US [337B]
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Get:13 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US [347B]
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_US
Ign [http://ppa.launchpad.net/compiz/ubuntu/](http://ppa.launchpad.net/compiz/ubuntu/) lucid/main Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/debfx/virtualbox/ubuntu/](http://ppa.launchpad.net/debfx/virtualbox/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) lucid/main Translation-en_US                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Get:14 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US [345B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:15 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US [347B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:16 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_US [355B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:17 [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release [1,722B]                       
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages                     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [71.2kB]        
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,998B]  
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [36.6kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Get:23 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                            
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:24 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]                  
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [21.8kB]                   
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [14B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:27 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,045B]                      
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [8,949B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
99% [8 Translation-en_US bzip2 0B] [Waiting for headers]^C                     
ken@ken-desktop:~$ sudo apt-get update
[sudo] password for ken: 
Ign file: apt-build Release.gpg
Ign file:/var/cache/apt-build/repository/ apt-build/main Translation-en_US     
Get:1 file: apt-build Release [89B]                                            
Ign file: apt-build/main Packages                                              
Ign file: apt-build/main Packages                                              
Get:2 [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid Release.gpg [189B]                      
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/restricted Translation-en_US      
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/main Translation-en_US            
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/universe Translation-en_US        
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/multiverse Translation-en_US      
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates Release.gpg                       
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/main Translation-en_US    
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/universe Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed Release.gpg                      
Get:4 [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/restricted Translation-en_US [169B]
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/main Translation-en_US   
  Bad header line
93% [4 Translation-en_US bzip2 0B] [Waiting for headers] [Connecting to archivebzip2: (stdin) is not a bzip2 file.
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/restricted Translation-en_US
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/multiverse Translation-en_US
  Bad header line
Hit [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/universe Translation-en_US
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid Release                                   
Get:5 [http://downloadue.info](http://downloadue.info) lucid Release.gpg                                 
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Get:7 [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) lucid/main Translation-en_US [349B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:8 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                    
Get:9 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US [337B]
88% [7 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers] bzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) lucid/main Translation-en_US
69% [9 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers] bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Get:10 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US [347B]
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg                           
58% [10 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://ppa.launchpad.net/compiz/ubuntu/](http://ppa.launchpad.net/compiz/ubuntu/) lucid/main Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/debfx/virtualbox/ubuntu/](http://ppa.launchpad.net/debfx/virtualbox/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Get:11 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                            
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_US
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) lucid/main Translation-en_US                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Get:12 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US [345B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
75% [12 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:13 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US [347B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:14 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_US [355B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
72% [13 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
66% [14 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_US
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Get:15 [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release [1,722B]                       
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:17 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages                     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [71.2kB]        
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,998B]  
Get:20 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,045B]                      
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [36.6kB]    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [21.8kB]         
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [14B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [8,949B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:26 [http://downloadue.info/repo/](http://downloadue.info/repo/) lucid/all Translation-en_US       
98% [26 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers]^C
ken@ken-desktop:~$ clear

ken@ken-desktop:~$ sudo apt-get update
Ign file: apt-build Release.gpg
Ign file:/var/cache/apt-build/repository/ apt-build/main Translation-en_US     
Get:1 file: apt-build Release [89B]                                            
Ign file: apt-build/main Packages                                              
Ign file: apt-build/main Packages                                              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid Release.gpg                               
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/restricted Translation-en_US      
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/main Translation-en_US            
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/universe Translation-en_US        
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/multiverse Translation-en_US      
Get:2 [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates Release.gpg [189B]              
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/main Translation-en_US    
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/universe Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Get:4 [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed Release.gpg [189B]             
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Get:5 [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/restricted Translation-en_US [169B]
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/main Translation-en_US   
  Bad header line
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/multiverse Translation-en_US
  Bad header line
Err [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/universe Translation-en_US
  Bad header line
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
95% [5 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers] bzip2: (stdin) is not a bzip2 file.
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid Release                                   
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates Release                           
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed Release                          
Get:6 [http://downloadue.info](http://downloadue.info) lucid Release.gpg                                 
Get:7 [http://downloadue.info/repo/](http://downloadue.info/repo/) lucid/all Translation-en_US                 
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Get:8 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US [347B]
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Get:10 [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) lucid/main Translation-en_US [349B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:11 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                   
Get:12 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US [337B]
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/restricted Packages                       
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/main Packages                             
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/universe Packages                         
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/restricted Sources                        
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/multiverse Packages                       
Get:13 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                            
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release.gpg                               
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/multiverse Sources                        
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/restricted Packages               
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/main Packages                     
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/multiverse Packages               
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/universe Packages                 
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/restricted Packages              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/main Packages                    
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_US
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/multiverse Packages              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://ppa.launchpad.net/compiz/ubuntu/](http://ppa.launchpad.net/compiz/ubuntu/) lucid/main Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/debfx/virtualbox/ubuntu/](http://ppa.launchpad.net/debfx/virtualbox/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-proposed/universe Packages                
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) lucid/main Translation-en_US                   
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Get:14 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US [345B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:15 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US [347B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:16 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_US [355B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:17 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]                  
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages                     
Get:18 [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release [1,722B]                       
Get:19 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,045B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages               
99% [7 Translation-en_US bzip2 0B] [Waiting for headers]            10.4kB/s 0s^C
ken@ken-desktop:~$ 

OK but it is different every time I run it.

---

### Post by snowpine on 2010-09-17
Not sure what to tell you. Your software sources are a mess. You have a mix of Karmic and Lucid sources, and many 3rd-party repositories that are not part of a standard Ubuntu install. Either you or someone with administrative access to your computer did this.

I would recommend either trimming your software sources back to the Ubuntu defaults, or else go through line-by-line and test the legitimacy of each link.

---

### Post by broadcast23 on 2010-09-17
OK I admit that the sources are not all authenticated, but this does this on other distros that are default install sources eg mint-debian (fresh install on virtual box.  I googled for the bug in apt and there was one in 2008 in debian testing.  Mint Debian is based on Debian testing. Same thing happens with no specific source getting stuck.  Actually I'm running Ultimate Edition, but want to get rid of it when 10.10 comes out.  But it is doing the same thing.  Even worse I have 10.10 in virtual box, but it has some dependency problems So many distros are based on either Ubuntu or Debian and I like the apt for a package manager.  I once tried to just run this with just the Ubuntu repositories but the same thing happens.

---

