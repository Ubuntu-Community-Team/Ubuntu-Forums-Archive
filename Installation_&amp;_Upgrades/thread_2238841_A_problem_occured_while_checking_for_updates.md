---
title: "A problem occured while checking for updates"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by kennethdorman on 2014-08-10
What am I doing wrong here? Software updater as well as Synaptic quits randomly all the time. Running 14.04 LTS, Sony Viao VPCEE31FX, 6GB RAM, 256 Samsung Evo 840 SSD. Here is what I get from a sudo apt-get update:
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
root@hacker-4-life:~# sudo aptitude update && sudo aptitude safe-upgrade
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                 
Get: 1 [http://http.kali.org](http://http.kali.org) kali InRelease [22.0 kB]                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                       
Ign [http://http.kali.org](http://http.kali.org) kali InRelease                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages        
Get: 2 [http://security.kali.org](http://security.kali.org) kali/updates InRelease [11.8 kB]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                         
Ign [http://security.kali.org](http://security.kali.org) kali/updates InRelease                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages          
Ign [http://http.kali.org](http://http.kali.org) kali/main Sources/DiffIndex                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                                
Ign [http://security.kali.org](http://security.kali.org) kali/updates/main Sources/DiffIndex                
Ign [http://http.kali.org](http://http.kali.org) kali/non-free Sources/DiffIndex                        
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages         
Ign [http://security.kali.org](http://security.kali.org) kali/updates/contrib Sources/DiffIndex             
Ign [http://http.kali.org](http://http.kali.org) kali/contrib Sources/DiffIndex                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages               
Get: 4 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                        
Ign [http://security.kali.org](http://security.kali.org) kali/updates/non-free Sources/DiffIndex            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en        
Get: 5 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse amd64 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                    
Hit [http://http.kali.org](http://http.kali.org) kali/main Sources                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en          
Hit [http://security.kali.org](http://security.kali.org) kali/updates/main Sources                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources              
Hit [http://http.kali.org](http://http.kali.org) kali/non-free Sources                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages       
Hit [http://security.kali.org](http://security.kali.org) kali/updates/contrib Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages       
Hit [http://http.kali.org](http://http.kali.org) kali/contrib Sources                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                      
Hit [http://security.kali.org](http://security.kali.org) kali/updates/non-free Sources                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources/DiffIndex                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                         
Fetched 34.8 kB in 7s (4,567 B/s)                                               
W: GPG error: [http://http.kali.org](http://http.kali.org) kali InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6
W: GPG error: [http://security.kali.org](http://security.kali.org) kali/updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 680E1A5A78A7ABE1
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9D6E2FB47AC15133
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9D6E2FB47AC15133
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/multiverse amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages)
root@hacker-4-life:~# clear

root@hacker-4-life:~# sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg [933 B]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release [59.7 kB]               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Get:5 [http://security.kali.org](http://security.kali.org) kali/updates InRelease [11.8 kB]                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [59.7 kB]            
Ign [http://security.kali.org](http://security.kali.org) kali/updates InRelease                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Get:7 [http://http.kali.org](http://http.kali.org) kali InRelease [22.0 kB]                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Ign [http://security.kali.org](http://security.kali.org) kali/updates/main Sources/DiffIndex               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Ign [http://http.kali.org](http://http.kali.org) kali InRelease                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages                 
Ign [http://security.kali.org](http://security.kali.org) kali/updates/contrib Sources/DiffIndex            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [59.7 kB]          
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://http.kali.org](http://http.kali.org) kali/main Sources/DiffIndex                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Ign [http://security.kali.org](http://security.kali.org) kali/updates/non-free Sources/DiffIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Ign [http://http.kali.org](http://http.kali.org) kali/non-free Sources/DiffIndex                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Ign [http://http.kali.org](http://http.kali.org) kali/contrib Sources/DiffIndex                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages [284 kB]   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://security.kali.org](http://security.kali.org) kali/updates/main Sources                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Hit [http://http.kali.org](http://http.kali.org) kali/main Sources                                     
Hit [http://security.kali.org](http://security.kali.org) kali/updates/contrib Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [105 kB]       
Hit [http://http.kali.org](http://http.kali.org) kali/non-free Sources                                 
Hit [http://security.kali.org](http://security.kali.org) kali/updates/non-free Sources                     
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages [5,820 B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages [168 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://http.kali.org](http://http.kali.org) kali/contrib Sources                                  
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [1,408 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources/DiffIndex                     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [67.1 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages/DiffIndex              
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [7,381 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [2,686 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [279 kB]    
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [284 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages/DiffIndex               
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [168 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [5,820 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [168 kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,598 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources/DiffIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [7,381 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en         
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [279 kB] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages/DiffIndex               
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [168 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,598 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US           
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [2,859 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [14 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US              
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [11.0 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US                
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [768 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [4,277 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [14 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [14.0 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [619 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [4,261 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                        
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                 
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [14.0 kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [619 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Fetched 2,297 kB in 7s (305 kB/s)                                              
Reading package lists... Done
W: GPG error: [http://security.kali.org](http://security.kali.org) kali/updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6
W: GPG error: [http://http.kali.org](http://http.kali.org) kali InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 680E1A5A78A7ABE1
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9D6E2FB47AC15133
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9D6E2FB47AC15133
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/multiverse amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages)

---

### Post by kansasnoob on 2014-08-10
Seems to be vomiting over the kali linux sources and you apparently have some duplicates in your sources.list:

```
W: GPG error: http://http.kali.org kali InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6
W: GPG error: http://security.kali.org kali/updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 680E1A5A78A7ABE1
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9D6E2FB47AC15133
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9D6E2FB47AC15133
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages)
```

In other words, you broke it!

---

### Post by kennethdorman on 2014-08-10
Is it possible to recover from this issue? If so, what would I need to do to rectifiy the vomiting problem? Any help is greatly appreciated. Thanks

---

### Post by grahammechanical on 2014-08-10
You are running trusty (14.04) but you also have PPAs for precise (12.04). That can cause problems. Go to system settings>software and updates and disable PPAs and see what other software sources are listed and may be remove them.

The question is, does this stop the system from being updated?

Regards.

---

### Post by kennethdorman on 2014-08-10
> **grahammechanical said:**
> You are running trusty (14.04) but you also have PPAs for precise (12.04). That can cause problems. Go to system settings>software and updates and disable PPAs and see what other software sources are listed and may be remove them.

The question is, does this stop the system from being updated?

Regards.

This worked. I was trying to install Kali tools and that is what broke the OS. Is there any good guide to do this? (obviously the one I followed was no good)

---

