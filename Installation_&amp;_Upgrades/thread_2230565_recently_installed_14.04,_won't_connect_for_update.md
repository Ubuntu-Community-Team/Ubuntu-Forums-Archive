---
title: "recently installed 14.04, won't connect for updates"
date: 2014-06-19
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2014-06-19
I recently installed 14.04 on a older laptop.  When updates are requested by the OS and I say go ahead, it won't connect.  

Of course, it connects to the internet just fine.

How do I fix this?

---

### Post by grahammechanical on 2014-06-19
The OS usually gives an error message in situations like this. Did Ubuntu not do that? The message will often suggest a solution. Or you could run in a terminal

```
sudo apt-get update
sudo apt-get upgrade
```

and post any error messages back here wrapped in code tags for good presentation.

Otherwise, all I can say is: "No idea."

---

### Post by RogerDavis on 2014-06-20
> **grahammechanical said:**
> The OS usually gives an error message in situations like this. Did Ubuntu not do that? The message will often suggest a solution. Or you could run in a terminal

```
sudo apt-get update
sudo apt-get upgrade
```

and post any error messages back here wrapped in code tags for good presentation.

Otherwise, all I can say is: "No idea."
-----------------------------------------------------------------------------------------------------------
I don't know how to do "code tags"...
It seems to have worked this time.  Last time I used the update app.
============================================
```

roger@earlleen-ThinkPad-R50p:~$ sudo apt-get update
[sudo] password for roger: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Get:3 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease [1,891 B]                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58.5 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main i386 Packages/DiffIndex          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [20.6 kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [4,727 B]    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [688 B]    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [58.9 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [21.5 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,392 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [67.1 kB]      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]   
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [50.7 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [2,681 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [162 kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Err [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Sources                          
  404  Not Found
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [125 kB]
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Translation-en_US                
Hit [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main i386 Packages                    
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,569 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
Fetched 644 kB in 11s (57.1 kB/s)                                              
W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/source/Sources](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/source/Sources)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
roger@earlleen-ThinkPad-R50p:~$ 
```
-------------------------------------------------------------
LONG list here, so only questionable or ? items shown
...
```
WARNING: The following packages cannot be authenticated!
  seamonkey-mozilla-build
Install these packages without verification? [y/N] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main mount i386 2.20.1-5.1ubuntu20.1 [113 kB]
Get:2 [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main seamonkey-mozilla-build i386 2.26.1-0ubuntu1 [32.3 MB]
...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-29-generic
roger@earlleen-ThinkPad-R50p:~$ 
```
-------------------------------------------------------------------------------------

---

### Post by QIII on 2014-06-20
To use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

It appears to me that you are good except for that sourceforge source.

Go to the Software Center, Edit, Software Sources.  In the "Other Sources" tab, find that one and uncheck it.

---

### Post by RogerDavis on 2014-06-20
Thanks for the "code" info!

---

### Post by QIII on 2014-06-20
You're welcome.

I guess I should add that if you remove that source, anything you installed from there will not be updated -- or, if it is a package that is in the normal repos it may be replaced with what is available from Canonical.

---

### Post by RogerDavis on 2014-06-20
I'll know more about if it works next time I get a normal update.

---

### Post by Don Heard on 2014-06-23
I am no expert but I have been using Ubuntu since version 6 and it has been my experience that new installs and some upgrades require a hardwire connection to do updates.  It appears that it is necessary for the computer to recognize the network adapter and then it will find the wifi apparatus.    Just a thought.

---

### Post by RogerDavis on 2014-06-23
Now it's saying "Failed to download Repository Information" when I do a manual check, and suggests I check the internet connection.  However, it did pop up an update, and that one worked.

---

