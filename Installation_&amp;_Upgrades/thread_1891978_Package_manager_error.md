---
title: "Package manager error"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by satya ub on 2011-12-07
Hi,
     I have been using Ubuntu for the past couple of months. Let me explain my problem. 

First i noticed this with Transmission. When the torrent is about 99.9% it again reverts back to 99.4%. The torrent never completes.

This morning i saw a red color stop sign on the Top Bar, which says:

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: "Error opening the cache (E:Encountered a section with no Package: header, E:Problem with MergeList/var/lib/apt/lists/ubuntu.oss/eznetsols.orgubuntudistsoneiricsecuritymaini18nTranslation-en, E:The package lists or status file could not be parsed or opened.)'. This usually means that your installed packages have unmet dependencies."

I tried to run the Synaptic Package Manager from the Dash. I got this 

An error occurred
"E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ubuntu.oss.eznetsols.org_ubuntu_dists_oneiric-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."

And it aborted.

Can someone explain to me what happened in simple terms and how to fix this issue.

---

### Post by satya ub on 2011-12-07
Hi,
I have been using Ubuntu for the past couple of months. Let me explain my problem. 

First i noticed this with Transmission. When the torrent is about 99.9% it again reverts back to 99.4%. The torrent never completes.

This morning i saw a red color stop sign on the Top Bar, which says:

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: "Error opening the cache (E:Encountered a section with no Package: header, Eroblem with MergeList/var/lib/apt/lists/ubuntu.oss/eznetsols.orgubuntudistsoneiricsecuritymaini18nTra nslation-en, E:The package lists or status file could not be parsed or opened.)'. This usually means that your installed packages have unmet dependencies."

I tried to run the Synaptic Package Manager from the Dash. I got this 

An error occurred
"E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ubuntu.oss.eznetsols.org_ubuntu_dists_oneiric-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."

And it aborted.
I cannot open Ubuntu Software Center even.

Can someone explain to me what happened in simple terms and how to fix this issue.

---

### Post by typhoon_tip on 2011-12-07
Please post the result of this command.

Press CTRL+ALT+T to open a terminal, then copy/paste (**CTRL+C** / **CTRL+SHIFT+V** into the terminal) this command:
```
sudo apt-get check
```

To copy the result from terminal, select with mouse and press **CTRL+SHIFT+C**.

---

### Post by satya ub on 2011-12-07
I did what you said. This is what i got from the Terminal.

"E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ubuntu.oss.eznetsols.org_ubuntu_dists_oneiric-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened."

---

### Post by fantab on 2011-12-07
Open TERMINAL and run following command and Post its output:

```
sudo apt-get update
```

---

### Post by satya ub on 2011-12-07
This is what i got from the Terminal.

"Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Ign [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric InRelease                          
Ign [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates InRelease        
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Ign [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security InRelease                 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric Release.gpg              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Get:2 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates Release.gpg [198 B]      
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security Release.gpg               
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric Release                            
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                    
Get:3 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates Release [32.4 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex               
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security Release                   
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/main Sources                       
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/restricted Sources                 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/universe Sources                   
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/multiverse Sources                 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/main i386 Packages                 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/restricted i386 Packages           
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/universe i386 Packages             
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/multiverse i386 Packages           
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/main TranslationIndex              
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/multiverse TranslationIndex        
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/restricted TranslationIndex        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/universe TranslationIndex          
Get:4 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/main Sources [94.6 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Get:5 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Get:6 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/restricted Sources [1,348 B]
Get:7 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/universe Sources [25.8 kB]
Get:8 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/multiverse Sources [1,992 B]
Get:9 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/main i386 Packages [219 kB]
Get:10 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/restricted i386 Packages [2,935 B]
Get:11 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/universe i386 Packages [64.1 kB]
Get:12 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/multiverse i386 Packages [4,396 B]
Get:13 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/main TranslationIndex [73 B]
Get:14 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/multiverse TranslationIndex [72 B]
Get:15 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/restricted TranslationIndex [71 B]
Get:16 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/universe TranslationIndex [73 B]
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/main Sources      
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/restricted Sources
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/universe Sources  
Get:17 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                   
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/multiverse Sources        
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/main i386 Packages        
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/restricted i386 Packages  
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/universe i386 Packages    
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/multiverse i386 Packages  
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/main TranslationIndex     
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/multiverse TranslationIndex
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/restricted TranslationIndex
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/universe TranslationIndex 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/main Translation-en                
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/multiverse Translation-en          
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/restricted Translation-en          
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric/universe Translation-en            
Get:18 [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/main Translation-en [99.5 kB]
Get:19 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,228 B]                
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/multiverse Translation-en  
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/restricted Translation-en  
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-updates/universe Translation-en    
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/main Translation-en       
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/multiverse Translation-en 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/restricted Translation-en 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) oneiric-security/universe Translation-en   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 550 kB in 36s (14.9 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ubuntu.oss.eznetsols.org_ubuntu_dists_oneiric-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened."

---

### Post by plucky on 2011-12-07
> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ubuntu.oss.eznetsols.org_ubuntu_dists_oneiric-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened." 


From the terminal ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command will delete the list files and the second command will download them again.If you get the same result,try changing your download server in "Software Sources".

Good Luck

---

### Post by satya ub on 2011-12-07
Thank you very much. It worked. The error is fixed. The Software Center is displayed on a click. Will check for Transmission Client.

---

### Post by Krytarik on 2011-12-07
Apparently, you have an unstable internet connection, which is the cause of both the issues you are describing.

To fix the package manager issue, just delete the corrupted file:
```
sudo rm /var/lib/apt/lists/ubuntu.oss.eznetsols.org_ubuntu_dists_oneiric-security_main_i18n_Translation-en
```Then update the package lists again:
```
sudo apt-get update
```For fixing the general, underlying network issue: Sorry, I'm not really an expert in this area, but you might wait for some knowledgeable people here, or post that particular question in the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") sub-forum.

Regards, and good luck with the latter!

---

### Post by Rubi1200 on 2011-12-11
Threads merged.

Please don't post the same question in different forums; it dilutes community effort.

Thanks to plucky and others you have the solution.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

