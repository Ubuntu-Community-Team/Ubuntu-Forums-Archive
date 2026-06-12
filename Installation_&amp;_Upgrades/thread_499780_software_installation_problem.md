---
title: "software installation problem"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by romihim on 2007-07-13
This has happened with two programs so writing this in here .
i installed vdrift(from synaptic) . its a game. but now i m not getting to know where to run it i.e. no shortcut in games menu or any thing. i tried in terminal ,but it says command not found(as if vdrift is not installed). 
same thing happens with w32 codecs . movie player is not able to use them . tell me why ths is happening
.
Its not that synaptic is not workin , i have installed many apps through it ,but having prob with these two .

---

### Post by aquavitae on 2007-07-13
> **romihim said:**
> This has happened with two programs so writing this in here .
i installed vdrift(from synaptic) . its a game. but now i m not getting to know where to run it i.e. no shortcut in games menu or any thing. i tried in terminal ,but it says command not found(as if vdrift is not installed). 
In synaptic, view the package properties.  In one of the tabs theres a list of the files installed.  Look for something under /bin, /usr/bin or /usr/share/bin - it may be just that the executable file is not named vdrift.  If you find something under a bin directory try running it in a terminal and see what happens.
> same thing happens with w32 codecs . movie player is not able to use them . tell me why ths is happening
What movie player are you using?  I assume you've got the right architecture for w32codecs? i.e. 32bit, not 64.

---

### Post by Sef on 2007-07-13
How did you instll the win32 codecs?

---

### Post by romihim on 2007-07-13
installed w32 codecs using synaptic. its for 32 bit architecture.
as it was not working so i removed it and again used terminal to install .

---

### Post by romihim on 2007-07-13
vdrift is ubuntu's native game , in its site its given that vdrift should make its shortcut in games menu . but that didnot happen

---

### Post by Pumalite on 2007-07-13
Run sudo apt-get update and make sure you have all this in your sources.list:

Get:1 [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/main Translation-en_US                 
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Get:4 [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release.gpg [189B]               
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Get:6 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                   
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/main Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Ign [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Translation-en_US   
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US   
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/main Sources                           
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/restricted Sources                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release [32.4kB]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/universe Sources                   
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release                            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                  
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release [38.4kB]              
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Ign [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages               
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages           
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Hit [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages [14B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages [55.0kB]      
Hit [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Packages                      
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages [2108B]   
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages [12.6kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages [14B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages [10.7kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages [14B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages [11.4kB]
Fetched 163kB in 4s (35.1kB/s)                          
Reading package lists... Done

---

### Post by romihim on 2007-07-13
problem sorted out 
thanks for ur replys

---

### Post by terrapisces on 2007-07-24
so what was the solution? i am also having an issue getting vdrift to install. the problem i'm running into is that the sdl_net package cannot be found. i've tried looking it up but cant find where to get it.

---

