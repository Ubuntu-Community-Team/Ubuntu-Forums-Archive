---
title: "E: Encountered a section with no Package: header"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by BioS615 on 2011-06-16
I cannot find a solution for the life of me, everything from Google to reinstalling several different images have failed. 

Whenever I try to open Synaptic, or update manager, I get a slew of failed downloads concerning repos. Heres a complete terminal log of sudo apt-get update:
```
bios@ubuntu:~$ sudo apt-get update
[sudo] password for bios: 
Get:1 http://extras.ubuntu.com natty InRelease [308 B]
Get:2 http://archive.ubuntu.com natty InRelease [310 B]                       
Ign http://archive.ubuntu.com natty-updates InRelease
Ign http://archive.ubuntu.com natty-security InRelease
Get:3 http://archive.canonical.com natty InRelease [312 B]
Ign http://extras.ubuntu.com natty InRelease   
Ign http://archive.ubuntu.com natty InRelease                           
Ign http://archive.canonical.com natty InRelease                        
Ign http://archive.ubuntu.com natty-updates Release.gpg                 
Hit http://archive.ubuntu.com natty-security Release.gpg
Get:4 http://archive.ubuntu.com natty/main i386 Packages/DiffIndex [337 B]
Ign http://archive.ubuntu.com natty/restricted i386 Packages/DiffIndex       
Ign http://archive.ubuntu.com natty/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty/main TranslationIndex            
Get:5 http://extras.ubuntu.com natty/main i386 Packages/DiffIndex [335 B]
Ign http://extras.ubuntu.com natty/main TranslationIndex                     
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex              
Ign http://archive.ubuntu.com natty/restricted TranslationIndex      
Get:6 http://archive.canonical.com natty/partner i386 Packages/DiffIndex [342 B]
Ign http://archive.canonical.com natty/partner TranslationIndex      
Hit http://archive.ubuntu.com natty-updates Release                  
Hit http://archive.ubuntu.com natty-security Release
Hit http://archive.ubuntu.com natty/main i386 Packages
Get:7 http://archive.ubuntu.com natty/restricted i386 Packages [183 kB]        
Get:8 http://extras.ubuntu.com natty/main Translation-en_US [330 B]            
7% [8 Translation-en_US bzip2 0 B] [7 Packages 12.7 kB/183 kB 6%] [Waiting for bzip2: (stdin) is not a bzip2 file.
Get:9 http://archive.canonical.com natty/partner Translation-en_US [337 B]     
17% [9 Translation-en_US bzip2 0 B] [7 Packages 30.3 kB/183 kB 16%] [Waiting fobzip2: (stdin) is not a bzip2 file.
25% [8 Translation-en_US xz 0 B] [7 Packages 45.3 kB/183 kB 24%] [Waiting for h/usr/bin/xz: (stdin): File format not recognized
Err http://extras.ubuntu.com natty/main Sources                                
  0  Ok
Get:10 http://archive.canonical.com natty/partner i386 Packages [336 B]        
57% [10 Packages lzma 0 B] [7 Packages 105 kB/183 kB 57%] [Waiting for headers]/usr/bin/lzma: Decoder error
Ign http://archive.ubuntu.com natty-updates/main i386 Packages/DiffIndex       
Get:11 http://extras.ubuntu.com natty/main Translation-en [326 B]              
Err http://archive.canonical.com natty/partner Sources                         
  0  Ok
Get:12 http://archive.ubuntu.com natty-updates/restricted i386 Packages/DiffIndex [351 B]
Ign http://archive.ubuntu.com natty-updates/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Err http://extras.ubuntu.com natty/main i386 Packages
  0  Ok
Get:13 http://archive.ubuntu.com natty-security/restricted i386 Packages [2,065 B]
Get:14 http://archive.ubuntu.com natty-security/main TranslationIndex [331 B]  
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://extras.ubuntu.com natty/main Translation-en_US                 
Hit http://archive.ubuntu.com natty-updates/main i386 Packages            
Get:15 http://archive.ubuntu.com natty-updates/restricted i386 Packages [4,270 B]
Get:16 http://archive.ubuntu.com natty-updates/multiverse i386 Packages [340 B]
98% [16 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:17 http://archive.canonical.com natty/partner Translation-en [330 B]
Get:18 http://archive.ubuntu.com natty-security/main i386 Packages [1,913 B]
Get:19 http://archive.ubuntu.com natty-security/main Translation-en_US [338 B]
98% [19 Translation-en_US bzip2 0 B] [Waiting for headers] [Waiting for headersbzip2: (stdin) is not a bzip2 file.
Ign http://archive.canonical.com natty/partner Translation-en_US               
Err http://archive.ubuntu.com natty-security/multiverse i386 Packages          
  0  Ok [IP: 91.189.88.31 80]
Get:20 http://archive.ubuntu.com natty-updates/main Translation-en [347 B]
98% [20 Translation-en lzma 0 B] [Waiting for headers]/usr/bin/lzma: Decoder error
Err http://archive.ubuntu.com natty/multiverse i386 Packages
  0  Ok [IP: 91.189.88.31 80]
Get:21 http://archive.ubuntu.com natty/main Translation-en_US [328 B]
Ign http://archive.ubuntu.com natty/main Translation-en    
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Fetched 197 kB in 4s (45.5 kB/s)
W: GPG error: http://extras.ubuntu.com natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://archive.ubuntu.com natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://archive.canonical.com natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources  0  Ok

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/source/Sources  0  Ok

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages  0  Ok [IP: 91.189.88.31 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  0  Ok

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages  0  Ok [IP: 91.189.88.31 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I've done sudo rm /var/apt/lists/* && sudo apt-get update, and every other solution I could find on Google. It gives me this error even when trying to update during installation, and as a last ditch effort, I'm turning to the forums because usually I don't like to post about a problem if I can find the solution on my own.

Any help would be greatly appreciated.

EDIT: I also feel its worthy to note I'm doing this in a virtual machine.

---

