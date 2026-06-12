---
title: "Error when updating/installing the system and apps"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by GisliKarl on 2011-11-14
I have been having this problem for some time now and I still haven't found a solution. Everytime I try to update or install new apps I get an error. When I run sudo apt-get update into the terminal all I get is this. Does anyone know how to fix this problem? I am running Ubuntu 11.10 64-bit

> gislikarl@gislikarl-ubuntu:~$ sudo apt-get update
[sudo] password for gislikarl: 
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Sources                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages/DiffIndex             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free amd64 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free amd64 Packages                
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates InRelease                         
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports InRelease                       
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security InRelease              
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric Release.gpg                               
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates Release.gpg                       
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports Release.gpg                     
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security Release.gpg                      
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric Release                                   
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates Release                           
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security Release                          
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/main Sources                              
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/restricted Sources                        
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/universe Sources                          
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/multiverse Sources                        
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/main amd64 Packages                       
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/restricted amd64 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en             
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/universe amd64 Packages                   
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/multiverse amd64 Packages                 
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/main i386 Packages                        
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/restricted i386 Packages                  
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/universe i386 Packages          
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/multiverse i386 Packages        
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/main TranslationIndex                     
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/multiverse TranslationIndex               
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/restricted TranslationIndex     
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/universe TranslationIndex                 
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/main Sources                      
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/restricted Sources                
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/universe Sources                  
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/multiverse Sources                
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/main amd64 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US          
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/restricted amd64 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/universe amd64 Packages           
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/multiverse amd64 Packages         
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/main i386 Packages                
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/restricted i386 Packages          
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/universe i386 Packages            
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/multiverse i386 Packages          
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/main TranslationIndex   
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/multiverse TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/restricted TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/universe TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/main Sources          
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/restricted Sources    
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/universe Sources      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en             
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/multiverse Sources    
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/main amd64 Packages   
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/restricted amd64 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/universe amd64 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/multiverse amd64 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/main i386 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/restricted i386 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/universe i386 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/multiverse i386 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/main TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/multiverse TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/restricted TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/universe TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/main Sources
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/restricted Sources
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/universe Sources
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/multiverse Sources
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/main amd64 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/restricted amd64 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/universe amd64 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/multiverse amd64 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/main i386 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/restricted i386 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/universe i386 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/multiverse i386 Packages
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/main TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/multiverse TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/restricted TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/universe TranslationIndex
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/main Translation-en
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/multiverse Translation-en
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/restricted Translation-en       
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric/universe Translation-en         
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/main Translation-en     
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/multiverse Translation-en
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/restricted Translation-en
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates/universe Translation-en 
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/main Translation-en   
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/multiverse Translation-en
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/restricted Translation-en
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports/universe Translation-en
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/main Translation-en    
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/multiverse Translation-en
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/restricted Translation-en
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/universe Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en                 
Get:6 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                                                                                                                                                                 
Get:7 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,198 B]                                                                                                                                                     
Get:8 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,208 B]                                                                                                                                                      
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                                                                               
Get:9 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [764 B]                                                                                                                                                       
Get:10 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [779 B]                                                                                                                                                       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                                                                               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                                                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                                                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                                                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                                                                                                 
Fetched 7,671 B in 17s (442 B/s)                                                                                                                                                                                    
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7815DD7DC69E8E92
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
gislikarl@gislikarl-ubuntu:~$

---

### Post by dino99 on 2011-11-14
open synaptic and use only genuine Oneiric archives from "main" server, comment out everything else, then update.

---

### Post by ubume2 on 2011-11-14
> **dino99 said:**
> open synaptic and use only genuine Oneiric archives from "main" server, comment out everything else, then update.

ditto

Was this a fresh install of 11.10 or an upgrade?

Possibly you missed a critical update somewhere along the line.

---

### Post by raja.genupula on 2011-11-14
1....update manager --> settings --> other software --> uncheck all the CD-ROM check box's.

2 open your terminal and the do this
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7815DD7DC69E8E92
```
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
C2518248EEA14886
```

---

### Post by GisliKarl on 2011-11-14
I removed everything but the default ubuntu sources in software  sources and changed to the main server and fixed the GPG errors but I still can't update properly. Only received about 4 updates. Now after putting all software sources back on I receive this in the terminal. 

>  gislikarl@gislikarl-ubuntu:~$ sudo apt-get update
[sudo] password for gislikarl: 
Sorry, try again.
[sudo] password for gislikarl: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease [7,092 B]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                       
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg [198 B]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg                     
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,742 B]                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,766 B]                       
Get:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Sources [3,293 B]              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages                       
Get:11 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Sources [4,361 B]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,743 B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources                 
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [8,242 B]                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe amd64 Packages          
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages [13.7 kB]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages               
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [13.7 kB]           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Sources                   
Get:16 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free amd64 Packages [3,257 B]       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [637 B]                   
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages [454 B]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Sources               
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [453 B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main amd64 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted amd64 Packages      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex    
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [911 B]                   
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages [763 B]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources                
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [763 B]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main amd64 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:23 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free amd64 Packages [6,104 B]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en         
Get:24 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages [3,262 B]        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Get:25 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages [6,689 B]    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                      
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                     
Get:26 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Get:27 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                           
Get:28 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]
Get:29 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_US                   
Get:30 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,198 B]                                                                                                                                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en                                                                                                                                                         
Get:31 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,208 B]                                                                                                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                                                                               
Get:32 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [764 B]                                                                                                                                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_US                                                                                                                                                  
Get:33 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [779 B]                                                                                                                                                       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                                                                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en                                                                                                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                                                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                                                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                                                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                                                                                                 
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                                                                                                                                                           
Get:34 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189 B]                                                                                                                                                              
Get:35 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189 B]                                                                                                                                                              
Get:36 [http://deb.opera.com](http://deb.opera.com) stable Release [633 B]                                                                                                                                                                  
Get:37 [http://deb.opera.com](http://deb.opera.com) stable Release [633 B]                                                                                                                                                                  
Get:38 [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages [848 B]                                                                                                                                                  
Get:39 [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages [853 B]                                                                                                                                                   
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                                                                                                                                                           
Get:40 [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages [844 B]                                                                                                                                                  
Get:41 [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages [849 B]                                                                                                                                                   
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                                                                                                                                                           
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                                                                                                                                                          
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                                                                                                                                                             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                                                                                                                                                          
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                                                                                                                                                             
Fetched 117 kB in 18s (6,426 B/s)                                                                                                                                                                                   
W: Failed to fetch [http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
gislikarl@gislikarl-ubuntu:~$ 

---

### Post by raja.genupula on 2011-11-15
update manager -> settings -> 1st tab change your server to other best mirror and try again .

---

### Post by GisliKarl on 2011-11-15
> **raja.genupula said:**
> update manager -> settings -> 1st tab change your server to other best mirror and try again .
I changed from the main server to USA server and got this error 

> W:A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG 7815DD7DC69E8E92 Launchpad PPA for Rémi Rérolle
, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: Unknown error executing gpgv, W:GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease: File /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-backports_InRelease doesn't start with a clearsigned message, W:GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security InRelease: File /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-security_InRelease doesn't start with a clearsigned message, E:GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: NODATA 1 NODATA 2

---

### Post by raja.genupula on 2011-11-15
```

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```
all the best.

---

### Post by GisliKarl on 2011-11-15
> **raja.genupula said:**
> ```

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```
all the best.
after I did this and fired up the update manager it asks me to do a partial upgrade which then quits after it opens :(

---

### Post by raja.genupula on 2011-11-15
> **GisliKarl said:**
> after I did this and fired up the update manager it asks me to do a partial upgrade which then quits after it opens :(

No no don't go for partial upgrade that will make your system as unstable.'

---

### Post by GisliKarl on 2011-11-16
I found out why this problem occurs. I opened all the files inside the lists folder and it turns out that the contents of each and every file isn't the way it should be so that's the good news. The bad news is I don't know how to get these files back to their normal way. Does anyone know?

---

