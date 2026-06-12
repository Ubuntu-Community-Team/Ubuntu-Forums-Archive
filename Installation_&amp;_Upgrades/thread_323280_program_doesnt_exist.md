---
title: "program doesnt exist"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by source on 2006-12-21
trying to install firestarter here and it seems it doesnt exist? or am i doing something wrong? take a look at my terminal guys.

source@source-desktop:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter
source@source-desktop:~$


?

---

### Post by taurus on 2006-12-21
You need to enable both universe and multiverse in /etc/apt/sources.list by removing the # in front of the lines with universe & multiverse at the end (with deb at the beginning)...

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install firestarter
```

---

### Post by source on 2006-12-21
hmm.....


didnt seem to work i dont think 

i think it would help if i told you that i am still running on 6.06 
LTS.

terminal...     ?


```
source@source-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:18814): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
source@source-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security Release
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Fetched 3B in 0s (3B/s)
Reading package lists... Done
source@source-desktop:~$ sudo aptitude install firestarter
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "firestarter"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by taurus on 2006-12-21
Then use a text editor!!!

Applications -> Accessories -> Terminal
```
sudo nano -Bw /etc/apt/sources.list
```
Use the arrow keys to navigate around and when you are done, hold down <Ctrl> while pressing x.  Just hit the Return key twice for both answer to save it.  Then, run

```
sudo aptitude update
sudo aptitude install firestarter
```

---

### Post by source on 2006-12-22
im so sorry for this i tried various times but still couldnt get it to work.

I even updated to edgy eft.

then i deleted all the #'s with the lines of universe and multiverse.

but i was missing 3 dependencies apparantly... idk what to do. 

```
source@source-desktop:~$ sudo aptitude install firestarter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  firestarter 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 391kB of archives. After unpacking 1946kB will be used.
The following packages have unmet dependencies:
  firestarter: Depends: libdbus-1-2 (>= 0.60) but it is not installable
               Depends: libgnutls12 (>= 1.2.5) but it is not installable
               Depends: libtasn1-2 (>= 0.2.13) but it is not installable
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
source@source-desktop:~$ 
```

---

### Post by taurus on 2006-12-22
Post your /etc/apt/sources.list here then!

```
cat /etc/apt/sources.list
```

---

### Post by source on 2006-12-22
```
source@source-desktop:~$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

 #Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb http://security.ubuntu.com/ubuntu dapper-security universe
 deb-src http://security.ubuntu.com/ubuntu dapper-security universe
source@source-desktop:~
```

---

### Post by taurus on 2006-12-22
How come you have dapper and edgy mix in /etc/apt/sources.list!!!  It is never a good thing to mix the two together in there.  Bad things would happen to your machine and will...

Therefore, if you are using Edgy right now, change the **dapper** to **edgy** in /etc/apt/sources.list; otherwise, replace the **edgy** with **dapper** if you are using Dapper right now.

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install firestarter
```

---

### Post by source on 2006-12-22
yay got it working you own :)

---

