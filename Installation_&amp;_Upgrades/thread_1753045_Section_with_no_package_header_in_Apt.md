---
title: "Section with no package header in Apt"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2011-05-08
When I run aptitude update (or anything that uses apt) I get an error saying that there is no package header for main.
Here is the output I get:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable InRelease      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease      
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]   
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B] 
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]
Get:5 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,073 B]      
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex               
Get:6 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [773 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                             
Fetched 4,935 B in 8s (594 B/s)                                                 
[ ERR] Reading package lists
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```
I checked /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages to see if it was different from /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages in any significant way, but I didn't see anything significantly different. Any suggestions?

---

### Post by caseygibbs on 2011-05-08
Bumpsky. Me too.

EDIT: Just tried this here:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

...and it worked.

---

### Post by camper365 on 2011-05-08
I found this thread [http://ubuntuforums.org/showthread.php?t=863742]("http://ubuntuforums.org/showthread.php?t=863742") and it works now. I rm'ed the folder contents too and that worked.

---

### Post by Hardelettrosoft on 2011-06-02
Yes, it work for me also :) Thanks !!

---

### Post by SolaceFile on 2012-05-19
It worked for me too.. :) Yepiee.. ! Hail Ubuntu.

---

### Post by netgooroo on 2012-08-19
This worked for me to. thanks guys..  I gotta say, I don't like the native desktop settings of 12.04 and, not having an option to go to a desktop with no effects. Installing gnome now. 

Thanks again. :-)

---

