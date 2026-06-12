---
title: "Could not download all repository indexes"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by JesMFN on 2011-03-13
update manager package error. this is the message: The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.GPG error: [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81D820A9BB7A1A83Failed to fetch [http://www.statux.org/ubuntu/dists/jaunty/Release](http://www.statux.org/ubuntu/dists/jaunty/Release)  
Some index files failed to download, they have been ignored, or old ones used instead.

whats the deal? im using eebuntu netbook edition

---

### Post by zvacet on 2011-03-13
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  81D820A9BB7A1A83
```

But if you really use Jaunty I think it is a time to upgrade.See [this.]("https://help.ubuntu.com/community/EOLUpgrades/Jaunty")

---

### Post by JesMFN on 2011-03-13
well when i went to that page and entered: Update the package list and upgrade all the installed packages

sudo aptitude update && sudo aptitude safe-upgrade<-- that in my terminal it loads alot of stuff but then stops and says 99% waiting for headers. is it supose to take a really long time.. cuz its not loading

---

### Post by sikander3786 on 2011-03-13
We need to see the _complete_ output of this command please.

```
sudo apt-get update
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags as this will be a long output.

---

### Post by JesMFN on 2011-03-13
jamie@jamie-laptop:~$ sudo aptitude update && sudo aptitude safe-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US     
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty Release.gpg                             
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main Translation-en_US                  
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/restricted Translation-en_US            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                          
Get:2 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release.gpg [489B]                          
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Translation-en_US                        
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/universe Translation-en_US              
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/multiverse Translation-en_US            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates Release.gpg                     
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/main Translation-en_US          
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US    
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/universe Translation-en_US      
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US    
Hit [http://www.array.org](http://www.array.org) jaunty Release.gpg                                     
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty Release                                 
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Translation-en_US                    
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Translation-en_US                     
Get:3 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release [8711B]                             
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release                                       
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1347B]                               
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                    
Ign [http://www.array.org](http://www.array.org) jaunty/main Translation-en_US                          
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Packages                                 
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main Packages                           
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/restricted Packages                     
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/universe Packages                       
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main Sources                            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/restricted Sources                      
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/universe Sources                        
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/multiverse Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages              
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Packages                             
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Packages                              
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1070B]                         
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/multiverse Sources                      
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/main Packages                   
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/restricted Packages             
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/universe Packages               
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/main Sources                    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/restricted Sources              
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/universe Sources                
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/multiverse Packages             
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources               
Hit [http://www.array.org](http://www.array.org) jaunty Release                                         
Hit [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Packages                                 
Hit [http://www.array.org](http://www.array.org) jaunty/main Packages                                   
Hit [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Packages                             
Hit [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Packages                              
Hit [http://www.array.org](http://www.array.org) jaunty/main Sources                                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                      
Ign [http://www.statux.org](http://www.statux.org) jaunty Release.gpg                                    
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Translation-en_US                         
99% [Waiting for headers]                                                       
Ign [http://www.statux.org](http://www.statux.org) jaunty Release
99% [Waiting for headers]
99% [Waiting for headers]
99% [Waiting for headers]
99% [Waiting for headers]
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Packages
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Packages
Err [http://www.statux.org](http://www.statux.org) jaunty/main Packages
  Undetermined Error [IP: 74.125.95.101 80]
Fetched 3104B in 12min 10s (4B/s)
Reading package lists... Done
W: GPG error: [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81D820A9BB7A1A83
W: You may want to run apt-get update to correct these problems

---

### Post by sikander3786 on 2011-03-13
Did you try adding the missing GPG key as mentioned above by *zvacet*?

And there is a lock error as well which means that you are running 2 or more package managers simultaneously e.g, apt-get, aptitude, Synaptic, Software Center, Update Manager or some other. Close the other one, log out and back in and try the commands once again.

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

And where did you get these repositories from? I don't know if you need them or not but disabling them might help.

> Ign [http://www.statux.org](http://www.statux.org) jaunty Release.gpg
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Translation-en_US
99% [Waiting for headers]
Ign [http://www.statux.org](http://www.statux.org) jaunty Release
99% [Waiting for headers]
99% [Waiting for headers]
99% [Waiting for headers]
99% [Waiting for headers]
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Packages
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Packages
Err [http://www.statux.org](http://www.statux.org) jaunty/main Packages

To disable them, open your sources.list file and place a # sign in the beginning of the intended line.

```
gksudo gedit /etc/apt/sources.list
```

It is recommended once again that you upgrade to a current release.

---

### Post by JesMFN on 2011-03-13
Did you try adding the missing GPG key as mentioned above by zvacet?<---- im a noob so thats like greek to me.... what does that mean?

i restarted it and got this out come: jamie@jamie-laptop:~$ sudo aptitude update && sudo aptitude safe-upgrade
[sudo] password for jamie: 
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty Release.gpg
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main Translation-en_US                  
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/restricted Translation-en_US            
Get:1 [http://www.array.org](http://www.array.org) jaunty Release.gpg [197B]                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US     
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/universe Translation-en_US              
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/multiverse Translation-en_US            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates Release.gpg                     
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/main Translation-en_US          
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US    
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/universe Translation-en_US      
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                          
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty Release                                 
Ign [http://www.array.org](http://www.array.org) jaunty/main Translation-en_US                          
Get:2 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release.gpg [489B]                          
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Translation-en_US                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates Release                         
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Translation-en_US                    
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Translation-en_US                     
Get:3 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release [8711B]                             
Hit [http://www.array.org](http://www.array.org) jaunty Release                                         
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main Packages                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                 
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages              
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/restricted Packages                     
Hit [http://www.array.org](http://www.array.org) jaunty/main Packages                                   
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/universe Packages                       
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main Sources                            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/restricted Sources                      
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/universe Sources                        
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/multiverse Packages                     
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/multiverse Sources                      
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Packages                             
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources               
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/main Packages                   
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/restricted Packages             
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/universe Packages               
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/main Sources                    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/restricted Sources              
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/universe Sources                
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/multiverse Packages             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US             
Hit [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Packages                                 
Hit [http://www.array.org](http://www.array.org) jaunty/main Sources                                    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/multiverse Sources              
Hit [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Packages                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                                
Hit [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages      
Ign [http://www.statux.org](http://www.statux.org) jaunty Release.gpg                    
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Translation-en_US                         
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US 
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [1347B]
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [1070B]
Ign [http://www.statux.org](http://www.statux.org) jaunty Release                                        
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Packages
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Packages
Err [http://www.statux.org](http://www.statux.org) jaunty/main Packages
  Undetermined Error [IP: 74.125.95.113 80]
Fetched 3301B in 12min 9s (5B/s)
Reading package lists... Done
W: GPG error: [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81D820A9BB7A1A83
W: You may want to run apt-get update to correct these problems

im not really sure how to disable them but i put in that code and got the repository

---

### Post by kagerato on 2011-03-13
> **JesMFN said:**
> Did you try adding the missing GPG key as mentioned above by zvacet?<---- im a noob so thats like greek to me.... what does that mean?

...

im not really sure how to disable them but i put in that code and got the repository

The DEB packages are cryptographically signed.  One of the errors you're getting is related to the fact that the signing key is not registered (trusted) locally.  You can trust it manually by running the `apt-key` command that zvacet gave you.

The core problem seems to be that this key is out-of-date or rescinded in some way.  Normally, you don't have to manually trust or manage any keys to add or remove packages in the core repositories.

As to disabling repositories, you just edit the textfile /etc/apt/sources.list  .  Add a hash mark '#' as the first character on the statusx lines to comment them out.  You need root access to write to that file; that's what the gksudo of `gksudo gedit /etc/apt/sources.list` is about.  You can accomplish the same goal with Synaptic, assuming you have it installed.  There's a repositories menu where you can enable and disable particular ones.

---

### Post by zvacet on 2011-03-14
Jaunty is not supported any more and that is source of all your problems.Please,read [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) for general info and [https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty) for upgrade Jaunty to Karmic.

---

### Post by JesMFN on 2011-03-14
i dont have jaunty.. so how can i got to karmac without having jaunty first.

---

### Post by sikander3786 on 2011-03-15
Do you mean you were using Karmic and not Jaunty and somehow messed your sources.list accidently? What is the output of this command.

```
cat /etc/*release
```

It it says Karmic, then you are definitely using Karmic Koala and you need to generate a new sources.list.

[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

---

