---
title: "Upgrade from 8.04 to 10.04 problem"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by x53x6ex69x67x67x65x72 on 2010-05-17
Hi
I downloaded Ubuntu 10.04 Alternate CD and tried to upgrade 8.04 to 10.04.
When I run upgrade (with the option "Include latest updates from the Internet?" set to "No" ) in the "Setting new software channels" it gives this error (ScreenShot attached):
```

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
```What's on?
What should I do?

Thanks

---

### Post by rolnics on 2010-05-17
Did you make sure you had applied all updates to Hardy before doing the upgrade?

---

### Post by x53x6ex69x67x67x65x72 on 2010-05-17
Yes I've updated Hardy completely !
Something:
I added some repositories manually (Medibuntu , launchpad ,...) 
Can it be because of them?

---

### Post by rolnics on 2010-05-17
I'm no expert, as I've never seen this error myself.

I won't have thought it would be a problem with the other repositories. Have you run an update via terminal, just to check? It might give us a clue?

It mentions packages being held, I'm going to do a google on this see what it comes up with.

Also have you installed anything via source? 

One other thing, I assume you have backup's of your data? As I said earlier, I'm no expert and don't want to make things worse for you!

---

### Post by rolnics on 2010-05-17
Right I've found similar problems reported else where, what might be another point to look at is your update logs

Open a terminal and post back what this brings up:-

```
cat /var/log/dist-upgrade/apt.log | grep broken
```

You also might want to check that all the updates have been applied, again in terminal.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Does the dist-upgrade bring up any messages?

Another command that might provide more information if the above doesn't do anything.

```
dpkg --get-
> selections | grep hold
```

Post back with the outcomes of these commands.

---

### Post by x53x6ex69x67x67x65x72 on 2010-05-18
Hi
Thanks for your attention.
Here are results:

cat /var/log/dist-upgrade/apt.log | grep broken:
```
Nothing!
```sudo apt-get update:
```

 Hit [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release.gpg                                                                                                                                 
 Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Translation-en_US                                                                                                                      
 Hit [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release                                                                                                                                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                                                                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                                                                                                       
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                                                                                                                 
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                                                                                                    
 Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                                                                                      
 Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                                                                                        
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US                                                                                        
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                                                                    
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US                                                                  
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                                                                           
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US                                                                
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US                                                          
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US                                                            
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US                                                          
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg                                                                          
 Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                                                                                          
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US                                                                                     
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US                                                         
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US                                                                                 
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US                                                                               
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg                                                                          
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_US                                                                               
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_US                                                                                     
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Translation-en_US                                                                               
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Translation-en_US                                                                                 
 Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                                                                                 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                                                          
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                                                         
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                                                                                             
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                                                                                                     
 Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Packages                                                                                                                            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                                                          
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                                                                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                                                          
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                                                                               
 Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                                                                                                   
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                                                                                                            
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release                                                                                                                         
 Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Sources                                                                                                                             
 Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                                                                                                   
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                                                                                              
 Ign [http://www.pvv.ntnu.no](http://www.pvv.ntnu.no) ./ Release.gpg                                                                                                                                    
 Ign [http://www.pvv.ntnu.no](http://www.pvv.ntnu.no) ./ Translation-en_US                                                                                                         
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                                                                                                       
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                                                                           
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                                                                                  
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                                                                                                  
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                                                                                                   
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                                                                              
 Hit [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Packages                                                                                                       
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                                                                                              
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                                                                             
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                                                         
 Get:3 [http://www.pvv.ntnu.no](http://www.pvv.ntnu.no) ./ Release [712B]                                                                                                          
 Hit [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Sources                                                                                                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                                   
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                            
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                                                     
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources                                                      
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                                                   
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                                             
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources                                                    
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources                                              
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages                                               
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources                                                
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages                                             
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources                                              
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages                                                  
 Hit [http://www.pvv.ntnu.no](http://www.pvv.ntnu.no) ./ Packages                                                                                            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                                   
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                                  
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                                  
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages                                                                  
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources                                                                         
 Hit [http://www.pvv.ntnu.no](http://www.pvv.ntnu.no) ./ Sources                                                                                             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                                   
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                             
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources                                             
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages                        
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources                         
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages                      
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources                       
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages                      
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages                            
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages                      
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages                        
 Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                          
 Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US  
 Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
 Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]
 Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release 
 Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
 Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
 Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Fetched 201B in 5s (37B/s)
Reading package lists... Done
 W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```sudo apt-get dist-upgrade:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by rolnics on 2010-05-20
I see some lines that I'm not sure about. Are you using Ubuntu repros? It might be advisable to, if you are happy to change your source.list and comment out any non-ubuntu repros, maybe even going as far as commenting out the launch pad lines.

On another note I see you dont have medibuntu correctly authenticated and you need to add the key files. Run this command:```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Just so you know I got that command from:[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

It might even be worth trying to upgrade after that's corrected, it could be as simple as that?! I really don't know.

Let me know how it goes?

---

### Post by x53x6ex69x67x67x65x72 on 2010-05-29
Hi
Excuse me for late response !
I replaced Hardy default "sources.lst" with my current file 
Then I ran:
```

sudo apt-get update
sudo apt-get dist-upgrade

```And again tried to upgrade.
Again got that error.

Additionally it gives this error:
```
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet  warnings.warn("apt API not stable yet", FutureWarning)
reWarning: apt API not stable yetWARNING: Failed to read mirror file
```another thing is when I click "Yes" when it asks for "Include latest updates from the Internet?" it works correctly until it announces download size but I don't want do that download (it has very big size) so I don't know that if it works in that way or not

I'm confused !
previously when I tried to upgrade from Dapper to Hardy I had this problem too.
So I did a fresh Hardy installation

Whats on?

---

### Post by WinRiddance on 2010-05-29
Could it have something to do with your file system or with 32bit versus 64bit ???
I'm not even sure if 10.04 runs on ext3 perfectly stable ... ???

---

### Post by x53x6ex69x67x67x65x72 on 2010-05-29
> **WinRiddance said:**
> Could it have something to do with your file system or with 32bit versus 64bit ???
No 
That was my Desktop PC
And this is my laptop!!
The upgrade doesn't even start!

> **WinRiddance said:**
> 
I'm not even sure if 10.04 runs on ext3 perfectly stable ... ???
It is 
Ubuntu itself says it is(and recommends to use it if we want high I/O)

I by myself think the 3rd reason causes the problem
I installed lots of packages from non-Ubuntu repositories.
What can I do ?!

---

