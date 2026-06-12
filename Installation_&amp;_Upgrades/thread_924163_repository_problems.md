---
title: "repository problems"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by crofty_boy on 2008-09-19
I am trying to get remote desktop working , my sister has installed
ubuntu 6.06 on her laptop and she needs me to do the more complex
stuff with the wireless card , so i thought it would be good to do it
via remote desktop.


here the results when i tried to do an update.

been having problems with this computer for a while when trying to
install software and left it alone cos it working.


nancy@nancy-desktop:~$
nancy@nancy-desktop:~$
nancy@nancy-desktop:~$
nancy@nancy-desktop:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
 404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
 404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
 404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
 404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
 404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
 404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
 404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)
 404 Not Found
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)
 404 Not Found
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)
 404 Not Found
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)
 404 Not Found
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz)
 404 Not Found
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)
 404 Not Found
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)
404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz)
 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz)
 404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old
ones used instead.
nancy@nancy-desktop:~$
nancy@nancy-desktop:~$
nancy@nancy-desktop:~$

My /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main
restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main
restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Partyboi2 on 2008-09-19
Edgy is no longer supported, you would need to upgrade.

Edit: You could try changing repos to
```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy universe
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy universe
deb http://old-releases.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
``` But upgrading is the way to go.

---

### Post by iaculallad on 2008-09-19
Edgy Eft (v.6.10) version already had meet it's [End-Of-Life]("https://wiki.ubuntu.com/Releases") last April 2008. Time for you to upgrade to a higher Ubuntu version so you could continue receiving updates.

---

### Post by crofty_boy on 2008-09-19
how would i go about upgrading it?
will it keep the settings and everything the same?

---

### Post by crofty_boy on 2008-09-19
It still having problems with new  /etc/apt/sources.list from above.


nancy@nancy-desktop:~$ 
nancy@nancy-desktop:~$ 
nancy@nancy-desktop:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Get:1 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release.gpg [191B]         
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Translation-en_US       
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release     
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/universe Translation-en_US   
Get:2 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release.gpg [191B] 
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Translation-en_US      
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:3 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/main Translation-en_US    
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                   
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
  404 Not Found
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Packages                          
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
  404 Not Found
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Packages                    
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Sources                
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Sources          
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages        
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/universe Packages           
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/universe Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/universe Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-backports/multiverse Sources
Fetched 3B in 1s (2B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
nancy@nancy-desktop:~$

---

### Post by Partyboi2 on 2008-09-19
Sorry those repo's must no longer be working. You could try to manually upgrade to feisty, but not sure what problems you might encounter upgrading from a end of life release.
[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)
or method 2 from
[http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html](http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html)
It might be easier and quicker to backup all your data you want to keep and do a clean install of hardy. (Lts)

---

