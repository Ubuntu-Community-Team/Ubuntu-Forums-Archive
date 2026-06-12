---
title: "Unity 2d"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by LinkBreaksPots on 2011-01-31
Hi guys,
So I'm trying to install Unity 2D, and when I type in 
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily

Everything works fine, but when I type in 

sudo apt-get update

it says failed to fetch. I'm not sure if I'm doing something wrong, or if the source is down. 
I wasn't sure if anyone else has experienced this problem or if I'm doing something wrong, which is quite possible.
Any help on this would be appreciated. Thanks.

---

### Post by Kirboosy on 2011-02-02
Just for future reference when you type code you should always make it stand out. ;)

```
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
```

As far as I know the source isn't down. I updated mine last night no problems. What did it output after running the add repository command?

---

### Post by roofuskit on 2011-02-02
> **LinkBreaksPots said:**
> Hi guys,
Everything works fine, but when I type in 

sudo apt-get update

it says failed to fetch. I'm not sure if I'm doing something wrong, or if the source is down.

I have the exact same issue

---

### Post by LinkBreaksPots on 2011-02-02
Caboose, I didn't do it because Idk how. I'm still new to the forums. I'll try it again later today and if it still doesn't work, I believe that natty will have Unity as default to my knowledge. As for the output, I'm not entirely sure how to check that. Like I said, I'm still relatively new to Ubuntu. But when I log in, insteadof being able to switch from Gnome to Unity, there is no Unity option as there should be.

---

### Post by Kirboosy on 2011-02-02
Run this command
```
**sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update**
```

it should print out an output like PGP key added...and also automatically update

Then to actually install it just run
```
**sudo apt-get install ****unity-qt-default-settings**
```


For marking code just use [ CODE] (with out the space between the [C) and at the end of the code put [ /CODE] (Again without the space.)

---

### Post by roofuskit on 2011-02-02
> **Caboose885 said:**
> Run this command
```
**sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update**
```

it should print out an output like PGP key added...and also automatically update

Then to actually install it just run
```
**sudo apt-get install ****unity-qt-default-settings**
```


For marking code just use [ CODE] (with out the space between the [C) and at the end of the code put [ /CODE] (Again without the space.)

Yeah, I should have stated that I'm getting the same error, and I know I'm doing it correctly.

---

### Post by Kirboosy on 2011-02-02
Can you copy and everything you entered from terminal? That way I can see what you did and the error exact wording...

---

### Post by Reduced_Oxygen on 2011-02-25
i cant install it either

```
 To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

twodee@Twodee:~$ sudo add-apt-repository ppa:untiy-2d-team/unity-2d-daily && sudo apt-get update
[sudo] password for twodee: 
Error reading https://launchpad.net/api/1.0/~untiy-2d-team/+archive/unity-2d-daily: HTTP Error 404: Not Found
Get:1 http://au.archive.ubuntu.com natty Release.gpg [198 B]
Ign http://au.archive.ubuntu.com/ubuntu/ natty/main Translation-en             
Get:2 http://au.archive.ubuntu.com/ubuntu/ natty/main Translation-en_AU [2,703 B]
Ign http://au.archive.ubuntu.com/ubuntu/ natty/multiverse Translation-en       
Get:3 http://au.archive.ubuntu.com/ubuntu/ natty/multiverse Translation-en_AU [89.3 kB]
Hit http://archive.canonical.com natty Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ natty/partner Translation-en          
Get:4 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Ign http://archive.canonical.com/ubuntu/ natty/partner Translation-en_AU       
Hit http://archive.canonical.com natty Release                                 
Get:5 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Ign http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/ natty/main Translation-en
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://security.ubuntu.com natty-security Release.gpg                      
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://extras.ubuntu.com/ubuntu/ natty/main Translation-en                 
Ign http://extras.ubuntu.com/ubuntu/ natty/main Translation-en_AU              
Ign http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/ natty/main Translation-en_AU
Ign http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net/untiy-2d-team/unity-2d-daily/ubuntu/ natty/main Translation-en
Ign http://ppa.launchpad.net/untiy-2d-team/unity-2d-daily/ubuntu/ natty/main Translation-en_AU
Hit http://extras.ubuntu.com natty Release                                     
Ign http://security.ubuntu.com/ubuntu/ natty-security/main Translation-en      
Ign http://security.ubuntu.com/ubuntu/ natty-security/main Translation-en_AU   
Ign http://security.ubuntu.com/ubuntu/ natty-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ natty-security/multiverse Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ natty-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ natty-security/restricted Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ natty-security/universe Translation-en  
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://security.ubuntu.com/ubuntu/ natty-security/universe Translation-en_AU
Hit http://security.ubuntu.com natty-security Release              
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://security.ubuntu.com natty-security/restricted Sources   
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Get:6 http://ppa.launchpad.net natty Release [9,761 B]                         
Ign http://au.archive.ubuntu.com/ubuntu/ natty/restricted Translation-en       
Get:7 http://au.archive.ubuntu.com/ubuntu/ natty/restricted Translation-en_AU [2,273 B]
Ign http://au.archive.ubuntu.com/ubuntu/ natty/universe Translation-en         
Ign http://au.archive.ubuntu.com/ubuntu/ natty/universe Translation-en_AU
Get:8 http://au.archive.ubuntu.com natty-updates Release.gpg [198 B]    
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/main Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/main Translation-en_AU  
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/multiverse Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/restricted Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/universe Translation-en 
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/universe Translation-en_AU
Get:9 http://au.archive.ubuntu.com natty Release [39.8 kB]                     
Hit http://au.archive.ubuntu.com natty-updates Release                         
Get:10 http://au.archive.ubuntu.com natty/main Sources [864 kB]                
Ign http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty/main Sources                                
Ign http://ppa.launchpad.net natty/main i386 Packages                          
Get:11 http://ppa.launchpad.net natty/main Sources [2,417 B]                   
Get:12 http://ppa.launchpad.net natty/main i386 Packages [5,078 B]             
Ign http://ppa.launchpad.net natty/main Sources                                
Ign http://ppa.launchpad.net natty/main i386 Packages               
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                          
  404  Not Found
Get:13 http://au.archive.ubuntu.com natty/restricted Sources [4,098 B]         
Get:14 http://au.archive.ubuntu.com natty/universe Sources [4,400 kB]          
Get:15 http://au.archive.ubuntu.com natty/multiverse Sources [155 kB]          
Get:16 http://au.archive.ubuntu.com natty/main i386 Packages [1,576 kB]        
Get:17 http://au.archive.ubuntu.com natty/restricted i386 Packages [8,803 B]   
Get:18 http://au.archive.ubuntu.com natty/universe i386 Packages [6,027 kB]    
Get:19 http://au.archive.ubuntu.com natty/multiverse i386 Packages [183 kB]    
Hit http://au.archive.ubuntu.com natty-updates/main Sources                    
Hit http://au.archive.ubuntu.com natty-updates/restricted Sources              
Get:20 http://au.archive.ubuntu.com natty-updates/universe Sources [14 B]      
Hit http://au.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://au.archive.ubuntu.com natty-updates/main i386 Packages              
Get:21 http://au.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Hit http://au.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://au.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Fetched 13.4 MB in 15min 23s (14.5 kB/s)                                       
W: Failed to fetch http://ppa.launchpad.net/untiy-2d-team/unity-2d-daily/ubuntu/dists/natty/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/untiy-2d-team/unity-2d-daily/ubuntu/dists/natty/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
twodee@Twodee:~$ sudo apt-get install unity-qt-default-settings
[sudo] password for twodee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package unity-qt-default-settings 
```

---

### Post by Reduced_Oxygen on 2011-03-02
if anyones still stuck

```
 sudo apt-get install unity-qt-default-settings 
```

has bean changed to

```
 sudo apt-get install unity-2d-default-settings 
```

---

### Post by Mediosordo on 2011-04-02
I have the same issue in my wife's AspireOne running Lucid.

I try  
```
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update
```and then
```
sudo apt-get install unity-2d-default-settings
```[FONT=monospace]
and it tells me that it can't find the package unity-2d-default-settings:

[/FONT]```
rosi@rosi-laptop:~$ sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update
[sudo] password for rosi: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver[keyserver.ubuntu.com]("http://keyserver.ubuntu.com/") --recv AD8079E4480677B271DCE8EB6CECEA1EE32DD113
gpg: requesting key E32DD113 from hkp server [keyserver.ubuntu.com]("http://keyserver.ubuntu.com/")
gpg: key E32DD113: "Launchpad PPA for unity-2d-team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid Release.gpg
Get: 1 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB [62.9kB]
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release.gpg                            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg                 
Ign [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/) lucid/main Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release            
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                       
Get: 2 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB [2,332B]
Get: 3 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB [33.9kB]
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                                                                      
Get: 4 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB [37.7kB]                               
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Packages                                                           
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates Release.gpg                             
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid Release                                
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                              
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Packages                                      
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Sources           
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/multiverse Packages
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                     
  404  Not Found
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates Release               
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/multiverse Sources     
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid/main Packages                 
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid/restricted Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid/main Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid/restricted Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid/universe Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid/universe Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid/multiverse Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid/multiverse Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates/main Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates/restricted Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates/main Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates/restricted Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates/universe Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates/universe Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates/multiverse Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") lucid-updates/multiverse Sources
Fetched 137kB in 1s (105kB/s)
W: Failed to fetch [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
rosi@rosi-laptop:~$ sudo apt-get install unity-2d-default-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package unity-2d-default-settings
```

Any ideas? Thanks in advance.

---

### Post by Dutch70 on 2011-04-02
You can install Unity 2D from software center.

---

### Post by Mediosordo on 2011-04-04
Well, I'm afraid it doesn't show up on the Software Centre of my wife's laptop (lucid), nor on mine (maverick). Weird.

---

### Post by Dutch70 on 2011-04-04
That's odd. Have you tried running the commands again? Maybe the servers were down.

---

### Post by Mediosordo on 2011-04-04
Just did. "Couldn't find package unity-2d-default-settings"

Also checked Software Center on both laptops. Not there.

---

### Post by Dutch70 on 2011-04-04
Well, I really don't know what the problem could be. I used nothing but the advice of this thread to add it to mine, 
just about the time I posted on here the first time. 

Do you think it has something to do with the mirror your downloading from?

---

