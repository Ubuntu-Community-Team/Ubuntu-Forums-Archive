---
title: "impossible to delete new kernels..."
date: 2015-01-12
forum: Installation &amp; Upgrades
---

### Post by papilonaa on 2015-01-12
[COLOR=#333333][FONT=UbuntuRegular]Helo...i have on this ubuntu 14.04 a huge problem
 it run an 13.3.0-39 kernel, some times ago i wanted to update via synaptic to 13.3.0-40 and 13.3.0-43..
Unfortunately, the kernel upgrade did not complete since then nothing works..i did several times sudo apt update sudo apt upgrade .i try to delete via synaptic or via the terminal ..even with a live cd , i try to reinstall those kernel..I tried sudo apt-get autoremove and sudo apt-get clean and repeatedly did sudo update-grub after all those, but nothing noticable happens, and in result there are a lot of errors...but nope... i cannot update,i cannot upgrade..i cannot install anythings ect... my question is, is it possible to delete those kernel, thanks for help.

```
[/FONT][/COLOR]dom@dom-Latitude-D630:~$ sudo dpkg --list | grep linux-image
ii  linux-image-3.13.0-39-generic                               3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-40-generic                               3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-40-lowlatency                            3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-3.13.0-43-generic                               3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-3.13.0-43-lowlatency                            3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                         3.13.0.43.50                                        amd64        Generic Linux kernel image
iU  linux-image-lowlatency                                      3.13.0.43.50                                        amd64        lowlatency Linux kernel image
dom@dom-Latitude-D630:~$ 


[COLOR=#333333][FONT=UbuntuRegular]
```
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]

---

### Post by tokyobadger on 2015-01-12
To delete unwanted kernels you could try from synaptic or you could try from CLI using the suggestion [here](http://markmcb.com/2013/02/04/cleanup-unused-linux-kernels-in-ubuntu/).

The appearance of the low-latency kernel suggests that you have either added a ppa or are not running vanilla Ubuntu - Studio?

---

### Post by Impavidus on 2015-01-12
It would be helpful to see those error messages. Start with these commands:```
sudo apt-get update
sudo dpkg --configure -a
```

---

### Post by papilonaa on 2015-01-12
Thanks here is the result
```
dom@dom-Latitude-D630:~$ sudo apt-get update[sudo] password for dom: 
Ign http://liveusb.info all InRelease                                          
Ign http://archive.canonical.com trusty InRelease                              
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://dl.google.com stable InRelease                                      
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://liveusb.info all Release.gpg [490 B]                              
Ign http://archive.canonical.com trusty InRelease                              
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Ign http://dl.google.com stable InRelease                                      
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://liveusb.info all Release                                            
Get:3 http://archive.canonical.com trusty Release.gpg [933 B]                  
Ign http://liveusb.info all Release                                            
Ign http://archive.ubuntu.com trusty-security InRelease                        
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://extras.ubuntu.com trusty Release                                    
Get:4 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://liveusb.info all/main amd64 Packages/DiffIndex                      
Get:5 http://archive.canonical.com trusty Release.gpg [933 B]                  
Ign http://archive.ubuntu.com trusty-backports InRelease                       
Ign http://extras.ubuntu.com trusty/main amd64 Packages/DiffIndex              
Get:6 http://dl.google.com stable Release.gpg [198 B]                          
Get:7 http://archive.getdeb.net trusty-getdeb InRelease [8 131 B]              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.getdeb.net trusty-getdeb InRelease                          
Ign http://liveusb.info all/main i386 Packages/DiffIndex                       
Hit http://archive.canonical.com trusty Release                                
Ign http://archive.canonical.com trusty Release                                
Hit http://dl.google.com stable Release                                        
Ign http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Ign http://archive.canonical.com trusty Release                                
Hit http://dl.google.com stable Release                                        
Ign http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty/partner amd64 Packages/DiffIndex       
Ign http://extras.ubuntu.com trusty/main i386 Packages/DiffIndex               
Get:8 http://archive.ubuntu.com trusty Release.gpg [933 B]                     
Ign http://archive.getdeb.net trusty-getdeb/apps amd64 Packages/DiffIndex      
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty/partner i386 Packages/DiffIndex        
Get:9 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                   
Ign http://archive.getdeb.net trusty-getdeb/apps i386 Packages/DiffIndex       
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:10 http://archive.ubuntu.com trusty-security Release.gpg [933 B]           
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:11 http://archive.ubuntu.com trusty-backports Release.gpg [933 B]          
Ign http://archive.canonical.com trusty/partner amd64 Packages/DiffIndex       
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty Release                                   
Ign http://archive.ubuntu.com trusty Release                                   
Get:12 https://download.01.org trusty InRelease                                
Ign https://download.01.org trusty InRelease                                   
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex                  
Ign http://archive.canonical.com trusty/partner i386 Packages/DiffIndex        
Get:13 http://archive.ubuntu.com trusty-updates Release [62,0 kB]              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                   
Get:14 https://download.01.org trusty/main amd64 Packages/DiffIndex            
Ign https://download.01.org trusty/main amd64 Packages/DiffIndex               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Hit http://archive.canonical.com trusty/partner Translation-en                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign https://download.01.org trusty/main i386 Packages/DiffIndex                
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign http://archive.ubuntu.com trusty-updates Release                           
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Get:15 http://downloads.sourceforge.net all InRelease [1 891 B]                
Ign http://downloads.sourceforge.net all InRelease                             
Hit http://archive.ubuntu.com trusty-security Release                          
Ign http://archive.ubuntu.com trusty-security Release                          
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://archive.ubuntu.com trusty-backports Release                         
Ign http://archive.ubuntu.com trusty-backports Release                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://archive.ubuntu.com trusty/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://liveusb.info all/main amd64 Packages                                
Ign http://downloads.sourceforge.net all/main amd64 Packages/DiffIndex         
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://archive.ubuntu.com trusty/restricted amd64 Packages/DiffIndex       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://liveusb.info all/main i386 Packages                                 
Ign http://archive.ubuntu.com trusty/universe amd64 Packages/DiffIndex         
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://archive.ubuntu.com trusty/multiverse amd64 Packages/DiffIndex       
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://downloads.sourceforge.net all/main i386 Packages/DiffIndex          
Ign http://liveusb.info all/main Translation-en_US                             
Ign http://archive.ubuntu.com trusty/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://liveusb.info all/main Translation-en                                
Ign http://archive.ubuntu.com trusty/restricted i386 Packages/DiffIndex        
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.ubuntu.com trusty/universe i386 Packages/DiffIndex          
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Ign http://archive.ubuntu.com trusty/multiverse i386 Packages/DiffIndex        
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://archive.ubuntu.com trusty/universe Translation-en          
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://dl.google.com stable/main Translation-en                            
Ign http://archive.ubuntu.com trusty-updates/main amd64 Packages/DiffIndex     
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://archive.ubuntu.com trusty-updates/restricted amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net saucy InRelease                                   
Ign http://dl.google.com stable/main Translation-en                   
Ign http://archive.ubuntu.com trusty-updates/universe amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-updates/main i386 Packages/DiffIndex      
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-updates/restricted i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-updates/universe i386 Packages/DiffIndex  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-updates/multiverse i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Get:16 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Hit https://download.01.org trusty/main amd64 Packages                         
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit https://download.01.org trusty/main i386 Packages                          
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:17 https://download.01.org trusty/main Translation-en_US                   
Ign https://download.01.org trusty/main Translation-en_US                      
Ign http://archive.ubuntu.com trusty-security/main amd64 Packages/DiffIndex    
Get:18 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://archive.ubuntu.com trusty-security/restricted amd64 Packages/DiffIndex
Get:19 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign https://download.01.org trusty/main Translation-en                         
Ign http://archive.ubuntu.com trusty-security/universe amd64 Packages/DiffIndex
Get:20 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://archive.ubuntu.com trusty-security/multiverse amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-security/main i386 Packages/DiffIndex     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-security/restricted i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-security/universe i386 Packages/DiffIndex 
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-security/multiverse i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:21 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Hit http://archive.ubuntu.com trusty-security/main Translation-en     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:22 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                       
Hit http://archive.ubuntu.com trusty-security/universe Translation-en          
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-backports/main amd64 Packages/DiffIndex   
Ign http://archive.ubuntu.com trusty-backports/universe amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://downloads.sourceforge.net all/main amd64 Packages                   
Ign http://archive.ubuntu.com trusty-backports/restricted amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.ubuntu.com trusty-backports/main i386 Packages/DiffIndex    
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.ubuntu.com trusty-backports/universe i386 Packages/DiffIndex
Ign http://downloads.sourceforge.net all/main Translation-en_US                
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.ubuntu.com trusty-backports/multiverse i386 Packages/DiffIndex
Hit http://downloads.sourceforge.net all/main i386 Packages                    
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.ubuntu.com trusty-backports/restricted i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://downloads.sourceforge.net all/main Translation-en                   
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/main Translation-en             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Ign http://ppa.launchpad.net trusty Release                                    
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en         
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                   
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Get:23 http://ppa.launchpad.net trusty Release [15,1 kB]           
Hit http://archive.ubuntu.com trusty/main i386 Packages                      
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://ppa.launchpad.net trusty Release                        
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Get:24 http://ppa.launchpad.net trusty Release [15,1 kB]                       
Get:25 http://archive.ubuntu.com trusty-updates/main amd64 Packages [392 kB]   
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Get:26 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [8 875 B]
Hit http://ppa.launchpad.net saucy Release                                     
Get:27 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [236 kB]
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:28 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [9 370 B]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:29 http://archive.ubuntu.com trusty-updates/main i386 Packages [384 kB]    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:30 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [8 846 B]
Get:31 http://archive.ubuntu.com trusty-updates/universe i386 Packages [237 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:32 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [9 553 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages              
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex              
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages        
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex               
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages          
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty-security/main i386 Packages               
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages         
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages           
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages             
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages              
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages          
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex              
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:33 http://ppa.launchpad.net trusty/main amd64 Packages [19,3 kB]           
Get:34 http://ppa.launchpad.net trusty/main i386 Packages [19,3 kB]            
Get:35 http://ppa.launchpad.net trusty/main Translation-en [15,8 kB]           
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex              
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:36 http://ppa.launchpad.net trusty/main amd64 Packages [12,1 kB]           
Get:37 http://ppa.launchpad.net trusty/main i386 Packages [12,1 kB]            
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Get:38 http://ppa.launchpad.net trusty/main Translation-en [4 758 B]           
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US            
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-en_US      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://archive.ubuntu.com trusty-security/main Translation-en_US           
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.ubuntu.com trusty-security/restricted Translation-en_US     
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex              
Ign http://archive.ubuntu.com trusty-security/universe Translation-en_US       
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex               
Ign http://archive.ubuntu.com trusty-backports/main Translation-en_US          
Ign http://archive.ubuntu.com trusty-backports/multiverse Translation-en_US    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.ubuntu.com trusty-backports/restricted Translation-en_US    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://archive.ubuntu.com trusty-backports/universe Translation-en_US      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Hit http://ppa.launchpad.net saucy/main Translation-en                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Fetched 1 483 kB in 1min 6s (22,4 kB/s)
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: GPG error: http://liveusb.info all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4E940D7FDD7FB8CC
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.getdeb.net trusty-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: https://download.01.org trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: GPG error: http://archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://downloads.sourceforge.net all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
W: GPG error: http://archive.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4B6DCB2258043CFF
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2B3F92F902D65EFF
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D99B1D2629935E8D
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 566BCB5EF661FE79
W: Failed to fetch http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
dom@dom-Latitude-D630:~$ sudo dpkg --configure -a
Setting up linux-image-3.13.0-43-lowlatency (3.13.0-43.72) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
Error! Error! Your kernel headers for kernel 3.13.0-43-lowlatency cannot be found.
Please install the linux-headers-3.13.0-43-lowlatency package,
or use the --kernelsourcedir option to tell DKMS where it's located
Your kernel headers for kernel 3.13.0-43-lowlatency cannot be found.
Please install the linux-headers-3.13.0-43-lowlatency package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
update-initramfs: Generating /boot/initrd.img-3.13.0-43-lowlatency
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-43-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-43-generic...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_CMDLINE_LINUX_DEFAULT=drm.debug=0xe plymouth:debug'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-43-lowlatency.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-43-lowlatency (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up getdeb-repository (0.1-1~getdeb1) ...
--2015-01-12 14:17:38--  http://archive.getdeb.net/getdeb-archive.key
Resolving archive.getdeb.net (archive.getdeb.net)... 144.76.200.19
Connecting to archive.getdeb.net (archive.getdeb.net)|144.76.200.19|:80... gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntu-x-swat-x-updates.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntukylin-archive-keyring.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/uck-team-uck-stable.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_10.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_12.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
connected.
HTTP request sent, awaiting response... 200 OK
Length: 1682 (1,6K) [application/pgp-keys]
Saving to: ‘STDOUT’


100%[======================================>] 1 682       --.-K/s   in 0s      


2015-01-12 14:17:39 (86,3 MB/s) - written to stdout [1682/1682]


dpkg: error processing package getdeb-repository (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-lowlatency:
 linux-image-lowlatency depends on linux-image-3.13.0-43-lowlatency; however:
  Package linux-image-3.13.0-43-lowlatency is not configured yet.


dpkg: error processing package linux-image-lowlatency (--configure):
 dependency problems - leaving unconfigured
Setting up playdeb (0.3-1~getdeb1) ...
--2015-01-12 14:17:39--  http://archive.getdeb.net/getdeb-archive.key
Resolving archive.getdeb.net (archive.getdeb.net)... 144.76.200.19
Connecting to archive.getdeb.net (archive.getdeb.net)|144.76.200.19|:80... gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntu-x-swat-x-updates.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntukylin-archive-keyring.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/uck-team-uck-stable.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_10.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_12.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
connected.
HTTP request sent, awaiting response... 200 OK
Length: 1682 (1,6K) [application/pgp-keys]
Saving to: ‘STDOUT’


100%[======================================>] 1 682       --.-K/s   in 0s      


2015-01-12 14:17:40 (4,06 MB/s) - written to stdout [1682/1682]


dpkg: error processing package playdeb (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up opera (12.16.1860) ...
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntukylin-archive-keyring.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/uck-team-uck-stable.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_10.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_12.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntukylin-archive-keyring.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/uck-team-uck-stable.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_10.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_12.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntukylin-archive-keyring.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/uck-team-uck-stable.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_10.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_12.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntukylin-archive-keyring.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/uck-team-uck-stable.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_10.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_12.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntukylin-archive-keyring.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/uck-team-uck-stable.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_10.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_12.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntukylin-archive-keyring.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/uck-team-uck-stable.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_10.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_12.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntu-x-swat-x-updates.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntukylin-archive-keyring.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/uck-team-uck-stable.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_10.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/xubuntu-dev-xfce-4_12.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
dpkg: error processing package opera (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-43-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-43-generic...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_CMDLINE_LINUX_DEFAULT=drm.debug=0xe plymouth:debug'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-43-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.13.0-43-lowlatency
 getdeb-repository
 linux-image-lowlatency
 playdeb
 opera
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic



```

---

### Post by papilonaa on 2015-01-12
Thanks
i problably did stupid upgrade via Synaptic..cause I don`t have vanilla Ubuntu Studio running, I` ll have a look at the links, but I am not so advanced.

---

### Post by tokyobadger on 2015-01-12
You've all kinds of stuff going on there - I'd clean out the non-standard ppa's, but that's just me

---

### Post by papilonaa on 2015-01-13
Thanks  witch ppa should i clean?

---

### Post by Impavidus on 2015-01-13
You have a huge load of PPAs, some of which seem broken. PPAs are a common cause of trouble. Maybe you can remove all PPAs, solve your other problems and then add your PPAs back one by one, until you encounter a problem. If you still need all those PPAs, that is.

I don't know about getdeb-repository, playdeb and opera. They are not in the standard repositories. I assume you got them from a PPA. The low latency kernel packages cannot be installed because the headers are not present. But if you don't know why the low latency kernel is there to be installed, you could as well remove it:```
sudo apt-get purge linux-image-lowlatency linux-image-3.13.0-40-lowlatency linux-image-3.13.0-43-lowlatency
```I can't say whether that will work, given the current status of your system.

Your main problem is this:```
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_CMDLINE_LINUX_DEFAULT=drm.debug=0xe plymouth:debug'.
No path or device is specified.
```I don't know what to do with that. It could be a syntax error in one of the grub related files. Maybe somebody knows something to try and solve this.

---

### Post by MAFoElffen on 2015-01-13
Why do you have debug turned on for plymouth and the graphics layer? did you previously have other issues you were trying to work out with those two? IMHO- a good idea to work on one problem at a time...

Was that am indication that your graphics driver was having problems working with a certain kernel?

---

### Post by papilonaa on 2015-01-16
Well guys...thanks for your help
I have in this computor, fortunatly , or maybe not severals instaled distros
The main probleme is with this one.an ubuntu 14.04...I ugraded the kernel -39 to -40 and then to -43 but that was wrong, since then all went bad.
I tried to delete the -40 and purge it here are the result...it seems that the -40 is still making problems
How do i delete all ppa?How can i delete complitly those -40 and -43 kernels..is this possible or not..?should i better reinstall all?
```
dom@dom-Latitude-D630:~$ sudo apt-get purge linux-image-lowlatency linux-image-3.13.0-40-lowlatency linux-image-3.13.0-43-lowlatency[sudo] password for dom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-40-generic linux-image-3.13.0-40-lowlatency
  linux-image-3.13.0-43-lowlatency* linux-image-extra-3.13.0-40-generic
  linux-image-lowlatency*
0 upgraded, 0 newly installed, 5 to remove and 82 not upgraded.
11 not fully installed or removed.
After this operation, 581 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 361526 files and directories currently installed.)
Removing linux-image-extra-3.13.0-40-generic (3.13.0-40.69) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-40-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Error! Your kernel headers for kernel 3.13.0-40-generic cannot be found.
Please install the linux-headers-3.13.0-40-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-40-generic cannot be found.
Please install the linux-headers-3.13.0-40-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-40-generic
grep: /boot/config-3.13.0-40-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-40-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-40-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_C6EDnr/lib/modules/3.13.0-40-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_C6EDnr/lib/modules/3.13.0-40-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-43-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-43-generic...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_CMDLINE_LINUX_DEFAULT=drm.debug=0xe plymouth:debug'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.13.0-40-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-40-generic (3.13.0-40.69) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-43-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-43-generic...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_CMDLINE_LINUX_DEFAULT=drm.debug=0xe plymouth:debug'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-40-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-40-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-40-lowlatency (3.13.0-40.69) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.13.0-40-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-43-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-43-generic...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_CMDLINE_LINUX_DEFAULT=drm.debug=0xe plymouth:debug'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-40-lowlatency.postrm line 328.
dpkg: error processing package linux-image-3.13.0-40-lowlatency (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-40-generic
 linux-image-3.13.0-40-generic
 linux-image-3.13.0-40-lowlatency
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by tokyobadger on 2015-01-17
Please post the output of
```
ls -a /etc/apt/sources.list.d/
```
This will show us what PPAs you have and then we can start removing them

---

### Post by Bucky Ball on 2015-01-17
Just a note for future reference: just update with the Software Updater or:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That is all. The current kernel for 14.04 is 3.13.0-44. Those commands will get you there. No need to go anywhere near Synaptics. 

Best suggestion above is to kill all those PPAs, run the commands above, then add the PPAs you need back one by one. To get rid of kernels in Synaptic, find the one you are currently using with:

```
uname -a
```

... so you don't try and kill that by accident, then in Synaptic search for 'linux image' and kill the images you don't want. Then:

```
sudo update-grub
```

... and run the update commands I gave at the start again. Reboot. 

To kill the PPAs, go to Synaptic>Settings>Repositories>Other Software and untick or remove them. Good luck.

---

