---
title: "Strange gpg error"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by oranged on 2006-11-19
I have exhausted every avenue trying to resolve this strange gpg error under Edgy. I've even wiped and reinstalled.  So now i'm introducing my problem here.

I get the following error for each repository when 'sudo apt-get update' is ran.

```
W: GPG error: http://security.ubuntu.com edgy-security Release: Internal error: Good signature, but could not determine key fingerprint?!
```

Heres the whole 'sudo apt-get update' output:

```
jason@breadbox:~$ sudo apt-get update
Ign http://espergreen.com edgy Release.gpg
Ign http://espergreen.com edgy/main Translation-en_US                          
Hit http://espergreen.com edgy Release                                         
Ign http://espergreen.com edgy/main Packages                                   
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Get:2 http://archive.canonical.com edgy-commercial Release.gpg [191B]          
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US        
Hit http://espergreen.com edgy/main Packages                                   
Get:3 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://archive.ubuntu.com edgy/main Translation-en_US                      
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com edgy-security Release                 
Get:4 http://packages.freecontrib.org edgy-plf Release.gpg [189B]    
Hit http://archive.canonical.com edgy-commercial Release             
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US      
Ign http://archive.ubuntu.com edgy/universe Translation-en_US       
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US     
Get:5 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]    
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US  
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US
Ign http://packages.freecontrib.org edgy-plf/free Translation-en_US 
Ign http://packages.freecontrib.org edgy-plf/non-free Translation-en_US
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US
Get:6 http://archive.ubuntu.com edgy-updates Release.gpg [189B]
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US   
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://packages.freecontrib.org edgy-plf Release                
Err http://security.ubuntu.com edgy-security Release                
  
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Get:7 http://archive.ubuntu.com edgy-backports Release.gpg [191B]  
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com edgy Release                         
Hit http://archive.ubuntu.com edgy-proposed Release                
Get:8 http://security.ubuntu.com edgy-security Release [27.3kB]    
Hit http://archive.ubuntu.com edgy-updates Release                          
Err http://archive.canonical.com edgy-commercial Release                      
  
Hit http://archive.ubuntu.com edgy-backports Release                          
Get:9 http://archive.canonical.com edgy-commercial Release [4874B]            
Err http://packages.freecontrib.org edgy-plf Release                           
  
Get:10 http://packages.freecontrib.org edgy-plf Release [9454B]
Err http://archive.ubuntu.com edgy Release               
  
Get:11 http://archive.ubuntu.com edgy Release [34.7kB]                         
Ign http://security.ubuntu.com edgy-security Release                           
Hit http://security.ubuntu.com edgy-security/main Packages           
Get:12 http://archive.ubuntu.com edgy-proposed Release [19.6kB]      
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Ign http://archive.canonical.com edgy-commercial Release                       
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Hit http://security.ubuntu.com edgy-security/multiverse Sources                
Hit http://archive.canonical.com edgy-commercial/main Packages                 
Get:13 http://archive.ubuntu.com edgy-updates Release [19.6kB]                 
Ign http://packages.freecontrib.org edgy-plf Release         
Hit http://packages.freecontrib.org edgy-plf/free Packages                     
Ign http://archive.ubuntu.com edgy Release                                     
Hit http://packages.freecontrib.org edgy-plf/non-free Packages                 
Hit http://packages.freecontrib.org edgy-plf/free Sources                      
Hit http://packages.freecontrib.org edgy-plf/non-free Sources                  
Ign http://archive.ubuntu.com edgy-proposed Release                            
Get:14 http://archive.ubuntu.com edgy-backports Release [23.3kB]
Ign http://archive.ubuntu.com edgy-updates Release           
Hit http://archive.ubuntu.com edgy/main Packages             
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy/main Sources  
Hit http://archive.ubuntu.com edgy/restricted Sources
Hit http://archive.ubuntu.com edgy/universe Sources
Hit http://archive.ubuntu.com edgy/multiverse Sources
Hit http://archive.ubuntu.com edgy-proposed/main Packages
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages
Hit http://archive.ubuntu.com edgy-proposed/universe Packages
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Ign http://archive.ubuntu.com edgy-backports Release
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://archive.ubuntu.com edgy-updates/main Sources
Hit http://archive.ubuntu.com edgy-updates/restricted Sources
Hit http://archive.ubuntu.com edgy-updates/universe Sources
Hit http://archive.ubuntu.com edgy-updates/multiverse Sources
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/main Sources
Hit http://archive.ubuntu.com edgy-backports/restricted Sources
Hit http://archive.ubuntu.com edgy-backports/universe Sources
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources
Fetched 140kB in 6s (23.3kB/s)                                                 
Reading package lists... Done
W: GPG error: http://security.ubuntu.com edgy-security Release: Internal error: Good signature, but could not determine key fingerprint?!
W: GPG error: http://archive.canonical.com edgy-commercial Release: Internal error: Good signature, but could not determine key fingerprint?!
W: GPG error: http://packages.freecontrib.org edgy-plf Release: Internal error: Good signature, but could not determine key fingerprint?!
W: GPG error: http://archive.ubuntu.com edgy Release: Internal error: Good signature, but could not determine key fingerprint?!
W: GPG error: http://archive.ubuntu.com edgy-proposed Release: Internal error: Good signature, but could not determine key fingerprint?!
W: GPG error: http://archive.ubuntu.com edgy-updates Release: Internal error: Good signature, but could not determine key fingerprint?!
W: GPG error: http://archive.ubuntu.com edgy-backports Release: Internal error: Good signature, but could not determine key fingerprint?!
W: You may want to run apt-get update to correct these problems

```

Any input would be appreciated. I have searched high and low for some kind of fix but the only mailing lists where this problem might be discussed is in every other language except english. ](*,)

Thanks!

Jason

---

### Post by oranged on 2006-11-23
bump.

Any ideas?

---

### Post by taurus on 2006-11-23
I would at least put a # in front of those lines in /etc/apt/sources.list to comment them out for now...

```
gksudo gedit /etc/apt/sources.list
```

```

#http://security.ubuntu.com edgy-security 
#http://archive.canonical.com edgy-commercial 
#http://packages.freecontrib.org edgy-plf 
#http://archive.ubuntu.com edgy 
#http://archive.ubuntu.com edgy-proposed 
#http://archive.ubuntu.com edgy-updates 
#http://archive.ubuntu.com edgy-backports

```
Then,

```
sudo aptitude update
sudo aptitude upgrade
```

---

