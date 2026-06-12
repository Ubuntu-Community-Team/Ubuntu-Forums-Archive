---
title: "Help. Synaptic's Update url's always say error."
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by skygazer4k on 2006-09-27
Hello guru's.
 I really need some help here. I installed 6.06.1 amd64 bit. Security updates available button top right flashes. Then I Go to synaptic to update/install whatevers. No matter what source(s) selected gives a Connection failed error. The only source that works is the DVD. And I am connected to the net just fine. Web-Browsing is fine. Home lan is OK. Only the url sources get errors. I did run a script to add full multimedia support for mp3 and such. I think that it may have changed my apt/sources file. But to note that before I did that I was still having this same errors with the url's so it was existing before the script thing. I tried to do security immediately after I installed  this yesterday and got the problem right away. Are the supplied source url's correct or is there a bug maybe? I have no clue:confused: .
Please help. Many thanks.:cool:

---

### Post by cammj on 2006-09-27
What are the errors?

---

### Post by skygazer4k on 2006-09-28
Always error of IP Connect. Except the DVD.Do I need to do some special command to update via url's? Thanks'

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz:) Connection failed [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz:) Connection failed [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz:) Connection failed [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-amd64/Packages.gz:) Connection failed [IP: 195.248.90.54 80]

---

### Post by confused57 on 2006-09-28
You might want to post the output of:
```
cat /etc/apt/sources.list
```

You can always replace your current repositories:
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

---

### Post by skygazer4k on 2006-09-29
Well I did the link you sent (Very helpful, thank's) but belive it or not I get the same probs. It's almost like I am being firewalled or ports blocked. But I know thats not true since I setupv the router myself. No UpNp, blocked sites or port forwarding at all. Anyway, here is apt/sources contents. Then below that is the output from command."sudo aptitude update"  
 This is a bit strange at this point. Is it possably missing some sort of libs or a protocol or like that?  Obviously i am just guessing. arghhh..:evil: 

```

[COLOR="Teal"][FONT="Tahoma"]## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free[/FONT][/COLOR]

```


```
[FONT="Tahoma"][COLOR="DarkSlateGray"]jeff@ubuntu-laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err http://archive.canonical.com dapper-commercial Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Ign http://archive.canonical.com dapper-commercial Release
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Ign http://archive.canonical.com dapper-commercial/main Packages
Ign http://security.ubuntu.com dapper-security/main Packages
Err http://packages.freecontrib.org dapper Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.canonical.com dapper-commercial/main Packages
  Connection failed
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://packages.freecontrib.org dapper Release
Ign http://archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://packages.freecontrib.org dapper/free Packages
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://packages.freecontrib.org dapper/non-free Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper/main Packages
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://packages.freecontrib.org dapper/non-free Sources
Ign http://archive.ubuntu.com dapper/restricted Packages
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Err http://packages.freecontrib.org dapper/free Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/main Sources
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Err http://packages.freecontrib.org dapper/non-free Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Ign http://archive.ubuntu.com dapper/restricted Sources
Err http://packages.freecontrib.org dapper/free Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://packages.freecontrib.org dapper/non-free Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Sources
Ign http://archive.ubuntu.com dapper/multiverse Packages
Ign http://archive.ubuntu.com dapper/multiverse Sources
Ign http://archive.ubuntu.com dapper-updates/main Packages
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Err http://archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 195.248.90.23 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed [IP: 195.248.90.23 80]
Reading package lists... Done
jeff@ubuntu-laptop:~$

[/COLOR][/FONT]
```

---

### Post by bokibre on 2006-10-05
I have the same problem and I've installed ubuntu 6.06.1 i386 from dvd!!! I had problem to open webpages then i turned off ipv6 and i can open webpages but synaptic ain't working at all nor update is working and the adresses that synaptic is showing error i manage to open via firefox!!!!

---

### Post by John Melbourne on 2007-07-20
I had the same problem

The following is not a cure but certainly a workaround.

In synaptic, go to  settings-preferences-network Manual Proxy and set the HTTP proxy to 91.189.89.3 (the IP address of old-releases.ubuntu.com).

RESULT fast connect and some 200MB of update.

N.B. you might possibly have a different IP address.  To check use terminal  then
" PING old-releases,ubuntu.com"         and check the reply IP address

---

