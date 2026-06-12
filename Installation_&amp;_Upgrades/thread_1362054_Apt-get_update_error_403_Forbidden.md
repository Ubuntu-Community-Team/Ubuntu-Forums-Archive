---
title: "Apt-get update error 403 Forbidden"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Ultimate_goblin on 2009-12-22
Hi everyone!
I want to upgrade Ubuntu. I read on the site that it's recommended to have Intrepid fully updated before upgrading. So I ran the apt-get update command but all it's happening it's a 403 error type. This is the output:
```
Ign http://giano.com.dist.unige.it jaunty Release.gpg
Ign http://archive.canonical.com jaunty Release.gpg  
Ign http://giano.com.dist.unige.it jaunty/main Translation-en_US
Ign http://archive.canonical.com jaunty/partner Translation-en_US
Ign http://giano.com.dist.unige.it jaunty/restricted Translation-en_US
Ign http://archive.canonical.com jaunty Release                       
Ign http://giano.com.dist.unige.it jaunty/universe Translation-en_US  
Ign http://archive.canonical.com jaunty/partner Packages              
Ign http://giano.com.dist.unige.it jaunty/multiverse Translation-en_US
Ign http://archive.canonical.com jaunty/partner Sources               
Ign http://giano.com.dist.unige.it jaunty-updates Release.gpg         
Ign http://archive.canonical.com jaunty/partner Packages              
Ign http://giano.com.dist.unige.it jaunty-updates/main Translation-en_US
Ign http://archive.canonical.com jaunty/partner Sources                 
Ign http://giano.com.dist.unige.it jaunty-updates/restricted Translation-en_US
Err http://archive.canonical.com jaunty/partner Packages                      
  403 Forbidden [IP: 193.1.172.104 8484]                                      
Ign http://giano.com.dist.unige.it jaunty-updates/universe Translation-en_US  
Err http://archive.canonical.com jaunty/partner Sources                       
  403 Forbidden [IP: 193.1.172.104 8484]                                      
Ign http://giano.com.dist.unige.it jaunty-updates/multiverse Translation-en_US
Ign http://giano.com.dist.unige.it jaunty-security Release.gpg                
Ign http://giano.com.dist.unige.it jaunty-security/main Translation-en_US     
Ign http://giano.com.dist.unige.it jaunty-security/restricted Translation-en_US
Ign http://giano.com.dist.unige.it jaunty-security/universe Translation-en_US  
Ign http://giano.com.dist.unige.it jaunty-security/multiverse Translation-en_US
Ign http://giano.com.dist.unige.it jaunty Release                              
Ign http://giano.com.dist.unige.it jaunty-updates Release                      
Ign http://giano.com.dist.unige.it jaunty-security Release                     
Ign http://giano.com.dist.unige.it jaunty/main Packages                        
Ign http://giano.com.dist.unige.it jaunty/restricted Packages                  
Ign http://giano.com.dist.unige.it jaunty/main Sources                         
Ign http://giano.com.dist.unige.it jaunty/restricted Sources                   
Ign http://giano.com.dist.unige.it jaunty/universe Packages                    
Ign http://giano.com.dist.unige.it jaunty/universe Sources                     
Ign http://giano.com.dist.unige.it jaunty/multiverse Packages                  
Ign http://giano.com.dist.unige.it jaunty/multiverse Sources                   
Ign http://giano.com.dist.unige.it jaunty-updates/main Packages                
Ign http://giano.com.dist.unige.it jaunty-updates/restricted Packages          
Ign http://giano.com.dist.unige.it jaunty-updates/main Sources                 
Ign http://giano.com.dist.unige.it jaunty-updates/restricted Sources           
Ign http://giano.com.dist.unige.it jaunty-updates/universe Packages            
Ign http://giano.com.dist.unige.it jaunty-updates/universe Sources             
Ign http://giano.com.dist.unige.it jaunty-updates/multiverse Packages          
Ign http://giano.com.dist.unige.it jaunty-updates/multiverse Sources           
Ign http://giano.com.dist.unige.it jaunty-security/main Packages               
Ign http://giano.com.dist.unige.it jaunty-security/restricted Packages         
Ign http://giano.com.dist.unige.it jaunty-security/main Sources                
Ign http://giano.com.dist.unige.it jaunty-security/restricted Sources          
Ign http://giano.com.dist.unige.it jaunty-security/universe Packages           
Ign http://giano.com.dist.unige.it jaunty-security/universe Sources            
Ign http://giano.com.dist.unige.it jaunty-security/multiverse Packages         
Ign http://giano.com.dist.unige.it jaunty-security/multiverse Sources          
Ign http://giano.com.dist.unige.it jaunty/main Packages                        
Ign http://giano.com.dist.unige.it jaunty/restricted Packages                  
Ign http://giano.com.dist.unige.it jaunty/main Sources                         
Ign http://giano.com.dist.unige.it jaunty/restricted Sources                   
Ign http://giano.com.dist.unige.it jaunty/universe Packages                    
Ign http://giano.com.dist.unige.it jaunty/universe Sources                     
Ign http://giano.com.dist.unige.it jaunty/multiverse Packages                  
Ign http://giano.com.dist.unige.it jaunty/multiverse Sources                   
Ign http://giano.com.dist.unige.it jaunty-updates/main Packages                
Ign http://giano.com.dist.unige.it jaunty-updates/restricted Packages          
Ign http://giano.com.dist.unige.it jaunty-updates/main Sources                 
Ign http://giano.com.dist.unige.it jaunty-updates/restricted Sources           
Ign http://giano.com.dist.unige.it jaunty-updates/universe Packages            
Ign http://giano.com.dist.unige.it jaunty-updates/universe Sources             
Ign http://giano.com.dist.unige.it jaunty-updates/multiverse Packages          
Ign http://giano.com.dist.unige.it jaunty-updates/multiverse Sources           
Ign http://giano.com.dist.unige.it jaunty-security/main Packages               
Ign http://giano.com.dist.unige.it jaunty-security/restricted Packages         
Ign http://giano.com.dist.unige.it jaunty-security/main Sources                
Ign http://giano.com.dist.unige.it jaunty-security/restricted Sources          
Ign http://giano.com.dist.unige.it jaunty-security/universe Packages           
Ign http://giano.com.dist.unige.it jaunty-security/universe Sources            
Ign http://giano.com.dist.unige.it jaunty-security/multiverse Packages         
Ign http://giano.com.dist.unige.it jaunty-security/multiverse Sources          
Err http://giano.com.dist.unige.it jaunty/main Packages                        
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty/restricted Packages                  
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty/main Sources                         
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty/restricted Sources                   
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty/universe Packages                    
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty/universe Sources                     
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty/multiverse Packages                  
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty/multiverse Sources                   
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-updates/main Packages                
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-updates/restricted Packages          
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-updates/main Sources                 
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-updates/restricted Sources           
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-updates/universe Packages            
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-updates/universe Sources             
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-updates/multiverse Packages          
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-updates/multiverse Sources           
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-security/main Packages               
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-security/restricted Packages         
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-security/main Sources                
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-security/restricted Sources          
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-security/universe Packages           
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-security/universe Sources            
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-security/multiverse Packages         
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://giano.com.dist.unige.it jaunty-security/multiverse Sources          
  403 Forbidden [IP: 193.1.172.104 8484]                                       
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]                       

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                              

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]                        

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty/restricted/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]                  

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty/main/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                               

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty/restricted/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                         

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty/universe/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]                    

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty/universe/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                           

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]                  

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty/multiverse/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                         

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-updates/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]                

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-updates/restricted/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]          

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-updates/main/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                       

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-updates/restricted/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                 

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-updates/universe/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-updates/universe/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-updates/multiverse/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-updates/multiverse/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-security/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-security/restricted/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-security/main/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-security/restricted/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-security/universe/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-security/universe/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-security/multiverse/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/jaunty-security/multiverse/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I want to make clear this: I am NOT trying to upgrade to Karmic, I am just trying to update all my programs and everything. I saw somewhere that I can try to change the "http" string in the sources.list with the "ftp". I think I did it, but it didn't work.

Anyone? Please? :)

---

### Post by wojox on 2009-12-22
Can you change Server locations in System > Administration > Software Sources > Download from:

---

### Post by Ultimate_goblin on 2009-12-22
Yes, I can.

---

### Post by wojox on 2009-12-22
Okay and if you choose Server for <Your Country> and close and apply changes, does that help. I also noticed you said Intrepid but are using a fetching Jaunty packages?

---

### Post by Ultimate_goblin on 2009-12-22
Yes, it's true, I have Intrepid repositories... do you think I have to add new repositories? The server is the one of where I'm living, I clicked on "choose best server" and there it is. Even if I change it, same errors.

---

### Post by wojox on 2009-12-22
Go here and make a new sources.list for intrepid: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Ultimate_goblin on 2009-12-22
Did it!And I saw some very interesting repositories. I added them. But still... same error! 403 Forbidden: ```
Ign http://it.archive.ubuntu.com jaunty Release.gpg
Ign http://dl.google.com stable Release.gpg                                    
Ign http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.getdeb.net jaunty-getdeb Release.gpg                        
Ign http://download.skype.com stable Release.gpg                               
Ign http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://it.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://dl.google.com stable/non-free Translation-en_US                     
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Ign http://archive.getdeb.net jaunty-getdeb/games Translation-en_US            
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://it.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://archive.canonical.com jaunty Release                                
Ign http://archive.getdeb.net jaunty-getdeb Release                            
Ign http://download.skype.com stable Release                                   
Ign http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://it.archive.ubuntu.com jaunty-security Release.gpg                   
Ign http://archive.canonical.com jaunty/partner Packages                       
Ign http://archive.getdeb.net jaunty-getdeb/games Packages                     
Ign http://download.skype.com stable/non-free Packages                         
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://it.archive.ubuntu.com jaunty-security/main Translation-en_US        
Ign http://archive.canonical.com jaunty/partner Sources                        
Ign http://archive.getdeb.net jaunty-getdeb/games Packages                     
Ign http://download.skype.com stable/non-free Packages                         
Ign http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://it.archive.ubuntu.com jaunty-security/universe Translation-en_US    
Ign http://archive.canonical.com jaunty/partner Packages                       
Err http://archive.getdeb.net jaunty-getdeb/games Packages                     
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Err http://download.skype.com stable/non-free Packages                         
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://dl.google.com stable Release                                        
Ign http://it.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://archive.canonical.com jaunty/partner Sources                        
Ign http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://dl.google.com stable/non-free Packages                              
Ign http://it.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Err http://archive.canonical.com jaunty/partner Packages                       
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://dl.google.com stable/non-free Packages                              
Ign http://it.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Err http://archive.canonical.com jaunty/partner Sources                        
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Ign http://ppa.launchpad.net jaunty Release.gpg                                
Err http://dl.google.com stable/non-free Packages                              
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty-proposed Release.gpg                   
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://it.archive.ubuntu.com jaunty-proposed/main Translation-en_US        
Ign http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://it.archive.ubuntu.com jaunty-proposed/universe Translation-en_US    
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://it.archive.ubuntu.com jaunty Release                                
Ign http://ppa.launchpad.net jaunty Release                                    
Ign http://it.archive.ubuntu.com jaunty-security Release                       
Ign http://ppa.launchpad.net jaunty Release                                    
Ign http://it.archive.ubuntu.com jaunty-updates Release                        
Ign http://ppa.launchpad.net jaunty Release                                    
Ign http://it.archive.ubuntu.com jaunty-proposed Release                       
Ign http://ppa.launchpad.net jaunty Release                                    
Ign http://it.archive.ubuntu.com jaunty/main Packages                          
Ign http://ppa.launchpad.net jaunty Release                                    
Ign http://it.archive.ubuntu.com jaunty/universe Packages                      
Ign http://ppa.launchpad.net jaunty Release                                    
Ign http://it.archive.ubuntu.com jaunty/main Sources                           
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://it.archive.ubuntu.com jaunty/universe Sources                       
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://it.archive.ubuntu.com jaunty-security/main Packages                 
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://it.archive.ubuntu.com jaunty-security/universe Packages             
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://it.archive.ubuntu.com jaunty-security/main Sources                  
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://it.archive.ubuntu.com jaunty-security/universe Sources              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://it.archive.ubuntu.com jaunty-updates/main Packages                  
Ign http://ppa.launchpad.net jaunty/main Sources                               
Ign http://it.archive.ubuntu.com jaunty-updates/universe Packages              
Err http://ppa.launchpad.net jaunty/main Packages                              
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty-updates/main Sources                   
Err http://ppa.launchpad.net jaunty/main Sources                               
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty-updates/universe Sources               
Err http://ppa.launchpad.net jaunty/main Packages                              
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty-proposed/main Packages                 
Err http://ppa.launchpad.net jaunty/main Sources                               
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty-proposed/universe Packages             
Err http://ppa.launchpad.net jaunty/main Packages                              
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty-proposed/main Sources                  
Err http://ppa.launchpad.net jaunty/main Sources                               
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty-proposed/universe Sources              
Err http://ppa.launchpad.net jaunty/main Packages                              
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty/main Packages                          
Err http://ppa.launchpad.net jaunty/main Sources                               
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty/universe Packages                      
Err http://ppa.launchpad.net jaunty/main Packages                              
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty/main Sources                           
Err http://ppa.launchpad.net jaunty/main Sources                               
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty/universe Sources                       
Err http://ppa.launchpad.net jaunty/main Packages                              
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty-security/main Packages                 
Err http://ppa.launchpad.net jaunty/main Sources                               
  403 Forbidden [IP: 193.1.172.188 8484]                                       
Ign http://it.archive.ubuntu.com jaunty-security/universe Packages             
Ign http://it.archive.ubuntu.com jaunty-security/main Sources                  
Ign http://it.archive.ubuntu.com jaunty-security/universe Sources              
Ign http://it.archive.ubuntu.com jaunty-updates/main Packages                  
Ign http://it.archive.ubuntu.com jaunty-updates/universe Packages              
Ign http://it.archive.ubuntu.com jaunty-updates/main Sources                   
Ign http://it.archive.ubuntu.com jaunty-updates/universe Sources               
Ign http://it.archive.ubuntu.com jaunty-proposed/main Packages                 
Ign http://it.archive.ubuntu.com jaunty-proposed/universe Packages             
Ign http://it.archive.ubuntu.com jaunty-proposed/main Sources                  
Ign http://it.archive.ubuntu.com jaunty-proposed/universe Sources              
Err http://it.archive.ubuntu.com jaunty/main Packages                          
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty/universe Packages                      
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty/main Sources                           
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty/universe Sources                       
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-security/main Packages                 
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-security/universe Packages             
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-security/main Sources                  
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-security/universe Sources              
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-updates/main Packages                  
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-updates/universe Packages              
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-updates/main Sources                   
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-updates/universe Sources               
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-proposed/main Packages                 
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-proposed/universe Packages             
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-proposed/main Sources                  
  403 Forbidden [IP: 193.1.172.104 8484]                                       
Err http://it.archive.ubuntu.com jaunty-proposed/universe Sources              
  403 Forbidden [IP: 193.1.172.104 8484]                                       
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/jaunty-getdeb/games/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.188 8484]                     

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]             

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]                       

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                              

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/non-free/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.188 8484]                           

W: Failed to fetch http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu/dists/jaunty/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.188 8484]         

W: Failed to fetch http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu/dists/jaunty/main/source/Sources  403 Forbidden [IP: 193.1.172.188 8484]                

W: Failed to fetch http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/dists/jaunty/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.188 8484]              

W: Failed to fetch http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/dists/jaunty/main/source/Sources  403 Forbidden [IP: 193.1.172.188 8484]                     

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/jaunty/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.188 8484]              

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/jaunty/main/source/Sources  403 Forbidden [IP: 193.1.172.188 8484]                     

W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/jaunty/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.188 8484]        

W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/jaunty/main/source/Sources  403 Forbidden [IP: 193.1.172.188 8484]               

W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.188 8484]                   

W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/main/source/Sources  403 Forbidden [IP: 193.1.172.188 8484]                          

W: Failed to fetch http://ppa.launchpad.net/smaioli/ppa/ubuntu/dists/jaunty/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.188 8484]                  

W: Failed to fetch http://ppa.launchpad.net/smaioli/ppa/ubuntu/dists/jaunty/main/source/Sources  403 Forbidden [IP: 193.1.172.188 8484]                         

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]                          

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]                      

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                                 

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]                             

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/main/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/universe/binary-amd64/Packages  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/main/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/universe/source/Sources  403 Forbidden [IP: 193.1.172.104 8484]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
What do I have to do now? Important note: I run under no proxies, but the terminal says "waiting for headers" and then "connecting to proxy.ucd.ie" and then he says something like "fail", I think.
Last year, in fact, I was in a college and I had a proxy. Do I have to "remove" this proxy? I went to Synaptic>Settings>Preferences>Network and I did "direct connection to the internet" but it appears not to work...
Hmm, interesting case!! Proxy.ucd.ie seems to be hiding somewhere...

---

### Post by Ultimate_goblin on 2009-12-23
I edited the last post of mine. I think there is some interesting information for people that can handle them. I'm referring to the "connecting to proxy.ucd.ie" part.

---

