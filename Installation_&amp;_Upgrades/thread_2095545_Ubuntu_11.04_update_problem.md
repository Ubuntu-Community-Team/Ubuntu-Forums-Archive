---
title: "Ubuntu 11.04 update problem"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by Simon4360 on 2012-12-17
Hey,

Im having trouble updating my Ubuntu 11.04. When i go to update manager it says upgade to 11.04 available although my system>about ubuntu says that i am already on 11.04.

When i click upgrade in update manager the distribution upgrade window starts and get to the setting new software channels stage where i then get an error:

W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

also when i try in through terminal i get:

it [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main Translation-en             
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/multiverse Translation-en       
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/multiverse Translation-en_GB    
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/restricted Translation-en       
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/universe Translation-en         
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty/partner Translation-en          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty/partner Translation-en_GB       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty/main Translation-en                 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty/main Translation-en_GB              
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main Translation-en     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main Translation-en_GB  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe Translation-en 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main Translation-en      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main Translation-en_GB   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/universe Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/universe Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports Release.gpg                   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports/main Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed Release.gpg                    
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-proposed/main Translation-en    
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-proposed/main Translation-en_GB 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-proposed/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-proposed/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-proposed/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-proposed/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-proposed/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed Release              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386 Packages        
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                      
  404  Not Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages
  404  Not Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-proposed/universe i386 Packages
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Any ideas?

---

### Post by dino99 on 2012-12-17
natty is no more supported since  oct 28 , its time to use something newer like oneiric (if you does not want to reinstall, but simply dist-upgrade) or do a fresh new install with precise or quantal.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/](http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/)

---

### Post by Simon4360 on 2012-12-17
ahh right, so how would i change to oneric?

---

### Post by sahabcse on 2012-12-17
Open the Update Manager application from the System &#8594; Administration menu.

    In Update Manager, click the Settings... button, and enter your password to start the Software Sources application.

    Select the sub menu Updates from the Software Sources application.

    Check the "Release upgrade - Show new distribution releases" drop down to make sure "Normal releases" is selected, and change it if otherwise.
    Close the Software Sources application and return to Update Manager.

    In Update Manager, click the Check button to check for new updates.

    If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
    A message will appear informing you of the availability of the new release.

    Click Upgrade.
    Follow the on-screen instructions.

---

### Post by Simon4360 on 2012-12-17
im not sure that i actually am on 11.04 you know. When i load up the boot screen says ubuntu 10.10 and i don't have the option to put in a password and go to software sources like you describe in settings. I installed using a 10.10 disk and i used update manager to update to 11.04 and it seems to work. Plus like i said before it says 11.04 when i go to system>about ubuntu. There any command i can use to determine which version i'm on through terminal?

---

### Post by Simon4360 on 2012-12-17
ok, i am infact on ubuntu 10.10.....

---

### Post by mörgæs on 2012-12-17
The references to natty in your first post indicate that you are on 11.04.

Anyway, time for a fresh install of 12.10.

---

