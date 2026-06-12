---
title: "Problem updating packages"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by Booyaches on 2013-02-27
Hi,
i'll start by saying I'am a total beginner in Linux. I have Ubuntu 12.04.1 LTS installed on a separate machine and I use it for storing data and hosting some services. I usually use Webmin to update my packages (and other simple stuff) and I didn't do it for quite a while. Today I tried to update them and this is what I saw with every single package (215 times):

```

Installing package(s) with command apt-get -y install appmenu-gtk ..
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-37-generic-pae; however:
  Package linux-image-3.2.0-37-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
Setting up postfix (2.9.1-5) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: fatal: bad string length 0 < 1: setgid_group = 
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.37.44); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.37.44); however:
  Version of linux-headers-generic-pae on system is 3.2.0.38.46.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailutils:
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailutils (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-generic-pae
 postfix
 bsd-mailx
 linux-generic-pae
 mailutils
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.37.44) but 3.2.0.38.46 is to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-37-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

As adviced in this error message i connected through SSH and run:
```
sudo apt-get -f install
```

Here is the result:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gconf-2.0 libutouch-grail1 libunity6 libidl-common libglew1.5
  linux-headers-3.2.0-25 linux-headers-3.2.0-25-generic-pae libglewmx1.5 libutouch-evemu1
  libidl0 libdee-1.0-1 libutouch-frame1 linux-headers-3.2.0-25-generic liborbit2
  libutouch-geis1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-image-3.2.0-38-generic-pae linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-38-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 1 newly installed, 0 to remove and 217 not upgraded.
5 not fully installed or removed.
Need to get 0 B/38.2 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 526203 files and directories currently installed.)
Unpacking linux-image-3.2.0-38-generic-pae (from .../linux-image-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-38-generic-pae': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Generally, I can see that I have a problem with **linux-image-3.2.0-37-generic-pae**  or simply "linux kernel image". 

Can you please suggest any steps that I should take to fix that? Or maybe there is a way to reinstall Ubuntu components without messing up my configurations? (kinda like in Windows ?) Please keep in mind I'am a beginner user.

---

### Post by plucky on 2013-02-27
> dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-38-generic-pae': [color=red]No space left on device[/color]
No apport report written because the error message indicates a disk full error

Do you have a separate /boot partition?

Post output for ```
df -h
sudo fdisk -l
```

Good Luck

---

### Post by Booyaches on 2013-02-27
> **plucky said:**
> Do you have a separate /boot partition?

Post output for ```
df -h
sudo fdisk -l
```

Good Luck

Yes I do and it was 100% full. I checked running: ```
sudo df
```

So I managed to clean my /boot up to 60% by following [this thread]("http://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to"). Then I run: 
```
sudo apt-get -f install
``` 
and I get:
```
 dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb (--unpack): corrupted filesystem tarfile - corrupted package archive No apport report written because MaxReports is reached already.
``` Did I mess something up already?

---

### Post by plucky on 2013-02-27
>  dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb (--unpack): corrupted filesystem tarfile - corrupted package archive No apport report written because MaxReports is reached already.

Try running ```
sudo apt-get clean
``` so your system has to download the packages again as that command clears out all the .deb packages in /var/cache/apt/archives/ directory.


Good Luck

---

### Post by Booyaches on 2013-02-27
> **plucky said:**
> Try running ```
sudo apt-get clean
``` so your system has to download the packages again as that command clears out all the .deb packages in /var/cache/apt/archives/ directory.


Good Luck

So first i rebooted the machine. Then I run: 
```
sudo apt-get clean
```
later:
```
sudo apt-get -f install
```

And, unfortunatelly, nothing seems to change:

```

...
Fetched 455 kB in 2s (201 kB/s)
Reading package lists... Done
booyaches@BooyaHost:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 217 not upgraded.
5 not fully installed or removed.
Need to get 4,344 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dk.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic-pae i386 3.2.0.38.46 [1,728 B]
Get:2 http://dk.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic-pae i386 3.2.0.38.46 [2,616 B]
Fetched 4,344 B in 0s (52.4 kB/s)             
Setting up postfix (2.9.1-5) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: fatal: bad string length 0 < 1: setgid_group = 
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailutils:
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             pae depends on linux-image-3.2.0-37-generic-pae; however:
  Package linux-image-3.2.0-37-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.37.44); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.37.44); however:
  Version of linux-headers-generic-pae on system is 3.2.0.38.46.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
 bsd-mailx
 mailutils
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How about connecting my machine to monitor and keyboard and simply updating to Ubuntu 12.10? Would that "override" those errors?

---

### Post by plucky on 2013-02-27
Why is it trying to install postfix?

Were trying to install postfix before this all started?

> dpkg: dependency problems prevent configuration of bsd-mailx:


Have you at any point run ```
sudo apt-get update
```? to update the index files.

---

### Post by dino99 on 2013-02-27
from your post #1, you already have been said what to do:

[HTML]Use 'apt-get autoremove' to remove them.[/HTML]

how can we tell you that more clearly ?  ;)

```
sudo apt-get autoremove
```

that should wipe out the actual conflict.

---

### Post by Booyaches on 2013-02-28
I tried a lot of apt-get commands. I just tried first: ```
sudo apt-get update
``` That goes well. Then I go: ```
sudo apt-get -f autoremove
``` and I get the same errors. Basically when i try **apt-get install/autoremove **it always tells me that I have some missing dependencies and I should try with -f, when I do I get those errors.

```

Do you want to continue [Y/n]? y
Setting up postfix (2.9.1-5) ...


Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).


After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.


Running newaliases
newaliases: fatal: bad string length 0 < 1: setgid_group = 
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mailutils:
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailutils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-37-generic-pae; however:
  Package linux-image-3.2.0-37-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.37.44); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.37.44); however:
  Version of linux-headers-generic-pae on system is 3.2.0.38.46.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
 bsd-mailx
 mailutils
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

About Postfix... yes I might have tried to install postfix sometime in the past when I was playing around.

---

### Post by plucky on 2013-02-28
Can you post your sources.list ```
cat /etc/apt/sources.list
```

---

### Post by Booyaches on 2013-02-28
Sure:
```

# 


# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release i386 (20111011)]/ oneiric main restricted


# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release i386 (20111011)]/ oneiric main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://dk.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ precise universe
deb http://dk.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://dk.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

---

### Post by plucky on 2013-03-01
That looks good.


You could try removing postfix ```
sudo dpkg -r postfix
``` and see if that works.

Good Luck

---

### Post by Booyaches on 2013-03-01
Finally the problem is fixed!!
First I plugged my machine to monitor and keyboard and updated to 12.10. That fixed the problem with[FONT=Ubuntu Mono, monospace][COLOR=#000000]: **linux-image-generic-pae** and **linux generic pae**. Later, I removed: **postfix, bsd-mailx and mailutils: **using previously suggested:
```
[/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg -r ...[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
```
Next: 
[/FONT][/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000]```
[/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get -f autoremove[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
```
[/FONT][/COLOR]Next:
[FONT=Ubuntu Mono, monospace][COLOR=#000000]```
[/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
```
[/FONT][/COLOR]Next:
[FONT=Ubuntu Mono, monospace][COLOR=#000000]```
[/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get -f install[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
```
[/FONT][/COLOR]
And now I have no packages left to update and everything works like a charm. Thank you for everyone who was active in this thread :-)
[FONT=Ubuntu Mono, monospace][COLOR=#000000]
[/COLOR][/FONT]

---

