---
title: "Can't update"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by JGT on 2008-04-25
Hi

I get the following while running the update manager in a clean install of Xubuntu... Will I be able to receive bugfixes?

Thanks

John



Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by JGT on 2008-04-26
Bump...

Xubuntu can't see my Windows partition and I understand this is a bug - I really need to be able to update...

---

### Post by bapoumba on 2008-04-26
Please post your sources.list file. I cannot access these repos either.
```
cat /etc/apt/sources.list
```

For your windows partition, it is NTFS ?

---

### Post by JGT on 2008-04-26
Thanks

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted web
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe web
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by bapoumba on 2008-04-26
You need to add the following to the file:
```
## General.
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe muliverse
## Major bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe muliverse

```

I would also comment (place a **#** at the beginning of the line) the -proposed repos (on line before last line), as this is the line with the -gb repos giving you trouble and they are for testing packages. You probably won't need them.

So, please open a terminal and run:
```
sudo nano -B /etc/apt/sources.list 
```
nano is a small text editor workiing from the terminal.
Highlight my lines above and click to paste at the beginning of the file.

CTRL-O to save the file (same name).
CTRL-X to exit nano.

```
sudo apt-get update
sudo apt-get dist-upgrade
```
to reload the file and see if there are nay updates available (I have not had any since I installed hardy, but this was just yesterday).
Please post any error message you get, and your new sources.list if you are still having troubles.

---

### Post by JGT on 2008-04-26
Hi thanks

There was a lot of action but still some errors at the end






john@john-desktop:~$ sudo apt-get update
[sudo] password for john: 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/web Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/web Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/web Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/web Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Packages
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
john@john-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted web
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted web
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted web
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe web
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
john@john-desktop:~$ sudo nano -B /etc/apt/sources.list
[sudo] password for john: 
john@john-desktop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [191B]                      
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB [19.6kB]         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_GB [1956B]    
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_GB [4368B]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_GB [36.1kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/web Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_GB             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_GB         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB       
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release [65.9kB]                        
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [37.0kB]                
Get: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages [1178kB]               
Get: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages [6986B]            
Get: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages [4297kB]             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/web Translation-en_GB                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/web Translation-en_GB           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/web Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Packages              
Get: 12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages [179kB]            
Get: 13 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources [338kB]                   
Get: 14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources [1488B]             
Get: 15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources [1323kB]              
Get: 16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [14B]            
Get: 17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [14B]      
Get: 18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages [14B]        
Get: 19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages [14B]      
Get: 20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources [14B]             
Get: 21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [14B]       
Get: 22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources [14B]         
Fetched 7489kB in 50s (149kB/s)                                                
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  muliverse/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  muliverse/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bapoumba on 2008-04-26
Okay, at the bottom of your sources.list there is this line, and it is malformed (sorry, I did not catch it at first). "web" should not be at the end (in red).
So either you delete the "web" word, _or_ you comment it (add the #, in green below, at the beginning). I favor commenting the line, as these repos are for tests.
```
[COLOR="Green"]#[/COLOR] deb http://gb.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe [COLOR="Red"]web[/COLOR]
```

---

### Post by JGT on 2008-04-26
Hi 

I commented out both the lines with "web" at the end.

## General.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe muliverse
## Major bug fix updates.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe muliverse
# deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted web
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted web
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

[COLOR="Lime"]# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted web[/COLOR]
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
[COLOR="Lime"]# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe web[/COLOR]
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


Here was the output...




john@john-desktop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_GB     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_GB                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/web Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/web Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  muliverse/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  muliverse/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by SnakeHips on 2008-04-26
> **JGT said:**
> Bump...

Xubuntu can't see my Windows partition and I understand this is a bug - I really need to be able to update...

post output from terminal 

```
mount
```

I dont use windows anymore but as the other poster asked ,are you using NTFS ? If so ntfsprogs (from synaptic) may help...

---

### Post by bapoumba on 2008-04-26
I'm very sorry, I got mislead with the sources.list you posted in post #4 that was incomplete. Looks like there are problems with the .gb archives. Here is my sources.list, you can replace all yours with it (delete everything and copy/paste in the blanked file, I know it is working ;))
```
## General.
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe muliverse

## Major bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe muliverse

## Security.
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by JGT on 2008-04-26
Okay, did it:

john@john-desktop:~$ cat /etc/apt/sources.list
## General.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe muliverse

## Major bug fix updates.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe muliverse

## Security.
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse



Still get this one though!


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  muliverse/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  muliverse/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


Should it say xubuntu rather than ubuntu or they the repos the same?

---

### Post by bapoumba on 2008-04-26
Hmm, I do not quite get it. Must be coming from somewhere else. Let me think about this one and run some googling as I do not have this problem..
I'm also running xubuntu hardy ;)

---

### Post by JGT on 2008-04-26
Double post - deleted

---

### Post by bapoumba on 2008-04-26
Found it!
You have "muliverse" line 2 under ## General and line 2 under ## Major bug fix updates. It should be multiverse (with a "t").

---

### Post by JGT on 2008-04-26
Thanks! As simple as that.

Cheers for your help

John

---

### Post by bapoumba on 2008-04-27
You're welcome.
I had never seen that error message worded this way before, it may have changed for hardy, I'll check.

---

