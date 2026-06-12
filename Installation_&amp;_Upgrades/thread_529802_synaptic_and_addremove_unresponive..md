---
title: "synaptic and add/remove unresponive."
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by peterson2k4 on 2007-08-19
when I try to access synaptic package manager it asks for my password and after I put it in the box goes away but, the screen still has that gray tint to it and I have to crt+alt+del to get out of it.

Add/remove gives me this;


This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

when I put in 'sudo apt-get updater'  it hangs on 99%

and when I open a new tab and type 'sudo apt-get install-f'  it tells me I need to due the previous.

anyone know how to make Ubuntu like me again?

---

### Post by taurus on 2007-08-19
Can you post the complete output of this command?

```
sudo apt-get update
```

---

### Post by peterson2k4 on 2007-08-19
paul@paul-desktop:~$ sudo apt-get update
Password:
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Get:2 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]                
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Get:3 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release.gpg [189B]                     
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Translation-en_US             
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release                             
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Get:5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:6 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                
Get:7 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US              
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Get:9 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US            
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Get:11 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release [6906B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US       
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages       
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources        
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages       
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources        
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages                     
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Packages
Fetched 7296B in 2s (3635B/s)
Reading package lists... Done
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: You may want to run apt-get update to correct these problems





btw how do you do that neat code box?

---

### Post by taurus on 2007-08-19
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # sign in front of this line to comment it out.

```
http://hendrik.kaju.pri.ee
```
Save it.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by peterson2k4 on 2007-08-19
it didn't work.  I got the following

paul@paul-desktop:~$ gksudo gedit /etc/apt/sources.list
paul@paul-desktop:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Get:2 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]                
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Get:3 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release                             
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Get:4 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US           
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US       
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Get:11 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]       
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US          
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Get:12 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release.gpg [189B]                    
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release               
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                        
  
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages             
Get:13 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release [6906B]             
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages       
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages                     
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release             
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Packages
Fetched 7296B in 2s (2468B/s)
Reading package lists... Done
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: You may want to run apt-get update to correct these problems
paul@paul-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubuntustudio-audio: Depends: ardour
                      Recommends: linux-image-lowlatency but it is not installed
E: Unmet dependencies. Try using -f.
paul@paul-desktop:~$ sudo apt-get update -f
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Get:2 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]                
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Get:3 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release                             
Get:5 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US              
Get:8 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Get:9 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release.gpg [189B]                     
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Translation-en_US             
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US       
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Get:11 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                 
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US  
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
  
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Get:13 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release [6906B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages                     
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release             
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Packages
Fetched 7296B in 2s (2647B/s)
Reading package lists... Done
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: You may want to run apt-get update to correct these problems

---

### Post by peterson2k4 on 2007-08-19
when I copied the last code line exactly like the box you gave I got this

paul@paul-desktop:~$ sudo apt-get update
Get:1 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]                
Get:2 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release.gpg [189B]                     
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Translation-en_US             
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Get:3 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release                             
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
  
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US            
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Get:6 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release [6906B]                        
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages       
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources        
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages       
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources        
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages                     
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources                      
Get:7 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Get:9 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US       
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Packages                      
Fetched 7296B in 12s (570B/s)                                                  
Reading package lists... Done
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: You may want to run apt-get update to cor

---

### Post by peterson2k4 on 2007-08-19
bump

---

### Post by taurus on 2007-08-19
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by peterson2k4 on 2007-08-19
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

## Avant Window Navigator
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
#AUTOMATIX REPOS END
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

## Avant Window Navigator
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

#[http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee)

---

