---
title: "Package installation and updates fail in Ubuntu 11.04"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by ScottSanbar on 2011-09-28
I can no longer use apt-get or the Gui Package Manager in Ubuntu 11.04 Desktop to install packages or updates.  Here is some output from some failed apt-get attempts.  Please help!

```
scott@scotts2ub:~/Downloads$ ls
irssi  paultag  randconverse_1.0-0~5~natty1_i386.deb  typescript
scott@scotts2ub:~/Downloads$ sudo apt-get install *.deb
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package randconverse_1.0-0~5~natty1_i386.deb
E: Couldn't find any package by regex 'randconverse_1.0-0~5~natty1_i386.deb'
scott@scotts2ub:~/Downloads$ sudo apt-get update
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main TranslationIndex                                                                                                              
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted TranslationIndex                                                                                                        
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en_US                                                                                                             
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en                                                                                                                
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en_US                                                                                                       
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en                                                                                                          
Ign http://dl.google.com stable InRelease                                                                                                                                                                     
Ign http://extras.ubuntu.com natty InRelease                                                                                                                                                                  
Ign http://archive.canonical.com natty InRelease                                                                                                                                                              
Ign http://security.ubuntu.com natty-security InRelease                                                          
Ign http://us.archive.ubuntu.com natty InRelease                                                                 
Ign http://us.archive.ubuntu.com natty-updates InRelease                                                         
Hit http://archive.canonical.com natty Release.gpg                                                               
Hit http://extras.ubuntu.com natty Release.gpg                                                                   
Hit http://security.ubuntu.com natty-security Release.gpg                                                        
Hit http://us.archive.ubuntu.com natty Release.gpg                                                               
Hit http://archive.canonical.com natty Release                                                                   
Hit http://extras.ubuntu.com natty Release                                                                       
Hit http://security.ubuntu.com natty-security Release                                                                                   
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                                                                              
Hit http://archive.canonical.com natty/partner i386 Packages                                                     
Hit http://extras.ubuntu.com natty/main Sources                                                                  
Hit http://security.ubuntu.com natty-security/main Sources                                                       
Hit http://us.archive.ubuntu.com natty Release                                                                   
Ign http://archive.canonical.com natty/partner TranslationIndex                                                                                               
Hit http://extras.ubuntu.com natty/main i386 Packages                                                                                  
Ign http://extras.ubuntu.com natty/main TranslationIndex                                                                               
Ign http://ppa.launchpad.net natty InRelease                                                                                           
Ign http://ppa.launchpad.net natty InRelease                                                                     
Hit http://security.ubuntu.com natty-security/restricted Sources                                                 
Hit http://security.ubuntu.com natty-security/universe Sources                                                   
Hit http://security.ubuntu.com natty-security/multiverse Sources                                                 
Hit http://security.ubuntu.com natty-security/main i386 Packages                                                 
Hit http://security.ubuntu.com natty-security/restricted i386 Packages                                           
Hit http://us.archive.ubuntu.com natty-updates Release                                                                                 
Ign http://ppa.launchpad.net natty Release.gpg                                                                                                                
Hit http://security.ubuntu.com natty-security/universe i386 Packages                                                                   
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages                                           
Ign http://security.ubuntu.com natty-security/main TranslationIndex                                              
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex                                        
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex                                        
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                                          
Hit http://us.archive.ubuntu.com natty/main Sources                                                              
Hit http://us.archive.ubuntu.com natty/restricted Sources                                                                              
Hit http://us.archive.ubuntu.com natty/universe Sources                                                                                
Hit http://us.archive.ubuntu.com natty/multiverse Sources                                                                              
Hit http://us.archive.ubuntu.com natty/main i386 Packages                                                                              
Ign http://ppa.launchpad.net natty Release.gpg                                                                                         
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                                                                        
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                                                    
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                                                  
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                                                     
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex                                               
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex                                               
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex                                                 
Hit http://us.archive.ubuntu.com natty-updates/main Sources                                                                            
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources                                                                      
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                                                                        
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources                                                                      
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages                                                                      
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages                                                                
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages                                                                  
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages                                                                
Get:1 http://dl.google.com stable Release.gpg [198 B]                                                                                  
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex                                                                          
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex                                                                    
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex                                                                    
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex                                                                      
Ign http://ppa.launchpad.net natty Release                                                                                                    
Ign http://ppa.launchpad.net natty Release                                                                                                    
Get:2 http://dl.google.com stable Release [1,347 B]                                                              
Ign http://archive.canonical.com natty/partner Translation-en_US                                                                            
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                         
Ign http://extras.ubuntu.com natty/main Translation-en_US                                                                              
Ign http://archive.canonical.com natty/partner Translation-en                                                                          
Ign http://extras.ubuntu.com natty/main Translation-en                                                           
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                         
Ign http://security.ubuntu.com natty-security/main Translation-en_US                       
Ign http://security.ubuntu.com natty-security/main Translation-en                          
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US                 
Ign http://security.ubuntu.com natty-security/multiverse Translation-en                    
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US                 
Ign http://security.ubuntu.com natty-security/restricted Translation-en                    
Ign http://security.ubuntu.com natty-security/universe Translation-en_US                   
Ign http://security.ubuntu.com natty-security/universe Translation-en                      
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                              
Ign http://us.archive.ubuntu.com natty/main Translation-en           
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en     
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com natty/restricted Translation-en     
Err http://ppa.launchpad.net natty/main Sources                                                      
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                                                
  404  Not Found
Get:3 http://dl.google.com stable/main i386 Packages [1,190 B]                                       
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US          
Ign http://us.archive.ubuntu.com natty/universe Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US      
Err http://ppa.launchpad.net natty/main Sources                            
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                      
  404  Not Found
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en         
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en   
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en   
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US  
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en     
Ign http://ppa.launchpad.net natty/main Translation-en_US                  
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_US                                                                                                                                                        
Ign http://dl.google.com stable/main Translation-en
Fetched 2,735 B in 13s (195 B/s)
W: Failed to fetch http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
scott@scotts2ub:~/Downloads$ 

```

---

### Post by ApOgEEs on 2011-09-28
try 
```
$ sudo dpkg -i *.deb 
```
instead

---

### Post by ScottSanbar on 2011-09-28
Yes - you are correct, of course.

However, I still have the problem "sudo apt-get update" giving me errors.

Thanks ... Scott

---

### Post by ApOgEEs on 2011-09-28
> **ScottSanbar said:**
> Yes - you are correct, of course.

However, I still have the problem "sudo apt-get update" giving me errors.

Thanks ... Scott


actually, that was because there is no natty release for that specific ppa. You may disable those ppa and you won't see that error again. 

check it here: 
[http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/](http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/)
[http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/](http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/)

You may also ask the maintainer of that ppa repositories if they are will update their repo.

---

### Post by sonucool on 2011-09-28
absolutely correct buddy![img]http://goo.gl/0pzLP[/img]

---

### Post by ScottSanbar on 2011-09-28
Thanks, ApOgEEs!  However, there is some more info I got from tumbleweed on irc.freenode.net channel #ubuntu-packaging.  To sum up all the fixes for this issue:

1.  As shown by ApOgEEs above, to install my package from a .deb file, I was improperly using:

```
sudo apt-get install filename.deb
```instead of:

```
sudo dpkg -i filename.deb
```2.  As discussed by ApOgEEs above, I had entries for PPAs that were not maintained for Natty in the following files:

/etc/apt/sources.list.d/*.list (multiple .list files in the sources.list.d subdirectory

3.  I could just comment out those lines, or rename or delete the files that contained those repositories, However, these entries were a result of adding packages not meant for natty following this tutorial:

[https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Development/Devbeginnings#Installing_Development_Tools](https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Development/Devbeginnings#Installing_Development_Tools)

Which directs you to this page to do the install:

[http://www.ubuntugeek.com/bazaar-explorer-advanced-version-control-made-simple.html](http://www.ubuntugeek.com/bazaar-explorer-advanced-version-control-made-simple.html)

I somehow managed (probably through my own twisted logic) to get the two packages (bzr-explorer and qbzr) to install using the following .list files I added to the above directory:

bzr-explorer-dev-ppa-natty.list - contents:

deb [http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu](http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu) natty main
deb-src [http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu](http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu) natty main

and:

qbzr-dev-ppa-natty.list - contents:

deb [http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu](http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu) natty main
deb-src [http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu](http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu) natty main

4.  Finally, from tumbleweed, I learned the proper way to fix all this stuff that I should never have installed on Natty in the first place:

```
sudo apt-get-install ppa-purge

ppa-purge bzr-explorer
ppa-purge qbzr
```however, this did not work because I had pointers to natty versions of these two binary and source packages which installed somehow but would not uninstall because those repositories were not found, so what I did was first use dpkg to uninstall each package:

```
sudo dpkg -r bzr-explorer
sudo dpkg -r qbzr
```Then, I just deleted the two offending .list files above completely, and this seems to have solved my problem.  I hope this took care of it completely, and it seems to have:

```
sudo apt-get update
```Now is clean.  I am now going to write a bug on the above mentioned tutorial to add a warning to users of the tutorial that if they have natty (or newer) they should not install bzr-explorer and qbzr.

---

### Post by ApOgEEs on 2011-09-28
good to hear it is solved.

Nice detailed explanation ScottSanbar! :)

---

### Post by ScottSanbar on 2011-10-05
New details on this post:

After I had deleted the bzr-explorer and qbzr packages and had gotten rid of the offending ppa references as described above, I tried to do the following:

```
bzr help commands
```It erred out complaining that bzr-explorer needed qbzr to work correctly.  I tried the following:

```
sudo apt-get purge bzr
```Then reinstalled bzr, but it still seemed to indicate I had bzr-explorer installed even though I did not.  So, I installed using regular sudo apt-get install bzr, qbzr and bzr-exlorer in that order.  Then everything worked.

I think the following Wiki needs to be updated to indicate that you can now, apparently, install qbzr and bzr-explorer using just apt-get without needing to mess with ppas for Natty:

[https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Development/Devbeginnings#Minimal_Shortcut:_Verify_Bazaar_.28bzr.29_is_installed](https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Development/Devbeginnings#Minimal_Shortcut:_Verify_Bazaar_.28bzr.29_is_installed)

---

