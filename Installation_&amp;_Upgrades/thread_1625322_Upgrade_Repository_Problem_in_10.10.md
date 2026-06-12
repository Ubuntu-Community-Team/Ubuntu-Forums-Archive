---
title: "Upgrade Repository Problem in 10.10"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by pgoffa01 on 2010-11-18
The past few days, I've noticed the my Ubuntu box hasn't gotten any updates.  I open up update manager and find that it's been twelve days since the repositories have been updated.  So I run a

 ```
sudo apt-get update
``` a few times and nothing. I keep getting this:

```
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://linux.dropbox.com maverick Release.gpg                              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_CA           
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://linux.dropbox.com maverick Release                                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_CA           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net//ppa/ubuntu/ maverick/main Translation-en         
Ign http://ppa.launchpad.net//ppa/ubuntu/ maverick/main Translation-en_CA      
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_CA
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/bit-team/stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/bit-team/stable/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Hit http://archive.getdeb.net maverick-getdeb Release.gpg                      
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en      
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en_CA   
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Ign http://ppa.launchpad.net/doctormo/barry-snapshot/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/doctormo/barry-snapshot/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_CA
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_CA       
Get:2 http://dl.google.com stable Release [1,347B]                             
Get:3 http://ca.archive.ubuntu.com maverick Release.gpg [198B]                 
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Get:4 http://dl.google.com stable/main i386 Packages [1,088B]                  
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_CA       
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_CA 
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_CA 
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_CA   
Hit http://ca.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick-backports Release.gpg                
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick-proposed Release.gpg                 
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en 
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick Release                              
Hit http://ca.archive.ubuntu.com maverick-updates Release                      
Hit http://ca.archive.ubuntu.com maverick-backports Release                    
Hit http://ca.archive.ubuntu.com maverick-proposed Release                     
Hit http://ca.archive.ubuntu.com maverick/main Sources                         
Hit http://ca.archive.ubuntu.com maverick/restricted Sources                   
Hit http://ca.archive.ubuntu.com maverick/universe Sources                     
Hit http://ca.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://ca.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://ca.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://ca.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://ca.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://ca.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://ca.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://ca.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://ca.archive.ubuntu.com maverick-updates/main i386 Packages           
Hit http://ca.archive.ubuntu.com maverick-updates/restricted i386 Packages     
Hit http://ca.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Hit http://ca.archive.ubuntu.com maverick-backports/main i386 Packages         
Hit http://ca.archive.ubuntu.com maverick-backports/restricted i386 Packages   
Hit http://ca.archive.ubuntu.com maverick-backports/universe i386 Packages     
Hit http://ca.archive.ubuntu.com maverick-backports/multiverse i386 Packages   
Hit http://ca.archive.ubuntu.com maverick-proposed/restricted i386 Packages    
Hit http://ca.archive.ubuntu.com maverick-proposed/main i386 Packages          
Hit http://ca.archive.ubuntu.com maverick-proposed/multiverse i386 Packages    
Hit http://ca.archive.ubuntu.com maverick-proposed/universe i386 Packages      
Hit http://archive.getdeb.net maverick-getdeb Release                          
Hit http://archive.getdeb.net maverick-getdeb/apps Sources                     
Err http://archive.canonical.com maverick Release.gpg                          
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Hit http://archive.getdeb.net maverick-getdeb/apps i386 Packages               
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_CA    
Hit http://archive.canonical.com maverick Release                              
Ign http://archive.canonical.com maverick/partner Sources/DiffIndex            
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex      
Hit http://archive.canonical.com maverick/partner Sources                      
Hit http://archive.canonical.com maverick/partner i386 Packages                
Fetched 2,830B in 11s (250B/s)                                                 
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net//ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net//ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```So, I go through the list of software sources and all the ones that Ubuntu cannot find, when opened in a browser, are non existent on the host server?  Is this a problem with Canonical or is something screwy with my sources?

---

### Post by dino99 on 2010-11-19
desactivate extras repo

---

### Post by sikander3786 on 2010-11-19
For these errors,

> W: Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net//ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net//ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

Go to Software Center > Edit > Software Sources > Other Software Tab and deactivate the offensive ppas and try apt-get update again.

If this one is still there,

> W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

You'll need to setup a DNS. You can try Google DNS.

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

Or OpenDNS,

[http://ubuntuforums.org/showpost.php?p=9397572&postcount=23](http://ubuntuforums.org/showpost.php?p=9397572&postcount=23)

Good Luck!

---

### Post by pgoffa01 on 2010-11-19
I changed my DNS settings (applied static ip and set to public DNS server with two addressess), and tried it again.  Same error but with a different site.  Once again, I tried to open each of the funky urls in firefox and they were all apache domains but none of them could be found.  

I'm also dual booting Mint and for some reason, ubuntu was looking at the sources in the other drive as well as its own so it thought that there were duplicate entries.

So.........heres what ive done so far........

1. Manual DNS and IP settings
2. Removed any ppa entries that were inop
3. Unmounted sister partition (so no more duplicate entries)
4. Changed the update server from Canada (default for some reason) to Main Server

My new output looks like this......

```
sudo apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_CA                                               
Hit http://archive.canonical.com maverick Release.gpg                                                              
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                           
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_CA                                        
Hit http://extras.ubuntu.com maverick Release                                                                      
Hit http://ppa.launchpad.net maverick Release.gpg                                                                  
Hit http://ppa.launchpad.net maverick Release.gpg                                                                  
Ign http://ppa.launchpad.net/doctormo/barry-snapshot/ubuntu/ maverick/main Translation-en                          
Hit http://archive.canonical.com maverick Release                                                                  
Hit http://linux.dropbox.com maverick Release.gpg                                                                  
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en                                                  
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_CA                                               
Hit http://extras.ubuntu.com maverick/main Sources                                                                 
Ign http://ppa.launchpad.net/doctormo/barry-snapshot/ubuntu/ maverick/main Translation-en_CA                       
Hit http://ppa.launchpad.net maverick Release.gpg                                                                  
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en                                    
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_CA                                 
Hit http://linux.dropbox.com maverick Release                                                                      
Hit http://ppa.launchpad.net maverick Release                                                                      
Hit http://ppa.launchpad.net maverick Release                                                                      
Hit http://archive.canonical.com maverick/partner Sources                                                          
Hit http://linux.dropbox.com maverick/main i386 Packages                                                           
Hit http://extras.ubuntu.com maverick/main i386 Packages                                                           
Hit http://ppa.launchpad.net maverick Release                                                                      
Hit http://archive.canonical.com maverick/partner i386 Packages                                                    
Hit http://archive.getdeb.net maverick-getdeb Release.gpg                                                          
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en         
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en_CA      
Hit http://ppa.launchpad.net maverick/main Sources                                             
Hit http://ppa.launchpad.net maverick/main Sources                                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                                       
Hit http://archive.getdeb.net maverick-getdeb Release                                          
Hit http://archive.getdeb.net maverick-getdeb/apps Sources  
Hit http://archive.getdeb.net maverick-getdeb/apps i386 Packages
Err http://archive.ubuntu.com maverick Release.gpg          
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Get:1 http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_CA [10.1kB]
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Get:2 http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_CA [425B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_CA
Get:3 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_CA
Get:4 http://archive.ubuntu.com maverick-backports Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_CA
Get:5 http://archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_CA
Get:6 http://archive.ubuntu.com maverick-proposed Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_CA                               
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_CA                               
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en                                    
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_CA                                 
Get:7 http://archive.ubuntu.com maverick Release [39.8kB]                                                          
Get:8 http://archive.ubuntu.com maverick-updates Release [31.4kB]                                                  
Get:9 http://archive.ubuntu.com maverick-backports Release [23.2kB]                                                
Get:10 http://archive.ubuntu.com maverick-security Release [27.2kB]                                                
Get:11 http://archive.ubuntu.com maverick-proposed Release [31.4kB]                                                
Get:12 http://archive.ubuntu.com maverick/restricted Sources [4,370B]                                              
Get:13 http://archive.ubuntu.com maverick/main Sources [829kB]                                                     
Get:14 http://archive.ubuntu.com maverick/multiverse Sources [151kB]                                               
Get:15 http://archive.ubuntu.com maverick/universe Sources [4,179kB]                                               
Get:16 http://archive.ubuntu.com maverick/main i386 Packages [1,492kB]                                             
Get:17 http://archive.ubuntu.com maverick/restricted i386 Packages [5,992B]                                        
Get:18 http://archive.ubuntu.com maverick/universe i386 Packages [5,791kB]                                         
Get:19 http://archive.ubuntu.com maverick/multiverse i386 Packages [183kB]                                         
Get:20 http://archive.ubuntu.com maverick-updates/restricted Sources [14B]                                         
Get:21 http://archive.ubuntu.com maverick-updates/main Sources [39.1kB]                                            
Get:22 http://archive.ubuntu.com maverick-updates/multiverse Sources [649B]                                        
Get:23 http://archive.ubuntu.com maverick-updates/universe Sources [11.8kB]                                        
Get:24 http://archive.ubuntu.com maverick-updates/main i386 Packages [100kB]                                       
Get:25 http://archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]                                   
Get:26 http://archive.ubuntu.com maverick-updates/universe i386 Packages [38.0kB]                                  
Get:27 http://archive.ubuntu.com maverick-updates/multiverse i386 Packages [1,958B]                                
Get:28 http://archive.ubuntu.com maverick-backports/main Sources [14B]                                             
Get:29 http://archive.ubuntu.com maverick-backports/restricted Sources [14B]                                       
Get:30 http://archive.ubuntu.com maverick-backports/universe Sources [789B]                                        
Get:31 http://archive.ubuntu.com maverick-backports/multiverse Sources [14B]                                       
Get:32 http://archive.ubuntu.com maverick-backports/main i386 Packages [14B]                                       
Get:33 http://archive.ubuntu.com maverick-backports/restricted i386 Packages [14B]                                 
Get:34 http://archive.ubuntu.com maverick-backports/universe i386 Packages [1,432B]                                
Get:35 http://archive.ubuntu.com maverick-backports/multiverse i386 Packages [14B]                                 
Get:36 http://archive.ubuntu.com maverick-security/restricted Sources [14B]                                        
Get:37 http://archive.ubuntu.com maverick-security/main Sources [12.7kB]                                           
Get:38 http://archive.ubuntu.com maverick-security/multiverse Sources [649B]                                       
Get:39 http://archive.ubuntu.com maverick-security/universe Sources [3,279B]                                       
Get:40 http://archive.ubuntu.com maverick-security/main i386 Packages [36.4kB]                                     
Get:41 http://archive.ubuntu.com maverick-security/restricted i386 Packages [14B]                                  
Get:42 http://archive.ubuntu.com maverick-security/universe i386 Packages [13.1kB]                                 
Get:43 http://archive.ubuntu.com maverick-security/multiverse i386 Packages [1,655B]                               
Get:44 http://archive.ubuntu.com maverick-proposed/restricted Sources [14B]                                        
Get:45 http://archive.ubuntu.com maverick-proposed/main Sources [10.2kB]                                           
Get:46 http://archive.ubuntu.com maverick-proposed/multiverse Sources [14B]                                        
Get:47 http://archive.ubuntu.com maverick-proposed/universe Sources [7,135B]                                       
Get:48 http://archive.ubuntu.com maverick-proposed/restricted i386 Packages [14B]                                  
Get:49 http://archive.ubuntu.com maverick-proposed/main i386 Packages [21.1kB]                                     
Get:50 http://archive.ubuntu.com maverick-proposed/multiverse i386 Packages [14B]                                  
Get:51 http://archive.ubuntu.com maverick-proposed/universe i386 Packages [15.7kB]                                 
Fetched 13.1MB in 3min 27s (63.2kB/s)                                                                              
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
 
```

Everytime I fix one, another one errors....


WHAT IS GOING ON???!!!!   Lol


I wonder if Macbooks will be on sale this Friday  lol  just kidding

---

