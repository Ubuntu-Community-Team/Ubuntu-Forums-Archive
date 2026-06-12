---
title: "Only one software management tool is allowed to run!"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by Etamami on 2008-05-03
Hey!

I get this error message everytime when I try to install some app, like with .deb files!

I wanted to install blueMarine 1st when it appeared!

Could someone tell me how to fix this!

*Thanks :)

---

### Post by mikewhatever on 2008-05-03
You must be running two programs for package management, for example, both synaptic and Add/Remove, or synaptic and apt-get command. Try using one and you shouldn't get that message.

---

### Post by Etamami on 2008-05-03
> **mikewhatever said:**
> You must be running two programs for package management, for example, both synaptic and Add/Remove, or synaptic and apt-get command. Try using one and you shouldn't get that message.

Naaa, i restarted and no...i'm not using those....maybe Ubuntu is running them in background, but then how could I shut them down?
:confused:

Thanks, :KS
...but I think this doesn't really help, if i'm just using one!

---

### Post by mikewhatever on 2008-05-03
If only one of those is running, then I don't know. None of them should run in the background, but still, try looking through Processes in System Monitor under System->Admin. What output do you get from <sudo apt-get update>?

---

### Post by ushaba on 2008-05-03
you may have a lock in /var/lock/
if this is the case, it is quite easy to remove with sudo rm /var/lock/nameoflock

---

### Post by Etamami on 2008-05-04
> **mikewhatever said:**
> If only one of those is running, then I don't know. None of them should run in the background, but still, try looking through Processes in System Monitor under System->Admin. What output do you get from <sudo apt-get update>?

Okay...here it comes, the output of <sudo apt-get update>!

```
Hit http://hu.archive.ubuntu.com hardy Release.gpg
Ign http://hu.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://hu.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://hu.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://hu.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://hu.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://hu.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://hu.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://hu.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://hu.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://hu.archive.ubuntu.com hardy-proposed Release.gpg                    
Ign http://hu.archive.ubuntu.com hardy-proposed/restricted Translation-en_US   
Ign http://hu.archive.ubuntu.com hardy-proposed/main Translation-en_US         
Ign http://hu.archive.ubuntu.com hardy-proposed/multiverse Translation-en_US   
Ign http://hu.archive.ubuntu.com hardy-proposed/universe Translation-en_US     
Hit http://hu.archive.ubuntu.com hardy Release                                 
Hit http://archive.ubuntu.com hardy Release.gpg                                
Hit http://hu.archive.ubuntu.com hardy-updates Release                         
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Hit http://hu.archive.ubuntu.com hardy-proposed Release                        
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Get:1 http://wine.budgetdedicated.com hardy Release.gpg [191B]                 
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Hit http://security.ubuntu.com hardy-security/main Packages                    
Get:2 http://wine.budgetdedicated.com hardy Release [1013B]          
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/main Sources                     
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://security.ubuntu.com hardy-security/universe Sources       
Hit http://security.ubuntu.com hardy-security/universe Packages      
Hit http://security.ubuntu.com hardy-security/multiverse Packages    
Get:3 http://wine.budgetdedicated.com hardy/main Packages [1085B]    
Hit http://hu.archive.ubuntu.com hardy/main Packages                 
Hit http://hu.archive.ubuntu.com hardy/restricted Packages
Hit http://hu.archive.ubuntu.com hardy/restricted Sources
Hit http://archive.ubuntu.com hardy Release    
Hit http://hu.archive.ubuntu.com hardy/main Sources
Hit http://hu.archive.ubuntu.com hardy/multiverse Sources
Hit http://hu.archive.ubuntu.com hardy/universe Sources
Hit http://hu.archive.ubuntu.com hardy/universe Packages
Hit http://hu.archive.ubuntu.com hardy/multiverse Packages
Hit http://hu.archive.ubuntu.com hardy-updates/main Packages
Hit http://hu.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://hu.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://hu.archive.ubuntu.com hardy-updates/main Sources
Hit http://hu.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://hu.archive.ubuntu.com hardy-updates/universe Sources
Hit http://hu.archive.ubuntu.com hardy-updates/universe Packages
Hit http://hu.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://hu.archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://hu.archive.ubuntu.com hardy-proposed/main Packages
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://hu.archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://hu.archive.ubuntu.com hardy-proposed/universe Packages
Fetched 2289B in 0s (3433B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

...the ending is not so nice, I guess! :confused:

---

### Post by Etamami on 2008-05-04
> **ushaba said:**
> you may have a lock in /var/lock/
if this is the case, it is quite easy to remove with sudo rm /var/lock/nameoflock

Naaa, lock folder is empty,totally empty! :(

---

### Post by Etamami on 2008-05-04
Ahh, and now Ubuntu wanted to update too, and is showed Wine should be updated, so I pressed install, and this came up here:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Any ideas how I could fix this? :confused:

---

### Post by jolx on 2008-05-04
easy - run 'dpkg --configure -a'

---

### Post by Etamami on 2008-05-04
...okay, now I run <sudo dpkg --configure -a>, and i told me that I have 1 brocken packege, and sould use the <Brocken> to locate it.

So, now I refreshed update, and now Ubuntu is represhing Java apps. Maybe  java had to do something with this "not updateting"?! :confused:

---

### Post by c4v3m4n on 2008-05-04
Usually that just means that synaptic and/or update manager are running at the same time, or you're running one of them and trying to install through terminal.

---

### Post by Etamami on 2008-05-04
TADA: now updates work again! :guitar:

**THANKS mikewhatever**, jolx and ushaba!

---

### Post by jolx on 2008-05-04
open synaptic and go ->edit ->fix broken packages

EDIT:soz too late

---

### Post by Etamami on 2008-05-04
> **jolx said:**
> open synaptic and go ->edit ->fix broken packages

EDIT:soz too late

Well, it sad "Succesfully fixed dependency problems", so I guess it's all right now. At least now I can istall again, and also update. :lolflag:

**THX AGAIN!**

---

