---
title: "Package manager died"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by SBMN7 on 2013-08-12
Dear valued user,

My synaptic package manager is dead. please help me to recover this problem. i have uploaded screen shot , which shows my problem.

---

### Post by SlugSlug on 2013-08-12
please post output of

cat /etc/apt/sources.list

---

### Post by SBMN7 on 2013-08-12
deb file:/home/saurav/kubuntu-desktop-repacked
deb cdrom:[Kubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main


this is output of that command. The main reason is i saw a articles in website about installing kde desktop on ubuntu using kubuntu live cd. and then i follow the process, then my package manager goes down and dead. please help me to solve this.

---

### Post by SlugSlug on 2013-08-12
ok try 

gksudo gedit /etc/apt/sources.list

add a # to the first line
so it looks like 
#deb file:/home/saurav/kubuntu-desktop-repacked


You could also add a # to all the deb-src lines if you don't download the source code

after that save and exit and run

sudo apt-get update


any errors post them here

---

### Post by SBMN7 on 2013-08-12
Hi slugslug, package manager is alive now. but another problem comes again. when i enter this command as you tell me "sudo apt-get update" it shows success, and when i go to package manager it shows that all programs are installed in my system (green symbol), but not in actually. im not sure what to do. please help me. i added screen shot again.

---

### Post by SlugSlug on 2013-08-12
not sure what you mean there..
to install updates now use 

sudo apt-get upgrade

---

### Post by SBMN7 on 2013-08-12
saurav@saurav-MS-7592:~$ sudo apt-get upgrade 
[sudo] password for saurav: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
saurav@saurav-MS-7592:~$ 

when i use this command it shows these information.

---

### Post by SlugSlug on 2013-08-12
that looks fine, no updates

---

### Post by SBMN7 on 2013-08-12
saurav@saurav-MS-7592:~$ cat /etc/apt/sources.list 
saurav@saurav-MS-7592:~$ cat /etc/apt/sources.list 
saurav@saurav-MS-7592:~$ cat /etc/apt/sources.list 
saurav@saurav-MS-7592:~$ cat /etc/apt/sources.list 
saurav@saurav-MS-7592:~$ cat /etc/apt/sources.list 
saurav@saurav-MS-7592:~$ 

this command has been stopped working and not displaying former text file.

---

### Post by SlugSlug on 2013-08-12
right ok, you blitzed it some how

Just noticed you also on an unsupported version (to old)

do this again.

gksudo gedit /etc/apt/sources.list

paste in this
```


###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner

```

then run 

sudo apt-get update

sudo do-release-upgrade

That will update you to the12.04 release

---

### Post by deadflowr on 2013-08-12
Your problem is going to persist as the oneric repos are dead.
The oneric repos where moved to the old-release repos.

Either upgrade your system to a supported release, or change the source.list to the old-release repos.

---

### Post by SBMN7 on 2013-08-12
now it is updating system without any error. thanks for your great help brother.

---

### Post by SBMN7 on 2013-08-12
Thanks for your great help. now my system is updating without error. when it will complete then i will run upgrade. many many thanks brother.

---

