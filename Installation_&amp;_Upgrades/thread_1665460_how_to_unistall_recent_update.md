---
title: "how to unistall recent update"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by alvinmoneypit on 2011-01-12
Is there a way to uninstall an update that hasn't been activated yet?  I don't think it is activated because I haven't rebooted - there were so many problems with it, I'm afraid it will crash my system.

```
sudo apt-get update
Hit http://packages.medibuntu.org maverick Release.gpg
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com maverick Release                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Get:2 http://us.archive.ubuntu.com maverick-updates Release.gpg [198B]         
Err http://pacakge.ubuntu.com maverick Release.gpg                             
  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com maverick-security Release.gpg [198B]        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en 
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://archive.canonical.com maverick/partner i386 Packages                
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Err http://pacakge.ubuntu.com/ubuntu/ maverick/main Translation-en             
  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                              
Get:4 http://us.archive.ubuntu.com maverick-updates Release [31.4kB]           
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Get:5 http://us.archive.ubuntu.com maverick-security Release [27.2kB]          
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US         
Err http://pacakge.ubuntu.com/ubuntu/ maverick/main Translation-en_US          
  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages             
Get:6 http://us.archive.ubuntu.com maverick-updates/main i386 Packages [196kB] 
Hit http://packages.medibuntu.org maverick Release                             
Ign http://pacakge.ubuntu.com maverick Release                                 
Hit http://packages.medibuntu.org maverick/free Sources                        
Ign http://pacakge.ubuntu.com maverick/main Sources                            
Hit http://packages.medibuntu.org maverick/non-free Sources        
Hit http://packages.medibuntu.org maverick/free i386 Packages                  
Ign http://pacakge.ubuntu.com maverick/main i386 Packages                      
Hit http://packages.medibuntu.org maverick/non-free i386 Packages              
Ign http://pacakge.ubuntu.com maverick/main Sources                            
Ign http://pacakge.ubuntu.com maverick/main i386 Packages           
Get:7 http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:8 http://us.archive.ubuntu.com maverick-updates/universe i386 Packages [77.2kB]
Err http://pacakge.ubuntu.com maverick/main Sources                            
  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)
Get:9 http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages [2,522B]
Get:10 http://us.archive.ubuntu.com maverick-security/main i386 Packages [66.6kB]
Err http://pacakge.ubuntu.com maverick/main i386 Packages                      
  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)
Get:11 http://us.archive.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:12 http://us.archive.ubuntu.com maverick-security/universe i386 Packages [33.0kB]
Get:13 http://us.archive.ubuntu.com maverick-security/multiverse i386 Packages [1,655B]
Fetched 436kB in 8s (54.0kB/s)                                                 
W: Failed to fetch http://pacakge.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://pacakge.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://pacakge.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://pacakge.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://pacakge.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

