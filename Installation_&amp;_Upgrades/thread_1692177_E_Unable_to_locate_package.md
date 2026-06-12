---
title: "E: Unable to locate package ???"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by reza_knight on 2011-02-21
i'm tried to install cacti on ubuntu, but when i enter the > sudo apt-get install cacti command. the result is **E[B]: **Unable** to locate package.**

[/B]
and i tried in **System>administrstion>synaptic package manager. **i tried to reload the result is error..


and it's not just for cacti, i've tried to install the other program the result still the same..

did i miss something or what??

---

### Post by mikewhatever on 2011-02-21
Something seems to be wrong with your software sources. Can you post the output of the **sudo apt-get update** command.

---

### Post by marcusaur on 2011-02-21
have you tried downloading from Ubuntu software center

---

### Post by reza_knight on 2011-02-22
> **mikewhatever said:**
> Something seems to be wrong with your software sources. Can you post the output of the sudo apt-get update command.

here's the output...
reza@reza-device:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg [198B]                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources [3,808B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en      
Get:5 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [7,448B]    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US   
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]           
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en   
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en   
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release [39.8kB]                 
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,750B]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                 
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages [1,492kB]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                      
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages [5,992B]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages               
Fetched 1,555kB in 1min 5s (23.9kB/s)                                         
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220


hey..it works..i can install cacti r8 now....
uhmm.... should i update it routinely before install program ??
i don't know what's going on, but it really works...
thanks dude!


> **marcusaur said:**
> have you tried downloading from Ubuntu software center

yeah, i never change that config...

---

