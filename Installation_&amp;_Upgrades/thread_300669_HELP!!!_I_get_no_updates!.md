---
title: "HELP!!! I get no updates!"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by danage on 2006-11-16
Hi! I'm using the Edgy beta, and until the final release it updated fine. But since the release day, I have been getting no further updates. Please -- this isn't normal, is it??? How do I reconfigure my apt??? Thank you very much!

---

### Post by ciscosurfer on 2006-11-16
More information is necessary before any assistance can be provided.

---

### Post by pandu.rs on 2006-11-16
In terminal type
sudo apt-get update

check if you get any errors.

---

### Post by danage on 2006-11-16
There are no errors, but some sources are being ignored. i'm pasting the output.```
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy Release.gpg [191B]                    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/main Translation-de                     
Hole:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-de               
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release.gpg                                   
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/restricted Translation-de               
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/multiverse Translation-de               
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/universe Translation-de                 
Hole:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates Release.gpg [189B]            
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates/main Translation-de              
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates/restricted Translation-de        
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates/multiverse Translation-de        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-de         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-de         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-de           
OK   [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                          
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates/universe Translation-de          
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy Release                     
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates Release                         
OK   [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                    
OK   [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages              
OK   [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages              
OK   [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                
OK   [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                     
OK   [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources               
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/main Packages                           
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/restricted Packages         
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/multiverse Packages         
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/universe Packages           
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates/main Packages       
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates/restricted Packages 
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates/multiverse Packages 
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy-updates/universe Packages   
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/. Translation-de                  
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release                                         
OK   [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/. Packages                                     
Es wurden 3B in 7s geholt (0B/s)                                                 
Paketlisten werden gelesen... Fertig
```

---

