---
title: "Oneric update problem - Failed to download repository information"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by nicki20048 on 2012-01-06
I have just done a fresh install of 11.10 on my new laptop but when I go to install the updates it keeps giving the following error:

'Failed to download repository information'

When I click on 'details' it gives the following info:

> W:Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.166 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I have tried using different repositories but the problem still exists.

Hope somebody can help

---

### Post by Cookieh on 2012-01-06
looks like the website is either down or it is incorrectly spelled... I would rewrite and redownload the iso boot image... That might work

---

### Post by ajgreeny on 2012-01-06
You should not need to do that.

I think you just need to remove any files from /var/lib/apt/lists/partial with ```
sudo rm /lib/apt/lists/partial/*
```Then try again to update.

---

### Post by nicki20048 on 2012-01-06
> **ajgreeny said:**
> You should not need to do that.

I think you just need to remove any files from /var/lib/apt/lists/partial with ```
sudo rm /lib/apt/lists/partial/*
```Then try again to update.

Thanks but i'm getting 'No such file or directory'

---

### Post by cortman on 2012-01-06
> **nicki20048 said:**
> Thanks but i'm getting 'No such file or directory'

Just a slight typo-

```
/var/lib/apt/lists/partial
```

---

### Post by nicki20048 on 2012-01-06
> **cortman said:**
> Just a slight typo-

```
/var/lib/apt/lists/partial
```
Still no luck.

This is what I get when I run apt-get update:

```
sudo apt-get update
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease                      
Get:1 http://archive.canonical.com oneiric Release.gpg [198 B]       
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Ign http://security.ubuntu.com oneiric-security InRelease                      
Get:3 http://archive.canonical.com oneiric Release [5,922 B]         
Get:4 http://extras.ubuntu.com oneiric Release [9,759 B]                       
Ign http://gb.archive.ubuntu.com oneiric InRelease                             
Ign http://gb.archive.ubuntu.com oneiric-security InRelease                    
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                     
Get:5 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Get:6 http://archive.canonical.com oneiric/partner amd64 Packages [3,081 B]    
Get:7 http://extras.ubuntu.com oneiric/main Sources [14 B]                     
Get:8 http://archive.canonical.com oneiric/partner i386 Packages [3,943 B]     
Get:9 http://extras.ubuntu.com oneiric/main amd64 Packages [14 B]              
Get:10 http://extras.ubuntu.com oneiric/main i386 Packages [14 B]              
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Get:11 http://security.ubuntu.com oneiric-security Release [40.8 kB]           
Err http://gb.archive.ubuntu.com oneiric Release.gpg                           
  Bad header line
Ign http://gb.archive.ubuntu.com oneiric-security Release.gpg                  
Err http://gb.archive.ubuntu.com oneiric-updates Release.gpg                   
  Bad header line
Ign http://gb.archive.ubuntu.com oneiric Release                               
Ign http://gb.archive.ubuntu.com oneiric-security Release                      
Ign http://gb.archive.ubuntu.com oneiric-updates Release                       
Get:12 http://security.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]
Get:13 http://security.ubuntu.com oneiric-security/main amd64 Packages [64.9 kB]
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:14 http://security.ubuntu.com oneiric-security/multiverse amd64 Packages [919 B]
Get:15 http://security.ubuntu.com oneiric-security/universe amd64 Packages [22.3 kB]
99% [15 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitin
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign http://security.ubuntu.com oneiric-security/main TranslationIndex          
Ign http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://security.ubuntu.com oneiric-security/universe TranslationIndex
Get:16 http://security.ubuntu.com oneiric-security/main i386 Packages [1,486 B]
Get:17 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [25.8 kB]
Get:18 http://security.ubuntu.com oneiric-security/main Translation-en_GB [34.5 kB]
Get:19 http://security.ubuntu.com oneiric-security/multiverse Translation-en_GB [840 B]
Get:20 http://security.ubuntu.com oneiric-security/restricted Translation-en_GB [14 B]
Get:21 http://security.ubuntu.com oneiric-security/universe Translation-en_GB [16.0 kB]
Err http://security.ubuntu.com oneiric-security/universe amd64 Packages        
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com oneiric-security/restricted i386 Packages       
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com oneiric-security/universe i386 Packages         
  404  Not Found [IP: 91.189.92.166 80]
Get:22 http://security.ubuntu.com oneiric-security/universe Translation-en [40.7 kB]
Get:23 http://security.ubuntu.com oneiric-security/main Translation-en [762 B] 
99% [22 Translation-en lzma 0 B] [Waiting for headers] [Waiting for headers] [W/usr/bin/lzma: Decoder error
Get:24 http://security.ubuntu.com oneiric-security/multiverse Translation-en [20 B]
Get:25 http://security.ubuntu.com oneiric-security/restricted Translation-en [16.4 kB]
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Get:26 http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]  
Get:27 http://gb.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B] 
Get:28 http://gb.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]  
Get:29 http://gb.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]      
Get:30 http://gb.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]    
Get:31 http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]
Get:32 http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]
Get:33 http://gb.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]
Get:34 http://gb.archive.ubuntu.com oneiric-security/restricted Sources [14 B] 
Get:35 http://gb.archive.ubuntu.com oneiric-security/main Sources [23.0 kB]    
Get:36 http://gb.archive.ubuntu.com oneiric-security/multiverse Sources [653 B]
Get:37 http://gb.archive.ubuntu.com oneiric-security/universe Sources [8,189 B]
Get:38 http://gb.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:39 http://gb.archive.ubuntu.com oneiric-updates/main Sources [110 kB]      
Get:40 http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources [2,916 B]
Get:41 http://gb.archive.ubuntu.com oneiric-updates/universe Sources [35.4 kB] 
Get:42 http://gb.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]
Get:43 http://gb.archive.ubuntu.com oneiric-updates/main amd64 Packages [251 kB]
Get:44 http://gb.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [4,342 B]
Get:45 http://gb.archive.ubuntu.com oneiric-updates/universe amd64 Packages [83.0 kB]
Get:46 http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:47 http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages [251 kB]
Get:48 http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [4,976 B]
Get:49 http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages [83.3 kB]
Get:50 http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:51 http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:52 http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:53 http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Get:54 http://gb.archive.ubuntu.com oneiric/main Translation-en_GB [69.0 kB]   
Get:55 http://gb.archive.ubuntu.com oneiric/main Translation-en [701 kB]       
Get:56 http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB [68.5 kB]
Get:57 http://gb.archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]
Get:58 http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB [1,937 B]
Get:59 http://gb.archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]
Get:60 http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB [4,365 B]
Get:61 http://gb.archive.ubuntu.com oneiric/universe Translation-en [3,165 kB] 
Get:62 http://gb.archive.ubuntu.com oneiric-updates/main Translation-en [117 kB]
Get:63 http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en [3,000 B]
Get:64 http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en [508 B]
Get:65 http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en [50.7 kB]
Get:66 http://gb.archive.ubuntu.com oneiric/restricted Sources [5,267 B]       
Get:67 http://gb.archive.ubuntu.com oneiric/main Sources [1,095 kB]            
Get:68 http://gb.archive.ubuntu.com oneiric/multiverse Sources [180 kB]        
Get:69 http://gb.archive.ubuntu.com oneiric/universe Sources [5,792 kB]        
Get:70 http://gb.archive.ubuntu.com oneiric/multiverse amd64 Packages [149 kB] 
Get:71 http://gb.archive.ubuntu.com oneiric/restricted amd64 Packages [8,905 B]
Get:72 http://gb.archive.ubuntu.com oneiric/universe amd64 Packages [5,758 kB] 
Get:73 http://gb.archive.ubuntu.com oneiric/main amd64 Packages [1,583 kB]     
Fetched 25.8 MB in 3min 52s (111 kB/s)                                         
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Bad header line

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg  Bad header line

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.166 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by nicki20048 on 2012-01-07
Anybody got any ideas? Removing those lists and running apt-get update doesn't seem to have solved anythiing.

I can't even download anything from the software centre while I have this problem. So any help is much appreciated.

---

### Post by Myddna on 2012-01-10
Exactly the same thing here, only that I'm using 386 version.

Also, some "bad header line" when trying to update.

Edit: Changed the mirror to rediris. only bzip error remains
```

Des:8 http://sunsite.rediris.es oneiric/main i386 Packages [1226 kB]          
86% [4 Sources bzip2 0 B] [8 Packages 261 kB/1226 kB 21%] [Waiting for headers
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

```
Complete log:
```

marta@tardis:~$ sudo rm -R /var/lib/apt/lists/partial/*
marta@tardis:~$ sudo vi /etc/apt/sources.list
marta@tardis:~$ sudo apt-get update && sudo apt-get upgrade
Ign http://sunsite.rediris.es oneiric InRelease
Ign http://es.archive.ubuntu.com oneiric-updates InRelease
Ign http://es.archive.ubuntu.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease
Des:1 http://sunsite.rediris.es oneiric Release.gpg [198 B]
Obj http://es.archive.ubuntu.com oneiric-updates Release.gpg                  
Obj http://security.ubuntu.com oneiric-security Release.gpg
Obj http://es.archive.ubuntu.com oneiric Release.gpg
Obj http://security.ubuntu.com oneiric-security Release
Des:2 http://sunsite.rediris.es oneiric Release [40,8 kB]             
Obj http://es.archive.ubuntu.com oneiric-updates Release                    
Obj http://es.archive.ubuntu.com oneiric Release                              
Obj http://security.ubuntu.com oneiric-security/main Sources                  
Obj http://es.archive.ubuntu.com oneiric-updates/main Sources                 
Obj http://es.archive.ubuntu.com oneiric-updates/restricted Sources
Obj http://es.archive.ubuntu.com oneiric-updates/universe Sources
Obj http://es.archive.ubuntu.com oneiric-updates/multiverse Sources
Obj http://es.archive.ubuntu.com oneiric-updates/main i386 Packages
Obj http://es.archive.ubuntu.com oneiric-updates/restricted i386 Packages     
Obj http://es.archive.ubuntu.com oneiric-updates/universe i386 Packages       
Obj http://es.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Obj http://es.archive.ubuntu.com oneiric-updates/main TranslationIndex
Obj http://es.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex  
Obj http://security.ubuntu.com oneiric-security/restricted Sources            
Obj http://security.ubuntu.com oneiric-security/universe Sources              
Obj http://security.ubuntu.com oneiric-security/multiverse Sources
Des:3 http://security.ubuntu.com oneiric-security/main i386 Packages [65,2 kB]
Obj http://es.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Obj http://es.archive.ubuntu.com oneiric-updates/universe TranslationIndex    
Des:4 http://es.archive.ubuntu.com oneiric/universe Sources [4677 kB]
Obj http://security.ubuntu.com oneiric-security/restricted i386 Packages      
Des:5 http://security.ubuntu.com oneiric-security/universe i386 Packages [22,2 kB]
Obj http://security.ubuntu.com oneiric-security/multiverse i386 Packages      
Obj http://security.ubuntu.com oneiric-security/main TranslationIndex
Obj http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Obj http://security.ubuntu.com oneiric-security/restricted TranslationIndex   
Obj http://security.ubuntu.com oneiric-security/universe TranslationIndex     
Obj http://security.ubuntu.com oneiric-security/main Translation-en           
Obj http://security.ubuntu.com oneiric-security/multiverse Translation-en     
Obj http://security.ubuntu.com oneiric-security/restricted Translation-en
Obj http://security.ubuntu.com oneiric-security/universe Translation-en
Des:6 http://sunsite.rediris.es oneiric/main Sources [877 kB]                 
Des:7 http://sunsite.rediris.es oneiric/restricted Sources [5351 B]           
Des:8 http://sunsite.rediris.es oneiric/main i386 Packages [1226 kB]          
86% [4 Sources bzip2 0 B] [8 Packages 261 kB/1226 kB 21%] [Waiting for headers
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Des:9 http://sunsite.rediris.es oneiric/restricted i386 Packages [8216 B]     
Des:10 http://sunsite.rediris.es oneiric/main TranslationIndex [3289 B]       
Des:11 http://sunsite.rediris.es oneiric/restricted TranslationIndex [2263 B] 
Des:12 http://sunsite.rediris.es oneiric/main Translation-es [681 kB]         
Des:13 http://sunsite.rediris.es oneiric/main Translation-en [701 kB]         
Des:14 http://sunsite.rediris.es oneiric/restricted Translation-es [2533 B]   
Des:15 http://sunsite.rediris.es oneiric/restricted Translation-en [2229 B]  
Des:16 http://es.archive.ubuntu.com oneiric/multiverse Sources [149 kB]       
Des:17 http://es.archive.ubuntu.com oneiric/universe i386 Packages [4468 kB]
Des:18 http://es.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB] 
Obj http://es.archive.ubuntu.com oneiric/multiverse TranslationIndex          
Obj http://es.archive.ubuntu.com oneiric/universe TranslationIndex            
Obj http://es.archive.ubuntu.com oneiric-updates/main Translation-en          
Obj http://es.archive.ubuntu.com oneiric-updates/multiverse Translation-en    
Obj http://es.archive.ubuntu.com oneiric-updates/restricted Translation-en    
Obj http://es.archive.ubuntu.com oneiric-updates/universe Translation-en      
Obj http://es.archive.ubuntu.com oneiric/multiverse Translation-es            
Obj http://es.archive.ubuntu.com oneiric/multiverse Translation-en            
Obj http://es.archive.ubuntu.com oneiric/universe Translation-es              
Obj http://es.archive.ubuntu.com oneiric/universe Translation-en              
Descargados 13,1 MB en 2min 26s (89,2 kB/s)                                   
W: Failed to fetch gzip:/var/lib/apt/lists/partial/es.archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/es.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/es.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/es.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Jan 11th:
```

marta@tardis:~$ sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease
Obj http://extras.ubuntu.com oneiric Release.gpg
Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Ign http://us.archive.ubuntu.com oneiric-backports InRelease
Ign http://security.ubuntu.com oneiric-security InRelease
Obj http://extras.ubuntu.com oneiric Release   
Obj http://extras.ubuntu.com oneiric/main Sources                    
Des:1 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]
Obj http://security.ubuntu.com oneiric-security Release.gpg                     
Obj http://us.archive.ubuntu.com oneiric-updates Release.gpg
Obj http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports Release.gpg
Obj http://security.ubuntu.com oneiric-security Release
Obj http://security.ubuntu.com oneiric-security/main Sources
Obj http://security.ubuntu.com oneiric-security/restricted Sources
Obj http://security.ubuntu.com oneiric-security/universe Sources
Obj http://security.ubuntu.com oneiric-security/multiverse Sources
Obj http://security.ubuntu.com oneiric-security/main i386 Packages
Obj http://security.ubuntu.com oneiric-security/restricted i386 Packages
Obj http://security.ubuntu.com oneiric-security/universe i386 Packages
Obj http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Obj http://security.ubuntu.com oneiric-security/main TranslationIndex
Obj http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Obj http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Err http://extras.ubuntu.com oneiric/main Translation-es_ES
  Bad header line
Err http://extras.ubuntu.com oneiric/main Translation-es
  Bad header line
Obj http://us.archive.ubuntu.com oneiric Release                                          
Obj http://us.archive.ubuntu.com oneiric-updates Release                                  
Ign http://us.archive.ubuntu.com oneiric Release                                          
Ign http://extras.ubuntu.com oneiric/main Translation-en                                  
Obj http://us.archive.ubuntu.com oneiric-backports Release           
Des:2 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]
Ign http://us.archive.ubuntu.com oneiric/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/universe Sources/DiffIndex  
Ign http://us.archive.ubuntu.com oneiric/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/universe i386 Packages/DiffIndex                 
Ign http://us.archive.ubuntu.com oneiric/multiverse i386 Packages/DiffIndex               
Obj http://us.archive.ubuntu.com oneiric/main TranslationIndex                            
Obj http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex                      
Obj http://us.archive.ubuntu.com oneiric/restricted TranslationIndex                      
Obj http://us.archive.ubuntu.com oneiric/universe TranslationIndex                        
Obj http://us.archive.ubuntu.com oneiric-updates/main Sources                             
Obj http://us.archive.ubuntu.com oneiric-updates/restricted Sources                       
Obj http://us.archive.ubuntu.com oneiric-updates/universe Sources                         
Obj http://us.archive.ubuntu.com oneiric-updates/multiverse Sources                       
Obj http://us.archive.ubuntu.com oneiric-updates/main i386 Packages                       
Obj http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages                 
Obj http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages                   
Obj http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages                 
Obj http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex                    
Obj http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex              
Obj http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex              
Obj http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex                
Ign http://us.archive.ubuntu.com oneiric-backports/main Sources/DiffIndex                 
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Sources/DiffIndex           
Ign http://us.archive.ubuntu.com oneiric-backports/universe Sources/DiffIndex             
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Sources/DiffIndex           
Ign http://us.archive.ubuntu.com oneiric-backports/main i386 Packages/DiffIndex           
Ign http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages/DiffIndex     
Ign http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages/DiffIndex       
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages/DiffIndex     
Obj http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex                  
Obj http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex            
Obj http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex            
Obj http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex              
Obj http://us.archive.ubuntu.com oneiric/restricted Sources                               
Obj http://us.archive.ubuntu.com oneiric/universe Sources                                 
Obj http://us.archive.ubuntu.com oneiric/multiverse Sources                               
Obj http://us.archive.ubuntu.com oneiric/main i386 Packages                               
Obj http://security.ubuntu.com oneiric-security/universe TranslationIndex                 
Obj http://us.archive.ubuntu.com oneiric/restricted i386 Packages                         
Obj http://security.ubuntu.com oneiric-security/main Translation-en                       
Obj http://us.archive.ubuntu.com oneiric/universe i386 Packages                           
Obj http://security.ubuntu.com oneiric-security/multiverse Translation-en
Obj http://us.archive.ubuntu.com oneiric/multiverse i386 Packages
Obj http://security.ubuntu.com oneiric-security/restricted Translation-en
Obj http://us.archive.ubuntu.com oneiric/main Translation-es
Obj http://security.ubuntu.com oneiric-security/universe Translation-en
Obj http://us.archive.ubuntu.com oneiric/main Translation-en
Obj http://us.archive.ubuntu.com oneiric/multiverse Translation-es
Obj http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Obj http://us.archive.ubuntu.com oneiric/restricted Translation-es
Obj http://us.archive.ubuntu.com oneiric/restricted Translation-en
Obj http://us.archive.ubuntu.com oneiric/universe Translation-es
Obj http://us.archive.ubuntu.com oneiric/universe Translation-en
Obj http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Obj http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Obj http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Obj http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Obj http://us.archive.ubuntu.com oneiric-backports/main Sources
Obj http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Obj http://us.archive.ubuntu.com oneiric-backports/universe Sources
Obj http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Obj http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Obj http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Obj http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Obj http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Obj http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Obj http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Obj http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Obj http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Descargados 877 kB en 46s (18,8 kB/s)
W: GPG error: http://us.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-es_ES  Bad header line

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-es  Bad header line

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
[]

---

### Post by Myddna on 2012-01-11
This worked: [http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3](http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3)

:D

---

### Post by nicki20048 on 2012-01-13
> **Myddna said:**
> This worked: [http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3](http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3)

:D
This seems to have solved my problem

Thanks :D

---

