---
title: "Updates in Ubuntu 11.04 won't work!"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by NewReformist on 2011-04-30
**So I recently installed the new Ubuntu 11.04, and at first updates would work, now I get this message in update center:**

W:Failed to fetch [http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

**Using the sudo apt update through terminal this is what I get:**

Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Bra [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Bra [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty InRelease                               
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates InRelease                       
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Bra [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Bra [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty Release.gpg                             
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Bra [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates Release.gpg                     
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Bra [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty Release                                 
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Bra [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages              
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages        
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Bra [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/main Sources                            
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/restricted Sources                      
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/universe Sources                        
Bra [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Bra [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/multiverse Sources                      
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/main amd64 Packages                     
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/restricted amd64 Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/universe amd64 Packages                 
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/multiverse TranslationIndex             
Bra [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/universe TranslationIndex               
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/main Sources                    
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/restricted Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/universe Sources                
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/multiverse Sources              
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/main amd64 Packages             
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/universe amd64 Packages         
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/multiverse amd64 Packages       
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/main Translation-sv                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-sv_SE               
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/multiverse Translation-sv               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-sv                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/restricted Translation-sv               
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/universe Translation-sv                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-sv_SE           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-sv              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-sv_SE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-sv 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-sv_SE                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-sv_SE     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-sv        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-sv_SE       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-sv                         
Fel [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Fel [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                  
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-sv   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-sv_SE               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-sv
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-sv_SE
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-sv
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-sv_SE
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-sv
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/main Translation-sv_SE
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/main Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/multiverse Translation-sv_SE
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/restricted Translation-sv_SE
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/universe Translation-sv_SE
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty/universe Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/main Translation-sv_SE
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/main Translation-sv
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/multiverse Translation-sv_SE
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/multiverse Translation-sv
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/restricted Translation-sv_SE
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/restricted Translation-sv
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/universe Translation-sv_SE
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/universe Translation-sv
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) natty-updates/universe Translation-en
W: Misslyckades med att hämta [http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Misslyckades med att hämta [http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Några indexfiler gick inte att hämta. De kommer att ignoreras eller så används de gamla istället.

[I]
NOTE : I have my system in Swedish but "Misslyckades med att hämta" is the same as "failed to fetch"[/I].
[B]
When trying to update Synaptic it's the same:[/B]

W:Failed to fetch [http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Now for reason I could not find my first thread written about this issue. I'm sorry but I am new to this forum so sorry for double posting. I added more info to this new one though.

Can someone help out? I'm thinking maybe re-installing it might work? I can't use a system which is unable to update.

---

### Post by Erafo on 2011-05-02
Yeah, that happened to me too...

---

