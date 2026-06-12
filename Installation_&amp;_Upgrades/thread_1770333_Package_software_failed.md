---
title: "Package software failed"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by grayling on 2011-05-29
Hello,

I tried downloading an application and I had a power failure so the install did not complete. I now get the following error message. E: Read error read (5: input/output error) E: The package lists or status file could not be parsed or opened. I cannot clear this.

I have seen a couple of things which say use Sudo with apt-get to rm /var/lib/apt/lists/* -vf and then apt-get update but this has not worked. Has anybody got any other suggestions.

Thanks

gary

---

### Post by drpjkurian on 2011-05-29
Hi,

First make sure that update-manager, synaptic, etc... are all closed and not running somewhere.

Then open a Terminal and enter the following commands:

sudo mkdir /var/lib/apt/lists/partial
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install -f

After that, retry opening update-manager.

Regards,

Courtesy Mark rijckenberg from launchpad

---

### Post by grayling on 2011-05-29
Hello,

the sudo mkdir command says that the file exists, so I carried on with the next command. This brought another error as below:

dpkg : failed in buffer_read(fd): copy infor file '/var/lib/dpkg/status' : Input/output error

Any thoughts?

Cheers for now

Gary

---

### Post by drpjkurian on 2011-05-30
Hi That means the file /var/lib/dpkg/status is the offending file.
So remove it 
try this command which gives you GUI```
sudo nautilus
```
Remove that file and then rerun the suggested commands above to let apt/dpkg/etc sort themselves out:

  ```
sudo apt-get -f install
  sudo apt-get update
  sudo apt-get upgrade
```

---

### Post by cdoebbler on 2011-06-02
I have same problem (with 11.04) and tried following your instructions but they did not work.

Here is what I got:

0:~$ sudo mkdir /var/lib/apt/lists/partial
[sudo] password for fb1: 
mkdir: cannot create directory `/var/lib/apt/lists/partial': File exists
0:~$ sudo dpkg --configure -a
0:~$ sudo aptitude update
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease                          
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed InRelease                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports InRelease                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                              
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg [198 B]                       
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72 B]                      
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg [198 B]               
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg [198 B]              
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed Release.gpg [198 B]              
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                  
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports Release.gpg [198 B]             
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release [39.8 kB]                         
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports InRelease                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                   
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports Release.gpg                 
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release [27.2 kB]                 
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports Release                     
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release [27.2 kB]                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick InRelease                       
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed Release [27.2 kB]     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                    
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports Release [23.3 kB]              
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main TranslationIndex                    
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources [4,104 B]             
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources [862 kB]                    
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/main i386 Packages          
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg                               
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/restricted i386 Packages    
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/universe i386 Packages      
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/multiverse i386 Packages    
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/main TranslationIndex       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US                
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/multiverse TranslationIndex 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Translation-en                       
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/restricted TranslationIndex
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages                      
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/universe TranslationIndex
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main TranslationIndex
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources [155 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Sources [4,380 kB]              
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en_US                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en                       
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/main Translation-en_US      
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/main Translation-en
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/multiverse Translation-en_US
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/multiverse Translation-en
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/restricted Translation-en_US
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/restricted Translation-en
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/universe Translation-en_US
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages [1,550 kB]
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) maverick-backports/universe Translation-en  
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted i386 Packages [8,986 B]       
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe i386 Packages [6,021 kB]        
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex                                       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources [14 B]                            
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources [35.8 kB]                               
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Sources [1,362 B]                         
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Sources [9,180 B]                           
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main i386 Packages [116 kB]                          
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted i386 Packages [14 B]                      
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe i386 Packages [44.0 kB]                     
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse i386 Packages [3,754 B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex                               
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Sources [14 B]                           
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Sources [10.2 kB]                              
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Sources [647 B]                          
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Sources [3,152 B]                          
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main i386 Packages [30.9 kB]                        
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted i386 Packages [14 B]                     
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe i386 Packages [11.6 kB]                    
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse i386 Packages [2,071 B]                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main TranslationIndex                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse TranslationIndex                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted TranslationIndex                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe TranslationIndex                              
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/restricted Sources [14 B]                           
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/main Sources [34.5 kB]                              
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/multiverse Sources [14 B]                           
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/universe Sources [2,747 B]                          
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/restricted i386 Packages [14 B]                     
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/main i386 Packages [78.3 kB]                        
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/multiverse i386 Packages [14 B]                     
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/universe i386 Packages [11.7 kB]                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/main TranslationIndex                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/multiverse TranslationIndex                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/restricted TranslationIndex                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/universe TranslationIndex                              
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/restricted Sources [14 B]                          
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/main Sources [1,651 B]                             
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/multiverse Sources [709 B]                         
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/universe Sources [3,892 B]                         
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/restricted i386 Packages [14 B]                    
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/main i386 Packages [2,150 B]                       
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/multiverse i386 Packages [702 B]                   
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/universe i386 Packages [5,465 B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/main TranslationIndex                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/multiverse TranslationIndex                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/restricted TranslationIndex                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/universe TranslationIndex                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_US                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en_US                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_US                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_US                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en_US                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_US                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Translation-en_US                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Translation-en                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Translation-en_US                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Translation-en                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Translation-en_US                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Translation-en                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Translation-en_US                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Translation-en                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/main Translation-en_US                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/main Translation-en                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/multiverse Translation-en_US                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/multiverse Translation-en                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/restricted Translation-en_US                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/restricted Translation-en                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/universe Translation-en_US                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-proposed/universe Translation-en                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/main Translation-en_US                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/main Translation-en                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/multiverse Translation-en_US                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/multiverse Translation-en                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/restricted Translation-en_US                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/restricted Translation-en                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/universe Translation-en_US                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports/universe Translation-en                               
Fetched 13.7 MB in 21s (649 kB/s)                                                                   
[ ERR] Reading package lists
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
0:~$

---

