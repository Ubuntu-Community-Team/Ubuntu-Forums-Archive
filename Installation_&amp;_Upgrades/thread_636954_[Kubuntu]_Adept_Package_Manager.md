---
title: "[Kubuntu] Adept Package Manager"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by DeForce on 2007-12-10
Hello there. I am new to kubuntu 6.06 Dapper Drake (LTS) and i need your help.
I've installed Kubuntu about 1 week ago and week was without problems...
But after I've installed some Upgrades that Adept say me. Upgrades was installed sucesfully and I go sleep. On another day I've power up my computer and worked.
When I needed to install some programmes I started Adept... but it wasn't starting at all. I think that I've bad started computer but after some reboots I also cannot start adept... It starts loading and don't say that I need to enter pass... after 20 seconds he just shut off and if I tried to start it again and it again start just loading and then nothing happend... what problem can be?
      This is my Sources.list
            ```
deb http://kubuntu.org/packages/kde-355 dapper main 

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted 
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse 
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse 
```

       sorry for my bad english

---

### Post by Pumalite on 2007-12-10
Post output of:
sudo apt-get install -f

---

