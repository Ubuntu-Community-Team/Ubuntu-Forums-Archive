---
title: "Ubuntu failing during update"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by p1atypusx on 2011-04-04
I am having a problem updating Ubuntu 10.10.  When I type

> sudo apt-get update

I get the following.

> Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg [198B]                    
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/plushuang-tw/uget-devel/ubuntu/](http://ppa.launchpad.net/plushuang-tw/uget-devel/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/plushuang-tw/uget-devel/ubuntu/](http://ppa.launchpad.net/plushuang-tw/uget-devel/ubuntu/) maverick/main Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Get:4 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                      
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg [198B]                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/r5u87x-loader/ppa/ubuntu/](http://ppa.launchpad.net/r5u87x-loader/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/r5u87x-loader/ppa/ubuntu/](http://ppa.launchpad.net/r5u87x-loader/ppa/ubuntu/) maverick/main Translation-en_US
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg [197B]                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg [198B]        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Ign [http://ppa.launchpad.net/user/ppa-name/ubuntu/](http://ppa.launchpad.net/user/ppa-name/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/user/ppa-name/ubuntu/](http://ppa.launchpad.net/user/ppa-name/ubuntu/) maverick/main Translation-en_US
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://ppa.launchpad.net/weboide/ppa/ubuntu/](http://ppa.launchpad.net/weboide/ppa/ubuntu/) maverick/main Translation-en  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://ppa.launchpad.net/weboide/ppa/ubuntu/](http://ppa.launchpad.net/weboide/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Get:12 [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release.gpg [836B]            
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en      
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en_US   
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/games Translation-en     
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/games Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,765B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources/DiffIndex  
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release [31.4kB]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources/DiffIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages/DiffIndex  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages                   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages             
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [34.3kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps i386 Packages               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/games i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [649B]  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages              
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources [778B] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [13.4kB]  
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources [94.7kB]     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                     
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [118kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources [1,496B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources [39.0kB] 
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [54.9kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages [261kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
  404  Not Found
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [1,660B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages [113kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [2,844B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,562B]
Fetched 773kB in 4min 46s (2,696B/s)                                           
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8BE3EAB5EBE14A20
W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.




When I use Update Manager I get the following error.

> W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8BE3EAB5EBE14A20, W:Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.


It also says that I have lost internet connection but I know that I haven't


It started doing this yesterday.  Don't know why.  Thought maybe it was just servers being serviced or what not so I tried it again today, several times and keep getting the errors.  

Since yesterday I was having problems conducting searches on my laptop so I installed Catfish and Gnome-Do and Tracker.  Don't remember if I installed these before or after my problems began.  

Any suggestions.

---

### Post by plucky on 2011-04-04
> W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8BE3EAB5EBE14A20,

Try in a terminal ```
gpg --keyserver keyserver.ubuntu.com --recv 8BE3EAB5EBE14A20
gpg --export --armor 8BE3EAB5EBE14A20 | sudo apt-key add -
```


> , W:Failed to fetch [http://ppa.launchpad.net/user/ppa-na...86/Packages.gz](http://ppa.launchpad.net/user/ppa-na...86/Packages.gz) 404 Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead. 

That doesn't seem to be a valid PPA

```
http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz
```

Use Software Sources and remove it.

Good Luck

---

### Post by p1atypusx on 2011-04-11
t
Thanks.  That helped.

---

