---
title: "Ubuntu 12.4 - Cannot upgrade"
date: 2016-10-24
forum: Installation &amp; Upgrades
---

### Post by Qualtrough on 2016-10-24
I have had 12.4 installed for a long time and want to upgrade to the next version.

When I check to make sure the current version is up to date I get messages like the following:

W:Failed to fetchhttp://mirror1.ku.ac.th/ubuntu/dists/quantal/main/binary-i386/Packages 404  Not Found 
, W:Failed to fetchhttp://mirror1.ku.ac.th/ubuntu/dists/quantal-updates/main/binary-i386/Packages 404  Not Found 
, W:Failed to fetchhttp://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages 404  Not Found [IP: 91.189.88.161 80] 
, E:Some index files failed todownload. They have been ignored, or old ones used instead.

I have consulted different forums and gone into terminal to clean things, changed the server for getting upgrades, get the upgrades, etc., but when I go to install the next version (12.10?) I get to the second stage and it can't download everything needed and terminates.

I would greatly appreciate it if anyone can offer advice on how I can get past this roadblock. Thanks in advance to anyone trying to assist me!

---

### Post by ajgreeny on 2016-10-24
You can not sensibly upgrade to 12.12 as it has no support and the repos are now moved.  You can, however, upgrade direct to 14.04, but will have to tell your system to use only LTS versions.

Open software-sources, updates tab, and there choose to be notified of LTS versions only.
I think you should now be given the option to upgrade to 14.04 instead of 12.12, though having always clean installed, it is not something I have any experience of personally.

---

### Post by Bucky Ball on 2016-10-24
Open 'Software and Updates'> 'Updates' tab> at the bottom of that tab you'll see 'Notify me of a new Ubuntu version'> next to that is a drop-down box> choose 'For long-term support versions'. When you go to close that you'll be asked if you want to update. Do so. After that you should be offered the 14.04 LTS upgrade ***if*** you have fixed the other problem first.

Be aware that you should make sure you can

 ```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

... with NO errors.

If you are using any third-party graphics drivers, see if you can run from the open-source ones during the upgrade and get the machine as 'vanilla' as possible. Disable all  third-party PPAs you may have manually added. 

Personally, I backup the valuables and do a clean install. Quicker.

---

### Post by Qualtrough on 2016-10-26
Thank you to both of your for your replies. It is set to install 14.04 but when I run the clean and upgrade instructions there are always errors, and trying the install results in failure every time.

So, it looks like I will need to back-up my data and do a clean install. The only issue I have with that is with my email (Thunderbird). I want to make sure that I am able to maintain my old sent and inbox emails and I have always found that very difficult to do. If you have any advice on how to do that with a fresh install I would certainly appreciate your letting me know. Also, I assume I should go for the latest LTS version? Can I download to a USB and use that for the install?

---

### Post by Bucky Ball on 2016-10-26
Like I said, if there are errors don't even bother trying to upgrade. Post those errors between code tags here so we can help. It is pointless to go any further with this until you fix those errors. Unless you do a clean install of 16.04 LTS or 14.04 LTS then none of this matters. 

> So, it looks like I will need to back-up my data and do a clean install.

Why? You haven't posted the errors from those commands for us to have a look at. Are they identical to the ones you posted in the first post? Is there more than in the first post?

On the other hand, a clean install would probably be quicker. Go for 16.04 LTS for longer support.

---

### Post by ajgreeny on 2016-10-26
If you do end up doing a clean install (of either 14.04 or 16.04) you will find all the configuration and your old T'bird emails in the hidden .thunderbird folder in your home; simply make sure that is backed up and restored and everything should still be there for you.

---

### Post by Qualtrough on 2016-10-26
Hello,

My preference would be upgrading rather than clean install because of the email issue, etc. I have run the commands above and hope I have pasted them correctly below in between code tags. If this isn't right please let me know what I did wrong and i will correct and resend.

Thank you.

```
qualtrough@qualtrough-desktop:~$ sudo apt-get autoremove
[sudo] password for qualtrough: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
qualtrough@qualtrough-desktop:~$ sudo apt-get update
Hit http://mirror1.ku.ac.th precise Release.gpg
Get:1 http://mirror1.ku.ac.th precise-updates Release.gpg [198 B]
Hit http://mirror1.ku.ac.th precise Release                                    
Get:2 http://mirror1.ku.ac.th precise-updates Release [55.4 kB]                
Ign http://th.archive.ubuntu.com quantal Release.gpg                           
Ign http://th.archive.ubuntu.com quantal-updates Release.gpg                   
Ign http://th.archive.ubuntu.com lucid-backports Release.gpg                   
Ign http://th.archive.ubuntu.com quantal Release                               
Hit http://dl.google.com stable Release.gpg                                    
Ign http://th.archive.ubuntu.com quantal-updates Release                       
Hit http://mirror1.ku.ac.th precise/main i386 Packages                         
Ign http://th.archive.ubuntu.com lucid-backports Release                       
Hit http://dl.google.com stable Release.gpg                                    
Hit http://mirror1.ku.ac.th precise/main TranslationIndex                      
Get:3 http://mirror1.ku.ac.th precise-updates/main i386 Packages [1,094 kB]    
Ign http://th.archive.ubuntu.com quantal/main TranslationIndex                 
Hit http://dl.google.com stable Release                                        
Ign http://th.archive.ubuntu.com quantal/multiverse TranslationIndex           
Ign http://th.archive.ubuntu.com quantal/restricted TranslationIndex           
Hit http://dl.google.com stable Release                                        
Ign http://th.archive.ubuntu.com quantal/universe TranslationIndex             
Ign http://th.archive.ubuntu.com quantal-updates/main TranslationIndex         
Ign http://th.archive.ubuntu.com quantal-updates/multiverse TranslationIndex   
Ign http://th.archive.ubuntu.com quantal-updates/restricted TranslationIndex   
Ign http://th.archive.ubuntu.com quantal-updates/universe TranslationIndex     
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://th.archive.ubuntu.com lucid-backports/main TranslationIndex         
Ign http://th.archive.ubuntu.com lucid-backports/multiverse TranslationIndex   
Ign http://th.archive.ubuntu.com lucid-backports/restricted TranslationIndex   
Ign http://th.archive.ubuntu.com lucid-backports/universe TranslationIndex     
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://mirror1.ku.ac.th precise-updates/main TranslationIndex              
Hit http://mirror1.ku.ac.th precise/main Translation-en                        
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://security.ubuntu.com quantal-security Release.gpg                    
Hit http://mirror1.ku.ac.th precise-updates/main Translation-en                
Get:4 http://archive.canonical.com quantal Release.gpg [933 B]                 
Get:5 http://extras.ubuntu.com quantal Release.gpg [72 B]                      
Get:6 http://archive.canonical.com lucid Release.gpg [198 B]                   
Hit http://extras.ubuntu.com quantal Release                                   
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:7 http://ppa.launchpad.net quantal Release.gpg [316 B]                     
Get:8 http://archive.canonical.com quantal Release [7,078 B]                   
Get:9 http://ppa.launchpad.net quantal Release.gpg [316 B]                     
Hit http://linux.dropbox.com maverick Release.gpg                              
Err http://th.archive.ubuntu.com quantal/main Sources                          
  404  Not Found
Get:10 http://archive.canonical.com lucid Release [8,215 B]                    
Get:11 http://packages.medibuntu.org maverick Release.gpg                      
Err http://th.archive.ubuntu.com quantal/restricted Sources                    
  404  Not Found
Err http://th.archive.ubuntu.com quantal/universe Sources                      
  404  Not Found
Err http://th.archive.ubuntu.com quantal/multiverse Sources                    
  404  Not Found
Err http://th.archive.ubuntu.com quantal/main i386 Packages                    
  404  Not Found
Err http://th.archive.ubuntu.com quantal/restricted i386 Packages              
  404  Not Found
Err http://th.archive.ubuntu.com quantal/universe i386 Packages                
  404  Not Found
Err http://th.archive.ubuntu.com quantal/multiverse i386 Packages              
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/main Sources                  
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/restricted Sources            
  404  Not Found
Get:12 http://deb.opera.com stable Release.gpg [819 B]                         
Err http://th.archive.ubuntu.com quantal-updates/universe Sources              
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/multiverse Sources            
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/main i386 Packages            
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/restricted i386 Packages      
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/universe i386 Packages        
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/multiverse i386 Packages      
  404  Not Found
Get:13 http://ppa.launchpad.net quantal Release.gpg [316 B]                    
Err http://th.archive.ubuntu.com lucid-backports/main Sources                  
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/restricted Sources            
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/universe Sources              
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/multiverse Sources            
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/main i386 Packages            
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/restricted i386 Packages      
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/universe i386 Packages        
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/multiverse i386 Packages      
  404  Not Found
Ign http://th.archive.ubuntu.com quantal/main Translation-en_US                
Ign http://th.archive.ubuntu.com quantal/main Translation-en                   
Ign http://th.archive.ubuntu.com quantal/multiverse Translation-en_US          
Ign http://th.archive.ubuntu.com quantal/multiverse Translation-en             
Ign http://th.archive.ubuntu.com quantal/restricted Translation-en_US          
Ign http://th.archive.ubuntu.com quantal/restricted Translation-en             
Ign http://th.archive.ubuntu.com quantal/universe Translation-en_US            
Ign http://th.archive.ubuntu.com quantal/universe Translation-en               
Ign http://th.archive.ubuntu.com quantal-updates/main Translation-en_US        
Ign http://th.archive.ubuntu.com quantal-updates/main Translation-en           
Ign http://th.archive.ubuntu.com quantal-updates/multiverse Translation-en_US  
Ign http://th.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Ign http://th.archive.ubuntu.com quantal-updates/restricted Translation-en_US  
Get:14 http://ppa.launchpad.net quantal Release.gpg [316 B]                    
Hit http://linux.dropbox.com maverick Release                                  
Ign http://th.archive.ubuntu.com quantal-updates/restricted Translation-en     
Ign http://th.archive.ubuntu.com quantal-updates/universe Translation-en_US    
Ign http://th.archive.ubuntu.com quantal-updates/universe Translation-en       
Ign http://th.archive.ubuntu.com lucid-backports/main Translation-en_US        
Ign http://th.archive.ubuntu.com lucid-backports/main Translation-en           
Ign http://th.archive.ubuntu.com lucid-backports/multiverse Translation-en_US  
Ign http://th.archive.ubuntu.com lucid-backports/multiverse Translation-en     
Get:15 http://deb.opera.com stable Release.gpg [819 B]                         
Ign http://th.archive.ubuntu.com lucid-backports/restricted Translation-en_US  
Ign http://th.archive.ubuntu.com lucid-backports/restricted Translation-en     
Ign http://th.archive.ubuntu.com lucid-backports/universe Translation-en_US    
Ign http://th.archive.ubuntu.com lucid-backports/universe Translation-en       
Get:16 http://ppa.launchpad.net quantal Release.gpg [316 B]                    
Get:17 http://deb.opera.com stable Release [1,724 B]                           
Ign http://deb.opera.com stable Release                                        
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Get:18 http://deb.opera.com stable Release [1,724 B]                           
Ign http://deb.opera.com stable Release                                        
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Ign http://linux.dropbox.com maverick/main TranslationIndex                    
Get:19 http://archive.canonical.com quantal/partner i386 Packages [5,355 B]    
Get:20 http://ppa.launchpad.net quantal Release [12.9 kB]                      
Ign http://archive.canonical.com quantal/partner TranslationIndex              
Get:21 http://ppa.launchpad.net quantal Release [11.9 kB]                      
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Get:22 http://ppa.launchpad.net quantal Release [11.9 kB]                      
Get:23 http://ppa.launchpad.net quantal Release [12.4 kB]                      
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Get:24 http://archive.canonical.com lucid/partner Sources [8,247 B]            
Get:25 http://ppa.launchpad.net quantal Release [12.9 kB]                      
Get:26 http://security.ubuntu.com precise-security Release.gpg [198 B]         
Ign http://security.ubuntu.com quantal-security Release                        
Get:27 http://extras.ubuntu.com quantal/main i386 Packages [3,779 B]           
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://extras.ubuntu.com quantal/main TranslationIndex                     
Ign http://ppa.launchpad.net maverick/main TranslationIndex                    
Get:28 http://security.ubuntu.com precise-security Release [55.5 kB]           
Get:29 http://ppa.launchpad.net quantal/main Sources [14 B]                    
Get:30 http://ppa.launchpad.net quantal/main i386 Packages [14 B]              
Get:31 http://ppa.launchpad.net quantal/main TranslationIndex [193 B]          
Get:32 http://ppa.launchpad.net quantal/main Sources [728 B]                   
Get:33 http://ppa.launchpad.net quantal/main i386 Packages [694 B]             
Ign http://ppa.launchpad.net quantal/main TranslationIndex                     
Get:34 http://ppa.launchpad.net quantal/main Sources [5,605 B]                 
Get:35 http://ppa.launchpad.net quantal/main i386 Packages [7,021 B]           
Ign http://ppa.launchpad.net quantal/main TranslationIndex                     
Get:36 http://ppa.launchpad.net quantal/main Sources [14 B]                    
Ign http://linux.dropbox.com maverick/main Translation-en_US                   
Get:37 http://ppa.launchpad.net quantal/main i386 Packages [14 B]              
Get:38 http://ppa.launchpad.net quantal/main TranslationIndex [70 B]           
Ign http://linux.dropbox.com maverick/main Translation-en                      
Get:39 http://ppa.launchpad.net quantal/main Sources [14 B]                    
Get:40 http://ppa.launchpad.net quantal/main i386 Packages [14 B]              
Get:41 http://ppa.launchpad.net quantal/main TranslationIndex [193 B]          
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Get:42 http://packages.medibuntu.org lucid Release.gpg                         
Ign http://archive.canonical.com quantal/partner Translation-en                
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Get:43 http://ppa.launchpad.net quantal/main Translation-en [14 B]             
Get:44 http://packages.medibuntu.org maverick Release                          
Ign http://security.ubuntu.com quantal-security/main TranslationIndex          
Ign http://security.ubuntu.com quantal-security/multiverse TranslationIndex    
Ign http://security.ubuntu.com quantal-security/restricted TranslationIndex    
Ign http://security.ubuntu.com quantal-security/universe TranslationIndex      
Get:45 http://security.ubuntu.com precise-security/main i386 Packages [711 kB] 
Get:46 http://ppa.launchpad.net quantal/main Translation-en [14 B]             
Get:47 http://ppa.launchpad.net quantal/main Translation-en [14 B]             
Get:48 http://security.ubuntu.com precise-security/main TranslationIndex [208 B]
Get:49 http://deb.opera.com stable/non-free i386 Packages [1,821 B]            
Ign http://packages.medibuntu.org maverick Release                             
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
E: GPG error: http://packages.medibuntu.org maverick Release: The following signatures were invalid: NODATA 3 NODATA 4
qualtrough@qualtrough-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libnspr4-0d
The following NEW packages will be installed:
  linux-headers-3.2.0-113 linux-headers-3.2.0-113-generic
  linux-headers-3.2.0-113-generic-pae linux-image-3.2.0-113-generic
The following packages have been kept back:
  acroread-bin
The following packages will be upgraded:
  google-earth-stable liblcms2-2 libmysqlclient18 libnspr4 libnss3 libnss3-1d
  linux-generic linux-headers-generic linux-headers-generic-pae
  linux-image-generic mysql-client-core-5.5 mysql-common mysql-server-core-5.5
  ubuntu-tweak
14 upgraded, 4 newly installed, 1 to remove and 1 not upgraded.
Need to get 26.4 MB/88.7 MB of archives.
After this operation, 194 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://dl.google.com/linux/earth/deb/ stable/main google-earth-stable i386 6.1.0.4738-r0
  404  Not Found [IP: 74.125.68.136 80]
Get:1 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main liblcms2-2 i386 2.4-0ubuntu3.1~quantal1~ppa1 [159 kB]
Get:2 http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ quantal/main ubuntu-tweak all 0.8.7-1~quantal1 [1,023 kB]
Fetched 1,182 kB in 6s (177 kB/s)                                              
Failed to fetch http://dl.google.com/linux/earth/deb/pool/main/g/google-earth-stable/google-earth-stable_6.1.0.4738-r0_i386.deb  404  Not Found [IP: 74.125.68.136 80]
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ quantal/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
qualtrough@qualtrough-desktop:~$ 




```

Hi, Just want to make sure I understand correctly. I need to perform the following in this order:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

It's late here, but I will try it again in that order and paste here:


```
qualtrough@qualtrough-desktop:~$ sudo apt-get autoremove
[sudo] password for qualtrough: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
qualtrough@qualtrough-desktop:~$ sudo apt-get update
Hit http://mirror1.ku.ac.th precise Release.gpg
Hit http://mirror1.ku.ac.th precise-updates Release.gpg
Hit http://mirror1.ku.ac.th precise Release                                    
Hit http://mirror1.ku.ac.th precise-updates Release                            
Hit http://mirror1.ku.ac.th precise/main i386 Packages                         
Hit http://mirror1.ku.ac.th precise/main TranslationIndex                      
Ign http://th.archive.ubuntu.com quantal Release.gpg                           
Ign http://th.archive.ubuntu.com quantal-updates Release.gpg                   
Ign http://th.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://mirror1.ku.ac.th precise-updates/main i386 Packages                 
Hit http://mirror1.ku.ac.th precise-updates/main TranslationIndex              
Hit http://dl.google.com stable Release.gpg                                    
Hit http://mirror1.ku.ac.th precise/main Translation-en                        
Ign http://th.archive.ubuntu.com quantal Release                               
Ign http://th.archive.ubuntu.com quantal-updates Release                       
Hit http://mirror1.ku.ac.th precise-updates/main Translation-en                
Hit http://dl.google.com stable Release.gpg                                    
Ign http://th.archive.ubuntu.com lucid-backports Release                       
Ign http://th.archive.ubuntu.com quantal/main TranslationIndex                 
Hit http://dl.google.com stable Release                                        
Ign http://th.archive.ubuntu.com quantal/multiverse TranslationIndex           
Ign http://th.archive.ubuntu.com quantal/restricted TranslationIndex           
Hit http://dl.google.com stable Release                                        
Ign http://th.archive.ubuntu.com quantal/universe TranslationIndex             
Ign http://th.archive.ubuntu.com quantal-updates/main TranslationIndex         
Ign http://th.archive.ubuntu.com quantal-updates/multiverse TranslationIndex   
Ign http://th.archive.ubuntu.com quantal-updates/restricted TranslationIndex   
Ign http://th.archive.ubuntu.com quantal-updates/universe TranslationIndex     
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://th.archive.ubuntu.com lucid-backports/main TranslationIndex         
Ign http://th.archive.ubuntu.com lucid-backports/multiverse TranslationIndex   
Ign http://th.archive.ubuntu.com lucid-backports/restricted TranslationIndex   
Ign http://th.archive.ubuntu.com lucid-backports/universe TranslationIndex     
Ign http://security.ubuntu.com quantal-security Release.gpg                    
Get:1 http://extras.ubuntu.com quantal Release.gpg [72 B]                      
Ign http://ppa.launchpad.net maverick Release.gpg                              
Get:2 http://archive.canonical.com quantal Release.gpg [933 B]                 
Hit http://extras.ubuntu.com quantal Release                                   
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:3 http://archive.canonical.com lucid Release.gpg [198 B]                   
Get:4 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:5 http://ppa.launchpad.net quantal Release.gpg [316 B]                     
Get:6 http://archive.canonical.com quantal Release [7,078 B]                   
Ign http://security.ubuntu.com quantal-security Release                        
Get:7 http://extras.ubuntu.com quantal/main i386 Packages [3,779 B]            
Get:8 http://ppa.launchpad.net quantal Release.gpg [316 B]                     
Hit http://linux.dropbox.com maverick Release.gpg                              
Err http://th.archive.ubuntu.com quantal/main Sources                          
  404  Not Found
Err http://th.archive.ubuntu.com quantal/restricted Sources                    
  404  Not Found
Err http://th.archive.ubuntu.com quantal/universe Sources                      
  404  Not Found
Err http://th.archive.ubuntu.com quantal/multiverse Sources                    
  404  Not Found
Err http://th.archive.ubuntu.com quantal/main i386 Packages                    
  404  Not Found
Err http://th.archive.ubuntu.com quantal/restricted i386 Packages              
  404  Not Found
Err http://th.archive.ubuntu.com quantal/universe i386 Packages                
  404  Not Found
Err http://th.archive.ubuntu.com quantal/multiverse i386 Packages              
  404  Not Found
Get:9 http://packages.medibuntu.org maverick Release.gpg                       
Err http://th.archive.ubuntu.com quantal-updates/main Sources                  
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/restricted Sources            
  404  Not Found
Get:10 http://ppa.launchpad.net quantal Release.gpg [316 B]                    
Ign http://extras.ubuntu.com quantal/main TranslationIndex                     
Get:11 http://archive.canonical.com lucid Release [8,215 B]                    
Err http://th.archive.ubuntu.com quantal-updates/universe Sources              
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/multiverse Sources            
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/main i386 Packages            
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/restricted i386 Packages      
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/universe i386 Packages        
  404  Not Found
Err http://th.archive.ubuntu.com quantal-updates/multiverse i386 Packages      
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/main Sources                  
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/restricted Sources            
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/universe Sources              
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/multiverse Sources            
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/main i386 Packages            
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/restricted i386 Packages      
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/universe i386 Packages        
  404  Not Found
Err http://th.archive.ubuntu.com lucid-backports/multiverse i386 Packages      
  404  Not Found
Ign http://th.archive.ubuntu.com quantal/main Translation-en_US                
Ign http://th.archive.ubuntu.com quantal/main Translation-en                   
Ign http://th.archive.ubuntu.com quantal/multiverse Translation-en_US          
Get:12 http://deb.opera.com stable Release.gpg [819 B]                         
Ign http://th.archive.ubuntu.com quantal/multiverse Translation-en             
Get:13 http://ppa.launchpad.net quantal Release.gpg [316 B]                    
Ign http://th.archive.ubuntu.com quantal/restricted Translation-en_US          
Ign http://th.archive.ubuntu.com quantal/restricted Translation-en             
Ign http://th.archive.ubuntu.com quantal/universe Translation-en_US            
Ign http://th.archive.ubuntu.com quantal/universe Translation-en               
Ign http://th.archive.ubuntu.com quantal-updates/main Translation-en_US        
Ign http://th.archive.ubuntu.com quantal-updates/main Translation-en           
Ign http://th.archive.ubuntu.com quantal-updates/multiverse Translation-en_US  
Ign http://th.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Ign http://th.archive.ubuntu.com quantal-updates/restricted Translation-en_US  
Get:14 http://archive.canonical.com quantal/partner i386 Packages [5,355 B]    
Ign http://th.archive.ubuntu.com quantal-updates/restricted Translation-en     
Ign http://th.archive.ubuntu.com quantal-updates/universe Translation-en_US    
Ign http://th.archive.ubuntu.com quantal-updates/universe Translation-en       
Ign http://th.archive.ubuntu.com lucid-backports/main Translation-en_US        
Ign http://th.archive.ubuntu.com lucid-backports/main Translation-en           
Ign http://th.archive.ubuntu.com lucid-backports/multiverse Translation-en_US  
Ign http://th.archive.ubuntu.com lucid-backports/multiverse Translation-en     
Ign http://th.archive.ubuntu.com lucid-backports/restricted Translation-en_US  
Ign http://th.archive.ubuntu.com lucid-backports/restricted Translation-en     
Ign http://th.archive.ubuntu.com lucid-backports/universe Translation-en_US    
Ign http://th.archive.ubuntu.com lucid-backports/universe Translation-en       
Get:15 http://deb.opera.com stable Release.gpg [819 B]                         
Get:16 http://ppa.launchpad.net quantal Release.gpg [316 B]                    
Ign http://archive.canonical.com quantal/partner TranslationIndex              
Get:17 http://deb.opera.com stable Release [1,724 B]                           
Ign http://deb.opera.com stable Release                                        
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://linux.dropbox.com maverick Release                                  
Get:18 http://deb.opera.com stable Release [1,724 B]                           
Ign http://deb.opera.com stable Release                                        
Get:19 http://archive.canonical.com lucid/partner Sources [8,247 B]            
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Get:20 http://ppa.launchpad.net quantal Release [12.9 kB]                      
Get:21 http://security.ubuntu.com precise-security Release [55.5 kB]           
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Get:22 http://ppa.launchpad.net quantal Release [11.9 kB]                      
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Get:23 http://ppa.launchpad.net quantal Release [11.9 kB]                      
Get:24 http://packages.medibuntu.org lucid Release.gpg                         
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Get:25 http://ppa.launchpad.net quantal Release [12.4 kB]                      
Ign http://linux.dropbox.com maverick/main TranslationIndex                    
Get:26 http://ppa.launchpad.net quantal Release [12.9 kB]                      
Ign http://ppa.launchpad.net maverick/main TranslationIndex                    
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Get:27 http://packages.medibuntu.org maverick Release                          
Get:28 http://ppa.launchpad.net quantal/main Sources [14 B]                    
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Ign http://packages.medibuntu.org maverick Release                             
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
E: GPG error: http://packages.medibuntu.org maverick Release: The following signatures were invalid: NODATA 1 NODATA 2
qualtrough@qualtrough-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libnspr4-0d
The following NEW packages will be installed:
  linux-headers-3.2.0-113 linux-headers-3.2.0-113-generic
  linux-headers-3.2.0-113-generic-pae linux-image-3.2.0-113-generic
The following packages have been kept back:
  acroread-bin
The following packages will be upgraded:
  google-earth-stable liblcms2-2 libmysqlclient18 libnspr4 libnss3 libnss3-1d
  linux-generic linux-headers-generic linux-headers-generic-pae
  linux-image-generic mysql-client-core-5.5 mysql-common mysql-server-core-5.5
  ubuntu-tweak
14 upgraded, 4 newly installed, 1 to remove and 1 not upgraded.
Need to get 25.2 MB/88.7 MB of archives.
After this operation, 194 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://dl.google.com/linux/earth/deb/ stable/main google-earth-stable i386 6.1.0.4738-r0
  404  Not Found [IP: 74.125.200.136 80]
Failed to fetch http://dl.google.com/linux/earth/deb/pool/main/g/google-earth-stable/google-earth-stable_6.1.0.4738-r0_i386.deb  404  Not Found [IP: 74.125.200.136 80]
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ quantal/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
qualtrough@qualtrough-desktop:~$ 

```

Just want to add for clarity that I performed all three commands, so if some are not showing up it must be that I didn't copy and paste correctly.

---

### Post by mörgæs on 2016-10-26
Have you considered doing a fresh install of 16.04.1 in a new partition? If you do then you can copy the e-mail contents without losing the old install. 

When 16.04.1 works including Thunderbird you can erase the old install. No worries until year 2021.

---

### Post by Bucky Ball on 2016-10-27
> **ajgreeny said:**
> If you do end up doing a clean install (of either 14.04 or 16.04) you will find all the configuration and your old T'bird emails in the hidden .thunderbird folder in your home; simply make sure that is backed up and restored and everything should still be there for you.

That's all you've got to do. Then just delete the .thunderbird folder in the new install and plop the old one in there. Done. No need to worry. You can make three back ups of that folder to put your mind at ease. If you have Firefox bookmarks you would need to back them up, too. That's dead easy. Bookmarks> Show all Bookmarks> Import and backup tab.

If you're intending to work your way through the changes over the years based around this one .thunderbird folder, you are in for a long haul. You're having enough trouble getting to 14.04 LTS because of this and you'll still be a release away from the latest LTS and if you want to get there you'll need to waste some more time jumping through more hoops (probably).

Net upgrades are never the best way to go. Take a few hours and generally problematic for obscure and common reasons. A clean install to 16.04 LTS and support until 2021 will take you about an hour or less and you're outta here. Your choice, of course. :)

* You can't go too far wrong if you have good, *_reliable_* backups of your valuable data (I generally make two, the old 'grandfather, father, son' rule of thumb, although you're going to be without the 'grandfather' soon after you create the father and son). 12.04 LTS is supported until April 2017 so you have some time to think about it.

---

### Post by Qualtrough on 2016-10-27
Thank you everyone here for your advice, very much appreciated! I will do the clean install next week and you may hear from me again :)

---

### Post by Bucky Ball on 2016-10-27
A pleasure and all good. Word of advice: if you have issues with the install better to start a new thread with a descriptive title rather than keep posting about it here. You will greatly improve your chances of support. Good luck and see you then. :)

---

### Post by Qualtrough on 2016-10-27
Thank you, will do that!

---

