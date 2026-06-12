---
title: "How do I disable Auto Updates?"
date: 2015-10-28
forum: Installation &amp; Upgrades
---

### Post by silverfox2 on 2015-10-28
I decided to give Linux another go, and have Ubuntu 14.04 LTS loaded as dual boot, on 3 Windows 7 boxes. The Windows 7 boxes are all different variations (HTPC/Server, Desktop, and Laptop) and do not have any issues. After installation, I went into "Software and Updates" and set the "Automatically check for updates" option to "Never". This doesnt work. Every time the machine is turned on from being completely shut down, it automatically checks for updates after booting. I normally suspend my computers, so it doesnt try to update daily, but it still does it every time the system is turned on, after being shut off.

I then found this thread  [http://sourcedigit.com/15388-turn-off-disable-update-manager-ubuntu-automatic-updates-in-ubuntu-14-0414-10/](http://sourcedigit.com/15388-turn-off-disable-update-manager-ubuntu-automatic-updates-in-ubuntu-14-0414-10/) and followed the instructions on running the commands to disable the update manager. This did not work either. 

How do I shut off the auto updates? Its pretty silly to give us the option to "Never" automatically check for updates, if it isnt going to recognize that choice. Thanks in advance for any and all help! :D

---

### Post by howefield on 2015-10-28
I might be wrong but I believe you will continue to be notified of the updates *that the system is aware of* irrespective of the setting you used to turn off automatic notification until you. Once those updates are downloaded your setting will take effect and no further automatic notifications will be given.

---

### Post by silverfox2 on 2015-10-28
> **howefield said:**
> I might be wrong but I believe you will continue to be notified of the updates *that the system is aware of* irrespective of the setting you used to turn off automatic notification until you. Once those updates are downloaded your setting will take effect and no further automatic notifications will be given.

Nope, its been like this for 5 months now. Ive updated it several times when notified, and it it still continues to notify me. It will even check in the background, and tell me that the "update information is out dated".

---

### Post by vasa1 on 2015-10-28
> **silverfox2 said:**
> I decided to give Linux another go, ... After installation, I went into "Software and Updates" and set the "Automatically check for updates" option to "Never". This doesnt work. ...
Could you explain why you don't want to "automatically check for updates"? Any specific reason?

---

### Post by nargaroth_reg on 2015-10-28
Disabling 'Update Notifier' from the startup aplications worked for me. In MATE this is done with the application mate-session-properties.

---

### Post by vasa1 on 2015-10-28
> **nargaroth_reg said:**
> 
[COLOR=#666666][FONT=Consolas] sudo apt-get remove update-notifier [/FONT][/COLOR]did not work either?
Well, that command may remove more than just the update notifier. You can see that by running *apt-get remove -s update-notifier*. Not a good idea, IMO.

---

### Post by vasa1 on 2015-10-28
> **silverfox2 said:**
> Nope, its been like this for 5 months now. Ive updated it several times when notified, and it it still continues to notify me. It will even check in the background, and tell me that the "update information is out dated".
If you post the output of *sudo apt-get update* here (**between code tags for readability**) someone maybe able to suggest something re "update information is out dated".

---

### Post by nargaroth_reg on 2015-10-28
Yeah, there is a section in the link in the op that indicates how to uninstall the update manager (I see I didn't copy the exact same name (corrected)), I was wondering if he had done that.

---

### Post by silverfox2 on 2015-10-28
> **nargaroth_reg said:**
> Disabling 'Update Notifier' from the startup aplications worked for me. In MATE this is done with the application mate-session-properties.

I had failed to mention, I had disabled the update manager from startup also. Evidently, it had been restarted after an update. It was enabled again. I once again, disabled it from startup. we shall see what happens. Thank you for reminding me of this. :D

> **vasa1 said:**
> If you post the output of *sudo apt-get update* here (**between code tags for readability**) someone maybe able to suggest something re "update information is out dated".

It only does it every so often. If I either check for updates, or change the update server.... the error message goes away. Here is the output you asked for:

```
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                            
Hit http://us.archive.ubuntu.com trusty-backports InRelease            
Get:2 http://us.archive.ubuntu.com trusty-security InRelease [64.4 kB]         
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner Translation-en                 
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty Release.gpg
Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [241 kB]
Get:4 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,722 B] 
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [140 kB]    
Get:6 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,145 B] 
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [637 kB] 
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:9 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [324 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [618 kB] 
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [325 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Get:15 http://us.archive.ubuntu.com trusty-updates/main Translation-en [309 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:17 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,569 B]
Get:18 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [171 kB]
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:19 http://us.archive.ubuntu.com trusty-security/main Sources [97.6 kB]     
Get:20 http://us.archive.ubuntu.com trusty-security/restricted Sources [3,357 B]
Get:21 http://us.archive.ubuntu.com trusty-security/universe Sources [31.0 kB] 
Get:22 http://us.archive.ubuntu.com trusty-security/multiverse Sources [2,346 B]
Get:23 http://us.archive.ubuntu.com trusty-security/main amd64 Packages [357 kB]
Get:24 http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Get:25 http://us.archive.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Get:26 http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Get:27 http://us.archive.ubuntu.com trusty-security/main i386 Packages [338 kB]
Get:28 http://us.archive.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Get:29 http://us.archive.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:30 http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Get:31 http://us.archive.ubuntu.com trusty-security/main Translation-en [194 kB]
Get:32 http://us.archive.ubuntu.com trusty-security/multiverse Translation-en [1,679 B]
Get:33 http://us.archive.ubuntu.com trusty-security/restricted Translation-en [3,076 B]
Get:34 http://us.archive.ubuntu.com trusty-security/universe Translation-en [68.3 kB]
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 4,331 kB in 1min 37s (44.4 kB/s)                                       
Reading package lists... Done
```

---

### Post by silverfox2 on 2015-10-29
> **nargaroth_reg said:**
> Disabling 'Update Notifier' from the startup aplications worked for me. In MATE this is done with the application mate-session-properties.

Ok, removed the update notifier from the startup applications (again) and it still phone home immediately after startup this morning, and told me what updates were available. Why is it so hard to shut off auto updates? They have been turn off/disabled in 3 locations, and they STILL phone home #-o

---

### Post by silverfox2 on 2015-11-04
So absolutely no one knows how to do something (that should be) so simple as to actually turn off auto updates? Wow, thats pretty sad :confused:

---

