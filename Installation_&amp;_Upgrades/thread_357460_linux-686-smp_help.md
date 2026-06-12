---
title: "linux-686-smp help"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by nav211 on 2007-02-09
I don't even know where to begin. I have read a lot of threads and enabling dual core support seems relatively easy as compared to installing the Intel Fortran Compiler. Anyways, I have no clue why I am getting this error. I am new to Ubuntu (recent dropout of Fedora). 
My laptop Dell E1505, is running a core duo proc and I am using Ububtu 6.06. Somebody please help..


Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-686-smp: Depends: linux-image-686 but it is not going to be installed
                 Depends: linux-restricted-modules-686 but it is not going to be installedE: Broken packages

---

### Post by Stemp on 2007-02-09
Could you post the outpout of this command :
```
sudo apt-get update
```

and your /etc/apt/sources.list file

---

### Post by nav211 on 2007-02-09
this is what i get

```
navneet@navneet-laptop:~$ sudo apt-get update
Get:1 http://www.beerorkid.com dapper Release.gpg [189B]
Get:2 http://ubuntu.beryl-project.org dapper Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://www.beerorkid.com dapper Release
Hit http://ubuntu.beryl-project.org dapper Release
Hit http://archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://ubuntu.beryl-project.org dapper/main Packages
Hit http://ubuntu.beryl-project.org dapper/main Sources
Ign http://www.beerorkid.com dapper/main Packages
Ign http://www.beerorkid.com dapper/aiglx Packages
Hit http://www.beerorkid.com dapper/main Packages
Hit http://www.beerorkid.com dapper/aiglx Packages
Get:6 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Fetched 6B in 33s (0B/s)
Reading package lists... Done

```

And here is my source.list

```
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://ubuntu.beryl-project.org dapper main
deb-src http://ubuntu.beryl-project.org dapper main
# deb http://gandalfn.club.fr/ubuntu/ dapper

deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe


```



Do you think its a good idea to go through with this knowing that I might have to redo my fglrx and wireless support? The reason I am doing this is because I am hoping to get the most of my fortran compiler and speed up my simulations.

---

### Post by Stemp on 2007-02-09
The second text is not the sources.list ;)

---

### Post by nav211 on 2007-02-09
Sry. Wrong copy and paste. I just changed it.

---

### Post by Stemp on 2007-02-09
Can't see a problem in your sources.list.

And if you try to install linux-image-686 ?

---

### Post by nav211 on 2007-02-09
My system just installed a few updates and now it works. Thanks Stemp..

---

