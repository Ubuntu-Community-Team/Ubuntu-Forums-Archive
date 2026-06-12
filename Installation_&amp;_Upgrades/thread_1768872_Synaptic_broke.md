---
title: "Synaptic broke"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by afajknaz on 2011-05-27
I installed [Double Commander]("http://sourceforge.net/projects/doublecmd/") only to find that it was broken and couldn't launch. So searched and found it was a known problem and fixed already in unstable version. There is a build on [Launchpad]("https://launchpad.net/%7Ealexx2000/+archive/doublecmd").
So:
```
sudo add-apt-repository ppa:alexx2000/doublecmd
```It finished fine. When I reloaded my Synaptic window, it did some work and I saw the first errors: Error 404 in IIRC 3 different places. Then came another error, I didn't understand it and clicked a button. Synaptic closed.
I think I know what was the 2nd error because no every time I start Synaptic, it shows a message and after I click the only available button (Close), it quits.
The message is:
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/
pl.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The packege lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by mörgæs on 2011-05-27
Hi, welcome to the fora.

Try to boot the computer and run

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by afajknaz on 2011-05-27
Thanks for fast reply. It didn't help though:
```
m@m-Nokia-Booklet-3G:/var/lib/apt/lists$ sudo rm /var/lib/apt/lists/* -vf
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
m@m-Nokia-Booklet-3G:/var/lib/apt/lists$ sudo apt-get clean
m@m-Nokia-Booklet-3G:/var/lib/apt/lists$ sudo apt-get update
Ign http://pl.archive.ubuntu.com natty InRelease                              
Ign http://pl.archive.ubuntu.com natty-updates InRelease                      
Ign http://ppa.launchpad.net natty InRelease                                  
Ign http://ppa.launchpad.net natty InRelease                                  
Ign http://security.ubuntu.com natty-security InRelease                       
Get:1 http://pl.archive.ubuntu.com natty Release.gpg [198 B]                  
Ign http://ppa.launchpad.net natty Release.gpg                                
Get:2 http://security.ubuntu.com natty-security Release.gpg [198 B]           
Get:3 http://pl.archive.ubuntu.com natty-updates Release.gpg [198 B]          
Get:4 http://ppa.launchpad.net natty Release.gpg [316 B]                      
Get:5 http://security.ubuntu.com natty-security Release [27.2 kB]             
Get:6 http://pl.archive.ubuntu.com natty Release [39.8 kB]                    
Ign http://ppa.launchpad.net natty Release                                    
Get:7 http://ppa.launchpad.net natty Release [9,739 B]                        
Get:8 http://pl.archive.ubuntu.com natty-updates Release [27.2 kB]            
Get:9 http://security.ubuntu.com natty-security/main Sources [8,285 B]        
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Get:10 http://ppa.launchpad.net natty/main Sources [14.6 kB]                  
Get:11 http://security.ubuntu.com natty-security/restricted Sources [14 B]    
Get:12 http://security.ubuntu.com natty-security/universe Sources [2,691 B]   
Get:13 http://pl.archive.ubuntu.com natty/main Sources [862 kB]               
Get:14 http://ppa.launchpad.net natty/main i386 Packages [18.8 kB]            
Get:15 http://security.ubuntu.com natty-security/multiverse Sources [647 B]   
Get:16 http://security.ubuntu.com natty-security/main i386 Packages [25.3 kB] 
Get:17 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Get:18 http://security.ubuntu.com natty-security/universe i386 Packages [10.1 kB]
Get:19 http://security.ubuntu.com natty-security/multiverse i386 Packages [2,071 B]
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
Ign http://security.ubuntu.com natty-security/main Translation-en_US          
Ign http://security.ubuntu.com natty-security/main Translation-en             
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en         
Get:20 http://extras.ubuntu.com natty InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                  
Get:21 http://extras.ubuntu.com natty/main TranslationIndex                   
Get:22 http://extras.ubuntu.com natty/main Sources                            
Get:23 http://extras.ubuntu.com natty/main i386 Packages                      
85% [22 Sources xz 0 B] [13 Sources 728 kB/862 kB 84%] [23 Packages 1,182 B]/usr/bin/xz: (stdin): File format not recognized
90% [23 Packages xz 0 B] [13 Sources 775 kB/862 kB 89%]           39.8 kB/s 2s/usr/bin/xz: (stdin): File format not recognized
97% [22 Sources lzma 0 B] [13 Sources 857 kB/862 kB 99%] [Waiting for headers]/usr/bin/lzma: Decoder error
Get:24 http://pl.archive.ubuntu.com natty/restricted Sources [4,104 B]        
Get:25 http://pl.archive.ubuntu.com natty/universe Sources [4,380 kB]         
Get:26 http://extras.ubuntu.com natty/main Translation-en_US                  
23% [26 Translation-en_US xz 0 B] [13 Sources bzip2 0 B] [25 Sources 123 kB/4,/usr/bin/xz: (stdin): File format not recognized
Get:27 http://extras.ubuntu.com natty/main Translation-en                     
26% [27 Translation-en xz 0 B] [25 Sources 297 kB/4,380 kB 6%]/usr/bin/xz: (stdin): File format not recognized
30% [23 Packages lzma 0 B] [25 Sources 492 kB/4,380 kB 11%] [Connecting to ext/usr/bin/lzma: Decoder error
33% [26 Translation-en_US lzma 0 B] [25 Sources 702 kB/4,380 kB 16%] [Waiting /usr/bin/lzma: Decoder error
36% [27 Translation-en lzma 0 B] [25 Sources 820 kB/4,380 kB 18%] [Waiting for/usr/bin/lzma: Decoder error
Get:28 http://pl.archive.ubuntu.com natty/multiverse Sources [155 kB]         
Get:29 http://pl.archive.ubuntu.com natty/main i386 Packages [1,550 kB]       
Get:30 http://pl.archive.ubuntu.com natty/restricted i386 Packages [8,986 B]  
Get:31 http://pl.archive.ubuntu.com natty/universe i386 Packages [6,021 kB]   
Get:32 http://pl.archive.ubuntu.com natty/multiverse i386 Packages [183 kB]   
Ign http://pl.archive.ubuntu.com natty/main TranslationIndex                  
Ign http://pl.archive.ubuntu.com natty/multiverse TranslationIndex            
Ign http://pl.archive.ubuntu.com natty/restricted TranslationIndex            
Ign http://pl.archive.ubuntu.com natty/universe TranslationIndex              
Get:33 http://pl.archive.ubuntu.com natty-updates/main Sources [30.3 kB]      
Get:34 http://pl.archive.ubuntu.com natty-updates/restricted Sources [14 B]   
Get:35 http://pl.archive.ubuntu.com natty-updates/universe Sources [7,976 B]  
Get:36 http://pl.archive.ubuntu.com natty-updates/multiverse Sources [1,362 B]
Get:37 http://pl.archive.ubuntu.com natty-updates/main i386 Packages [104 kB] 
Get:38 http://pl.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:39 http://pl.archive.ubuntu.com natty-updates/universe i386 Packages [40.5 kB]
Get:40 http://pl.archive.ubuntu.com natty-updates/multiverse i386 Packages [3,754 B]
Ign http://pl.archive.ubuntu.com natty-updates/main TranslationIndex          
Ign http://pl.archive.ubuntu.com natty-updates/multiverse TranslationIndex    
Ign http://pl.archive.ubuntu.com natty-updates/restricted TranslationIndex    
Ign http://pl.archive.ubuntu.com natty-updates/universe TranslationIndex      
Ign http://pl.archive.ubuntu.com natty/main Translation-en_US                 
Ign http://pl.archive.ubuntu.com natty/main Translation-en                    
Ign http://pl.archive.ubuntu.com natty/multiverse Translation-en_US           
Ign http://pl.archive.ubuntu.com natty/multiverse Translation-en              
Ign http://pl.archive.ubuntu.com natty/restricted Translation-en_US           
Ign http://pl.archive.ubuntu.com natty/restricted Translation-en              
Ign http://pl.archive.ubuntu.com natty/universe Translation-en_US             
Ign http://pl.archive.ubuntu.com natty/universe Translation-en                
Ign http://pl.archive.ubuntu.com natty-updates/main Translation-en_US         
Ign http://pl.archive.ubuntu.com natty-updates/main Translation-en            
Ign http://pl.archive.ubuntu.com natty-updates/multiverse Translation-en_US   
Ign http://pl.archive.ubuntu.com natty-updates/multiverse Translation-en      
Ign http://pl.archive.ubuntu.com natty-updates/restricted Translation-en_US   
Ign http://pl.archive.ubuntu.com natty-updates/restricted Translation-en      
Ign http://pl.archive.ubuntu.com natty-updates/universe Translation-en_US     
Ign http://pl.archive.ubuntu.com natty-updates/universe Translation-en        
Fetched 13.7 MB in 4min 6s (55.7 kB/s)                                        
W: GPG error: http://extras.ubuntu.com natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://ppa.launchpad.net//alexx2000/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net//alexx2000/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
m@m-Nokia-Booklet-3G:/var/lib/apt/lists$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```
Now I see that it talks about "ppa.launchpad.net//" (with double slash), I guess that's the problem?

---

### Post by afajknaz on 2011-05-27
I found a program called 'Software sources' and fixed the slashes. Then I followed the advice again. It fixed my Synaptic, thanks!

---

### Post by ceaucari on 2011-05-27
It seems that i have the same problem, 

when i try to run synsptic it gives me the same message

 ```

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

coud you be more specific about the software you use to solve
the problem
> 
I found a program called 'Software sources' and fixed the slashes. Then I followed the advice again. It fixed my Synaptic, thanks!

thanks in advance!

---

### Post by ceaucari on 2011-05-27
Nevermind, i found it,
in case someone else is looking for it, 

 it's under:

System Settings->Main Menu->System->Administration

---

### Post by mörgæs on 2011-05-28
Good that it works. Please mark the thread 'solved' Afajknaz, as this will help other users find the solution.

---

