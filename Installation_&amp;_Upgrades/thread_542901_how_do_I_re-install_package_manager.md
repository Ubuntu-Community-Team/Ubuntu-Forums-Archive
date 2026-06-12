---
title: "how do I re-install package manager"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by cjay on 2007-09-04
I keep getting this message every time I try to start package manager, please, how do I uninstall package manager and reinstall it? or how can I repair it, please be patient as I am a total newbie and need all the help I can get. I am running Ubuntu 7.04 Feisty Fawn:( Package manager is totally unusable at the moment

'E  Dynamic MMap ran out of room, E:Error occurred while processing tuxpuck (NewVersion1), E:Problem with Merge List /var/lib/apt/lists/http.us.Debian.org_Debian_dists_testing_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.':confused::confused:

---

### Post by wolfen69 on 2007-09-04
first:
```
sudo aptitude update
```
then:
```
sudo aptitude remove synaptic
```
then:
```
sudo aptitude install synaptic
```

---

### Post by cjay on 2007-09-06
Many thanks for your help unfortunately package manager will not update or uninstall or install?
I know that the below is a lot but this is the readout from my terminal.

root@cjays:/home/cjay# sudo aptitude update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_GB
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_GB
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg                                 
Get:1 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release.gpg [189B]                  
Ign [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Translation-en_GB                
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_GB       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB           
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                                
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_GB                 
Get:4 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release [5535B]                                       
Get:5 [http://mirror.noreply.org](http://mirror.noreply.org) stable Release.gpg [189B]                                                
Ign [http://mirror.noreply.org](http://mirror.noreply.org) stable/main Translation-en_GB                                              
Get:6 [http://http.us.debian.org](http://http.us.debian.org) testing Release.gpg [189B]                                               
Ign [http://http.us.debian.org](http://http.us.debian.org) testing/main Translation-en_GB                                             
Ign [http://http.us.debian.org](http://http.us.debian.org) testing/contrib Translation-en_GB                                          
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Translation-en_GB                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB                              
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION> Release.gpg                                                 
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/main Translation-en_GB                                      
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/main Translation-en_GB                                      
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/deb-src Translation-en_GB                                   
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/http://mirror.noreply.org/pub/tor Translation-en_GB         
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/Fiesty Translation-en_GB                                    
Ign [http://http.us.debian.org](http://http.us.debian.org) testing/non-free Translation-en_GB                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                                                   
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/main Translation-en_GB                                      
Ign [http://mirror.noreply.org](http://mirror.noreply.org) fiesty Release.gpg                                                         
Ign [http://mirror.noreply.org](http://mirror.noreply.org) fiesty/main Translation-en_GB                                              
Get:7 [http://mirror.noreply.org](http://mirror.noreply.org) stable Release [2499B]                                                   
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release                                                              
Ign [http://mirror.noreply.org](http://mirror.noreply.org) stable Release                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_GB                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_GB                                
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]                                       
Get:9 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty Release.gpg [191B]                                             
Ign [http://download.skype.com](http://download.skype.com) stable Release                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                                             
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION> Release                                                     
Get:10 [http://http.us.debian.org](http://http.us.debian.org) testing Release [68.5kB]                                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_GB                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_GB                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_GB                               
Get:11 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/main Translation-en_GB [4827B]                                
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                                                   
Ign [http://mirror.noreply.org](http://mirror.noreply.org) fiesty Release                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages                                       
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                                                        
Ign [http://mirror.noreply.org](http://mirror.noreply.org) stable/main Packages                                                       
Ign [http://mirror.noreply.org](http://mirror.noreply.org) stable/main Sources                                                        
Ign [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages                                       
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/main Packages                                               
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/main Packages                                               
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/deb-src Packages                                            
Hit [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_GB                                 
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_GB                              
Get:13 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Packages [41.0kB]                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_GB                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_GB                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_GB                                
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/restricted Translation-en_GB                                     
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/universe Translation-en_GB                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                                                     
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release [38.4kB]                                        
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/http://mirror.noreply.org/pub/tor Packages                  
Get:15 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/multiverse Translation-en_GB [1573B]                          
Get:16 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates Release.gpg [191B]                                    
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/main Translation-en_GB                                   
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB                             
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/universe Translation-en_GB                               
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty Release                                                          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates Release                                                  
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/main Packages                                                    
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/restricted Packages                                              
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/universe Packages                                                
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/restricted Sources                                               
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/Fiesty Packages                                             
Ign [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/main Packages                                               
Ign [http://mirror.noreply.org](http://mirror.noreply.org) fiesty/main Sources                                                        
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/main Sources                                                     
Ign [http://mirror.noreply.org](http://mirror.noreply.org) fiesty/main Packages                                                       
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/multiverse Sources                                               
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/multiverse Packages                                              
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/main Packages                                            
Hit [http://mirror.noreply.org](http://mirror.noreply.org) stable/main Packages                                                       
Hit [http://mirror.noreply.org](http://mirror.noreply.org) stable/main Sources                                                        
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/restricted Packages                                      
Err [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/main Packages                                               
  404 Not Found
Err [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/main Packages                                               
  404 Not Found
Err [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/deb-src Packages                                            
  404 Not Found
Err [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/http://mirror.noreply.org/pub/tor Packages                  
  404 Not Found
Err [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/Fiesty Packages                                             
  404 Not Found
Err [http://mirror.noreply.org](http://mirror.noreply.org) <DISTRIBUTION>/main Packages                                               
  404 Not Found
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/universe Packages                                        
Err [http://mirror.noreply.org](http://mirror.noreply.org) fiesty/main Sources                                                        
  404 Not Found
Err [http://mirror.noreply.org](http://mirror.noreply.org) fiesty/main Packages                                                       
  404 Not Found
Ign [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Packages                                                  
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/main Sources                                             
Get:17 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Packages [50.0kB]                                      
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release [44.6kB]                                       
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/restricted Sources                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources                       
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages [14B]                               
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages [65.9kB]                                  
Ign [http://http.us.debian.org](http://http.us.debian.org) testing Release                                                            
Get:21 [http://http.us.debian.org](http://http.us.debian.org) testing/main Packages [4701kB]                                          
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages [8614B]                             
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages [14.9kB]                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages                                         
Get:24 [http://http.us.debian.org](http://http.us.debian.org) testing/contrib Packages [68.4kB]                                       
Hit [http://http.us.debian.org](http://http.us.debian.org) testing/non-free Packages                                                  
Get:25 [http://http.us.debian.org](http://http.us.debian.org) testing/main Sources [1349kB]                                           
Get:26 [http://http.us.debian.org](http://http.us.debian.org) testing/contrib Sources [21.8kB]                                        
Hit [http://http.us.debian.org](http://http.us.debian.org) testing/non-free Sources                                                   
Fetched 6403kB in 40m34s (2631B/s)
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing tla-buildpackage (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/http.us.debian.org_debian_dists_testing_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
root@cjays:/home/cjay# sudo aptitude remove synaptic
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing tla-buildpackage (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/http.us.debian.org_debian_dists_testing_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing tla-buildpackage (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/http.us.debian.org_debian_dists_testing_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
root@cjays:/home/cjay# sudo aptitude install synaptic
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing tla-buildpackage (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/http.us.debian.org_debian_dists_testing_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing tla-buildpackage (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/http.us.debian.org_debian_dists_testing_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
root@cjays:/home/cjay#

---

