---
title: "Reinstalling xserver on 7.10"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by BlueKnight84 on 2008-07-24
Hi all.

I feel like such a noob (it's because I am)...

I need to reinstall xserver because I uninstalled it, thinking it would solve a problem I was faced with.  More on that later (perhaps will be another thread if I can get that far).

Using command line, which is all I have at this point, when I type:

```
sudo apt-get install xserver-xorg
```

I get

```
$ sudo apt-get install xserver-xorg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  mdetect
The following NEW packages will be installed:
  xserver-xorg
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
Need to get 169kB of archives.
After unpacking 598kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  xserver-xorg
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com edgy-updates/main xserver-xorg 1:7.1.1ubuntu6.2
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.1.1ubuntu6.2_all.deb  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I've already tried

```
sudo apt-get update
```

Which gives me:

```
Ign http://security.ubuntu.com edgy-security Release.gpg
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://archive.ubuntu.com edgy-backports Release.gpg            
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US 
Ign http://us.archive.ubuntu.com edgy Release.gpg
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security Release                 
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Ign http://archive.ubuntu.com dapper/universe Translation-en_US             
Ign http://archive.ubuntu.com dapper/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates Release.gpg
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/main Packages
Ign http://archive.ubuntu.com edgy-backports Release
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com dapper Release   
Ign http://us.archive.ubuntu.com edgy-security Release.gpg
Ign http://security.ubuntu.com edgy-security/restricted Packages                          
Ign http://security.ubuntu.com edgy-security/main Sources                                 
Ign http://security.ubuntu.com edgy-security/restricted Sources                           
Ign http://us.archive.ubuntu.com edgy-security/main Translation-en_US                     
Ign http://us.archive.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy Release                        
Ign http://us.archive.ubuntu.com edgy-updates Release                
Ign http://archive.ubuntu.com edgy-backports/main Packages           
Ign http://archive.ubuntu.com edgy-backports/restricted Packages
Ign http://archive.ubuntu.com edgy-backports/universe Packages       
Ign http://security.ubuntu.com edgy-security/universe Packages       
Ign http://security.ubuntu.com edgy-security/universe Sources        
Err http://security.ubuntu.com edgy-security/main Packages           
  404 Not Found
Err http://security.ubuntu.com edgy-security/restricted Packages     
  404 Not Found
Err http://security.ubuntu.com edgy-security/main Sources            
  404 Not Found
Ign http://us.archive.ubuntu.com edgy-security Release               
Ign http://us.archive.ubuntu.com edgy/main Packages                  
Ign http://us.archive.ubuntu.com edgy/restricted Packages            
Ign http://us.archive.ubuntu.com edgy/main Packages                  
Ign http://archive.ubuntu.com edgy-backports/multiverse Packages     
Ign http://archive.ubuntu.com edgy-backports/main Sources            
Ign http://archive.ubuntu.com edgy-backports/restricted Sources      
Ign http://archive.ubuntu.com edgy-backports/universe Sources        
Ign http://archive.ubuntu.com edgy-backports/multiverse Sources      
Hit http://archive.ubuntu.com dapper/universe Packages               
Hit http://archive.ubuntu.com dapper/multiverse Packages             
Err http://security.ubuntu.com edgy-security/restricted Sources      
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Packages       
  404 Not Found
Ign http://us.archive.ubuntu.com edgy/restricted Packages            
Ign http://us.archive.ubuntu.com edgy/main Sources                   
Ign http://us.archive.ubuntu.com edgy/restricted Sources             
Ign http://us.archive.ubuntu.com edgy/universe Packages              
Ign http://us.archive.ubuntu.com edgy/universe Sources               
Hit http://archive.ubuntu.com dapper/universe Sources                
Hit http://archive.ubuntu.com dapper/multiverse Sources              
Err http://archive.ubuntu.com edgy-backports/main Packages           
  404 Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com edgy-security/universe Sources        
  404 Not Found
Ign http://us.archive.ubuntu.com edgy-updates/main Packages          
Ign http://us.archive.ubuntu.com edgy-updates/restricted Packages
Ign http://us.archive.ubuntu.com edgy-updates/main Packages
Ign http://us.archive.ubuntu.com edgy-updates/restricted Packages
Err http://archive.ubuntu.com edgy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com edgy-backports/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com edgy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com edgy-backports/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com edgy-backports/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Ign http://us.archive.ubuntu.com edgy-updates/main Sources
Ign http://us.archive.ubuntu.com edgy-updates/restricted Sources
Ign http://us.archive.ubuntu.com edgy-security/main Packages
Ign http://us.archive.ubuntu.com edgy-security/restricted Packages
Err http://us.archive.ubuntu.com edgy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com edgy-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-security/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-security/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Fetched 1B in 1s (1B/s)  
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

My source list reads like this:

```
$ cat /etc/apt/sources.list
 deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
 deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
 deb http://us.archive.ubuntu.com/ubuntu edgy-security main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
 deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

Based on the above, you might've noticed I've changed around some things thinking it would fix my "apt-get" problem.

The only reason I uninstalled xserver to begin with is because when it's booting up, the Ubuntu loading screen was very, very dark, and when it finished, the screen went black on one monitor, and on another, it said "OUT OF SCAN RANGE."  At the end of booting up in recovery mode out of the GRUB menu, it told me: "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? <Yes> <No>"

If anyone is able to help me, you have no idea how grateful I'd be!  Thanks for reading!

---

