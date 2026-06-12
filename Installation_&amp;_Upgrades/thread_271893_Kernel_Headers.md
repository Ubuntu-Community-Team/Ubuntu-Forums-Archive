---
title: "Kernel Headers?"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by Vekemi on 2006-10-05
I'm having an issue installing the proper kernel headers under /usr/src, which sort of conflicts with me being able to install certain drivers.

```

vekemi@vekemi-laptop:~$ sudo apt-get install kernel-headers
Reading package lists... Done
Building dependency tree... Done
Package kernel-headers is a virtual package provided by:
  kernel-headers-2.4.27-2-k7-smp 2.4.27-12
  kernel-headers-2.4.27-2-k7 2.4.27-12
  kernel-headers-2.4.27-2-k6 2.4.27-12
  kernel-headers-2.4.27-2-686-smp 2.4.27-12
  kernel-headers-2.4.27-2-686 2.4.27-12
  kernel-headers-2.4.27-2-586tsc 2.4.27-12
  kernel-headers-2.4.27-2-386 2.4.27-12
  kernel-headers-2.4.27-2 2.4.27-12
You should explicitly select one to install.
E: Package kernel-headers has no installation candidate
vekemi@vekemi-laptop:~$ echo `uname -r`
2.6.15-27-386
vekemi@vekemi-laptop:~$ sudo apt-get install kernel-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-headers-2.6.15-27-386
vekemi@vekemi-laptop:~$
```

---

### Post by Endwin on 2006-10-05
Try ```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by Vekemi on 2006-10-05
```
vekemi@vekemi-laptop:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-27-386
vekemi@vekemi-laptop:~$
```

---

### Post by Endwin on 2006-10-05
Ok that is kind of odd, let's try

```
sudo aptitude update
sudo aptitude search linux-header

```

Look through there for the headers.

If that gives nothing, what is in your /etc/apt/sources.list ?

---

### Post by tbnext on 2006-10-05
I'm having a similar problem to this, when i try installing vmware i get an error saying that the kernel i'm runnin is 2.6.15-27 but the only headers available from running the script

"sudo apt-get install linux-headers"

are all 2.6.15-23, and it's really getting to me, i'v tried finding the actual linux-headers-2.6.15-27-386_2.6.15-27.48_i386.deb and extracting that i get an error with the 2.6.15-27 headers. 

in case it helps this is what my /etc/apt/sources.list looks like

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

