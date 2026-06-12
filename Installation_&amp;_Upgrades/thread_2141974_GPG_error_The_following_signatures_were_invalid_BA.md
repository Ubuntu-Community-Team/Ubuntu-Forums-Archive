---
title: "GPG error: The following signatures were invalid: BADSIG 40976EAF437D05B5"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by wbridger on 2013-05-04
Hi All

I'm running ubuntu 11.10
I have an issue with apt-get update:
```

root@sparks:/var/lib/apt# apt-get update
Get:1 http://download.virtualbox.org oneiric Release.gpg [198 B]                              
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                                     
Get:3 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                                
Get:4 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]                        
Get:5 http://ppa.launchpad.net oneiric Release.gpg [316 B]                                    
Get:6 http://ppa.launchpad.net oneiric Release.gpg [316 B]                                    
Get:7 http://archive.canonical.com oneiric Release.gpg [198 B]                                
Get:8 http://us.archive.ubuntu.com oneiric-security Release.gpg [198 B]                       
Get:9 http://ppa.launchpad.net oneiric Release.gpg [316 B]                                    
Get:10 http://download.virtualbox.org oneiric Release [5,393 B]                               
Get:11 http://download.jitsi.org unstable/ Release.gpg [72 B]                                 
Get:12 http://extras.ubuntu.com oneiric Release [9,759 B]                                     
Get:13 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                                 
Get:14 http://archive.canonical.com oneiric Release [5,922 B]                                 
Get:15 http://ppa.launchpad.net oneiric Release [9,754 B]                                     
Get:16 http://download.jitsi.org unstable/ Release [1,547 B]                                  
Get:17 http://ppa.launchpad.net oneiric Release [9,739 B]                                     
Get:18 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]                         
Get:19 http://ppa.launchpad.net oneiric Release [9,741 B]                                     
Get:20 http://ppa.launchpad.net oneiric/main Sources [1,432 B]                                
Get:21 http://download.jitsi.org unstable/ Packages [3,347 B]                                 
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                    
Get:22 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]                
Get:23 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]                 
Get:24 http://extras.ubuntu.com oneiric/main i386 Packages [1,226 kB]                         
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                    
Get:25 http://ppa.launchpad.net oneiric/main i386 Packages [2,691 B]                          
Get:26 http://liveusb.info all Release.gpg [490 B]                                            
Get:27 http://liveusb.info all Release [4,635 B]                                              
Get:28 http://liveusb.info all/main i386 Packages [1,251 B]                                   
Ign http://liveusb.info all/main TranslationIndex                                             
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                    
Get:29 http://archive.canonical.com oneiric/partner i386 Packages [4,537 B]                   
Get:30 http://ppa.launchpad.net oneiric/main Sources [757 B]                                  
Ign http://archive.canonical.com oneiric/partner TranslationIndex                             
Get:31 http://ppa.launchpad.net oneiric/main i386 Packages [1,249 B]                          
Ign http://liveusb.info all/main Translation-en_US                                            
Ign http://liveusb.info all/main Translation-en                                               
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                    
Get:32 http://extras.ubuntu.com oneiric/main Translation-en [701 kB]                          
Get:33 http://ppa.launchpad.net oneiric/main Sources [949 B]                                  
Ign http://download.jitsi.org unstable/ Translation-en_US                                     
Ign http://download.jitsi.org unstable/ Translation-en                                        
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                                   
Get:34 http://ppa.launchpad.net oneiric/main i386 Packages [1,190 B]                          
Ign http://archive.canonical.com oneiric/partner Translation-en_US                            
Ign http://archive.canonical.com oneiric/partner Translation-en                               
Get:35 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]                                   
Get:36 http://us.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]                                     
Get:37 http://us.archive.ubuntu.com oneiric-security Release [877 kB]                                           
Ign http://us.archive.ubuntu.com oneiric-security Release                                                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                                                     
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Get:38 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:39 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]
Get:40 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]
Get:41 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]                                         
Get:42 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]                                       
Get:43 http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]                               
Get:44 http://us.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]                               
Get:45 http://us.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]                                 
Get:46 http://us.archive.ubuntu.com oneiric-updates/main Sources [180 kB]                                       
Get:47 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]                                
Get:48 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]                          
Get:49 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [3,349 B]                                
Get:50 http://us.archive.ubuntu.com oneiric-updates/universe Sources [72.0 kB]                                  
Get:51 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,700 B]                                
Get:52 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [440 kB]                                 
Get:53 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [6,645 B]                          
Get:54 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [152 kB]                             
Get:55 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,363 B]                          
Get:56 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [72 B]                          
Get:57 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]                            
Get:58 http://us.archive.ubuntu.com oneiric/main Translation-en [701 kB]                                        
Get:59 http://us.archive.ubuntu.com oneiric-security/main TranslationIndex [74 B]                               
Get:60 http://us.archive.ubuntu.com oneiric-security/main Sources [69.0 kB]                                     
Get:61 http://us.archive.ubuntu.com oneiric-security/restricted Sources [1,964 B]                               
Get:62 http://us.archive.ubuntu.com oneiric-security/universe Sources [29.4 kB]                                 
Get:63 http://us.archive.ubuntu.com oneiric-security/multiverse Sources [1,677 B]                               
Get:64 http://us.archive.ubuntu.com oneiric-security/main i386 Packages [249 kB]                                
Get:65 http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages [4,062 B]                         
Get:66 http://us.archive.ubuntu.com oneiric-security/universe i386 Packages [69.0 kB]                           
Get:67 http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages [3,386 B]                         
Get:68 http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]                         
Get:69 http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex [71 B]                         
Get:70 http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex [73 B]                           
Get:71 http://us.archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]                                 
Get:72 http://us.archive.ubuntu.com oneiric-updates/main Sources [180 kB]                                       
Get:73 http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en [1,547 B]                         
Get:74 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [92.6 kB]                           
Get:75 http://us.archive.ubuntu.com oneiric-security/main Translation-en [116 kB]                               
Get:76 http://us.archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]                                 
Get:77 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,165 kB]                                  
Get:78 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [209 kB]                                
Get:79 http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en [3,524 B]                         
Get:80 http://us.archive.ubuntu.com oneiric-security/restricted Translation-en [978 B]                          
Get:81 http://us.archive.ubuntu.com oneiric-security/universe Translation-en [46.7 kB]                          
Get:82 http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en [1,494 B]                        
Get:83 http://us.archive.ubuntu.com oneiric/main Translation-en [701 kB]                                        
Get:84 http://us.archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]                                 
99% [84 Translation-en gzip 0 B]                                                                     129 kB/s 0sW: GPG error: http://us.archive.ubuntu.com oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Unable to parse package file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Translation-en.decomp (1)
Fetched 20.4 MB in 2min 49s (121 kB/s)                                                                          
W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Translation-en  

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have tried the following:
First in the software center preferences, i remove the culprit key (40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>)
Then I run the following commands found [here]("http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3") 
```

apt-get clean 
cd /var/lib/apt 
mv lists lists.old 
mkdir -p lists/partial 
apt-get clean 
apt-get update
```

Yet the same error persists...

I tried running the command found on the thread mentionned above:
```
wget –q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x40976EAF437D05B5" -O- | sudo apt-key add
```
No luck there either

After further browsing this forum, I tried another solution that had worked for others:

```

root@sparks:/var/lib/apt# gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5
gpg: directory `/root/.gnupg' created
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/root/.gnupg/secring.gpg' created
gpg: keyring `/root/.gnupg/pubring.gpg' created
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: /root/.gnupg/trustdb.gpg: trustdb created
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
root@sparks:/var/lib/apt# gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
OK

```

Yet the same error persists.

I tried yet another solution found on this forum:
```

root@sparks:/var/lib/apt# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.48Iz5P2gmQ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

```

Still no luck:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Anyone has any idea?
Many thanks in advance

:D

---

### Post by ibjsb4 on 2013-05-04
Try

```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
sudo apt-get update
```

Still getting Hash Sum mismatch?  Try a different download source.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

---

### Post by wbridger on 2013-05-04
> **ibjsb4 said:**
> Try

```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
sudo apt-get update
```

Still getting Hash Sum mismatch?  Try a different download source.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

Thanks for the prompt reply. 
Unfortunately that did not work...

The result of the first command gave:
```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
Hit http://download.virtualbox.org oneiric Release.gpg                                                           
Hit http://extras.ubuntu.com oneiric Release.gpg                                                                 
Get: 1 http://ppa.launchpad.net oneiric Release.gpg [316 B]                                                      
Hit http://ppa.launchpad.net oneiric Release.gpg
Hit http://ppa.launchpad.net oneiric Release.gpg
Hit http://liveusb.info all Release.gpg                                                                          
Hit http://download.virtualbox.org oneiric Release                                                               
Hit http://us.archive.ubuntu.com oneiric Release.gpg                                                             
Get: 2 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Get: 3 http://us.archive.ubuntu.com oneiric-security Release.gpg [198 B]
Hit http://download.jitsi.org unstable/ Release.gpg
Hit http://archive.canonical.com oneiric Release.gpg                                                             
Hit http://extras.ubuntu.com oneiric Release                                                                     
Get: 4 http://ppa.launchpad.net oneiric Release [9,754 B]                                                        
Hit http://liveusb.info all Release                                                                              
Hit http://us.archive.ubuntu.com oneiric Release                                                                 
Get: 5 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]                                            
Hit http://archive.canonical.com oneiric Release                                                                 
Hit http://ppa.launchpad.net oneiric Release                                                                     
Hit http://download.jitsi.org unstable/ Release                                                                  
Hit http://liveusb.info all/main i386 Packages                                                                   
Hit http://ppa.launchpad.net oneiric Release                                                                     
Get: 6 http://us.archive.ubuntu.com oneiric-security Release [40.8 kB]                                           
Ign http://liveusb.info all/main TranslationIndex
Get: 7 http://extras.ubuntu.com oneiric/main i386 Packages [4,266 B]                                             
Hit http://download.jitsi.org unstable/ Packages                                                                 
Hit http://archive.canonical.com oneiric/partner i386 Packages                                                   
Get: 8 http://us.archive.ubuntu.com oneiric-security Release [40.8 kB]                                           
Hit http://us.archive.ubuntu.com oneiric/main Sources                                                            
Hit http://us.archive.ubuntu.com oneiric/restricted Sources
Hit http://us.archive.ubuntu.com oneiric/universe Sources
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages                                                
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security Release                                                        
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex                                             
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Get: 9 http://us.archive.ubuntu.com oneiric-updates/main Sources [180 kB]                                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                       
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages
Ign http://archive.canonical.com oneiric/partner TranslationIndex                                                
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                       
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                                       
Get: 10 http://extras.ubuntu.com oneiric/main Translation-en [701 kB]                                            
Get: 11 http://ppa.launchpad.net oneiric/main Sources [1,432 B]                                                  
Ign http://liveusb.info all/main Translation-en_US                                                               
Get: 12 http://ppa.launchpad.net oneiric/main i386 Packages [2,691 B]                                            
Ign http://liveusb.info all/main Translation-en                                                                  
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                                                      
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex                                           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex                                     
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                       
Get: 13 http://us.archive.ubuntu.com oneiric-updates/main Sources [180 kB]                                       
Hit http://ppa.launchpad.net oneiric/main Sources                                                                
Ign http://archive.canonical.com oneiric/partner Translation-en_US                                               
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                          
Ign http://archive.canonical.com oneiric/partner Translation-en                                                  
Ign http://download.jitsi.org unstable/ Translation-en_US                                                        
Ign http://download.jitsi.org unstable/ Translation-en                                                           
Get: 14 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [3,349 B]                                
Get: 15 http://us.archive.ubuntu.com oneiric-updates/universe Sources [72.0 kB]                                  
Get: 16 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,700 B]                                
Get: 17 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [440 kB]                                 
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                                                      
Get: 18 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [6,645 B]                          
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                         
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Get: 19 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [152 kB]                             
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                         
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                                                      
Get: 20 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,363 B]                          
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                         
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex                                     
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/main Sources/DiffIndex                                         
Ign http://us.archive.ubuntu.com oneiric-security/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/universe i386 Packages/DiffIndex                               
Ign http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages/DiffIndex                             
Hit http://us.archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex
Get: 21 http://us.archive.ubuntu.com oneiric-security/main Sources [69.0 kB]                                     
Get: 22 http://us.archive.ubuntu.com oneiric-security/restricted Sources [1,964 B]                               
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en                                               
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en                                               
Get: 23 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,165 kB]                                  
Get: 24 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [209 kB]                                
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en                                       
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en                                       
Get: 25 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [92.6 kB]                           
Hit http://us.archive.ubuntu.com oneiric-security/restricted Translation-en                                      
Hit http://us.archive.ubuntu.com oneiric-security/universe Translation-en
Get: 26 http://us.archive.ubuntu.com oneiric-security/universe Sources [29.4 kB]                                 
Get: 27 http://us.archive.ubuntu.com oneiric-security/multiverse Sources [1,677 B]                               
Get: 28 http://us.archive.ubuntu.com oneiric-security/main i386 Packages [249 kB]                                
Get: 29 http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages [4,062 B]                         
Get: 30 http://us.archive.ubuntu.com oneiric-security/universe i386 Packages [69.0 kB]                           
Get: 31 http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages [3,386 B]                         
Get: 32 http://us.archive.ubuntu.com oneiric-security/main Translation-en [116 kB]                               
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en                                      
Get: 33 http://us.archive.ubuntu.com oneiric/main Translation-en [861 kB]                                        
Fetched 5,604 kB in 38s (147 kB/s)                                                                               
W: GPG error: http://us.archive.ubuntu.com oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Size of file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index is not what the server reported 0 180422

W: GPG error: http://us.archive.ubuntu.com oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Size of file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index is not what the server reported 0 180422

```

The result of the second command gave:
```
W: GPG error: http://us.archive.ubuntu.com oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Size of file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index is not what the server reported 0 180422

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en  Encountered a section with no Package: header

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

I'm going to see about changing the download source...

---

