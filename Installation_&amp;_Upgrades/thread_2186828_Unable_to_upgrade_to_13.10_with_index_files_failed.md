---
title: "Unable to upgrade to 13.10 with index files failed to download"
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by its_me_rense on 2013-11-09
I&#7743; trying to upgrade from 13.04 to 13.10, but I get an error.

```
Genegeerd cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty Release.gpg
Genegeerd cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty Release
Fout cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main i386 Packages
  Om deze APT deze CD te laten herkennen kunt u best apt-cdrom gebruiken. 'apt-get update' is niet in staat om nieuwe CDs toe te voegen
Fout cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted i386 Packages
  Om deze APT deze CD te laten herkennen kunt u best apt-cdrom gebruiken. 'apt-get update' is niet in staat om nieuwe CDs toe te voegen
Genegeerd cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-nl_NL
Genegeerd cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-nl
Genegeerd cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en
Genegeerd cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-nl_NL
Genegeerd cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-nl
Genegeerd cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                            
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring Release.gpg                        
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                          
Geraakt [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                         
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring Release.gpg                    
Geraakt [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg                       
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates Release.gpg            
Geraakt [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates Release.gpg                
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed Release.gpg               
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                              
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports Release.gpg             
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring Release                            
Geraakt [http://archive.canonical.com](http://archive.canonical.com) natty Release                             
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security Release.gpg           
Geraakt [http://archive.canonical.com](http://archive.canonical.com) raring Release                            
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates Release                    
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring Release                        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed Release                   
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates Release                
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports Release                 
Ophalen:1 [http://linux.dropbox.com](http://linux.dropbox.com) quantal Release.gpg [489 B]                 
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security Release               
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                           
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                     
Geraakt [http://repository.spotify.com](http://repository.spotify.com) stable Release                           
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/main Sources                       
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/universe Sources                   
Geraakt [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                     
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/multiverse Sources                 
Geraakt [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages               
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/restricted Sources                 
Ophalen:2 [http://linux.dropbox.com](http://linux.dropbox.com) quantal Release [2603 B]                    
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/main i386 Packages                 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/universe i386 Packages             
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/multiverse i386 Packages           
Geraakt [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources                    
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/restricted i386 Packages           
Geraakt [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages            
Geraakt [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages              
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/main Translation-nl                
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/main Translation-en                
Ophalen:3 [http://linux.dropbox.com](http://linux.dropbox.com) quantal/main Sources [409 B]                
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/multiverse Translation-nl          
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/multiverse Translation-en          
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-nl_NL               
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-nl                  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/restricted Translation-nl          
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/restricted Translation-en          
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                  
Fout [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                              
  404  Not Found
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/universe Translation-nl            
Ophalen:4 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B]       
Ophalen:5 [http://linux.dropbox.com](http://linux.dropbox.com) quantal/main i386 Packages [1585 B]         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/universe Translation-en            
Fout [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                        
  404  Not Found
Ophalen:6 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40,8 kB]         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/main i386 Packages         
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-nl_NL               
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/multiverse i386 Packages   
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-nl                  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/restricted i386 Packages   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/universe i386 Packages     
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                  
Genegeerd [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-nl_NL      
Ophalen:7 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [132 kB]
Genegeerd [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-nl         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/main Translation-en        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/multiverse Translation-en  
Genegeerd [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en         
Ophalen:8 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3864 B]
Ophalen:9 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Ophalen:10 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [44,6 kB]
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/restricted Translation-en  
Genegeerd [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-nl_NL         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/universe Translation-en    
Genegeerd [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-nl            
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/main i386 Packages        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/multiverse i386 Packages  
Genegeerd [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en            
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/restricted i386 Packages  
Genegeerd [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-nl_NL        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/universe i386 Packages    
Genegeerd [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-nl           
Genegeerd [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en           
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/main Translation-nl       
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/main Translation-en       
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/multiverse Translation-nl 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/multiverse Translation-en 
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en     
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/restricted Translation-nl 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/restricted Translation-en 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/universe Translation-nl   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/universe Translation-en   
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main Sources            
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted Sources      
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe Sources        
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse Sources      
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main i386 Packages      
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-nl_NL    
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted i386 Packages
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-nl       
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-nl_NL
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-nl 
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe i386 Packages  
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-nl_NL
Geraakt [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse i386 Packages
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-nl 
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-nl_NL
Genegeerd [http://linux.dropbox.com](http://linux.dropbox.com) quantal/main Translation-nl_NL              
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-nl   
Genegeerd [http://linux.dropbox.com](http://linux.dropbox.com) quantal/main Translation-nl                 
Genegeerd [http://linux.dropbox.com](http://linux.dropbox.com) quantal/main Translation-en                 
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/main Translation-nl_NL           
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/multiverse Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/restricted Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring/universe Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/main Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/main Translation-nl
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/multiverse Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/multiverse Translation-nl
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/restricted Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/restricted Translation-nl
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/universe Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-updates/universe Translation-nl  
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/main Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/multiverse Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/restricted Translation-nl_NL
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) raring-proposed/universe Translation-nl_NL
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/universe Sources                    
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/main Sources                        
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/restricted Sources                  
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/multiverse Sources                  
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/main i386 Packages                  
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/restricted i386 Packages          
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/multiverse i386 Packages
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/universe i386 Packages
  404  Not Found
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/main Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/main Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/main Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/multiverse Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/multiverse Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/multiverse Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/restricted Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/restricted Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/restricted Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/universe Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/universe Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring/universe Translation-en
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/universe Sources
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/main Sources
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/restricted Sources
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/multiverse Sources
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/main i386 Packages
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/restricted i386 Packages
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/multiverse i386 Packages
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/universe i386 Packages
  404  Not Found
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/main Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/main Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/main Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/multiverse Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/multiverse Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/multiverse Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/restricted Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/restricted Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/restricted Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/universe Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/universe Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-updates/universe Translation-en
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Sources
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Sources
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Sources
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Sources
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main i386 Packages
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted i386 Packages
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse i386 Packages
  404  Not Found
Fout [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe i386 Packages
  404  Not Found
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted Translation-en
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe Translation-nl_NL
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe Translation-nl
Genegeerd [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe Translation-en
227 kB opgehaald in 15s (14,6 kB/s)
W: Ophalen van cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages is mislukt  Om deze APT deze CD te laten herkennen kunt u best apt-cdrom gebruiken. 'apt-get update' is niet in staat om nieuwe CDs toe te voegen

W: Ophalen van cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages is mislukt  Om deze APT deze CD te laten herkennen kunt u best apt-cdrom gebruiken. 'apt-get update' is niet in staat om nieuwe CDs toe te voegen

W: Ophalen van [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/raring/main/source/Sources](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/raring/main/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/raring/main/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring/universe/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring/universe/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring/main/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages) is mislukt  404  Not Found

W: Ophalen van [http://old-releases.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages) is mislukt  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Can anybody help me out here?
```

---

### Post by coffeecat on 2013-11-09
You have a lot of sources that are either creating problems, or have the potential to do so. The ones that need to be disabled are:

[list][*]All those related to natty. Natty (11.04) is past end-of-life.
[*]PPA and 3rd party repositories. They can cause problems in an upgrade.
[*]I can see linux.dropbox.com for quantal. It's best if you disable that.
[*]There are many lines referring to the old-releases repository for Raring. How did they get there? Old-releases is for - well - old releases. They don't exist for 13.04 (raring) which is why you get 404s for those. They need disabling.
[*]**Raring-proposed**. Raring proposed should only be enabled by experienced people wishing to help quality control test packages before they are put into the main repositories. Proposed packages do not all survive testing and have the potential to break your system. You need to disable all instances of raring-proposed. I don't wish to be unkind, but if you don't have the experience to see what has gone wrong here, you are best not using the proposed repository.[/list]

Disable all repositories that fall under the above categories, by:

Software Centre -> Edit Menu -> Software Sources. Look under these tabs: Ubuntu Software for the cdrom sources; Other Software; and Updates for raring-proposed. Untick any boxes that correspond with the problem sources.

or

Synaptic (if you have it installed) -> Setting Menu -> Repositories, and then as above.

or

Software Updater -> Settings Button, and then as above.

Run this command after you have unchecked all the problem repositories:

```
sudo apt-get update
```

Please be warned that with so many potential problem sources, your upgrade could go wrong. Back up all important data before you try to upgrade.

---

### Post by its_me_rense on 2013-11-09
The upgrade is started now. Thanks alot!

By the way, I use Ubuntu just for fooling around. It doesn't really matter if the upgrade will fail. I like to test things on Ubuntu :) But thanks alot for the help! I will let you know how the upgrade went.

---

### Post by its_me_rense on 2013-11-09
Upgrade is ready and it works fine. Thanks again for the help!

---

