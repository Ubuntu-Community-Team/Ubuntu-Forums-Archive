---
title: "Can't find some packages"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by José Serra on 2005-06-08
Hello... I've a problem, my system can't find several packages...
I.E.:
```
$ sudo apt-get install libglib2.0-dev
``` 
it returns that can't find the package.

Also Synaptic can't find packages like openoffice 2... my ubuntu release is: Hoary Hedgehog 5.04...

Thanks.

---

### Post by KLineD on 2005-06-08
[QUOTE=José Serra]Hello... I've a problem, my system can't find several packages...
I.E.:
```
$ sudo apt-get install libglib2.0-dev
``` 
it returns that can't find the package.

Also Synaptic can't find packages like openoffice 2... my ubuntu release is: Hoary Hedgehog 5.04...

Thanks.[/QUOTE]

Did you enabled the universe repositories?? That's where openoffice2 is. To enable the extra repositories check the ubuntu guide at [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by José Serra on 2005-06-08
mmm... When I
```
$ sudo apt-get update
``` 
or
When I open Synaptic

It can't connect with any of the URLs I've typed in */etc/apt/sources.list* 

I'm behind a firewall and I've a connected thru a proxy server...

what else can I do?
Thanks.

---

### Post by az on 2005-06-08
Can you go on the net with your computer?

---

### Post by José Serra on 2005-06-08
Yes... that's what I'm Using now...

---

### Post by KLineD on 2005-06-08
type 'cat /etc/apt/sources.list'

And post here the results. If you say you can't connect to any of the repositories maybe you've got something wrong in the sources file.

---

### Post by José Serra on 2005-06-10
Hello again.. Sorry for late response.
Ok I did what you say:

```
$ cat /etc/apt/sources.list
``` 
[I]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ve.archive.ubuntu.com/ubuntu](http://ve.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://ve.archive.ubuntu.com/ubuntu](http://ve.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ve.archive.ubuntu.com/ubuntu](http://ve.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://ve.archive.ubuntu.com/ubuntu](http://ve.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ve.archive.ubuntu.com/ubuntu](http://ve.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://ve.archive.ubuntu.com/ubuntu](http://ve.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/I] 

But still it can't connect...

any sugestions?

---

### Post by José Serra on 2005-06-10
mmm...
With firefox i can see the files on the URLs of the sourcelist.
In the web browser appears the usual
[I]Index of /ubuntu.
    *  Parent Directory
    * dists/
    * indices/
    * misc/
    * pool/
    * project/
Apache/2.1.3 (Ubuntu) Server at archive.ubuntu.com Port 80[/I]

my internet conexion seems to be fine...

when I... ```
sudo apt-get update
```
then...
```
[I]Err http://security.ubuntu.com hoary-security Release.gpg
  No pude conectarme a security.ubuntu.com:80 (82.211.81.138), expiró tiempo par a conexión [IP: 82.211.81.138 80]
Err http://archive.ubuntu.com hoary Release.gpg
  No pude conectarme a archive.ubuntu.com:80 (82.211.81.151), expiró tiempo para  conexión [IP: 82.211.81.151 80]
Err http://ve.archive.ubuntu.com hoary Release.gpg
  No pude conectarme a ve.archive.ubuntu.com:80 (82.211.81.151), expiró tiempo p ara conexión [IP: 82.211.81.151 80]
Err http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
  No pude conectarme a ubuntu-backports.mirrormax.net:80 (72.36.166.18), expiró tiempo para conexión [IP: 72.36.166.18 80]
Ign http://security.ubuntu.com hoary-security Release
Ign http://archive.ubuntu.com hoary Release
Ign http://ve.archive.ubuntu.com hoary Release
29% [Conectando a ve.archive.ubuntu.com (82.211.81.151)] [Conectando a security.ubun[/I]
```

---

### Post by Garrick on 2005-06-10
I am having a smillar issue.... It is showning a bunch of repositories missing...
> Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
  404 Not Found

Any ideas on what's causing the problem?

---

### Post by José Serra on 2005-06-13
What type conexion do you have... my system connects thru a proxy server.

May be that it's the problem... If you can solve it, please don't forget to post the solution here.

---

### Post by bluesman2333 on 2005-06-13
All of a sudden I'm having huge problems finding packages too. I can't even install Synaptic from the Knaptic manager because of dependancies. I've tried the repository change from ununtuguide.org and done a fresh install. Many packages needed are simply not in the repository. :?

---

### Post by bluesman2333 on 2005-06-13
This seems for me anyway to be centered around libgtk* and libpango* files. I even tried Xian's suggestion to delete the "us." part of the URI with no success. Can I just grab the files from another install?

---

### Post by Xian on 2005-06-13
[QUOTE=bluesman2333]This seems for me anyway to be centered around libgtk* and libpango* files. I even tried Xian's suggestion to delete the "us." part of the URI with no success. Can I just grab the files from another install?[/QUOTE]
What errors are you getting when you perform a 'sudo apt-get update' session?
Or is that even the problem?

---

### Post by José Serra on 2005-06-14
I've posted this earlier in this thread...

> when I... ```
sudo apt-get update
```
then...
```
[I]Err http://security.ubuntu.com hoary-security Release.gpg
  No pude conectarme a security.ubuntu.com:80 (82.211.81.138), expiró tiempo par a conexión [IP: 82.211.81.138 80]
Err http://archive.ubuntu.com hoary Release.gpg
  No pude conectarme a archive.ubuntu.com:80 (82.211.81.151), expiró tiempo para  conexión [IP: 82.211.81.151 80]
Err http://ve.archive.ubuntu.com hoary Release.gpg
  No pude conectarme a ve.archive.ubuntu.com:80 (82.211.81.151), expiró tiempo p ara conexión [IP: 82.211.81.151 80]
Err http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
  No pude conectarme a ubuntu-backports.mirrormax.net:80 (72.36.166.18), expiró tiempo para conexión [IP: 72.36.166.18 80]
Ign http://security.ubuntu.com hoary-security Release
Ign http://archive.ubuntu.com hoary Release
Ign http://ve.archive.ubuntu.com hoary Release
29% [Conectando a ve.archive.ubuntu.com (82.211.81.151)] [Conectando a security.ubun[/I]
``` 

I need Openoffice 2.0 what can I do?

---

### Post by bluesman2333 on 2005-06-14
[QUOTE=Xian]What errors are you getting when you perform a 'sudo apt-get update' session?
Or is that even the problem?[/QUOTE]

The errors I get are not with the update sesion, but with the install of some packages. It is looking for libs not in the repository. There are quite a few md5sum missmatch errors too. I fixed the problem on one box by installing another OS, and on this box, I have all the packages I need right now. 

Can I just transfer libs I need from one box to another if this happens again?

---

### Post by Xian on 2005-06-14
[QUOTE=bluesman2333]The errors I get are not with the update sesion, but with the install of some packages. It is looking for libs not in the repository. There are quite a few md5sum missmatch errors too.[/QUOTE]
Can you try the install using 'apt-get' from the command line and post back with some specific examples and errors received?

---

### Post by bluesman2333 on 2005-06-14
[QUOTE=Xian]Can you try the install using 'apt-get' from the command line and post back with some specific examples and errors received?[/QUOTE]

I just installed Kubuntu on a spare partition. I installed everything Just fine.  I even went through the changes mentioned the Ubuntu guide. The only errors I got were "Duplicate sources.list" entry errors. Sorry man, but the missing libs that were not there yesterday are there today, and there are no md5sum errors. I didn't need to make the changes in your posts deleting the us., because the ubuntu guide changes were working. Thank You for your effort and help, at this point it seems that everything fixed itself.  :-?

---

