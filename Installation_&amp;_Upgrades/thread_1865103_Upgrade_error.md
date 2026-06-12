---
title: "Upgrade error"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by Cagurtay on 2011-10-19
Hello,
i just installed xubuntu and tried to update it and there is an upgrade to 11.10 and another 150mb update, i picked upgrade but i get this error
W:Failed to fetch gzip:/var/lib/apt/lists/partial/tr.archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/tr.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.
My internet is working as i am writing this in xubuntu.
any ideas?
ty.

---

### Post by Cagurtay on 2011-10-19
my sudo apt-get update result.

> Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty InRelease
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty Release.gpg                             
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty Release                                 
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates Release                         
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/main Sources                            
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/multiverse Sources
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/restricted i386 Packages
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/multiverse i386 Packages      
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg 
Get:1 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/universe Sources [5,430 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Get:2 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/main i386 Packages [1,987 kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                     
Get:3 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/universe i386 Packages [7,755 kB]     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) natty-updates/universe Translation-en         
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
Fetched 3 B in 1s (2 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/tr.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/tr.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/tr.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by Cagurtay on 2011-10-19
and i did > sudo rm -rf /var/lib/apt/lists/partial/*
from [http://ubuntuforums.org/showthread.php?t=1817352&highlight=Hash+Sum+mismatch]("http://ubuntuforums.org/showthread.php?t=1817352&highlight=Hash+Sum+mismatch") and got this :
> W:Failed to fetch gzip:/var/lib/apt/lists/partial/tr.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Cagurtay on 2011-10-19
on second try at sudo rm -rf /var/lib/apt/lists/partial/* it fixed, sorry for bothering :popcorn:

---

### Post by garvinrick4 on 2011-10-19
You are fixed up already, enjoy you Ubuntu

---

### Post by Cagurtay on 2011-10-20
yeah but now i couldnt boot after upgrade stucked at something that i cant remember, that happened after i tried upgrading ubuntu 11.04 too, fixed though.
i though linux , ubuntu much more stable than windows but those thing put me off :( , windows forever :)

---

