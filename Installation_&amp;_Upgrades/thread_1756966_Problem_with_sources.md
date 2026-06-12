---
title: "Problem with sources"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by thomasfwilliams on 2011-05-12
When I did "apt-get update" the following happened:
thomasfwilliams@tomslaptop:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                                                                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                    
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty InRelease                                                                                   
Get:1 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                                                                        
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                                                                             
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                                                                            
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease [7,092 B]                                                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                                                                                   
Get:5 [http://packages.unknown-horizons.org](http://packages.unknown-horizons.org) release InRelease [5,317 B]                                                              
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates InRelease                                                                           
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,749 B]                                                                              
Get:7 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]                                                                          
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release [9,753 B]                                                                              
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages [3,262 B]                                                              
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports InRelease                                                                         
Get:10 [http://packages.unknown-horizons.org](http://packages.unknown-horizons.org) release/main Sources [1,110 B]                                                          
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [652 B]                                                                          
Get:12 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages [6,689 B]                                                         
Get:13 [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources [4,170 B]                                                                 
Get:14 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources [14 B]                                                                           
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security InRelease                                                                          
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [550 B]                                                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                                                                       
Get:16 [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages [7,871 B]                                                           
Get:17 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages [14 B]                                                                     
Get:18 [http://packages.unknown-horizons.org](http://packages.unknown-horizons.org) release/main i386 Packages [992 B]                                                      
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed InRelease                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                                                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                                                            
Get:19 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty Release.gpg [198 B]                                                                      
Ign [http://packages.unknown-horizons.org](http://packages.unknown-horizons.org) release/main TranslationIndex                                                              
Get:20 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex                                                                
Get:21 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates Release.gpg [198 B]                                                              
Get:22 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports Release.gpg [198 B]                                                            
Get:23 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security Release.gpg [198 B]                                                             
Get:24 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed Release.gpg [198 B]                                                             
Get:25 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty Release [39.8 kB]                                                                        
Get:26 [http://packages.unknown-horizons.org](http://packages.unknown-horizons.org) release/main Translation-en                                                             
88% [26 Translation-en xz 0 B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Connecting to packages.unknown-hor/usr/bin/xz: (stdin): File format not recognized
Get:27 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates Release [27.2 kB]                                                                
Get:28 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports Release [23.3 kB]                                                              
Get:29 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security Release [23.2 kB]                                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_CA                                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_CA                                                                           
Get:30 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed Release [27.2 kB]                                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                                              
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_CA                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                                                                              
Get:31 [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                                                                    
Get:32 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/main Sources [862 kB]                                                                    
Ign [http://packages.unknown-horizons.org](http://packages.unknown-horizons.org) release/main Translation-en_CA                                                             
Ign [http://packages.unknown-horizons.org](http://packages.unknown-horizons.org) release/main Translation-en                                                                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_CA                                                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en                                                                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_CA                                                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en                                                                     
Get:33 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/restricted Sources [4,104 B]                                                             
Get:34 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/multiverse Sources [155 kB]                                                              
Get:35 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/universe Sources [4,380 kB]                                                              
Get:36 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/main i386 Packages [1,550 kB]                                                            
Get:37 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/restricted i386 Packages [8,986 B]                                                       
Get:38 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/multiverse i386 Packages [183 kB]                                                        
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/main TranslationIndex                                                                       
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/multiverse TranslationIndex                                                                 
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/restricted TranslationIndex                                                                 
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/universe TranslationIndex                                                                   
Get:39 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/restricted Sources [14 B]                                                        
Get:40 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/main Sources [22.4 kB]                                                           
Get:41 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/multiverse Sources [980 B]                                                       
Get:42 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/universe Sources [6,905 B]                                                       
Get:43 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/universe i386 Packages                                                                   
99% [43 Packages bzip2 0 B] [Connecting to samaritan.ucmerced.edu]                                                 2 B/s 4h 6min 49sbzip2: (stdin) is not a bzip2 file.
Get:44 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/main i386 Packages [83.0 kB]                                                     
Get:45 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/restricted i386 Packages [14 B]                                                  
Get:46 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/universe i386 Packages [29.0 kB]                                                 
Get:47 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/multiverse i386 Packages [2,217 B]                                               
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/main TranslationIndex                                                               
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/multiverse TranslationIndex                                                         
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/restricted TranslationIndex                                                         
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/universe TranslationIndex                                                           
Get:48 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/main Sources [1,136 B]                                                         
Get:49 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/restricted Sources [14 B]                                                      
Get:50 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/universe Sources [1,536 B]                                                     
Get:51 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/multiverse Sources [14 B]                                                      
Get:52 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/main i386 Packages [1,122 B]                                                   
Get:53 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/restricted i386 Packages [14 B]                                                
Get:54 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/universe i386 Packages [2,267 B]                                               
Get:55 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/multiverse i386 Packages [14 B]                                                
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/main TranslationIndex                                                             
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/multiverse TranslationIndex                                                       
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/restricted TranslationIndex                                                       
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/universe TranslationIndex                                                         
Get:56 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/main Sources [5,941 B]                                                          
Get:57 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/multiverse Sources [14 B]                                                       
Get:58 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/universe Sources [2,151 B]                                                      
Get:59 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/main i386 Packages [20.6 kB]                                                    
Get:60 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/restricted i386 Packages [14 B]                                                 
Get:61 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/universe i386 Packages [9,495 B]                                                
Get:62 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/multiverse i386 Packages [14 B]                                                 
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/main TranslationIndex                                                              
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/multiverse TranslationIndex                                                        
Get:63 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/restricted Sources                                                              
99% [63 Sources bzip2 0 B] [Connecting to samaritan.ucmerced.edu]                                                      1,516 B/s 21sbzip2: (stdin) is not a bzip2 file.
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/restricted TranslationIndex                                                        
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/universe TranslationIndex                                                          
Get:64 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/restricted i386 Packages [14 B]                                                 
Get:65 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/main i386 Packages [86.3 kB]                                                    
Get:66 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/multiverse i386 Packages [14 B]                                                 
Get:67 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/universe i386 Packages [18.4 kB]                                                
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/main TranslationIndex                                                              
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/multiverse TranslationIndex                                                        
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/restricted TranslationIndex                                                        
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/universe TranslationIndex                                                          
Get:68 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/main Translation-en_CA [10.1 kB]                                                         
Get:69 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/restricted Translation-en_CA [425 B]                                                     
Get:70 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/restricted Translation-en_CA                                                    
99% [70 Translation-en_CA bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:71 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/restricted Translation-en_CA                                                    
99% [71 Translation-en_CA xz 0 B]/usr/bin/xz: (stdin): File format not recognized
Get:72 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/restricted Translation-en_CA                                                   
99% [72 Translation-en_CA lzma 0 B] [Waiting for headers]/usr/bin/lzma: Decoder error
Get:73 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/multiverse Translation-en                                                        
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/main Translation-en                                                                         
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/multiverse Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/restricted Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/universe Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/universe Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/main Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/main Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/multiverse Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/restricted Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/restricted Translation-en
Get:74 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty/multiverse Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/universe Translation-en_CA                                                          
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-updates/universe Translation-en                                                             
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/main Translation-en_CA                                                            
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/main Translation-en                                                               
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/multiverse Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/multiverse Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/restricted Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/universe Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/universe Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/main Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/main Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/multiverse Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/multiverse Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/restricted Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/universe Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-backports/restricted Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/universe Translation-en                                                            
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/main Translation-en_CA                                                             
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/main Translation-en                                                                
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/multiverse Translation-en_CA                                                       
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/restricted Translation-en                                                          
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/universe Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-security/restricted Translation-en_CA
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/universe Translation-en
Ign [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/restricted Translation-en_CA
Get:75 [http://samaritan.ucmerced.edu](http://samaritan.ucmerced.edu) natty-proposed/multiverse Translation-en                                                       
Fetched 7,830 kB in 17min 55s (7,282 B/s)                                                                                           
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/samaritan.ucmerced.edu_ubuntu_dists_natty_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

I deleted the files in the directory /var/lib/apt/lists/ as suggested in another thread and still got the above. Any ideas?

---

### Post by tommcd on 2011-05-13
Can you try selecting a different mirror for your sources? Then run *sudo apt-get update* again.
Also, remove any third party repositories until you get this sorted out.

---

### Post by thomasfwilliams on 2011-05-14
I have selected new sources twice. The hang ups appear to be in the translations files not being recognized as a bzip2 file and then dropping the whole process out no matter the source. Any ideas?

---

