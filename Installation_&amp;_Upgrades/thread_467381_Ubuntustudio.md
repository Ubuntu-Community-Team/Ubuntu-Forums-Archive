---
title: "Ubuntustudio"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by burt_57 on 2007-06-07
[http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2:](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
What does it mean? ](*,)

---

### Post by bapoumba on 2007-06-08
Thread moved to "Installation & Upgrades".
There is a ":" at the end of the line that should not be there. What is the output to:
```
cat /etc/apt/sources.list
```

---

### Post by burt_57 on 2007-06-08
> **bapoumba said:**
> Thread moved to "Installation & Upgrades".
There is a ":" at the end of the line that should not be there. What is the output to:
```
cat /etc/apt/sources.list
```

robert@robert-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
robert@robert-desktop:~$

---

### Post by bapoumba on 2007-06-08
Two things:

- you should have only one instance of the ubuntustudio repo (delete all but one of the line).
- the repo is actually ...empty, I cannot see anything in there :/

Did you follow [this way]("http://ubuntustudio.org/downloads") to include the repo in your sources.list ?

---

### Post by burt_57 on 2007-06-08
> **bapoumba said:**
> Two things:

- you should have only one instance of the ubuntustudio repo (delete all but one of the line).
- the repo is actually ...empty, I cannot see anything in there :/

Did you follow [this way]("http://ubuntustudio.org/downloads") to include the repo in your sources.list ?

robert@robert-desktop:~$ sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
Password:
robert@robert-desktop:~$ wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_CA                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_CA             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Translation-en_CA           
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_CA         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources
Get:3 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]      
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA            
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources   
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA    
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_CA
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Get:5 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]
99% [5 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages            
  Sub-process bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Get:6 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]
99% [6 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages            
  Sub-process bzip2 returned an error code (2)
Get:7 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]  
Get:8 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]  
99% [7 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages            
  Sub-process bzip2 returned an error code (2)
99% [8 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages            
  Sub-process bzip2 returned an error code (2)
Get:9 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]  
99% [9 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages            
  Sub-process bzip2 returned an error code (2)
Get:10 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
99% [10 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
  Sub-process bzip2 returned an error code (2)
Get:11 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]
Get:12 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]
99% [11 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
  Sub-process bzip2 returned an error code (2)
99% [12 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
  Sub-process bzip2 returned an error code (2)
Get:13 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]
99% [13 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
  Sub-process bzip2 returned an error code (2)
Get:14 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]
99% [14 Packages bzip2 0]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
  Sub-process bzip2 returned an error code (2)
Fetched 14B in 0s (16B/s)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
robert@robert-desktop:~$

---

### Post by MetalMusicAddict on 2007-06-08
Th repo is up but isnt viewable from the web.

---

### Post by burt_57 on 2007-06-08
> **MetalMusicAddict said:**
> Th repo is up but isnt viewable from the web.
Oh boy now what? 
You are a great help... and quick to answer ;)

---

### Post by NeoLithium on 2007-06-08
I'm not having any problems with the repo from ubuntu studio, you've removed all but one of the entries, right?  Try:
```
sudo apt-get clean
sudo aptitude update

```

---

### Post by mmlnewbie on 2007-06-09
I'm downloading the Ubuntu Studio DVD via torrent to test on a spare home PC. Anybody know if:

a) It's a complete installation or just the Studio parts? do I need to install a vanilla 7.0.4 first?
b) Studio can be completely installed by upgrading 7.0.4 using the repos (well, once it comes back to life) or are there extra things on the DVD?

---

### Post by mmlnewbie on 2007-06-09
I'll just go ahead and answer this myself:

a) It's a complete install on the CD
b) Don't know and don't care any longer - I installed from the CD

---

