---
title: "Having problems with installing or upgrading to Dapper? Here are some fixes"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2006-06-03
Are you having problems with installing or upgrading to Dapper? Here are some fixes.

**This is all on your own risk. Please be very careful.**

**WARNING / take a look here prior to upgrading and installing! :**
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

**Offical Ubuntu Upgrade Guide at Ubuntu Wiki:**
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

**Offical Ubuntu Installation page at Ubuntu Wiki**:
[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

**Offical Ubuntu Upgrade Guide - troubleshooting section (including pcmcia services hang)**:
[https://wiki.ubuntu.com/DapperUpgrades#head-2d31cca9e09f221550a1b8b52ccd60ea3eb655c7](https://wiki.ubuntu.com/DapperUpgrades#head-2d31cca9e09f221550a1b8b52ccd60ea3eb655c7)

**Dealing with problems with the Xserver by tseliot**
[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

**Guides for Dapper Drake**
[http://www.ubuntuforums.org/showthread.php?t=182716](http://www.ubuntuforums.org/showthread.php?t=182716)

**need a clean Dapper sources.list?**
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

**Problems with booting (ACPI)**
[http://www.ubuntuforums.org/showthread.php?t=140981](http://www.ubuntuforums.org/showthread.php?t=140981)

**booting stalls during "mounting root filesystem"?**
[http://www.ubuntuforums.org/showthread.php?t=197956](http://www.ubuntuforums.org/showthread.php?t=197956)
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)
[http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41](http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41)
[http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62](http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62)
[http://ubuntuforums.org/showthread.php?t=212839](http://ubuntuforums.org/showthread.php?t=212839)
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)

The devs know about this bug and we might see a dapper-update someday. See this thread :
[http://www.ubuntuforums.org/showthread.php?t=208207](http://www.ubuntuforums.org/showthread.php?t=208207)

Here are workarounds (which need testing) :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)

**having problems with locales and/or libc6 ?**
Sometimes problems with locales are related to problems with libc6. Look here for more information :
[http://www.ubuntuforums.org/showpost.php?p=1057281&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1057281&postcount=8)
[http://www.ubuntuforums.org/showthread.php?t=186570](http://www.ubuntuforums.org/showthread.php?t=186570)
After you've solved it do this guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

**Dependency problems with clvm which you don't need unless you are sure that you need it**
$sudo rm /etc/init.d/clvm
$sudo apt-get remove clvm -f --purge
after that do this guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

**HOWTO fix problems regarding broken dependencies**
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

**Problems with apt regarding gpg keys?**
[http://www.ubuntuforums.org/showthread.php?t=188295](http://www.ubuntuforums.org/showthread.php?t=188295)

**Fixes by RavenOfOdin for these problems**
[I]Help! My packages are returning these errors!
```

<package name here> : unable to make backup link of </path/to/file here> : Operation not permitted.
dpkg-deb: Subprocess <package name here> killed by broken pipe: -1.
dpkg-deb: Error : Operation not permitted.

```
My packages won't configure via dpkg!
My installer bails with something like "<file name> is trying to overwrite file in </path/to/file here> which belongs to package <package here>."
Package A depends on Package B to install, but Package B depends on Package A to install! HELP![/I]
**[http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12)**

[B]
Please tell: your network problems and solutions[/B]
[http://www.ubuntuforums.org/showthread.php?t=184795](http://www.ubuntuforums.org/showthread.php?t=184795)

**How to fix problem with Davicom ethernet adapter**
[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

**[WARNING]some problems with the latest updates ? (with auto-login for example)**
[http://www.ubuntuforums.org/showthread.php?t=197754](http://www.ubuntuforums.org/showthread.php?t=197754)

**sources.list and/or apt.conf permissions**
check the permissions of your sources.list and of /etc/apt/apt.conf :
$ ls -al /etc/apt/sources.list
$ ls -al /etc/apt/apt.conf

the results both be :
```

-rw-r--r-- 1 root root ......

```

If it's something else do this get the permissions right :
$ sudo chmod 644 /etc/apt/sources.list
$ sudo chmod 644 /etc/apt/apt.conf

if it's not owned by root:root do this :
$sudo chown root:root /etc/apt/sources.list
$sudo chown root:root /etc/apt/apt.conf

**More fixes :**
[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

**Please post your tips and/or fixes here :**
[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

If you have problems and you need help IMHO it's best to start a new thread. In your own new thread : be elaborate about your problems. **Post the errors you get.** Post your /var/log/Xorg.0.log and ~/xsession-errors log files. Post the result of $lspci and post your /etc/apt/sources.list.

Also please post this :

1) System Specifications:
Monitor: CRT/LCD
Ram Amount:
HD: IDE/SATA/Scsi
Onboard or Discreet Graphics Card: NV/ATI/Intel/SiS/ect
CPU: 
MainBoard: Intel/Via/NV
Modem / Eth / Wifi brand:
Adapter cards you have installed:
2) Version of Ubuntu your using: (K)(X)(ED)Ubuntu or server.
3) Any error or output codes you receive durring the install or after:

forum staff : feel free to edit and improve this post

edit :
There will be an update to the dist-upgrader which will prevent some of these problems for new upgraders :
[http://www.ubuntuforums.org/showpost.php?p=1194942&postcount=57](http://www.ubuntuforums.org/showpost.php?p=1194942&postcount=57)

---

### Post by ubuntu_demon on 2006-06-04
**I'm posting this as a forum user and not as a staff member. First read the entire post before doing anything. This is all on your own risk. Please be careful.**

**WARNING / take a look here prior to upgrading and installing! :**
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

This sources.list has no third party repositories enabled. But **it has backports,multiverse and universe enabled**. If you intentionally kept backports,multiverse and/or universe disabled in your sources.list then **don't forget to** comment them before using this sources.list or use the other sources.list below. 

**Here's a clean sources.list for Dapper :**

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

Here's a clean sources.list for dapper **without backports,multiverse and universe enabled**. Some people use such a sources.list. I recommend this one for servers for example.

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
## deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
## deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

To use this sources.list replace your sources.list with this one using your favorite editor. Do the following command in the terminal (without the $):
$sudo gedit /etc/apt/sources.list

Then do this command to take the new sources.list into effect do the following command in the terminal (without the $) :

get into ctrl-alt-f1

$sudo apt-get update

It happens quite often that this command wants to remove ubuntu-desktop / kubuntu-desktop so don't worry :

$sudo apt-get dist-upgrade

Make sure everything is installed by :
$sudo apt-get install ubuntu-base
$sudo apt-get install ubuntu-desktop (or kubuntu-desktop / edubuntu-desktop / xubuntu-desktop)

Now do a reboot :
$sudo reboot

---

