---
title: "error on sudo apt-get update"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by Jackum on 2011-06-30
Error: N: Ignoring file 'transmission.lista' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

**Above error comes when i put sudo apt-get update **

And another problem is - Using online flash player (Online Radio), full list of the songs are shown but only the current song I can see the exact names others' names are blank.

E.g.

Playlist:

1)---------
2)You Are my Hero (Current song)
3)--------
4)--------

So, I tried to update my ubuntu 10.10 (2.6.35-30-generic) using code: sudo apt-get update but no success. 


Here is the result while running the code:


$ sudo apt-get update
[sudo] password for XXXXX: 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy/main Translation-en             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy/main Translation-en_IN          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/main Translation-en      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/main Translation-en_IN   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed/main Translation-en       
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy/multiverse Translation-en       
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy/multiverse Translation-en_IN    
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy/restricted Translation-en       
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy/restricted Translation-en_IN    
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy/universe Translation-en         
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy/universe Translation-en_IN      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/universe Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/universe Translation-en_IN
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates/main Translation-en     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates/main Translation-en_IN  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed/main Translation-en_IN    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed/multiverse Translation-en 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed/restricted Translation-en 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed/universe Translation-en   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed/universe Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,775B]                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release                           
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports Release.gpg                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates/multiverse Translation-en_IN
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates/restricted Translation-en_IN
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates/universe Translation-en 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates/universe Translation-en_IN
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports/main Translation-en   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports/main Translation-en_IN
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports/multiverse Translation-en_IN
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports/restricted Translation-en_IN
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports/universe Translation-en_IN
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse i386 Packages         
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [24.8kB]                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse i386 Packages          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed Release.gpg [198B]      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release                     
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_IN
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main i386 Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe i386 Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse i386 Packages        
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [28.0kB]  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports Release                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security Release                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse i386 Packages      
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed Release [31.4kB]          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/multiverse i386 Packages
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed/main i386 Packages [123kB]
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [1,124B]
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed/universe i386 Packages [10.9kB]
Fetched 229kB in 5s (45.8kB/s)                        
Reading package lists... Done
**[COLOR="Red"]N: Ignoring file 'transmission.lista' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension[/COLOR]**

Plz help me someone :popcorn:

---

### Post by oldos2er on 2011-06-30
```
sudo mv /etc/apt/sources.list.d/transmission.lista /etc/apt/sources.list.d/transmission.list
```

You need to remove all the hardy repos from your sources.list ```
gksu gedit /etc/apt/sources.list
```

When you're done with both these things, run ```
sudo apt-get update
``` If there are any errors, please post the terminal output here.

---

### Post by Jackum on 2011-07-02
Thank you oldos2er for the reply. 

I just did run but still error is there, plz find the terminal output:

:~$ sudo mv /etc/apt/sources.list.d/transmission.lista /etc/apt/sources.list.d/transmission.list
james@james-Presario:~$ gksu gedit /etc/apt/sources.list
james@james-Presario:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en_IN
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN       
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net/bortis/ubuntu/](http://ppa.launchpad.net/bortis/ubuntu/) intrepid/main Translation-en       
Ign [http://ppa.launchpad.net/bortis/ubuntu/](http://ppa.launchpad.net/bortis/ubuntu/) intrepid/main Translation-en_IN    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [65.9kB]                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports Release.gpg                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security Release.gpg               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_IN
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources [672B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security Release                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed Release                     
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main i386 Packages [1,973B]            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-proposed/universe i386 Packages
Fetched 68.8kB in 3s (17.9kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FCA4A9D8F45955CE

---

### Post by drs305 on 2011-07-02
> **Jackum said:**
> Thank you oldos2er for the reply. 

I just did run but still error is there, plz find the terminal output:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) **[COLOR="Red"]intrepid[/COLOR]** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FCA4A9D8F45955CE

Now do the same thing and remove or replace *[COLOR="Red"]intrepid[/COLOR]*

---

### Post by Jackum on 2011-07-02
Hi drs305,

I am not able to find  [COLOR="Red"]**intrepid **[/COLOR] on Source list.

---

### Post by drs305 on 2011-07-02
> **drs305 said:**
> Now do the same thing and remove or replace *[COLOR="Red"]intrepid[/COLOR]*

It could be listed within a file in the /etc/apt/sources.list.d folder.

You could also find and deselect it via Synaptic: Settings, Repositories > Other Software tab. Find the [http://ppa.launchpad](http://ppa.launchpad) entry for intrepid and untick it.

---

### Post by Jackum on 2011-07-02
i did untick the below from  Synaptic: Settings, Repositories > Other Software tab
[http://ppa.lauchpad.net/bortis/ubuntu](http://ppa.lauchpad.net/bortis/ubuntu) intrepid main
[http://ppa.lauchpad.net/bortis/ubuntu](http://ppa.lauchpad.net/bortis/ubuntu) intrepid main(source code)
Reload and try to sudo apt-get update

Error comes again:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by drs305 on 2011-07-02
> **Jackum said:**
> i did untick the below from  Synaptic: Settings, Repositories > Other Software tab
[http://ppa.lauchpad.net/bortis/ubuntu](http://ppa.lauchpad.net/bortis/ubuntu) intrepid main
[http://ppa.lauchpad.net/bortis/ubuntu](http://ppa.lauchpad.net/bortis/ubuntu) intrepid main(source code)
Reload and try to sudo apt-get update

Error comes again:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You probably tried to run "sudo apt-get update" with Synaptic still open. If you use two processes that simultaneously try to use APT those error messages are generated. Close Synaptic and run "sudo apt-get update", or hit the Reload button in Synaptic.

---

### Post by Jackum on 2011-07-02
Gr8, it is done, i can update using sudo apt-get update

now, still flash problem is there...

Using online flash player (Online Radio), full list of the songs are shown but only the current song I can see the exact names but others names are blank.

E.g.

Playlist:

1)---------
2)You Are my Hero (Current song)
3)--------
4)--------

I hAVE dual boot with WinXp, I checked, there all plyalist with each names are shown, I tried to uninstalled firefox on Ubuntu but no success, I have no idea how to resolve this issue, 
Would you please help me !!

---

### Post by drs305 on 2011-07-02
> **Jackum said:**
> Gr8, it is done, i can update using sudo apt-get update

now, still flash problem is there...

Using online flash player (Online Radio), full list of the songs are shown but only the current song I can see the exact names but others names are blank.

E.g.

Playlist:

1)---------
2)You Are my Hero (Current song)
3)--------
4)--------

I hAVE dual boot with WinXp, I checked, there all plyalist with each names are shown, I tried to uninstalled firefox on Ubuntu but no success, I have no idea how to resolve this issue, 
Would you please help me !!

I don't know the reason. It would probably be best for you to start a new thread about this issue. Make a title that addresses this problem. Consider putting it in [Multimedia]("http://ubuntuforums.org/forumdisplay.php?f=334") forum, but General would be appropriate as well. 

If you create a new thread, please mark this one Solved via the 'Thread Tools' link at the top right of the first post. Good luck with your playlist issue.

---

### Post by Jackum on 2011-07-02
thaNKs for ur help !!!

---

