---
title: "[SOLVED] &amp;quot;translation error&amp;quot; in Intrepid Ibex"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Zlatan on 2008-11-05
the same issue as following:
[http://ubuntuforums.org/showthread.php?t=965625]("http://ubuntuforums.org/showthread.php?t=965625")
but removing partner repository does not solve the problem.
maybe someone is familiar with this?

thank you

---

### Post by Partyboi2 on 2008-11-05
Can you post your sources.list please
```
cat /etc/apt/sources.list
```

---

### Post by Zlatan on 2008-11-06
> **Partyboi2 said:**
> Can you post your sources.list please
```
cat /etc/apt/sources.list
```

I have enabled partners now:
```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main universe restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://lt.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://lt.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main universe restricted multiverse
```

any ideas?

---

### Post by Partyboi2 on 2008-11-06
Your sources.list seem ok. Can you also post the output to
```
sudo apt-get update
```

---

### Post by Zlatan on 2008-11-06
> **Partyboi2 said:**
> Your sources.list seem ok. Can you also post the output to
```
sudo apt-get update
```

here you go:

```
Hit http://archive.canonical.com intrepid Release.gpg               
Ign http://archive.canonical.com intrepid/partner Translation-en_US 
Get:1 http://archive.ubuntu.com intrepid Release.gpg [189B]         
Ign http://archive.ubuntu.com intrepid/main Translation-en_US                
Hit http://packages.medibuntu.org intrepid Release.gpg                       
Hit http://archive.canonical.com intrepid Release                              
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US              
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US            
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US            
Get:2 http://archive.ubuntu.com intrepid-updates Release.gpg [189B]            
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US          
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US      
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US    
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com intrepid-security Release.gpg [189B]
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US      
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US  
Ign http://packages.medibuntu.org intrepid/free Translation-en_US           
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US   
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US   
Hit http://archive.canonical.com intrepid/partner Packages                     
Get:4 http://archive.ubuntu.com intrepid Release [65.9kB]                      
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US          
Hit http://packages.medibuntu.org intrepid Release                             
Get:5 http://archive.ubuntu.com intrepid-updates Release [44.0kB]
Get:6 http://archive.ubuntu.com intrepid-security Release [44.0kB]
Get:7 http://archive.ubuntu.com intrepid/main Packages [1256kB]                
Hit http://packages.medibuntu.org intrepid/free Packages                     
Hit http://packages.medibuntu.org intrepid/non-free Packages                   
Get:8 http://archive.ubuntu.com intrepid/universe Packages [4542kB]            
Get:9 http://archive.ubuntu.com intrepid/restricted Packages [8408B]           
Get:10 http://archive.ubuntu.com intrepid/multiverse Packages [199kB]          
Get:11 http://archive.ubuntu.com intrepid-updates/main Packages [17.8kB]       
Get:12 http://archive.ubuntu.com intrepid-updates/universe Packages [3716B]    
Get:13 http://archive.ubuntu.com intrepid-updates/restricted Packages [2447B]  
Get:14 http://archive.ubuntu.com intrepid-updates/multiverse Packages [14B]    
Get:15 http://archive.ubuntu.com intrepid-security/main Packages [5252B]       
Get:16 http://archive.ubuntu.com intrepid-security/universe Packages [1352B]   
Get:17 http://archive.ubuntu.com intrepid-security/restricted Packages [14B]   
Get:18 http://archive.ubuntu.com intrepid-security/multiverse Packages [14B]   
Fetched 6191kB in 47s (129kB/s)                                                                                                                             
Reading package lists... Done

```

---

### Post by Partyboi2 on 2008-11-06
It looks like everything is working as apt-get update did not produce the errors as mentioned in that other thread..

---

### Post by Zlatan on 2008-11-07
> **Partyboi2 said:**
> It looks like everything is working as apt-get update did not produce the errors as mentioned in that other thread..

What does this line mean:
```
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US   
```
?
There were not such lines in previous versions of Ubuntu.

---

### Post by Partyboi2 on 2008-11-07
From what I have read up on it, it means that the repo information has not changed since you last checked. So there is nothing for it to update.

---

### Post by Zlatan on 2008-11-07
> **Partyboi2 said:**
> From what I have read up on it, it means that the repo information has not changed since you last checked. So there is nothing for it to update.

OK, thank you then, have a good day;)

---

