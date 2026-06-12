---
title: "Broken packages after upgrading to Lubuntu 12.10"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by Mr.MountainLurk on 2013-02-06
After upgrading form Lubuntu 12.04 to 12.10 I got the message that I have 2 broken packages: 

linux-image-extra-3.5.0-23-generic
linux-image-generic

How do I fix this? I'm not that familiar with ubuntu yet :-P

I'm on a old IBM Thinkpad R50e
Intel Celeron M 1.4GHz
768MB RAM

Dualboot with Windows 7

---

### Post by Sealbhach on 2013-02-06
Try this first.  In a terminal paste or write this command:

```
sudo dpkg --configure -a
```If it gives you back any interesting comments copy and paste them here.

.

---

### Post by Mr.MountainLurk on 2013-02-06
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-dbus (>= 4:4.5.3); however:
  Package libqt4-dbus is not installed.
 skype depends on libqt4-network (>= 4:4.8.0); however:
  Package libqt4-network is not installed.
 skype depends on libqt4-xml (>= 4:4.5.3); however:
  Package libqt4-xml is not installed.
 skype depends on libqtcore4 (>= 4:4.7.0~beta1); however:
  Package libqtcore4 is not installed.
 skype depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not installed.
 skype depends on libqtwebkit4 (>= 2.2~2011week36); however:
  Package libqtwebkit4 is not installed.

dpkg: error processing skype (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-23-generic; however:
  Package linux-image-3.5.0-23-generic is not installed.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-23-generic:
 linux-image-extra-3.5.0-23-generic depends on linux-image-3.5.0-23-generic; however:
  Package linux-image-3.5.0-23-generic is not installed.

dpkg: error processing linux-image-extra-3.5.0-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
 linux-image-generic
 linux-image-extra-3.5.0-23-generic
 linux-generic

---

### Post by Sealbhach on 2013-02-06
OK. Do a dist-upgrade

```
sudo apt-get dist-upgrade
```

If that doesn't fix it just reinstall those packages mentioned

```
sudo apt-get install --reinstall skype linux-image-generic linux-image-extra-3.5.0-23-generic
```

That should probably clear it.


.

---

### Post by Mr.MountainLurk on 2013-02-06
Nope, neighter worked :-(

vegard@vegard-ThinkPad-R50e:~$ sudo apt-get dist-upgrade
[sudo] password for vegard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.5.0-23-generic : Depends: linux-image-3.5.0-23-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.5.0-23-generic but it is not installed
 skype : Depends: libqt4-dbus (>= 4:4.5.3) but it is not installed
         Depends: libqt4-network (>= 4:4.8.0) but it is not installed
         Depends: libqt4-xml (>= 4:4.5.3) but it is not installed
         Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installed
         Depends: libqtgui4 (>= 4:4.8.0) but it is not installed
         Depends: libqtwebkit4 (>= 2.2~2011week36) but it is not installed
         Recommends: sni-qt but it is not installed
E: Unmet dependencies. Try using -f.
vegard@vegard-ThinkPad-R50e:~$ sudo apt-get install --reinstall skype linux-image-generic linux-image-extra-3.5.0-23-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.5.0-23-generic : Depends: linux-image-3.5.0-23-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.5.0-23-generic but it is not going to be installed
 skype : Depends: skype-bin but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Can it have something to do with my cpu not having support for "pae"?

---

### Post by Sealbhach on 2013-02-06
There is a problem with your software sources I think, check them and make sure you have got all the software sources for 12.10. 

Post your sources list here, maybe we can get to the bottom of it. You can quickly see them with:

```
cat /etc/apt/sources.list
```Also check what kernel you're using, if the problem one is not the current one you're using you can just delete it.

```
uname -rvp
```.

---

### Post by Mr.MountainLurk on 2013-02-07
Sources list:

vegard@vegard-ThinkPad-R50e:~$ cat /etc/apt/sources.list
# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main




vegard@vegard-ThinkPad-R50e:~$ uname -rvp
3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:57 UTC 2013 i686

Really thanks a lot for the help :)

---

### Post by dino99 on 2013-02-07
that line should not be commented out:

```
# deb http://extras.ubuntu.com/ubuntu quantal main
```

remove # to get:
```
deb http://extras.ubuntu.com/ubuntu quantal main
```

by using : ```
sudo gedit /etc/apt/sources.list
```

then update; if the problem persist, then purge the libqt4*/skype packages, then reinstall them after having tried to fix the kernel issue (using synaptic; install it if necessary)

---

### Post by Mr.MountainLurk on 2013-02-08
Uncomment this as well?
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main

The uncomment did'nt work :-/

Removed all the skype packages. All the libqt4 packages as well?

The problem started before I installed anything btw. It was a clean 12.04 install upgraded to 12.10.

---

### Post by 7bit on 2013-02-08
could you please try to run that script as root:
[http://paste.ubuntu.com/1622104/](http://paste.ubuntu.com/1622104/)

(save it a a file, chmod +x the file and then run it with sudo)

and then again try to (re)install that linux-image-3.5.0-23-generic package? I am asking this because I think I have found a way to install these pae kernels on my ThinkPad T40 without jumping through too many hoops. I have already running the Quantal-pae kernel on my T40 (rest of the system is still Precise) and after patching the /proc/cpuinfo this kernel intalled without any problems (and it boots and works perfectly on this Pentium-M). 

Since you are using a ThinkPad fom that era too I believe it might work on your system too. 

Please do NOT uninstall your old 3.2 Kernel before you are 100% sure the 3.5-pae actually boots and runs without problems.

---

### Post by Mr.MountainLurk on 2013-02-11
It worked! Thanks a lot! :o)

---

### Post by 7bit on 2013-02-11
> **Mr.MountainLurk said:**
> It worked! Thanks a lot! :o)

this is good to hear :-)

please also see this other thread: [http://ubuntuforums.org/showthread.php?p=12498964](http://ubuntuforums.org/showthread.php?p=12498964)
this is where this script came from. I am planning to convert this into a .deb package soon that can be installed on the affected thinkpad models and that would solve these update problems (also all future kernel updates and updates to Ubuntu 13.xx and 14.xx and later) automatically once and for all.

---

### Post by ClausQ on 2013-04-12
> **7bit said:**
> could you please try to run that script as root:
[http://paste.ubuntu.com/1622104/](http://paste.ubuntu.com/1622104/)

(save it a a file, chmod +x the file and then run it with sudo)

and then again try to (re)install that linux-image-3.5.0-23-generic package? I am asking this because I think I have found a way to install these pae kernels on my ThinkPad T40 without jumping through too many hoops. I have already running the Quantal-pae kernel on my T40 (rest of the system is still Precise) and after patching the /proc/cpuinfo this kernel intalled without any problems (and it boots and works perfectly on this Pentium-M). 

Since you are using a ThinkPad fom that era too I believe it might work on your system too. 

Please do NOT uninstall your old 3.2 Kernel before you are 100% sure the 3.5-pae actually boots and runs without problems.

Hi 7bit,

I have exactly the same problem on a Fujitsu Stylistic tablet, but now the link in your post is 'dead'. Could you maybe repost? Thanks

-- update: now I read your other post and used your package - works perfectly! Thanks and sorry for posting ...

Cheers, Claus

---

