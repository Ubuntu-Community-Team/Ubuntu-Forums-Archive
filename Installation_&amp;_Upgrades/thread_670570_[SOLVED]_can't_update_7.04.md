---
title: "[SOLVED] can't update 7.04"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by prezbedard on 2008-01-17
I recently installed ubuntu 7.04 on a test system at work. When I went to update it I got a whole lot of errors of being unable to connect to the source. I first though it might have something to so with our webfilter but no. Here is what I get when I run aptitude or update manager

```
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Err http://us.archive.ubuntu.com feisty Release.gpg   
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Get:2 http://us.archive.ubuntu.com feisty/main Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]
Get:5 http://security.ubuntu.com feisty-security/main Translation-en_US
Get:6 http://security.ubuntu.com feisty-security/restricted Translation-en_US
Get:7 http://us.archive.ubuntu.com feisty/universe Translation-en_US
Get:8 http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:9 http://security.ubuntu.com feisty-security/universe Translation-en_US   
98% [2 Translation-en_US bzip2 0] [Waiting for headers] [Connecting to security.bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                  
Get:10 http://security.ubuntu.com feisty-security/multiverse Translation-en_US  
87% [5 Translation-en_US bzip2 0] [Waiting for headers] [Connecting to security.bzip2: (stdin) is not a bzip2 file.
Get:11 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Hit http://security.ubuntu.com feisty-security Release                          
Ign http://security.ubuntu.com feisty-security/main Translation-en_US           
Get:12 http://us.archive.ubuntu.com feisty-updates/main Translation-en_US       
Get:13 http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US 
Hit http://us.archive.ubuntu.com feisty Release                                 
Hit http://us.archive.ubuntu.com feisty-updates Release                         
80% [Release gpgv 50880] [6 Translation-en_US bzip2 0] [Connecting to us.archivebzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US     
70% [Release gpgv 50880] [3 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US        
61% [Release gpgv 50880] [7 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US          
51% [Release gpgv 50880] [8 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US        
43% [Release gpgv 50880] [9 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US   
34% [Release gpgv 50880] [10 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US  
20% [Release gpgv 50880] [12 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US       
11% [Release gpgv 50880] [13 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US 
Get:14 http://us.archive.ubuntu.com feisty/main Packages                        
Get:15 http://us.archive.ubuntu.com feisty/restricted Packages                  
77% [Release gpgv 50878] [14 Packages bzip2 0] [Waiting for headers] [Waiting fobzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/main Packages                           
  Sub-process bzip2 returned an error code (2)
77% [Release gpgv 50878] [15 Packages bzip2 0] [Waiting for headers] [Waiting fobzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/restricted Packages                     
  Sub-process bzip2 returned an error code (2)
Get:16 http://security.ubuntu.com feisty-security/main Packages                 
86% [16 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/main Packages         
  Sub-process bzip2 returned an error code (2)
Get:17 http://security.ubuntu.com feisty-security/restricted Packages
87% [17 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:18 http://us.archive.ubuntu.com feisty/main Sources              
Err http://security.ubuntu.com feisty-security/restricted Packages              
  Sub-process bzip2 returned an error code (2)
Get:19 http://us.archive.ubuntu.com feisty/restricted Sources                   
87% [18 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/main Sources                
  Sub-process bzip2 returned an error code (2)
87% [19 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/restricted Sources          
  Sub-process bzip2 returned an error code (2)
Get:20 http://security.ubuntu.com feisty-security/main Sources      
87% [20 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/main Sources         
  Sub-process bzip2 returned an error code (2)
Get:21 http://security.ubuntu.com feisty-security/restricted Sources
87% [21 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/restricted Sources   
  Sub-process bzip2 returned an error code (2)
Get:22 http://us.archive.ubuntu.com feisty/universe Packages        
87% [22 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/universe Packages            
  Sub-process bzip2 returned an error code (2)
Get:23 http://security.ubuntu.com feisty-security/universe Packages  
88% [23 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/universe Packages     
  Sub-process bzip2 returned an error code (2)
Get:24 http://security.ubuntu.com feisty-security/universe Sources   
88% [24 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/universe Sources     
  Sub-process bzip2 returned an error code (2)
Get:25 http://security.ubuntu.com feisty-security/multiverse Packages
Get:26 http://security.ubuntu.com feisty-security/multiverse Sources        
Get:27 http://us.archive.ubuntu.com feisty/universe Sources                 
88% [25 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/multiverse Packages
  Sub-process bzip2 returned an error code (2)
88% [26 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/multiverse Sources
  Sub-process bzip2 returned an error code (2)
88% [27 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/universe Sources
  Sub-process bzip2 returned an error code (2)
Get:28 http://us.archive.ubuntu.com feisty/multiverse Packages
88% [28 Packages bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.88.31)]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/multiverse Packages                   
  Sub-process bzip2 returned an error code (2)
Get:29 http://us.archive.ubuntu.com feisty/multiverse Sources                 
88% [29 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/multiverse Sources
  Sub-process bzip2 returned an error code (2)
Get:30 http://us.archive.ubuntu.com feisty-updates/main Packages
89% [30 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty-updates/main Packages
  Sub-process bzip2 returned an error code (2)
Get:31 http://us.archive.ubuntu.com feisty-updates/restricted Packages
89% [31 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty-updates/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:32 http://us.archive.ubuntu.com feisty-updates/main Sources
89% [32 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty-updates/main Sources
  Sub-process bzip2 returned an error code (2)
Get:33 http://us.archive.ubuntu.com feisty-updates/restricted Sources
89% [33 Sources bzip2 0]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty-updates/restricted Sources
  Sub-process bzip2 returned an error code (2)
Fetched 50.8kB in 2s (22.9kB/s)
Reading package lists... Done
linda@linda-desktop:~$ sudo aptitude update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Get:2 http://security.ubuntu.com feisty-security/main Translation-en_US         
Get:3 http://us.archive.ubuntu.com feisty Release.gpg [191B]                    
Get:4 http://us.archive.ubuntu.com feisty/main Translation-en_US            
Get:5 http://security.ubuntu.com feisty-security/restricted Translation-en_US
Get:6 http://security.ubuntu.com feisty-security/universe Translation-en_US 
Get:7 http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Get:8 http://us.archive.ubuntu.com feisty/restricted Translation-en_US       
99% [2 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.8bzip2: (stdin) is not a bzip2 file.
Hit http://security.ubuntu.com feisty-security Release                          
Ign http://security.ubuntu.com feisty-security/main Translation-en_US           
85% [Release gpgv 50880] [4 Translation-en_US bzip2 0] [Connecting to us.archivebzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                  
64% [Release gpgv 50880] [5 Translation-en_US bzip2 0] [Connecting to us.archivebzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US     
54% [Release gpgv 50880] [6 Translation-en_US bzip2 0] [Connecting to us.archivebzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US       
39% [Release gpgv 50880] [7 Translation-en_US bzip2 0] [Connecting to us.archivebzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US     
18% [Release gpgv 50880] [8 Translation-en_US bzip2 0] [Connecting to us.archivebzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US            
Get:9 http://us.archive.ubuntu.com feisty/universe Translation-en_US            
Get:10 http://us.archive.ubuntu.com feisty/multiverse Translation-en_US      
83% [9 Translation-en_US bzip2 0] [Waiting for headers] [Connecting to security.bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US              
Get:11 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Get:12 http://us.archive.ubuntu.com feisty-updates/main Translation-en_US     
82% [10 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.bzip2: (stdin) is not a bzip2 file.
Get:13 http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US            
80% [12 Translation-en_US bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Hit http://us.archive.ubuntu.com feisty Release                               
Hit http://us.archive.ubuntu.com feisty-updates Release                         
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US          
78% [Release gpgv 57158] [13 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US 
Get:14 http://security.ubuntu.com feisty-security/main Packages                 
Get:15 http://security.ubuntu.com feisty-security/restricted Packages           
90% [14 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/main Packages         
  Sub-process bzip2 returned an error code (2)
90% [15 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/restricted Packages   
  Sub-process bzip2 returned an error code (2)
Get:16 http://us.archive.ubuntu.com feisty/main Packages             
90% [16 Packages bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.88.45)] [bzip2: (stdin) is not a bzip2 file.
Get:17 http://us.archive.ubuntu.com feisty/restricted Packages                  
Err http://us.archive.ubuntu.com feisty/main Packages                           
  Sub-process bzip2 returned an error code (2)
91% [17 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:18 http://security.ubuntu.com feisty-security/main Sources       
Get:19 http://security.ubuntu.com feisty-security/restricted Sources 
Err http://us.archive.ubuntu.com feisty/restricted Packages          
  Sub-process bzip2 returned an error code (2)
91% [18 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/main Sources         
  Sub-process bzip2 returned an error code (2)
91% [19 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/restricted Sources   
  Sub-process bzip2 returned an error code (2)
Get:20 http://us.archive.ubuntu.com feisty/main Sources             
91% [20 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/main Sources                
  Sub-process bzip2 returned an error code (2)
Get:21 http://us.archive.ubuntu.com feisty/restricted Sources       
91% [21 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/restricted Sources          
  Sub-process bzip2 returned an error code (2)
Get:22 http://security.ubuntu.com feisty-security/universe Packages 
Get:23 http://security.ubuntu.com feisty-security/universe Sources          
Get:24 http://security.ubuntu.com feisty-security/multiverse Packages       
Get:25 http://security.ubuntu.com feisty-security/multiverse Sources        
91% [22 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/universe Packages
  Sub-process bzip2 returned an error code (2)
91% [23 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/universe Sources
  Sub-process bzip2 returned an error code (2)
Get:26 http://us.archive.ubuntu.com feisty/universe Packages
91% [24 Packages bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/multiverse Packages            
  Sub-process bzip2 returned an error code (2)
91% [25 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com feisty-security/multiverse Sources
  Sub-process bzip2 returned an error code (2)
91% [26 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:27 http://us.archive.ubuntu.com feisty/universe Sources
91% [27 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/universe Sources
  Sub-process bzip2 returned an error code (2)
Get:28 http://us.archive.ubuntu.com feisty/multiverse Packages
91% [28 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get:29 http://us.archive.ubuntu.com feisty/multiverse Sources
91% [29 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty/multiverse Sources
  Sub-process bzip2 returned an error code (2)
Get:30 http://us.archive.ubuntu.com feisty-updates/main Packages
92% [30 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty-updates/main Packages
  Sub-process bzip2 returned an error code (2)
Get:31 http://us.archive.ubuntu.com feisty-updates/restricted Packages
92% [31 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty-updates/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:32 http://us.archive.ubuntu.com feisty-updates/main Sources
92% [32 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty-updates/main Sources
  Sub-process bzip2 returned an error code (2)
Get:33 http://us.archive.ubuntu.com feisty-updates/restricted Sources
92% [33 Sources bzip2 0]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com feisty-updates/restricted Sources
  Sub-process bzip2 returned an error code (2)
Fetched 53.8kB in 2s (20.7kB/s)
Reading package lists... Done
linda@linda-desktop:~$ Get:19 http://us.archive.ubuntu.com feisty/restricted Sources                   
bash: Get:19: command not found
linda@linda-desktop:~$ 87% [18 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
bash: syntax error near unexpected token `('
linda@linda-desktop:~$ Err http://us.archive.ubuntu.com feisty/main Sources                
bash: Err: command not found
linda@linda-desktop:~$   Sub-process bzip2 returned an error code (2)
bash: syntax error near unexpected token `('
linda@linda-desktop:~$ 87% [19 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
bash: syntax error near unexpected token `('
linda@linda-desktop:~$ Err http://us.archive.ubuntu.com feisty/restricted Sources          
bash: Err: command not found
linda@linda-desktop:~$   Sub-process bzip2 returned an error code (2)
bash: syntax error near unexpected token `('
linda@linda-desktop:~$ Get:20 http://security.ubuntu.com feisty-security/main Sources      
bash: Get:20: command not found
linda@linda-desktop:~$ 87% [20 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
bash: syntax error near unexpected token `('
linda@linda-desktop:~$ Err http://security.ubuntu.com feisty-security/main Sources         
bash: Err: command not found



```

---

### Post by zvacet on 2008-01-17
```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by prezbedard on 2008-01-17
never mind turns out it was the web filter guess it took just a bit longer for the new setting to settle in then I thought. Working now. Thanks!

---

