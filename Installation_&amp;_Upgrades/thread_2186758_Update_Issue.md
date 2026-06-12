---
title: "Update Issue"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by mvjt-dobson on 2013-11-08
I'm trying to update and I keep getting this error
```
dobbie@Dobbie-Acer:~$ sudo apt-get updateIgn http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                                                             
Ign http://archive.ubuntu.com saucy InRelease                                                                           
Hit http://dl.google.com stable Release                                                         
Ign http://extras.ubuntu.com saucy InRelease                                                                           
Ign http://archive.ubuntu.com saucy-updates InRelease                                           
Hit http://dl.google.com stable/main amd64 Packages                                             
Hit http://extras.ubuntu.com saucy Release.gpg                                                  
Hit http://dl.google.com stable/main i386 Packages                                              
Ign http://archive.ubuntu.com saucy-backports InRelease                                                               
Ign http://archive.ubuntu.com saucy-security InRelease                                                                
Hit http://extras.ubuntu.com saucy Release                                                                            
Ign http://archive.ubuntu.com saucy-proposed InRelease                                                                 
Hit http://extras.ubuntu.com saucy/main Sources                                                 
Get:1 http://archive.ubuntu.com saucy Release.gpg [933 B]                                       
Hit http://extras.ubuntu.com saucy/main amd64 Packages                                                                  
Get:2 http://archive.ubuntu.com saucy-updates Release.gpg [933 B]                               
Get:3 http://archive.ubuntu.com saucy-backports Release.gpg [933 B]                                                     
Hit http://extras.ubuntu.com saucy/main i386 Packages                                                                   
Get:4 http://archive.ubuntu.com saucy-security Release.gpg [933 B]                              
Ign http://dl.google.com stable/main Translation-en_NZ                                                                  
Get:5 http://archive.ubuntu.com saucy-proposed Release.gpg [933 B]                              
Ign http://dl.google.com stable/main Translation-en                                                                     
Get:6 http://archive.ubuntu.com saucy Release [49.6 kB]                                          
Get:7 http://archive.ubuntu.com saucy-updates Release [49.6 kB]                                                         
Get:8 http://archive.ubuntu.com saucy-backports Release [49.6 kB]                                                       
Get:9 http://archive.ubuntu.com saucy-security Release [49.6 kB]                                         
Ign http://extras.ubuntu.com saucy/main Translation-en_NZ                                                               
Get:10 http://archive.ubuntu.com saucy-proposed Release [49.6 kB]                                
Ign http://extras.ubuntu.com saucy/main Translation-en                                                    
Get:11 http://archive.ubuntu.com saucy/main Sources [1,009 kB]                                                          
Get:12 http://archive.ubuntu.com saucy/restricted Sources [4,759 B]                                                     
Get:13 http://archive.ubuntu.com saucy/universe Sources [6,108 kB]                                                      
Get:14 http://archive.ubuntu.com saucy/multiverse Sources [175 kB]                                                      
Get:15 http://archive.ubuntu.com saucy/main amd64 Packages [1,239 kB]                                                   
Get:16 http://archive.ubuntu.com saucy/restricted amd64 Packages [9,348 B]                                              
Get:17 http://archive.ubuntu.com saucy/universe amd64 Packages [5,643 kB]                                               
Get:18 http://archive.ubuntu.com saucy/multiverse amd64 Packages [131 kB]                                               
Get:19 http://archive.ubuntu.com saucy/main i386 Packages [1,238 kB]                                                    
Get:20 http://archive.ubuntu.com saucy/restricted i386 Packages [9,688 B]                                               
Get:21 http://archive.ubuntu.com saucy/universe i386 Packages [5,652 kB]                                                
Get:22 http://archive.ubuntu.com saucy/multiverse i386 Packages [133 kB]                                                
Get:23 http://archive.ubuntu.com saucy/main Translation-en [711 kB]                                                     
Get:24 http://archive.ubuntu.com saucy/multiverse Translation-en [101 kB]                                               
Get:25 http://archive.ubuntu.com saucy/restricted Translation-en [2,686 B]                                              
Get:26 http://archive.ubuntu.com saucy/universe Translation-en [3,886 kB]                                               
Get:27 http://archive.ubuntu.com saucy-updates/main Sources [28.5 kB]                                                   
Get:28 http://archive.ubuntu.com saucy-updates/restricted Sources [14 B]                                                
Get:29 http://archive.ubuntu.com saucy-updates/universe Sources [8,911 B]                                               
Get:30 http://archive.ubuntu.com saucy-updates/multiverse Sources [14 B]                                                
Get:31 http://archive.ubuntu.com saucy-updates/main amd64 Packages [71.5 kB]                                            
Get:32 http://archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]                                         
Get:33 http://archive.ubuntu.com saucy-updates/universe amd64 Packages [28.5 kB]                                        
Get:34 http://archive.ubuntu.com saucy-updates/multiverse amd64 Packages [14 B]                                         
Get:35 http://archive.ubuntu.com saucy-updates/main i386 Packages [71.0 kB]                                             
Get:36 http://archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]                                          
Get:37 http://archive.ubuntu.com saucy-updates/universe i386 Packages [28.9 kB]                                         
Get:38 http://archive.ubuntu.com saucy-updates/multiverse i386 Packages [14 B]                                          
Get:39 http://archive.ubuntu.com saucy-updates/main Translation-en [30.6 kB]                                            
Get:40 http://archive.ubuntu.com saucy-updates/multiverse Translation-en [14 B]                                         
Get:41 http://archive.ubuntu.com saucy-updates/restricted Translation-en [14 B]                                         
Get:42 http://archive.ubuntu.com saucy-updates/universe Translation-en [16.8 kB]                                        
Get:43 http://archive.ubuntu.com saucy-backports/main Sources [14 B]                                                    
Get:44 http://archive.ubuntu.com saucy-backports/restricted Sources [14 B]                                              
Get:45 http://archive.ubuntu.com saucy-backports/universe Sources [14 B]                                                
Get:46 http://archive.ubuntu.com saucy-backports/multiverse Sources [834 B]                                             
Get:47 http://archive.ubuntu.com saucy-backports/main amd64 Packages [14 B]                                             
Get:48 http://archive.ubuntu.com saucy-backports/restricted amd64 Packages [14 B]                                       
Get:49 http://archive.ubuntu.com saucy-backports/universe amd64 Packages [14 B]                                         
Get:50 http://archive.ubuntu.com saucy-backports/multiverse amd64 Packages [14 B]                                       
Get:51 http://archive.ubuntu.com saucy-backports/main i386 Packages [14 B]                                              
Get:52 http://archive.ubuntu.com saucy-backports/restricted i386 Packages [14 B]                                        
Get:53 http://archive.ubuntu.com saucy-backports/universe i386 Packages [14 B]                                          
Get:54 http://archive.ubuntu.com saucy-backports/multiverse i386 Packages [709 B]                                       
Get:55 http://archive.ubuntu.com saucy-backports/main Translation-en [14 B]                                             
Get:56 http://archive.ubuntu.com saucy-backports/multiverse Translation-en [525 B]                                      
Get:57 http://archive.ubuntu.com saucy-backports/restricted Translation-en [14 B]                                       
Get:58 http://archive.ubuntu.com saucy-backports/universe Translation-en [14 B]                                         
Get:59 http://archive.ubuntu.com saucy-security/main Sources [8,534 B]                                                  
Get:60 http://archive.ubuntu.com saucy-security/restricted Sources [14 B]                                               
Get:61 http://archive.ubuntu.com saucy-security/universe Sources [4,739 B]                                              
Get:62 http://archive.ubuntu.com saucy-security/multiverse Sources [14 B]                                               
Get:63 http://archive.ubuntu.com saucy-security/main amd64 Packages [33.4 kB]                                           
Get:64 http://archive.ubuntu.com saucy-security/restricted amd64 Packages [14 B]                                        
Get:65 http://archive.ubuntu.com saucy-security/universe amd64 Packages [9,783 B]                                       
Get:66 http://archive.ubuntu.com saucy-security/multiverse amd64 Packages [14 B]                                        
Get:67 http://archive.ubuntu.com saucy-security/main i386 Packages [33.4 kB]                                            
Get:68 http://archive.ubuntu.com saucy-security/restricted i386 Packages [14 B]                                         
Get:69 http://archive.ubuntu.com saucy-security/universe i386 Packages [10.1 kB]                                        
Get:70 http://archive.ubuntu.com saucy-security/multiverse i386 Packages [14 B]                                         
Get:71 http://archive.ubuntu.com saucy-security/main Translation-en [13.9 kB]                                           
Get:72 http://archive.ubuntu.com saucy-security/multiverse Translation-en [14 B]                                        
Get:73 http://archive.ubuntu.com saucy-security/restricted Translation-en [14 B]                                        
Get:74 http://archive.ubuntu.com saucy-security/universe Translation-en [6,004 B]                                       
Get:75 http://archive.ubuntu.com saucy-proposed/restricted amd64 Packages [14 B]                                        
Get:76 http://archive.ubuntu.com saucy-proposed/universe amd64 Packages [20.1 kB]                                       
Get:77 http://archive.ubuntu.com saucy-proposed/main amd64 Packages [24.9 kB]                                           
Get:78 http://archive.ubuntu.com saucy-proposed/multiverse amd64 Packages [14 B]                                        
Get:79 http://archive.ubuntu.com saucy-proposed/restricted i386 Packages [14 B]                                         
Get:80 http://archive.ubuntu.com saucy-proposed/universe i386 Packages [19.2 kB]                                        
Get:81 http://archive.ubuntu.com saucy-proposed/main i386 Packages [24.6 kB]                                            
Get:82 http://archive.ubuntu.com saucy-proposed/multiverse i386 Packages [14 B]                                         
Get:83 http://archive.ubuntu.com saucy-proposed/main Translation-en [14.1 kB]                                           
Get:84 http://archive.ubuntu.com saucy-proposed/multiverse Translation-en [14 B]                                        
Get:85 http://archive.ubuntu.com saucy-proposed/restricted Translation-en [14 B]                                        
Get:86 http://archive.ubuntu.com saucy-proposed/universe Translation-en [10.7 kB]                                       
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy InRelease                                                                            
  
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net saucy Release.gpg                                                                          
  Unable to connect to ppa.launchpad.net:http:
Ign http://archive.ubuntu.com saucy/main Translation-en_NZ                                                              
Ign http://archive.ubuntu.com saucy/multiverse Translation-en_NZ
Ign http://archive.ubuntu.com saucy/restricted Translation-en_NZ
Ign http://archive.ubuntu.com saucy/universe Translation-en_NZ
Ign http://archive.ubuntu.com saucy-updates/main Translation-en_NZ
Ign http://archive.ubuntu.com saucy-updates/multiverse Translation-en_NZ
Ign http://archive.ubuntu.com saucy-updates/restricted Translation-en_NZ
Ign http://archive.ubuntu.com saucy-updates/universe Translation-en_NZ
Ign http://archive.ubuntu.com saucy-backports/main Translation-en_NZ
Ign http://archive.ubuntu.com saucy-backports/multiverse Translation-en_NZ
Ign http://archive.ubuntu.com saucy-backports/restricted Translation-en_NZ
Ign http://archive.ubuntu.com saucy-backports/universe Translation-en_NZ
Ign http://archive.ubuntu.com saucy-security/main Translation-en_NZ
Ign http://archive.ubuntu.com saucy-security/multiverse Translation-en_NZ
Ign http://archive.ubuntu.com saucy-security/restricted Translation-en_NZ
Ign http://archive.ubuntu.com saucy-security/universe Translation-en_NZ
Ign http://archive.ubuntu.com saucy-proposed/main Translation-en_NZ
Ign http://archive.ubuntu.com saucy-proposed/multiverse Translation-en_NZ
Ign http://archive.ubuntu.com saucy-proposed/restricted Translation-en_NZ
Ign http://archive.ubuntu.com saucy-proposed/universe Translation-en_NZ
Fetched 26.8 MB in 2min 15s (198 kB/s)
Reading package lists... Done
W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/conscioususer/polly-unstable/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/elementary-os/daily/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/fsvh/pacifica-icon-theme/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3-next/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/numix/ppa/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/satyajit-happy/themes/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-icon-theme-daily/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/icons2/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/webupd8team/nemo/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/conscioususer/polly-unstable/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/elementary-os/daily/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/fsvh/pacifica-icon-theme/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3-next/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/numix/ppa/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/satyajit-happy/themes/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-icon-theme-daily/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/icons2/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch http://ppa.launchpad.net/webupd8team/nemo/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Some index files failed to download. They have been ignored, or old ones used instead.



```

I have tried changing servers and I am still getting the same issue, anyone have a solution?

---

### Post by ian-weisser on 2013-11-09
Well, all those are PPA's. PPAs are not mirrored, because they are not in the Ubuntu Repositories.
(They are also not community-supported software, PPAs are supported only by the PPA maintainer)


Let's see if a sample PPA exists for Saucy:
```
wget -O - http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu/dists/
```
Okay, that works...but it's very slow.

Next, let's see what the Launchpad Status ( [https://identi.ca/launchpadstatus](https://identi.ca/launchpadstatus) ) page has to day about the issue:

Aha:
> 
[LIST]
[*]                                         4 hours ago                           via                  Identi.ca Web                                    To:                 Public                                     CC:             [            Followers            ]("https://identi.ca/launchpadstatus/followers")                    
                 All affected services (including PPAs and codehosting) are back and stable. 
[*]                                         8 hours ago                           via                  Identi.ca Web                                    To:                 Public                                     CC:             [            Followers            ]("https://identi.ca/launchpadstatus/followers")                    

                 PPAs and codehosting are still offline, but everything else  has been healthy for a while. We're bringing the remaining services  back. 
[*]                                         12 hours ago                           via                  Identi.ca Web                                    To:                 Public                                     CC:             [            Followers            ]("https://identi.ca/launchpadstatus/followers")                    
                 Launchpad's currently offline due to a power failure. We're working to get things back up. 
[/LIST]


So, at the time you tried, Launchpad was down. But is seemingly back up now.

---

### Post by Bucky Ball on 2013-11-09
Confirming that it is all back up. Might take a little longer than normal, but wait and all should be fine. ;)

---

