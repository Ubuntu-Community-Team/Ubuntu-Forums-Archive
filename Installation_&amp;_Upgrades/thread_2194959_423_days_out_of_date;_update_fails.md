---
title: "423 days out of date; update fails"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2013-12-21
Due to a low space problem, I have not been able to update my ubuntu for.. 423 days.
I just (thanks to this forum) repartitioned things more optimally/flexibly but now the update fails. see the attached.

it says Check Your Internet, and I am on wifi, but it seems to be working OK.

[ATTACH=CONFIG]248790[/ATTACH]

---

### Post by Old_Grey_Wolf on 2013-12-21
Open a terminal and try the following command. Post the output using ```
 tags.

[CODE]sudo apt-get update && sudo apt-get upgrade
```

Edit: That screenshot looks like an old version of Ubuntu. 423 days ago was about the time 11.04 stopped getting updates because it reached end-of-life. What version are you using?

---

### Post by pjstock on 2013-12-21
indeed i seem to still be stuck in ver.11.04

not sure how these code tags work, but here goes:

```

Ign http://ca.archive.ubuntu.com natty InRelease
Ign http://ca.archive.ubuntu.com natty-updates InRelease                       
Ign http://linux.dropbox.com maverick InRelease                                
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://ca.archive.ubuntu.com natty Release.gpg                             
Ign http://archive.canonical.com natty InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://ca.archive.ubuntu.com natty-updates Release.gpg                     
Get:1 http://linux.dropbox.com maverick Release.gpg [489 B]                    
Ign http://ca.archive.ubuntu.com natty Release                                 
Ign http://security.ubuntu.com natty-security Release.gpg                      
Hit http://archive.canonical.com natty Release.gpg                             
Ign http://extras.ubuntu.com natty Release.gpg                                 
Ign http://ca.archive.ubuntu.com natty-updates Release                         
Get:2 http://linux.dropbox.com maverick Release [2,605 B]                      
Ign http://security.ubuntu.com natty-security Release                          
Hit http://archive.canonical.com natty Release                                 
Ign http://ca.archive.ubuntu.com natty/main Sources/DiffIndex                  
Ign http://ca.archive.ubuntu.com natty/restricted Sources/DiffIndex            
Ign http://ca.archive.ubuntu.com natty/universe Sources/DiffIndex              
Ign http://ca.archive.ubuntu.com natty/multiverse Sources/DiffIndex            
Ign http://ca.archive.ubuntu.com natty/main i386 Packages/DiffIndex            
Ign http://ca.archive.ubuntu.com natty/restricted i386 Packages/DiffIndex      
Ign http://ca.archive.ubuntu.com natty/universe i386 Packages/DiffIndex        
Ign http://ca.archive.ubuntu.com natty/multiverse i386 Packages/DiffIndex      
Ign http://ca.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://ca.archive.ubuntu.com natty/multiverse TranslationIndex      
Ign http://extras.ubuntu.com natty Release                                     
Ign http://ca.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://ca.archive.ubuntu.com natty/universe TranslationIndex        
Ign http://ca.archive.ubuntu.com natty-updates/main Sources/DiffIndex          
Ign http://ca.archive.ubuntu.com natty-updates/restricted Sources/DiffIndex    
Ign http://ca.archive.ubuntu.com natty-updates/universe Sources/DiffIndex      
Ign http://security.ubuntu.com natty-security/main Sources/DiffIndex           
Ign http://ca.archive.ubuntu.com natty-updates/multiverse Sources/DiffIndex    
Ign http://ca.archive.ubuntu.com natty-updates/main i386 Packages/DiffIndex    
Ign http://ca.archive.ubuntu.com natty-updates/restricted i386 Packages/DiffIndex
Ign http://ca.archive.ubuntu.com natty-updates/universe i386 Packages/DiffIndex
Ign http://ca.archive.ubuntu.com natty-updates/multiverse i386 Packages/DiffIndex
Ign http://extras.ubuntu.com natty/main Sources/DiffIndex                      
Get:3 http://linux.dropbox.com maverick/main i386 Packages [1,148 B]           
Ign http://ca.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://ca.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://ca.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://ca.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://security.ubuntu.com natty-security/restricted Sources/DiffIndex     
Ign http://security.ubuntu.com natty-security/universe Sources/DiffIndex       
Ign http://security.ubuntu.com natty-security/multiverse Sources/DiffIndex     
Ign http://security.ubuntu.com natty-security/main i386 Packages/DiffIndex     
Ign http://security.ubuntu.com natty-security/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/universe i386 Packages/DiffIndex 
Ign http://security.ubuntu.com natty-security/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://extras.ubuntu.com natty/main i386 Packages/DiffIndex                
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://linux.dropbox.com maverick/main TranslationIndex                    
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://linux.dropbox.com maverick/main Translation-en_CA                   
Ign http://linux.dropbox.com maverick/main Translation-en                      
Ign http://archive.canonical.com natty/partner Translation-en_CA               
Err http://security.ubuntu.com natty-security/main Sources                     
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com natty-security/restricted Sources     
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com natty-security/universe Sources                 
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com natty-security/multiverse Sources               
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com natty-security/main i386 Packages               
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com natty-security/restricted i386 Packages         
  404  Not Found [IP: 91.189.92.201 80]
Err http://security.ubuntu.com natty-security/universe i386 Packages 
  404  Not Found [IP: 91.189.92.201 80]
Ign http://archive.canonical.com natty/partner Translation-en        
Err http://ca.archive.ubuntu.com natty/main Sources                  
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty/restricted Sources            
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://extras.ubuntu.com natty/main Sources
  404  Not Found
Err http://ca.archive.ubuntu.com natty/multiverse Sources            
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty/main i386 Packages            
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://ca.archive.ubuntu.com natty/main Translation-en_CA
Ign http://ca.archive.ubuntu.com natty/main Translation-en
Err http://security.ubuntu.com natty-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign http://security.ubuntu.com natty-security/main Translation-en_CA 
Ign http://security.ubuntu.com natty-security/main Translation-en    
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_CA
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://ca.archive.ubuntu.com natty/multiverse Translation-en_CA  
Ign http://ca.archive.ubuntu.com natty/multiverse Translation-en     
Ign http://ca.archive.ubuntu.com natty/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com natty/restricted Translation-en
Ign http://ca.archive.ubuntu.com natty/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com natty/universe Translation-en
Err http://ca.archive.ubuntu.com natty-updates/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty-updates/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://extras.ubuntu.com natty/main i386 Packages
  404  Not Found
Ign http://extras.ubuntu.com natty/main Translation-en_CA            
Err http://ca.archive.ubuntu.com natty-updates/universe Sources      
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty-updates/multiverse Sources    
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://ca.archive.ubuntu.com natty-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://ca.archive.ubuntu.com natty-updates/main Translation-en_CA
Ign http://security.ubuntu.com natty-security/universe Translation-en_CA
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/main Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 4,242 B in 2s (1,433 B/s)
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
peter@peterx300:~$ 

```

---

### Post by arpanaut on 2013-12-21
This may help you to get upgraded to 12.04  [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But the better/easier path is to download the iso for 12.04 and do a fresh install.
you could backup your data and bookmarks etc.
From reading your other thread, for just a browsing machine, this would be the quickest option.

---

### Post by Bashing-om on 2013-12-21
pjstock; Hi !

Version upgrade from End Of Life versions is lengthy and prone to errors, It is generally advocated to do a much faster clean install.
But, the upgrade can be done ! The instruction:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
That starts with editing the sources list file to redirect to a supported software repository to efecct the upgrade(s) .

Whatever you choose, we are here to help.

---

### Post by pjstock on 2013-12-21
got it. it appears I have become obsolete.
step upgrading (to 11.10 before 12.04) seems overly fiddly. so I'll just do a fresh install of 12.04.
thank you all.

---

### Post by Old_Grey_Wolf on 2013-12-21
> **pjstock said:**
> got it. it appears I have become obsolete.
step upgrading (to 11.10 before 12.04) seems overly fiddly. so I'll just do a fresh install of 12.04.
thank you all.

With the specs I find in some of your other posts, you may be better off using Lubuntu or Xubuntu.

At least it seems you have your partition problems worked out.

---

