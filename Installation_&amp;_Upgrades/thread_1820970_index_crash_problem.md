---
title: "index crash problem"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by raja.genupula on 2011-08-08
i have done what i know to clear the issue but i wasnt succeeded , i am pasting the code here . please help me on this 

```
 assassin@genupulas:~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for assassin: 
assassin@genupulas:~$ sudo apt-get update
Ign http://deb.opera.com stable InRelease                                      
Ign http://archive.canonical.com natty InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://dl.google.com stable InRelease                                      
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://lk.archive.ubuntu.com natty InRelease                               
Ign http://lk.archive.ubuntu.com natty-updates InRelease                       
Get:1 http://deb.opera.com stable Release.gpg [189 B]                          
Get:2 http://archive.canonical.com natty Release.gpg [198 B]                   
Get:3 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Get:4 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Get:5 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Get:6 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Get:7 http://lk.archive.ubuntu.com natty Release.gpg [198 B]                   
Get:8 http://deb.opera.com stable Release [633 B]                              
Get:9 http://archive.canonical.com natty Release [5,916 B]                     
Get:10 http://extras.ubuntu.com natty Release [9,753 B]                        
Get:11 http://security.ubuntu.com natty-security Release [27.2 kB]             
Get:12 http://dl.google.com stable Release [1,347 B]                           
Ign http://ppa.launchpad.net natty Release.gpg                                 
Get:13 http://lk.archive.ubuntu.com natty-updates Release.gpg [198 B]          
Get:14 http://deb.opera.com stable/non-free i386 Packages [851 B]              
Get:15 http://ppa.launchpad.net natty Release.gpg [316 B]                      
Get:16 http://ppa.launchpad.net natty Release.gpg [316 B]                      
Get:17 http://ppa.launchpad.net natty Release.gpg [316 B]                      
Get:18 http://ppa.launchpad.net natty Release.gpg [316 B]                      
Get:19 http://ppa.launchpad.net natty Release.gpg [316 B]                      
Get:20 http://lk.archive.ubuntu.com natty Release [39.8 kB]                    
Get:21 http://archive.canonical.com natty/partner i386 Packages [8,648 B]      
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Get:22 http://extras.ubuntu.com natty/main Sources [14 B]                      
Get:23 http://dl.google.com stable/main i386 Packages [1,195 B]                
Get:24 http://ppa.launchpad.net natty Release [9,739 B]                        
Get:25 http://extras.ubuntu.com natty/main i386 Packages [14 B]                
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty Release                                     
Get:26 http://ppa.launchpad.net natty Release [9,753 B]                        
Get:27 http://ppa.launchpad.net natty Release [9,762 B]                        
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://dl.google.com stable/main TranslationIndex                          
Get:28 http://security.ubuntu.com natty-security/main Sources [63.5 kB]        
Get:29 http://ppa.launchpad.net natty Release [9,736 B]                        
Get:30 http://ppa.launchpad.net natty Release [9,733 B]                        
Get:31 http://ppa.launchpad.net natty Release [9,732 B]                        
Get:32 http://lk.archive.ubuntu.com natty-updates Release [27.2 kB]            
Get:33 http://ppa.launchpad.net natty/main Sources [1,269 B]                   
Get:34 http://ppa.launchpad.net natty/main i386 Packages [3,183 B]             
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:35 http://ppa.launchpad.net natty/main Sources [11.7 kB]                   
Get:36 http://ppa.launchpad.net natty/main i386 Packages [10.7 kB]             
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:37 http://ppa.launchpad.net natty/main Sources [1,675 B]                   
Get:38 http://security.ubuntu.com natty-security/restricted Sources [14 B]     
Get:39 http://security.ubuntu.com natty-security/universe Sources [9,829 B]    
Get:40 http://ppa.launchpad.net natty/main i386 Packages [8,181 B]             
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:41 http://ppa.launchpad.net natty/main Sources [10.7 kB]                   
Get:42 http://ppa.launchpad.net natty/main i386 Packages [16.9 kB]             
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:43 http://ppa.launchpad.net natty/main Sources [15.9 kB]                   
Get:44 http://security.ubuntu.com natty-security/multiverse Sources [658 B]    
Get:45 http://lk.archive.ubuntu.com natty/main Sources [862 kB]                
Get:46 http://security.ubuntu.com natty-security/main i386 Packages [165 kB]   
Get:47 http://ppa.launchpad.net natty/main i386 Packages [13.8 kB]             
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:48 http://ppa.launchpad.net natty/main Sources [675 B]                     
Get:49 http://ppa.launchpad.net natty/main i386 Packages [888 B]               
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://extras.ubuntu.com natty/main Translation-en                         
Get:50 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]
Get:51 http://security.ubuntu.com natty-security/universe i386 Packages [31.9 kB]
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://dl.google.com stable/main Translation-en                            
Get:52 http://security.ubuntu.com natty-security/multiverse i386 Packages [2,074 B]
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex     
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex     
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://ppa.launchpad.net natty/main Translation-en_US                     
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://ppa.launchpad.net natty/main Translation-en_US                     
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://ppa.launchpad.net natty/main Translation-en_US                     
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://ppa.launchpad.net natty/main Translation-en_US                     
Ign http://ppa.launchpad.net natty/main Translation-en                         
Get:53 http://lk.archive.ubuntu.com natty/restricted Sources [4,104 B]         
Get:54 http://lk.archive.ubuntu.com natty/universe Sources [4,380 kB]          
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Get:55 http://lk.archive.ubuntu.com natty/multiverse Sources [155 kB]          
Get:56 http://lk.archive.ubuntu.com natty/main i386 Packages [1,550 kB]        
Get:57 http://lk.archive.ubuntu.com natty/restricted i386 Packages [8,986 B]   
Get:58 http://lk.archive.ubuntu.com natty/universe i386 Packages [6,021 kB]    
Get:59 http://lk.archive.ubuntu.com natty/multiverse i386 Packages [183 kB]    
Ign http://lk.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://lk.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://lk.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://lk.archive.ubuntu.com natty/universe TranslationIndex               
Get:60 http://lk.archive.ubuntu.com natty-updates/main Sources [98.2 kB]       
Get:61 http://lk.archive.ubuntu.com natty-updates/restricted Sources [14 B]    
Get:62 http://lk.archive.ubuntu.com natty-updates/universe Sources [22.6 kB]   
Get:63 http://lk.archive.ubuntu.com natty-updates/multiverse Sources [1,893 B] 
Get:64 http://lk.archive.ubuntu.com natty-updates/main i386 Packages [286 kB]  
Get:65 http://lk.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:66 http://lk.archive.ubuntu.com natty-updates/universe i386 Packages [82.0 kB]
Get:67 http://lk.archive.ubuntu.com natty-updates/multiverse i386 Packages [4,267 B]
Ign http://lk.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://lk.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://lk.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://lk.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://lk.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://lk.archive.ubuntu.com natty/main Translation-en
Ign http://lk.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://lk.archive.ubuntu.com natty/multiverse Translation-en
Ign http://lk.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://lk.archive.ubuntu.com natty/restricted Translation-en
Ign http://lk.archive.ubuntu.com natty/universe Translation-en_US
Ign http://lk.archive.ubuntu.com natty/universe Translation-en
Ign http://lk.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://lk.archive.ubuntu.com natty-updates/main Translation-en
Ign http://lk.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://lk.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://lk.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://lk.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://lk.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://lk.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 14.2 MB in 23min 50s (9,932 B/s)
W: Failed to fetch http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
assassin@genupulas:~$ 

```thanks in  advance

---

### Post by wildmanne39 on 2011-08-08
Hi, it look like that ppa is not on the server or the server is down. You can open synaptic and click on settings, repositories, other software tab and uncheck or remove.
> [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/natty/main/source/Sources)
[http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/natty/main/binary-i386/Packages)
Then it should work ok.
Thanks

---

### Post by raja.genupula on 2011-08-09
yeah i will try it when i get back to room . thanks for looking  my thread.

---

### Post by wildmanne39 on 2011-08-09
Hi, your welcome! I hope it works.

---

### Post by raja.genupula on 2011-08-09
hey its done man , but tell me one thing , why some things are ignoring in the above output i have given

---

### Post by wildmanne39 on 2011-08-09
Hi, I image it is because those ppa's were not working.

Run the updates again and see if that message is gone.

---

### Post by raja.genupula on 2011-08-09
for example like this why i am getting , 

Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                       Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                                Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                    Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                         Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                       Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                    Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                    Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                    Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty InRelease                                Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates InRelease

---

