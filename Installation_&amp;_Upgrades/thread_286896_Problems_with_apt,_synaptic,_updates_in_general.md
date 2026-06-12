---
title: "Problems with apt, synaptic, updates in general"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by feki on 2006-10-28
Hi,

Been running Ubuntu since Warty, and have never experienced this problem.
I ran the dist-upgrade from 6.06 to 6.10 a few weeks back, and have been receiving a steady supply of new packages, up until a few days ago. 

Now, whenever I run update-manager, or apt-get update i get the following output, which looks kind of wrong:

```

fredrik@katamari:/$ sudo apt-get update

Get:1 http://security.ubuntu.com edgy-security Release.gpg [189B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_AU            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_AU      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_AU        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_AU      
Hit http://security.ubuntu.com edgy-security Release                           

Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://archive.ubuntu.com edgy/main Translation-en_AU                      
Hit http://security.ubuntu.com edgy-security/main Packages                     
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Ign http://archive.ubuntu.com edgy/restricted Translation-en_AU                
Ign http://archive.ubuntu.com edgy/universe Translation-en_AU                  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_AU                

Get:3 http://archive.ubuntu.com edgy-updates Release.gpg [189B]                
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_AU              
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_AU        
Hit http://security.ubuntu.com edgy-security/multiverse Sources                
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_AU          
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_AU        

Get:4 http://archive.ubuntu.com edgy-backports Release.gpg [189B]              
Get:5 http://au.archive.ubuntu.com edgy Release.gpg [191B]                     
Get:6 http://au.archive.ubuntu.com edgy-updates Release.gpg [189B]             
Ign http://au.archive.ubuntu.com edgy-updates/main Translation-en_AU           
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_AU            
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_AU      

Get:7 http://edevelop.org dapper Release.gpg [191B]                            
Ign http://edevelop.org dapper/e17 Translation-en_AU                           
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_AU        
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_AU      
Hit http://archive.ubuntu.com edgy Release                                     
Hit http://archive.ubuntu.com edgy-updates Release                             
Hit http://archive.ubuntu.com edgy-backports Release                           
Hit http://archive.ubuntu.com edgy/main Packages                               
Ign http://au.archive.ubuntu.com edgy-updates/restricted Translation-en_AU     
Hit http://au.archive.ubuntu.com edgy Release                                  
Hit http://au.archive.ubuntu.com edgy-updates Release                          
Hit http://archive.ubuntu.com edgy/restricted Packages                         
Hit http://archive.ubuntu.com edgy/universe Packages                           
Hit http://archive.ubuntu.com edgy/multiverse Packages                         
Hit http://archive.ubuntu.com edgy/main Sources                                

Get:8 http://edevelop.org edgy Release.gpg [191B]                              
Ign http://edevelop.org edgy/e17 Translation-en_AU                             
Hit http://archive.ubuntu.com edgy/restricted Sources                          
Hit http://archive.ubuntu.com edgy/universe Sources                            
Hit http://archive.ubuntu.com edgy/multiverse Sources                          
Hit http://archive.ubuntu.com edgy-updates/main Packages                       
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                 
Hit http://archive.ubuntu.com edgy-updates/universe Packages                   
Hit http://au.archive.ubuntu.com edgy/main Sources                             
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
Hit http://au.archive.ubuntu.com edgy/restricted Sources                       
Hit http://au.archive.ubuntu.com edgy-updates/main Packages                    
Hit http://au.archive.ubuntu.com edgy-updates/restricted Packages              
Hit http://au.archive.ubuntu.com edgy-updates/main Sources                     
Hit http://au.archive.ubuntu.com edgy-updates/restricted Sources               

Get:9 http://de.archive.ubuntu.com edgy Release.gpg [191B]                  
Ign http://de.archive.ubuntu.com edgy/main Translation-en_AU
Ign http://de.archive.ubuntu.com edgy/restricted Translation-en_AU
Ign http://de.archive.ubuntu.com edgy/universe Translation-en_AU
Ign http://de.archive.ubuntu.com edgy/multiverse Translation-en_AU
Hit http://de.archive.ubuntu.com edgy Release
Hit http://de.archive.ubuntu.com edgy/main Packages
Hit http://de.archive.ubuntu.com edgy/restricted Packages
Hit http://de.archive.ubuntu.com edgy/universe Packages
Hit http://de.archive.ubuntu.com edgy/multiverse Packages
Hit http://de.archive.ubuntu.com edgy/main Sources
Hit http://de.archive.ubuntu.com edgy/restricted Sources
Hit http://de.archive.ubuntu.com edgy/universe Sources
Hit http://de.archive.ubuntu.com edgy/multiverse Sources

Fetched 9B in 3s (2B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```


And, I basically haven't gotten any updates since October 24th, which I suspect is wrong. I mean, something must have been updated since then?

---

### Post by aysiu on 2006-10-28
```
sudo aptitude update
``` (or *sudo apt-get update*, as you're using) checks to see what's in the repositories--it doesn't actually install any updates or upgrades.

After you run that command, you need to run ```
sudo aptitude dist-upgrade
``` to install any updates. By the way, you have both Australian and German mirrors in your repositories list...?

---

### Post by feki on 2006-10-28
Hi, thanks for  the reply. I was beginning to feel quite alone out here ;)

> **aysiu said:**
> ```
sudo aptitude update
``` (or *sudo apt-get update*, as you're using) checks to see what's in the repositories--it doesn't actually install any updates or upgrades.


No, I knew that. The thing I was trying to get across was the unproportionate number of Ign's in the statistics, and requests for 
'Translation-en_AU' instead of 'Release' or 'Packages'. (See attached snapshot for example). Should it be like that? 

> **aysiu said:**
> 
After you run that command, you need to run ```
sudo aptitude dist-upgrade
``` to install any updates. By the way, you have both Australian and German mirrors in your repositories list...?


Whoa. Thanks. I hadn't actually noticed that. Removed those from my sources.list. However, there are no new packages for me. But maybe that is as it should be, ... Somehow I doubt that 2 days prior to release of a new version, and two days after, there are no new updates? ;)

Also, here is the entire sources.list now, after cleaning:

```
deb-src http://se.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.

deb http://se.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES 

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.) 
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.) 
# deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free
# deb http://compiztools.free.fr/debian unstable main

# deb http://xbgm.sourceforge.net/debian unstable/
# deb-src http://xbgm.sourceforge.net/debian unstable/
```

---

### Post by rsay on 2006-10-28
Same thing here, no upgraded packages for a few days. I was expecting at least one update as well. Are other people getting updated packages during the last few days??

---

### Post by javierfh on 2006-11-02
> **rsay said:**
> Same thing here, no upgraded packages for a few days. I was expecting at least one update as well. Are other people getting updated packages during the last few days??

Has anyone a fix for that?
I am not getting updates either..and when i run update-manager it really takes long and at the end nothing happens.

Is there any log about the packages that have been updated?because update-manager shows briefly some output saying that some things have failed and then says system it is up to date.

Javi


EDIT: i followed the command given here and thats what i get, it is scary that there are so many ign and well also that at the end, there is no update.

> 
javi@javi-desktop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources              
Get:2 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/universe Translation-en_US
Get:3 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates Release.gpg [189B]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Get:4 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports Release.gpg [189B]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy Release
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates Release
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports Release
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/main Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/universe Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/universe Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/universe Packages                                                                                  
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 4B in 54s (0B/s) 
Reading package lists... Done
javi@javi-desktop:~$ 



---

### Post by javierfh on 2006-11-03
Hello...
anyone has any solution for the updates problem?? anyone having same problem...and found a solution?
Is there anything wrong into that result i posted previously? sounds very scary that i dont get absolutely any update.

Thanks in advance,

Javi

---

### Post by feki on 2006-11-05
> **javierfh said:**
> Hello...
anyone has any solution for the updates problem?? anyone having same problem...and found a solution?
Is there anything wrong into that result i posted previously? sounds very scary that i dont get absolutely any update.

Thanks in advance,

Javi

Sorry, but I've been receiving a few updates now, so it seems to have been a false alarm, or just me panicking. =)

---

