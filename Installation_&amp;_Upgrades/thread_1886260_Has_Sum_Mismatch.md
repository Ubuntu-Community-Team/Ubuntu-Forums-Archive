---
title: "Has Sum Mismatch"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2011-11-24
I am having real trouble installing anything on my computer. (11.10) Everything I try comes up with the message 'Check your Internet Connection' - the latest error message is below - Can anyone help?

[IMG]http://i44.tinypic.com/nzgm01.png[/IMG]

---

### Post by fantab on 2011-11-24
> **bigtel said:**
> I am having real trouble installing anything on my computer. (11.10) Everything I try comes up with the message 'Check your Internet Connection' - the latest error message is below - Can anyone help?


The Problem could be with your Internet Connection breaking. 

How are you downloading your .iso? 
Is it a direct download or torrent download?
Are you using any Download Manager which supports resuming?

I suggest you do a torrent download as downloading files are checked and rechecked while downloading. Even if internet connection breaks it won't affect the download. You can use **qbittorrent **to download torrent files. Transmission is also good.

*sudo apt-get install qbittorrent*

---

### Post by bigtel on 2011-11-25
I am using the software center or the normal update manager to download the files. Even when I try to refresh the update list (eg press the 'check' button) I get an error saying -

W:Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

[IMG]http://i43.tinypic.com/1ta79z.png[/IMG]

I am using a wireless connection but I have since tried a wired one instead but I have the same issue.

When I try and sudo apt-get update I get the following output

```
terry@terry-A7N8X-E:~$ sudo apt-get update
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://gb.archive.ubuntu.com oneiric InRelease                             
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://gb.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://packages.medibuntu.org oneiric InRelease                            
Ign http://gb.archive.ubuntu.com oneiric-security InRelease                    
Hit http://gb.archive.ubuntu.com oneiric Release.gpg                           
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://gb.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://gb.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://gb.archive.ubuntu.com oneiric-security Release.gpg                  
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://gb.archive.ubuntu.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://gb.archive.ubuntu.com oneiric-updates Release                       
Hit http://gb.archive.ubuntu.com oneiric-backports Release                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://packages.medibuntu.org oneiric/free Sources                         
Hit http://gb.archive.ubuntu.com oneiric-security Release                      
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://gb.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://ppa.launchpad.net oneiric/main Sources                              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://packages.medibuntu.org oneiric/non-free Sources                     
Get:1 http://gb.archive.ubuntu.com oneiric/main Translation-en_GB [69.0 kB]    
Get:2 http://ppa.launchpad.net oneiric/main i386 Packages [18.4 kB]            
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages               
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Get:3 http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB [68.5 kB]
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en             
Get:4 http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB [1,937 B]
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en             
Get:5 http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB [4,365 B]
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://gb.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-backports/main TranslationIndex
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com oneiric-security/main i386 Packages           
Hit http://gb.archive.ubuntu.com oneiric-security/restricted i386 Packages     
Hit http://gb.archive.ubuntu.com oneiric-security/universe i386 Packages       
Hit http://gb.archive.ubuntu.com oneiric-security/multiverse i386 Packages     
Hit http://gb.archive.ubuntu.com oneiric-security/main TranslationIndex        
Hit http://gb.archive.ubuntu.com oneiric-security/multiverse TranslationIndex  
Hit http://gb.archive.ubuntu.com oneiric-security/restricted TranslationIndex  
Hit http://gb.archive.ubuntu.com oneiric-security/universe TranslationIndex    
Hit http://gb.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en     
Hit http://gb.archive.ubuntu.com oneiric-security/main Translation-en          
Hit http://gb.archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://gb.archive.ubuntu.com oneiric-security/restricted Translation-en    
Hit http://gb.archive.ubuntu.com oneiric-security/universe Translation-en      
Ign http://packages.medibuntu.org oneiric/free Translation-en_GB               
Ign http://packages.medibuntu.org oneiric/free Translation-en
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/non-free Translation-en
Fetched 144 kB in 2s (65.0 kB/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by fantab on 2011-11-25
> **fantab said:**
> The Problem could be with your Internet Connection breaking. 

How are you downloading your .iso? 
Is it a direct download or torrent download?
Are you using any Download Manager which supports resuming?

I suggest you do a torrent download as downloading files are checked and rechecked while downloading. Even if internet connection breaks it won't affect the download. You can use **qbittorrent **to download torrent files. Transmission is also good.

*sudo apt-get install qbittorrent*

My bad.... I completely misread your post. I must have had way too much:lolflag:

Are you running two package installers at the same time? This will give you the problem with updates and installation? If yes then don't.

[**See this Thread**]("http://ubuntuforums.org/showthread.php?t=1885976&highlight=fantab")- it should help.

---

### Post by raja.genupula on 2011-11-25
```
sudo rm -rf /var/lib/apt/lists/partial/*
sudo apt-get update
```

all the best.

---

### Post by bigtel on 2011-11-26
This seems to have done the trick, my - although top settings menu says my software is up to date - my update manager still says I have a Linux kernel update.

Thanks for your help.

---

### Post by raja.genupula on 2011-11-26
hi welcome man 

sudo apt-get update
sudo apt-get dist-upgrade

try this man. I am sure it gonna solve the issue.

---

### Post by bigtel on 2011-11-27
Hi There raja.genupula, I have tried the commands and this is the output from the upgrade -

```
terry@terry-A7N8X-E:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-image-3.0.0-13-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.5 MB/36.5 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric-updates/main linux-image-3.0.0-13-generic i386 3.0.0-13.22 [36.5 MB]
Fetched 36.5 MB in 30s (1,185 kB/s)                                            
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

It seems to have worked for some of the packages but sill not form the updated linux image - Is there a way to download this separately and then install it from the hard drive?

Thanks

---

### Post by bluexrider on 2011-11-27
Try
sudo apt-get dist-upgrade --fix-missing

---

### Post by bigtel on 2011-11-27
.....

I still have the error message - here is my code output

```
terry@terry-A7N8X-E:~$ sudo apt-get dist-upgrade --fix-missing
[sudo] password for terry: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-image-3.0.0-13-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.5 MB/36.5 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric-updates/main linux-image-3.0.0-13-generic i386 3.0.0-13.22 [36.5 MB]
Fetched 36.5 MB in 31s (1,146 kB/s)                                            
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb  Hash Sum mismatch

```


It looks like it is downloading at it does say downloaded 35.5 MB.

---

### Post by bluexrider on 2011-11-27
In your Software Sources change Download Form: Main Server to other...then select best server.

sudo apt-get update

sudo apt-get dist-upgrade --fix-missing

sounds like a proxy cache problem

---

### Post by bigtel on 2011-11-27
OK I have done that.

Here is the output from sudo apt-get update

```
terry@terry-A7N8X-E:~$ sudo apt-get update
[sudo] password for terry: 
Ign http://mirror.as29550.net oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Hit http://ppa.launchpad.net oneiric Release.gpg
Hit http://archive.canonical.com oneiric Release                              
Hit http://extras.ubuntu.com oneiric Release                                  
Hit http://packages.medibuntu.org oneiric InRelease                           
Ign http://mirror.as29550.net oneiric-updates InRelease                       
Hit http://ppa.launchpad.net oneiric Release.gpg
Ign http://mirror.as29550.net oneiric-backports InRelease                      
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://mirror.as29550.net oneiric-security InRelease                       
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:2 http://mirror.as29550.net oneiric Release.gpg [198 B]                    
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:3 http://mirror.as29550.net oneiric-updates Release.gpg [198 B]            
Hit http://packages.medibuntu.org oneiric/free Sources                         
Get:4 http://mirror.as29550.net oneiric-backports Release.gpg [198 B]          
Hit http://packages.medibuntu.org oneiric/non-free Sources                     
Get:5 http://mirror.as29550.net oneiric-security Release.gpg [198 B]           
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Get:6 http://mirror.as29550.net oneiric Release [40.8 kB]                      
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages               
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:7 http://mirror.as29550.net oneiric-updates Release [32.4 kB]    
Ign http://packages.medibuntu.org oneiric/free TranslationIndex
Get:8 http://mirror.as29550.net oneiric-backports Release [24.3 kB]            
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex           
Get:9 http://mirror.as29550.net oneiric-backports Release [24.3 kB]
Get:10 http://mirror.as29550.net oneiric-backports Release [24.3 kB]           
Get:11 http://mirror.as29550.net oneiric-backports Release [24.3 kB]           
Get:12 http://mirror.as29550.net oneiric-backports Release [24.3 kB]
Get:13 http://mirror.as29550.net oneiric-backports Release [24.3 kB]           
Get:14 http://mirror.as29550.net oneiric-backports Release [24.3 kB]           
Get:15 http://mirror.as29550.net oneiric-backports Release [24.3 kB]           
Get:16 http://mirror.as29550.net oneiric-backports Release [24.3 kB]           
Get:17 http://mirror.as29550.net oneiric-backports Release [24.3 kB]           
Ign http://mirror.as29550.net oneiric-backports Release                        
Get:18 http://mirror.as29550.net oneiric-security Release [32.4 kB]            
Get:19 http://mirror.as29550.net oneiric-security Release [32.4 kB]            
Get:20 http://mirror.as29550.net oneiric-security Release [32.4 kB]            
Get:21 http://mirror.as29550.net oneiric-security Release [32.4 kB]            
Get:22 http://mirror.as29550.net oneiric-security Release [32.4 kB]            
Get:23 http://mirror.as29550.net oneiric-security Release [32.4 kB]            
Get:24 http://mirror.as29550.net oneiric-security Release [32.4 kB]            
Get:25 http://mirror.as29550.net oneiric-security Release [32.4 kB]
Get:26 http://mirror.as29550.net oneiric-security Release [32.4 kB]
Get:27 http://mirror.as29550.net oneiric-security Release [32.4 kB]            
Get:28 http://mirror.as29550.net oneiric-security Release [32.4 kB]            
Get:29 http://mirror.as29550.net oneiric/main i386 Packages [1,226 kB]         
Ign http://packages.medibuntu.org oneiric/free Translation-en_GB               
Ign http://packages.medibuntu.org oneiric/free Translation-en                  
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/non-free Translation-en              
Get:30 http://mirror.as29550.net oneiric/restricted i386 Packages [8,216 B]    
Get:31 http://mirror.as29550.net oneiric/universe i386 Packages [4,468 kB]
Get:32 http://mirror.as29550.net oneiric/multiverse i386 Packages [119 kB]     
Get:33 http://mirror.as29550.net oneiric/main TranslationIndex [3,289 B]       
Get:34 http://mirror.as29550.net oneiric/multiverse TranslationIndex [2,265 B] 
Get:35 http://mirror.as29550.net oneiric/restricted TranslationIndex [2,263 B] 
Get:36 http://mirror.as29550.net oneiric/universe TranslationIndex [2,640 B]   
Get:37 http://mirror.as29550.net oneiric-updates/main i386 Packages [205 kB]   
Get:38 http://mirror.as29550.net oneiric-updates/restricted i386 Packages [2,935 B]
Get:39 http://mirror.as29550.net oneiric-updates/universe i386 Packages [56.2 kB]
Get:40 http://mirror.as29550.net oneiric-updates/multiverse i386 Packages [4,396 B]
Get:41 http://mirror.as29550.net oneiric-updates/main TranslationIndex [73 B]  
Get:42 http://mirror.as29550.net oneiric-updates/multiverse TranslationIndex [72 B]
Get:43 http://mirror.as29550.net oneiric-updates/restricted TranslationIndex [71 B]
Get:44 http://mirror.as29550.net oneiric-updates/universe TranslationIndex [73 B]
Get:45 http://mirror.as29550.net oneiric-backports/main i386 Packages [1,912 B]
Get:46 http://mirror.as29550.net oneiric-backports/restricted i386 Packages [14 B]
Get:47 http://mirror.as29550.net oneiric-backports/universe i386 Packages [4,051 B]
Get:48 http://mirror.as29550.net oneiric-backports/multiverse i386 Packages [14 B]
Get:49 http://mirror.as29550.net oneiric-backports/main TranslationIndex [72 B]
Get:50 http://mirror.as29550.net oneiric-backports/multiverse TranslationIndex [70 B]
Get:51 http://mirror.as29550.net oneiric-backports/restricted TranslationIndex [70 B]
Get:52 http://mirror.as29550.net oneiric-backports/universe TranslationIndex [72 B]
Get:53 http://mirror.as29550.net oneiric-security/main i386 Packages [46.0 kB] 
Get:54 http://mirror.as29550.net oneiric-security/restricted i386 Packages [14 B]
Get:55 http://mirror.as29550.net oneiric-security/universe i386 Packages [14.1 kB]
Get:56 http://mirror.as29550.net oneiric-security/multiverse i386 Packages [1,653 B]
Get:57 http://mirror.as29550.net oneiric-security/main TranslationIndex [73 B] 
Get:58 http://mirror.as29550.net oneiric-security/multiverse TranslationIndex [71 B]
Get:59 http://mirror.as29550.net oneiric-security/restricted TranslationIndex [70 B]
Get:60 http://mirror.as29550.net oneiric-security/universe TranslationIndex [73 B]
Get:61 http://mirror.as29550.net oneiric/main Translation-en_GB [69.0 kB]      
Get:62 http://mirror.as29550.net oneiric/main Translation-en [701 kB]          
Get:63 http://mirror.as29550.net oneiric/multiverse Translation-en_GB [68.5 kB]
Get:64 http://mirror.as29550.net oneiric/multiverse Translation-en [92.6 kB]   
Get:65 http://mirror.as29550.net oneiric/restricted Translation-en_GB [1,937 B]
Get:66 http://mirror.as29550.net oneiric/restricted Translation-en [2,229 B]   
Get:67 http://mirror.as29550.net oneiric/universe Translation-en_GB [4,365 B]  
Get:68 http://mirror.as29550.net oneiric/universe Translation-en [3,165 kB]    
Get:69 http://mirror.as29550.net oneiric-updates/main Translation-en [95.6 kB] 
Get:70 http://mirror.as29550.net oneiric-updates/multiverse Translation-en [2,419 B]
Get:71 http://mirror.as29550.net oneiric-updates/restricted Translation-en [508 B]
Get:72 http://mirror.as29550.net oneiric-updates/universe Translation-en [34.7 kB]
Get:73 http://mirror.as29550.net oneiric-backports/main Translation-en [1,203 B]
Get:74 http://mirror.as29550.net oneiric-backports/multiverse Translation-en [14 B]
Get:75 http://mirror.as29550.net oneiric-backports/restricted Translation-en [14 B]
Get:76 http://mirror.as29550.net oneiric-backports/universe Translation-en [3,624 B]
Get:77 http://mirror.as29550.net oneiric-security/main Translation-en [25.9 kB]
Get:78 http://mirror.as29550.net oneiric-security/multiverse Translation-en [840 B]
Get:79 http://mirror.as29550.net oneiric-security/restricted Translation-en [14 B]
Get:80 http://mirror.as29550.net oneiric-security/universe Translation-en [10.0 kB]
99% [62 Translation-en bzip2 0 B]                                              
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Fetched 10.5 MB in 35s (300 kB/s)                                              
W: GPG error: http://mirror.as29550.net oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror.as29550.net_archive.ubuntu.com_dists_oneiric_main_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

```


...and here is the output from sudo apt-get dist-upgrade --fix-missing


```
terry@terry-A7N8X-E:~$ sudo apt-get dist-upgrade --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-image-3.0.0-13-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.5 MB/36.5 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://mirror.as29550.net/archive.ubuntu.com/ oneiric-updates/main linux-image-3.0.0-13-generic i386 3.0.0-13.22 [36.5 MB]
Fetched 36.5 MB in 30s (1,178 kB/s)                                            
Failed to fetch http://mirror.as29550.net/archive.ubuntu.com/pool/main/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb  Hash Sum mismatch

```


Strange that it's still an issue..!

---

### Post by raja.genupula on 2011-11-27
hmmm...

server may be ?

ok man ...open update manager->settings->at 1st tab download from change your mirror to main server and try again.

---

### Post by bluexrider on 2011-11-27
@raja.genupula


> **bluexrider said:**
> In your Software Sources change Download Form: Main Server to other...then select best server.

sudo apt-get update

sudo apt-get dist-upgrade --fix-missing

sounds like a proxy cache problem

I told him to do that earlier. 

Read his output!

---

### Post by bluexrider on 2011-11-27
sudo rm /var/lib/apt/lists/partial/*

sudo apt-get update

sudo apt-get dist-upgrade --fix-missing

---

### Post by bigtel on 2011-11-27
Here is the output...

```
terry@terry-A7N8X-E:~$ sudo rm /var/lib/apt/lists/partial/*
[sudo] password for terry: 
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory
terry@terry-A7N8X-E:~$ sudo apt-get update
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-backports InRelease                      
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://archive.ubuntu.com oneiric-security InRelease                       
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Hit http://archive.ubuntu.com oneiric-backports Release.gpg                    
Hit http://archive.ubuntu.com oneiric-security Release.gpg                     
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://archive.ubuntu.com oneiric-backports Release               
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://packages.medibuntu.org oneiric InRelease                            
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric/main TranslationIndex
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages               
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages           
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com oneiric/main Translation-en_GB                   
Hit http://archive.ubuntu.com oneiric/main Translation-en                      
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en_GB             
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Hit http://archive.ubuntu.com oneiric/restricted Translation-en_GB             
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                
Hit http://archive.ubuntu.com oneiric/universe Translation-en_GB        
Hit http://archive.ubuntu.com oneiric/universe Translation-en           
Hit http://archive.ubuntu.com oneiric-backports/main i386 Packages      
Hit http://archive.ubuntu.com oneiric-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com oneiric-backports/universe i386 Packages         
Hit http://archive.ubuntu.com oneiric-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com oneiric-backports/main TranslationIndex          
Hit http://archive.ubuntu.com oneiric-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com oneiric-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com oneiric-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en              
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages              
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages          
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex           
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex       
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Hit http://archive.ubuntu.com oneiric-backports/main Translation-en            
Hit http://archive.ubuntu.com oneiric-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com oneiric-backports/restricted Translation-en      
Hit http://archive.ubuntu.com oneiric-backports/universe Translation-en        
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Hit http://archive.ubuntu.com oneiric-security/main Translation-en             
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en       
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en       
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en         
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Hit http://packages.medibuntu.org oneiric/free Sources
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://packages.medibuntu.org oneiric/non-free Sources
Hit http://packages.medibuntu.org oneiric/free i386 Packages
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages
Ign http://packages.medibuntu.org oneiric/free TranslationIndex
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex
Ign http://packages.medibuntu.org oneiric/free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/free Translation-en
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/non-free Translation-en
Reading package lists... Done
terry@terry-A7N8X-E:~$ sudo apt-get dist-upgrade --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-image-3.0.0-13-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.5 MB/36.5 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric-updates/main linux-image-3.0.0-13-generic i386 3.0.0-13.22 [36.5 MB]
Fetched 36.5 MB in 30s (1,179 kB/s)                                            
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb  Hash Sum mismatch
terry@terry-A7N8X-E:~$ 

```



There is still a Hash Sum mismatch...ahhhgggg...!

---

### Post by bluexrider on 2011-11-27
Getting frustrated myself

sudo apt-get --purge remove linux-image-3.0.0-13-generic

sudo apt-get clean

sudo apt-get update

sudo apt-get -f install linux-image-3.0.0-13-generic

---

### Post by bigtel on 2011-11-28
here is the code ...


```
terry@terry-A7N8X-E:~$ sudo apt-get --purge remove linux-image-3.0.0-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-3.0.0-13-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
terry@terry-A7N8X-E:~$ sudo apt-get clean
terry@terry-A7N8X-E:~$ sudo apt-get update
Ign http://archive.canonical.com oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-backports InRelease                      
Hit http://packages.medibuntu.org oneiric InRelease                            
Ign http://archive.ubuntu.com oneiric-security InRelease                       
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.ubuntu.com oneiric-backports Release.gpg                    
Hit http://archive.ubuntu.com oneiric-security Release.gpg                     
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://archive.ubuntu.com oneiric-backports Release                 
Hit http://archive.ubuntu.com oneiric-security Release                  
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://packages.medibuntu.org oneiric/free Sources                         
Hit http://archive.canonical.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages        
Hit http://archive.ubuntu.com oneiric/main TranslationIndex           
Hit http://packages.medibuntu.org oneiric/non-free Sources            
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages               
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages           
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en_GB         
Hit http://archive.ubuntu.com oneiric/main Translation-en            
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en_GB   
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en      
Hit http://archive.ubuntu.com oneiric/restricted Translation-en_GB   
Hit http://archive.ubuntu.com oneiric/restricted Translation-en      
Hit http://packages.medibuntu.org oneiric/free i386 Packages         
Hit http://archive.ubuntu.com oneiric/universe Translation-en_GB               
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Hit http://archive.ubuntu.com oneiric-backports/main i386 Packages             
Hit http://archive.ubuntu.com oneiric-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com oneiric-backports/universe i386 Packages         
Hit http://archive.ubuntu.com oneiric-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com oneiric-backports/main TranslationIndex          
Hit http://archive.ubuntu.com oneiric-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com oneiric-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com oneiric-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en              
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages     
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages              
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages          
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex           
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex       
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://archive.ubuntu.com oneiric-backports/main Translation-en            
Hit http://archive.ubuntu.com oneiric-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com oneiric-backports/restricted Translation-en      
Hit http://archive.ubuntu.com oneiric-backports/universe Translation-en        
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                
Hit http://archive.ubuntu.com oneiric-security/main Translation-en             
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en       
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en       
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en         
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Ign http://archive.canonical.com oneiric/partner Translation-en_GB
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://packages.medibuntu.org oneiric/free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/free Translation-en
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/non-free Translation-en
Fetched 72 B in 2s (31 B/s)
Reading package lists... Done
terry@terry-A7N8X-E:~$ sudo apt-get -f install linux-image-3.0.0-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-doc-3.0.0 linux-source-3.0.0 linux-tools
The following NEW packages will be installed
  linux-image-3.0.0-13-generic
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 36.5 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric-updates/main linux-image-3.0.0-13-generic i386 3.0.0-13.22 [36.5 MB]
Fetched 36.5 MB in 30s (1,197 kB/s)                                            
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
terry@terry-A7N8X-E:~$ 

```



My system is running OK without this update, perhaps one day it will decide to work on it's own..! Thanks for your help in trying to fix this.

---

### Post by raja.genupula on 2011-11-29
thats cool  man, mark the thread as solved from thread tools .

---

### Post by abmoraz on 2012-02-25
> **bigtel said:**
> here is the code ...


```
terry@terry-A7N8X-E:~$ sudo apt-get --purge remove linux-image-3.0.0-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-3.0.0-13-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
terry@terry-A7N8X-E:~$ sudo apt-get clean
terry@terry-A7N8X-E:~$ sudo apt-get update
Ign http://archive.canonical.com oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-backports InRelease                      
Hit http://packages.medibuntu.org oneiric InRelease                            
Ign http://archive.ubuntu.com oneiric-security InRelease                       
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.ubuntu.com oneiric-backports Release.gpg                    
Hit http://archive.ubuntu.com oneiric-security Release.gpg                     
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://archive.ubuntu.com oneiric-backports Release                 
Hit http://archive.ubuntu.com oneiric-security Release                  
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://packages.medibuntu.org oneiric/free Sources                         
Hit http://archive.canonical.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages        
Hit http://archive.ubuntu.com oneiric/main TranslationIndex           
Hit http://packages.medibuntu.org oneiric/non-free Sources            
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages               
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages           
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en_GB         
Hit http://archive.ubuntu.com oneiric/main Translation-en            
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en_GB   
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en      
Hit http://archive.ubuntu.com oneiric/restricted Translation-en_GB   
Hit http://archive.ubuntu.com oneiric/restricted Translation-en      
Hit http://packages.medibuntu.org oneiric/free i386 Packages         
Hit http://archive.ubuntu.com oneiric/universe Translation-en_GB               
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Hit http://archive.ubuntu.com oneiric-backports/main i386 Packages             
Hit http://archive.ubuntu.com oneiric-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com oneiric-backports/universe i386 Packages         
Hit http://archive.ubuntu.com oneiric-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com oneiric-backports/main TranslationIndex          
Hit http://archive.ubuntu.com oneiric-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com oneiric-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com oneiric-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en              
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages     
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages              
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages          
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex           
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex       
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://archive.ubuntu.com oneiric-backports/main Translation-en            
Hit http://archive.ubuntu.com oneiric-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com oneiric-backports/restricted Translation-en      
Hit http://archive.ubuntu.com oneiric-backports/universe Translation-en        
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                
Hit http://archive.ubuntu.com oneiric-security/main Translation-en             
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en       
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en       
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en         
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Ign http://archive.canonical.com oneiric/partner Translation-en_GB
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://packages.medibuntu.org oneiric/free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/free Translation-en
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/non-free Translation-en
Fetched 72 B in 2s (31 B/s)
Reading package lists... Done
terry@terry-A7N8X-E:~$ sudo apt-get -f install linux-image-3.0.0-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-doc-3.0.0 linux-source-3.0.0 linux-tools
The following NEW packages will be installed
  linux-image-3.0.0-13-generic
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 36.5 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric-updates/main linux-image-3.0.0-13-generic i386 3.0.0-13.22 [36.5 MB]
Fetched 36.5 MB in 30s (1,197 kB/s)                                            
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
terry@terry-A7N8X-E:~$ 

```



My system is running OK without this update, perhaps one day it will decide to work on it's own..! Thanks for your help in trying to fix this.

I have the same problem.  Fresh install and the first update I try it gives me the "bad hash sum" when doing an update.  Then I get errors any time I try to install any package.

Has anyone figured out why this happens and better yet, how to fix it?

---

