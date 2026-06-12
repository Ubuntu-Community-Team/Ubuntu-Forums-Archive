---
title: "Ubuntu Software center"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by amisukanta on 2011-10-01
I have installed Ubuntu 11.4. Previously it was working properly suddenly the **Software center **stopped connecting with server. Now i am unable to install any software. Please helpe

---

### Post by papibe on 2011-10-01
Welcome to the forums!

Could you post the result of this command?
```
sudo apt-get update
```
Regards.

---

### Post by amisukanta on 2011-10-01
[FONT=monospace]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty InRelease                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates InRelease             
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]              
Get:2 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release.gpg [198 B] 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [31.4 kB]    
Get:6 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Get:7 [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages [8,649 B]       
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release [31.4 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [70.4 kB]         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Sources                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Sources                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe TranslationIndex               
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Sources [109 kB]        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [11.3 kB]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [657 B]    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [189 kB]   
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Sources [753 B]   
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Sources [27.7 kB]   
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Sources [1,888 B] 
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main i386 Packages [326 kB]  
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [41.6 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,077 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_IN                      
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted i386 Packages [839 B]
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe i386 Packages [96.1 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,264 B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_IN               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_IN 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en_IN    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en_IN    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en_IN      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 960 kB in 6s (158 kB/s)                                                
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

[/FONT]

---

### Post by amisukanta on 2011-10-01
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty InRelease                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates InRelease             
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]              
Get:2 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release.gpg [198 B] 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [31.4 kB]    
Get:6 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Get:7 [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages [8,649 B]       
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release [31.4 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [70.4 kB]         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Sources                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Sources                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe TranslationIndex               
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Sources [109 kB]        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [11.3 kB]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [657 B]    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [189 kB]   
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Sources [753 B]   
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Sources [27.7 kB]   
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Sources [1,888 B] 
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main i386 Packages [326 kB]  
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [41.6 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,077 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_IN                      
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted i386 Packages [839 B]
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe i386 Packages [96.1 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,264 B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_IN               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_IN 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en_IN    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en_IN    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en_IN      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 960 kB in 6s (158 kB/s)                                                
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by papibe on 2011-10-01
Somehow your sources got corrupted.

To solve it try this:
```
sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update

```
Then try using the Software Center.

Regards.

---

