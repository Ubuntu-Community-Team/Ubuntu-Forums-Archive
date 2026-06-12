---
title: "Update problems (package fails)"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by timmyhiggy on 2010-03-19
Hi

Whenever I do an update using update-manager, it says "failed" next to all the "translation_en_GB" packages.
I tried doing a command line update and here is what is says:

```
tim@netbook:~$ sudo apt-get update
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_GB          
Hit http://ppa.launchpad.net karmic Release.gpg                     
Hit http://security.ubuntu.com karmic-security Release.gpg                                 
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB                      
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com karmic Release.gpg                  
Hit http://gb.archive.ubuntu.com karmic/main Translation-en_GB       
Hit http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB                       
Get: 1 http://dl.google.com stable Release.gpg [189B]                                      
Ign http://ppa.launchpad.net karmic/main Translation-en_GB                                 
Hit http://ppa.launchpad.net karmic Release.gpg                                            
Ign http://ppa.launchpad.net karmic/main Translation-en_GB                                 
Hit http://ppa.launchpad.net karmic Release                                                
Hit http://gb.archive.ubuntu.com karmic/universe Translation-en_GB                         
Hit http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB                       
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg                                
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB                     
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB               
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB                 
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB               
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB                  
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB                
Hit http://security.ubuntu.com karmic-security Release                                     
Hit http://ppa.launchpad.net karmic Release                                                
Hit http://ppa.launchpad.net karmic Release                          
Hit http://gb.archive.ubuntu.com karmic Release                      
Hit http://gb.archive.ubuntu.com karmic-updates Release                                   
Hit http://ppa.launchpad.net karmic/main Packages                                         
Hit http://security.ubuntu.com karmic-security/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                                         
Hit http://security.ubuntu.com karmic-security/restricted Packages                                              
Hit http://security.ubuntu.com karmic-security/main Sources                                
Hit http://security.ubuntu.com karmic-security/restricted Sources                          
Hit http://security.ubuntu.com karmic-security/universe Packages                           
Hit http://gb.archive.ubuntu.com karmic/main Packages                                      
Hit http://ppa.launchpad.net karmic/main Packages                                          
Hit http://security.ubuntu.com karmic-security/universe Sources      
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://security.ubuntu.com karmic-security/multiverse Sources    
Hit http://gb.archive.ubuntu.com karmic/restricted Packages          
Hit http://gb.archive.ubuntu.com karmic/main Sources
Hit http://gb.archive.ubuntu.com karmic/restricted Sources
Hit http://gb.archive.ubuntu.com karmic/universe Packages
Hit http://gb.archive.ubuntu.com karmic/universe Sources
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://gb.archive.ubuntu.com karmic-updates/main Sources
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages
Hit http://gb.archive.ubuntu.com karmic-updates/universe Sources
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://dl.google.com stable/main Translation-en_GB                                                                      
Get: 2 http://dl.google.com stable Release [2,540B]
Get: 3 http://dl.google.com stable/main Packages [916B]
Fetched 3,645B in 2min 0s (30B/s)
Reading package lists... Done

```

---

### Post by zvacet on 2010-03-19
You can see that kind of things from time to time.Nothing to be worried about.You didn't update language packages.You can live without that.

---

### Post by timmyhiggy on 2010-03-19
It's been like it for quite a few weeks now. Is there a way of making update ignore it? Cos it takes ages!!

---

### Post by slakkie on 2010-03-19
Remove the repo which is slow.. ?

---

### Post by zvacet on 2010-03-19
Under system>admin>software sources change server to main.Maybe that will help.

---

### Post by alexcckll on 2010-04-20
I'm also affected... translation GB lines also failing.

I am scared.  Will my machine break if I tell it to collect updates...or WHNE WILL IT WORK AGAIN?!

---

### Post by alexcckll on 2010-04-20
Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  
Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_GB.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_GB.bz2](http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_GB.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.

When is this going to be fixed?

---

### Post by blade1950 on 2010-04-20
I'm getting the same thing now for the last few days.
Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/karmic/free/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/karmic/non-free/binary-i386/Packages.gz)  Connection failed
Some index files failed to download, they have been ignored, or old ones used instead.
](*,)

---

### Post by BucksBunny on 2010-04-20
There's a problem with the medibuntu repos:

[http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

---

