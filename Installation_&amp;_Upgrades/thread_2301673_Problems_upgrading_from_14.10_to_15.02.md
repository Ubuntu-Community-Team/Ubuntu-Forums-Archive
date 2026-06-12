---
title: "Problems upgrading from 14.10 to 15.02"
date: 2015-11-04
forum: Installation &amp; Upgrades
---

### Post by Fsirett on 2015-11-04
I am afraid I have another problem.

First of all, I tried to install XBMC/Kodi to have a look at it and I found it has bits and bobs it will not install. 

I thought I might go from 14.10 to 15.02, since I seem to be having a few problems. First of all, when I try to update, I get:

failed to download repository information and, when I ask for details, I get this:

```
W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/main/binary-amd64/Packages  404  Not Found, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/universe/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/multiverse/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/restricted/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/universe/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/multiverse/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/restricted/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/restricted/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/universe/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/multiverse/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/restricted/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/universe/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/multiverse/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

If that is of any help.

I tried to do it all from the terminal. I got this:

```
Ign http://ftp.udc.es vivid-backports InReleaseHit http://archive.canonical.com vivid InRelease
Ign http://ftp.udc.es vivid-proposed InRelease                          
Ign http://ftp.udc.es vivid-backports Release.gpg
Ign http://archive.ubuntu.com utopic InRelease 
Ign http://ftp.udc.es vivid-proposed Release.gpg
Ign http://ftp.udc.es vivid-backports Release                        
Ign http://archive.ubuntu.com utopic Release.gpg                     
Ign http://ftp.udc.es vivid-proposed Release                         
Ign http://archive.ubuntu.com utopic Release                         
Hit http://archive.canonical.com vivid/partner Sources
Hit http://archive.canonical.com vivid/partner amd64 Packages                  
Hit http://archive.canonical.com vivid/partner i386 Packages          
Ign http://archive.canonical.com vivid/partner Translation-en                  
Err http://archive.ubuntu.com utopic/main amd64 Packages                       
  404  Not Found [IP: 91.189.91.23 80]
Err http://archive.ubuntu.com utopic/universe amd64 Packages                   
  404  Not Found [IP: 91.189.91.23 80]
Err http://archive.ubuntu.com utopic/main i386 Packages                        
  404  Not Found [IP: 91.189.91.23 80]
Err http://archive.ubuntu.com utopic/universe i386 Packages                    
  404  Not Found [IP: 91.189.91.23 80]
Ign http://archive.ubuntu.com utopic/main Translation-en_GB                    
Ign http://archive.ubuntu.com utopic/main Translation-en                       
Ign http://archive.ubuntu.com utopic/universe Translation-en_GB                
Ign http://archive.ubuntu.com utopic/universe Translation-en                   
Err http://ftp.udc.es vivid-backports/main amd64 Packages                      
  404  Not Found
Err http://ftp.udc.es vivid-backports/universe amd64 Packages                  
  404  Not Found
Err http://ftp.udc.es vivid-backports/multiverse amd64 Packages                
  404  Not Found
Err http://ftp.udc.es vivid-backports/restricted amd64 Packages                
  404  Not Found
Err http://ftp.udc.es vivid-backports/main i386 Packages                       
  404  Not Found
Err http://ftp.udc.es vivid-backports/universe i386 Packages                   
  404  Not Found
Err http://ftp.udc.es vivid-backports/multiverse i386 Packages                 
  404  Not Found
Err http://ftp.udc.es vivid-backports/restricted i386 Packages                 
  404  Not Found
Ign http://ftp.udc.es vivid-backports/main Translation-en_GB                   
Ign http://ftp.udc.es vivid-backports/main Translation-en                      
Ign http://ftp.udc.es vivid-backports/multiverse Translation-en_GB             
Ign http://ftp.udc.es vivid-backports/multiverse Translation-en                
Ign http://ftp.udc.es vivid-backports/restricted Translation-en_GB             
Ign http://ftp.udc.es vivid-backports/restricted Translation-en                
Ign http://ftp.udc.es vivid-backports/universe Translation-en_GB               
Ign http://ftp.udc.es vivid-backports/universe Translation-en                  
Err http://ftp.udc.es vivid-proposed/restricted amd64 Packages                 
  404  Not Found
Err http://ftp.udc.es vivid-proposed/universe amd64 Packages                   
  404  Not Found
Err http://ftp.udc.es vivid-proposed/main amd64 Packages                       
  404  Not Found
Err http://ftp.udc.es vivid-proposed/multiverse amd64 Packages                 
  404  Not Found
Err http://ftp.udc.es vivid-proposed/restricted i386 Packages                  
  404  Not Found
Err http://ftp.udc.es vivid-proposed/universe i386 Packages                    
  404  Not Found
Err http://ftp.udc.es vivid-proposed/main i386 Packages                        
  404  Not Found
Err http://ftp.udc.es vivid-proposed/multiverse i386 Packages                  
  404  Not Found
Ign http://ftp.udc.es vivid-proposed/main Translation-en_GB                    
Ign http://ftp.udc.es vivid-proposed/main Translation-en                       
Ign http://ftp.udc.es vivid-proposed/multiverse Translation-en_GB              
Ign http://ftp.udc.es vivid-proposed/multiverse Translation-en                 
Ign http://ftp.udc.es vivid-proposed/restricted Translation-en_GB              
Ign http://ftp.udc.es vivid-proposed/restricted Translation-en                 
Ign http://ftp.udc.es vivid-proposed/universe Translation-en_GB                
Ign http://ftp.udc.es vivid-proposed/universe Translation-en                   
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/universe/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/restricted/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/restricted/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/universe/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.23 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.23 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.23 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.23 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have looked over everything I can find and tried a few of them but they have provided no joy.

I might point out that it keeps on telling me that it is a connection problem, but I am having no probem connecting, even streaming, from the self same connection on the self same computer. I have shut everything down to have a go and I have tried while I had browsers running, but it is all the same.

Any ideas?

---

### Post by grahammechanical on 2015-11-04
Have you successfully completed the upgrade from Ubuntu 14.10 to 15.04? If so then you should disable the proposed repository. It is only useful if you want to test packages before the are moved in toto the regular update channels.

You can disable both the proposed repository and the backports repository by going to System Settings>Software & Updates>Updates tab and un-checking the boxes Pre-release updates (vivid-proposed) & Unsupported updates (vivid-backports). And those messages will go away.

Now that 15.10 has been released you should keep in mind that 15.04 is now 2 thirds through it life span. All you really need in the Updates tab is Important Security updates (vivid-security) and Recommended updates (vivid-updates).

Regards.

---

### Post by Keith_Valin on 2015-11-04
If you have access to the terminal, try ```
sudo apt-get update
``` then try the update, otherwise, dump what's in there on the forum.

---

### Post by Fsirett on 2015-11-04
Cheers! Just back and just read. 

First of all, I cannot update the system. I started the update (again) and I am getting hung up on the second step. I did change mirrors, thinking that might have been a problem.

It seems to get through part one (Preparing to upgrade), however part two (Setting new software channels). 

It tells me it thinks this is a network problem, so I changed the source, but this is what comes up:

```
[COLOR=#000000]W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...amd64/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-backports/main/binary-amd64/Packages")[COLOR=#000000] 404 Not Found, W:Failed to fetch[/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...amd64/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-backports/universe/binary-amd64/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...amd64/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-backports/multiverse/binary-amd64/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...amd64/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-backports/restricted/binary-amd64/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...-i386/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-backports/main/binary-i386/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...-i386/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-backports/universe/binary-i386/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...-i386/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-backports/multiverse/binary-i386/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...-i386/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-backports/restricted/binary-i386/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...amd64/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-proposed/restricted/binary-amd64/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...amd64/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-proposed/universe/binary-amd64/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...amd64/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-proposed/main/binary-amd64/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...amd64/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-proposed/multiverse/binary-amd64/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...-i386/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-proposed/restricted/binary-i386/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...-i386/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-proposed/universe/binary-i386/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...-i386/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-proposed/main/binary-i386/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], W:Failed to fetch [/COLOR][http://ftp.udc.es/ubuntu/dists/vivid...-i386/Packages]("http://ftp.udc.es/ubuntu/dists/vivid-proposed/multiverse/binary-i386/Packages")[COLOR=#000000] 404 Not Found[/COLOR]
[COLOR=#000000], E:Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]
```



I am just about to try update again, although I am fairly certain it will not work, nor did it. 

My response was:

```
Ign http://ftp.udc.es vivid-backports InReleaseHit http://archive.canonical.com vivid InRelease
Ign http://ftp.udc.es vivid-proposed InRelease                          
Ign http://ftp.udc.es vivid-backports Release.gpg
Ign http://ftp.udc.es vivid-proposed Release.gpg
Ign http://ftp.udc.es vivid-backports Release                        
Ign http://ftp.udc.es vivid-proposed Release                         
Hit http://archive.canonical.com vivid/partner Sources               
Hit http://archive.canonical.com vivid/partner amd64 Packages                  
Hit http://archive.canonical.com vivid/partner i386 Packages          
Hit http://archive.canonical.com vivid/partner Translation-en                  
Ign http://sunsite.rediris.es vivid InRelease                         
Hit http://sunsite.rediris.es vivid Release.gpg 
Hit http://sunsite.rediris.es vivid Release     
Err http://ftp.udc.es vivid-backports/main amd64 Packages                      
  404  Not Found
Err http://ftp.udc.es vivid-backports/universe amd64 Packages                  
  404  Not Found
Err http://ftp.udc.es vivid-backports/multiverse amd64 Packages                
  404  Not Found
Err http://ftp.udc.es vivid-backports/restricted amd64 Packages                
  404  Not Found
Err http://ftp.udc.es vivid-backports/main i386 Packages                       
  404  Not Found
Err http://ftp.udc.es vivid-backports/universe i386 Packages                   
  404  Not Found
Err http://ftp.udc.es vivid-backports/multiverse i386 Packages                 
  404  Not Found
Err http://ftp.udc.es vivid-backports/restricted i386 Packages                 
  404  Not Found
Ign http://ftp.udc.es vivid-backports/main Translation-en_GB                   
Ign http://ftp.udc.es vivid-backports/main Translation-en                      
Ign http://ftp.udc.es vivid-backports/main Translation-en_CA                   
Ign http://ftp.udc.es vivid-backports/multiverse Translation-en_GB             
Ign http://ftp.udc.es vivid-backports/multiverse Translation-en                
Ign http://ftp.udc.es vivid-backports/multiverse Translation-en_CA
Ign http://ftp.udc.es vivid-backports/restricted Translation-en_GB
Ign http://ftp.udc.es vivid-backports/restricted Translation-en
Ign http://ftp.udc.es vivid-backports/restricted Translation-en_CA
Ign http://ftp.udc.es vivid-backports/universe Translation-en_GB
Ign http://ftp.udc.es vivid-backports/universe Translation-en
Ign http://ftp.udc.es vivid-backports/universe Translation-en_CA
Err http://ftp.udc.es vivid-proposed/restricted amd64 Packages             
  404  Not Found
Err http://ftp.udc.es vivid-proposed/universe amd64 Packages               
  404  Not Found
Err http://ftp.udc.es vivid-proposed/main amd64 Packages
  404  Not Found
Err http://ftp.udc.es vivid-proposed/multiverse amd64 Packages
  404  Not Found
Err http://ftp.udc.es vivid-proposed/restricted i386 Packages
  404  Not Found
Err http://ftp.udc.es vivid-proposed/universe i386 Packages
  404  Not Found
Err http://ftp.udc.es vivid-proposed/main i386 Packages
  404  Not Found
Err http://ftp.udc.es vivid-proposed/multiverse i386 Packages
  404  Not Found
Ign http://ftp.udc.es vivid-proposed/main Translation-en_GB
Ign http://ftp.udc.es vivid-proposed/main Translation-en
Ign http://ftp.udc.es vivid-proposed/main Translation-en_CA
Ign http://ftp.udc.es vivid-proposed/multiverse Translation-en_GB
Ign http://ftp.udc.es vivid-proposed/multiverse Translation-en
Ign http://ftp.udc.es vivid-proposed/multiverse Translation-en_CA
Ign http://ftp.udc.es vivid-proposed/restricted Translation-en_GB
Ign http://ftp.udc.es vivid-proposed/restricted Translation-en
Ign http://ftp.udc.es vivid-proposed/restricted Translation-en_CA
Ign http://ftp.udc.es vivid-proposed/universe Translation-en_GB
Ign http://ftp.udc.es vivid-proposed/universe Translation-en
Ign http://ftp.udc.es vivid-proposed/universe Translation-en_CA
Hit http://sunsite.rediris.es vivid/main amd64 Packages
Hit http://sunsite.rediris.es vivid/universe amd64 Packages         
Hit http://sunsite.rediris.es vivid/main i386 Packages              
Hit http://sunsite.rediris.es vivid/universe i386 Packages
Hit http://sunsite.rediris.es vivid/main Translation-en_GB          
Hit http://sunsite.rediris.es vivid/main Translation-en                 
Hit http://sunsite.rediris.es vivid/main Translation-en_CA              
Hit http://sunsite.rediris.es vivid/universe Translation-en_GB          
Hit http://sunsite.rediris.es vivid/universe Translation-en             
Hit http://sunsite.rediris.es vivid/universe Translation-en_CA
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/universe/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/restricted/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-backports/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/restricted/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/universe/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ftp.udc.es/ubuntu/dists/vivid-proposed/multiverse/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead. 
```


Well, it was not my response, exactly, but it is the response that the computer sent my way. At least we are still on speaking terms!

Cheers

---

### Post by Fsirett on 2015-11-19
To close this thread, and hope another coming this way will find some help, here are my newest adventures:

As advised (Many thanks to those who gave me their excellent advice) I turned off all my repos and tried to upgrade and the result was the same. I continued to turn them on and off over the intervening days and always the same result. I tried some three or four times a day and was considering a (much needed) new computer.

However, a day or two ago, I turned on and off all of the repos, as per what was becoming a habit, and the upgrade kicked in successfully.

Completely as speculation, I assume the screen was telling me the repos were off when they had actually not changed status at all. This may not be so surprising as my computer has been through the wars, is over ten years old, and has been through a good few power surges. 

So if you find yourself in a similar situation as I, remember my tale of woe and continue to try as it might just be something of an ornery computer that has to be humoured until it decides to cooperate. It might not appear anywhere else, but this is not the first time a computer has decided to not and say it did.

Thanks again for your help all.

---

