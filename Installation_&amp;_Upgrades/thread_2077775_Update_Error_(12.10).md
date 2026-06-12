---
title: "Update Error (12.10)"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by hardikbv on 2012-10-29
Hello Friends, 

I recently upgraded to 12.10.

Since then when I run sudo apt-get update, at the end following error comes.

Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) quantal/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I did not get anything like this in 12.4 Please help..

Hardik

---

### Post by dino99 on 2012-10-29
please post the result of :

```
cat /etc/apt/sources.list
```

---

### Post by hardikbv on 2012-10-29
Results : 

hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$ cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

---

### Post by kanikilu on 2012-10-29
You have the 'partner' repository listed twice, just comment out one instance of them.

Open up the sources.list file for editing (this example uses gedit):
```
gksu gedit /etc/apt/sources.list
```

Now scroll to the bottom where the partner repository is listed for a second time, and put a hash/pound symbol (#) in front of them:

> # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

Save and close the file, and then run: ```
sudo apt-get update
```

---

### Post by hardikbv on 2012-10-30
Hi, I ran that. See the result below and suggest the way forward.  I see some new errors have cropped up :(

[sudo] password for hardik: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates InRelease                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports InRelease                   
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal Release.gpg                         
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources/DiffIndex           
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates Release.gpg [933 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources/DiffIndex                    
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages/DiffIndex       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports Release.gpg                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages/DiffIndex              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal Release                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources/DiffIndex         
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates Release [49.6 kB]           
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources/DiffIndex   
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources/DiffIndex     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources/DiffIndex   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports Release            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages/DiffIndex   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/main Sources                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages/DiffIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/restricted Sources           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages/DiffIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/universe Sources             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages/DiffIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/multiverse Sources           
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_IN    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/main i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en   
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/restricted i386 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/universe i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/multiverse i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_IN                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/main Translation-en                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/multiverse Translation-en             
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [6,018 B]       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/restricted Translation-en             
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [1,457 B]   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [14 B]    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/universe Translation-en               
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [27.7 kB] 
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/main Sources [12.9 kB]      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [5,060 B]
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/restricted Sources [14 B]  
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/universe Sources [3,218 B] 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [14 B]
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/multiverse Sources [14 B]  
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/main i386 Packages [45.2 kB]
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/restricted i386 Packages [14 B]
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/universe i386 Packages [18.5 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_IN         
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_IN   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_IN   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/main Translation-en           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_IN     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/universe Translation-en       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/main i386 Packages          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/restricted i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/universe Translation-en     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/main Translation-en_IN                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/universe Translation-en_IN
Fetched 220 kB in 1min 25s (2,575 B/s)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/quantal/Release.gpg](http://archive.canonical.com/ubuntu/dists/quantal/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by dino99 on 2012-10-30
you are mostly using your local archive (in.archive...) but some are set to the native servers. As the US have actually very bad weather and electric powering issues, maybe these servers are also affected; dont worry and wait a few days to get them back.

---

### Post by hardikbv on 2012-10-30
Ok, Thanks.

Does this mean that previous problem is solved and my editing was right?!

---

