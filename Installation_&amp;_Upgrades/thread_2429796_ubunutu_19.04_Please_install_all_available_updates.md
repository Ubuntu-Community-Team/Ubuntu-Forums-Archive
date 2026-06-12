---
title: "ubunutu 19.04 Please install all available updates for your release before upgrading."
date: 2019-10-23
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2019-10-23
I am trying to upgrade from ubuntu 19.04 to ubuntu 19.10.
when I trying to this 
```
sudo apt list --upgradable -a
Listing... Done
libsnmp30/disco-updates 5.7.3+dfsg-5ubuntu1.2 amd64 [upgradable from: 5.7.3+dfsg-1.8ubuntu3.1]
libsnmp30/disco 5.7.3+dfsg-5ubuntu1 amd64
libsnmp30/now 5.7.3+dfsg-1.8ubuntu3.1 amd64 [installed,upgradable to: 5.7.3+dfsg-5ubuntu1.2]
----
```
when I run upgrade I get the following
lease install all available updates for your release before upgrading.
Cheers

---

### Post by TheFu on 2019-10-23
[B]Stop if any step fails with any errors. DO NOT move onto the next step.
[/B]
Steps to upgrade between releases on Ubuntu:
* Plug into power (never use battery)
* make a 100% know-you-can-restore backup
* sudo apt update
* sudo apt dist-upgrade
* reboot (if anything new was installed)
* sudo do-release-upgrade

The release-upgrade process will disable any PPAs. In a new release, the software provided by a PPA might be upgraded to an acceptable version, so the PPA may not be needed.  The prior PPAs are listed in /etc/apt/sources.list.d/*save so you can go through them one-by-one and update the release listed.

If there are any errors, fix those ASAP.  DO NOT continue. After corrected, restart with a fresh backup.  

If you need help with issues, please show the exact command and the exact output as it appears in a terminal.  Use *code tags*.  Don't interpret.  Copy/paste everything.

---

### Post by pablosquared on 2019-10-23
I had this same problem when upgrading last night. Using synaptic, I found there was a held update package (nvidia-settings) that was not going to be upgraded because of an unmet dependency. 

I'd recent.y upgraded the nvidia driver from 390 to 400. I removed 440, and reinstalled 390. 

I also purged the apt-sources.list of PPAs not pointing to the disco release (19.04). Rebooted, and was able to run the upgrade successfully. 

Not sure which action did the trick, but I'd suggest cleaning the APT repositories list first, then looking at the nvidiai driver, if that's relevant to your system.

---

### Post by hoboy on 2019-10-23
Hi TheFu:
the directory /etc/apt/sources.list.d/* contains

```
/etc/apt/sources.list.d$ ls -l
total 60
-rw-r--r-- 1 root root 251 Oct 23 13:34 graphics-drivers-ubuntu-ppa-bionic.list
-rw-r--r-- 1 root root 219 Aug 26 07:40 graphics-drivers-ubuntu-ppa-bionic.list.distUpgrade
-rw-r--r-- 1 root root 251 Oct 23 13:34 graphics-drivers-ubuntu-ppa-bionic.list.save
-rw-r--r-- 1 root root   0 Aug 26 10:07 graphics-drivers-ubuntu-ppa-disco.list
-rw-r--r-- 1 root root   0 Aug 26 10:07 graphics-drivers-ubuntu-ppa-disco.list.save
-rw-r--r-- 1 root root 334 Oct 23 13:34 oibaf-ubuntu-graphics-drivers-bionic.list
-rw-r--r-- 1 root root 302 Aug 26 07:40 oibaf-ubuntu-graphics-drivers-bionic.list.distUpgrade
-rw-r--r-- 1 root root 334 Oct 23 13:34 oibaf-ubuntu-graphics-drivers-bionic.list.save
-rw-r--r-- 1 root root 186 Oct 23 13:34 opera-stable.list
-rw-r--r-- 1 root root 186 Aug 26 07:40 opera-stable.list.distUpgrade
-rw-r--r-- 1 root root 186 Oct 23 13:34 opera-stable.list.save
-rw-r--r-- 1 root root  89 Oct 23 13:34 skype-stable.list
-rw-r--r-- 1 root root  56 Aug 26 07:40 skype-stable.list.distUpgrade
-rw-r--r-- 1 root root  89 Oct 23 13:34 skype-stable.list.save
-rw-r--r-- 1 root root 165 Oct 23 13:34 webupd8team-ubuntu-java-vivid.list
-rw-r--r-- 1 root root 165 Aug 26 07:40 webupd8team-ubuntu-java-vivid.list.distUpgrade
-rw-r--r-- 1 root root 165 Oct 23 13:34 webupd8team-ubuntu-java-vivid.list.save
```
how do I do what you have proposed ?
I have tried the suggestion from "pablosquared"
that hasn't succeeded
Cheers

---

### Post by deadflowr on 2019-10-23
ppas will all autodisabled when the upgrader starts.

Actually looking at the apt list those packages currently listed as installed are from cosmic, so something is off somewhere.
Please post the output from 
```
sudo apt update
sudo apt full-upgrade
```

---

### Post by hoboy on 2019-10-23
```
sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libsnmp30
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
*******************************************************************************
sudo apt list --upgradable
Listing... Done
libsnmp30/disco-updates 5.7.3+dfsg-5ubuntu1.2 amd64 [upgradable from: 5.7.3+dfsg-1.8ubuntu3.1]
N: There are 2 additional versions. Please use the '-a' switch to see them.
******************************************************************************************************
sudo apt list --upgradable -a
Listing... Done
libsnmp30/disco-updates 5.7.3+dfsg-5ubuntu1.2 amd64 [upgradable from: 5.7.3+dfsg-1.8ubuntu3.1]
libsnmp30/disco 5.7.3+dfsg-5ubuntu1 amd64
libsnmp30/now 5.7.3+dfsg-1.8ubuntu3.1 amd64 [installed,upgradable to: 5.7.3+dfsg-5ubuntu1.2]
```

Cheers

---

### Post by deadflowr on 2019-10-23
I asked for full output of both commands.

---

### Post by hoboy on 2019-10-23
In Software Updater.
I only see Bionic.. nothing with disco
but in 
sudo gedit /etc/apt/sources.list

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main restricted multiverse universe #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates main restricted multiverse universe #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security restricted multiverse main universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security restricted multiverse main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-proposed main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-proposed main restricted multiverse universe #Added by software-properties

```

cheers

---

### Post by TheFu on 2019-10-23
There is a reason that deadflowr asked for the output.
```
sudo apt update
sudo apt full-upgrade
```

And the *update* output?  Also, please use code tags so it is easier to read.

BTW, *sudo apt full-upgrade*  ===== *sudo apt dist-upgrade* ; those are the same.

Lastly, hopefully unrelated, but using **sudo gedit /etc/apt/sources.list** is dangerous.  Use **sudoedit /etc/apt/sources.list** to edit system files safely.  All those tutorials showing *sudo gedit WHATEVER* are making all sorts of assumptions which may not be true on any specific system.

libsnmp30 isn't exactly a core library.

---

### Post by hoboy on 2019-10-24
Bump

---

### Post by TheFu on 2019-10-24
> **hoboy said:**
> Bump

Bump. Please answer the questions asked.

---

### Post by hoboy on 2019-10-24
Re: upgrade from 19.04 to 19.10 cause unknown subsys name errors

    I was able to upgrade to ubuntu 19.10.
    but new I have new problem worst then before upgrading.

    upgrade from 19.04 to 19.10 cause unknown subsys name errors

    I have upgrade form ubuntu 19.04 to 19.10.
    but when I lunch ubuntu
    I get 4 lines of the errors messages bellow
    just only one of message is bellow,
    cgroup1: Unknown susbsys name ' __DEVEL__same_behaviour'
    cgroup1: Unknown susbsys name ' __DEVEL__same_behaviour'
    cgroup1: Unknown susbsys name ' __DEVEL__same_behaviour'
    then the ubuntu stop launching, it freeze there, with black screen .
    I have no desktop only console
    where I can run commands
    Cheers

---

### Post by kkovach on 2019-10-24
Same problem here. I don't know what to do with the following...

kkovach@frost:~$ sudo apt list --upgradable -a
Listing... Done
libsnmp30/disco-updates 5.7.3+dfsg-5ubuntu1.2 amd64 [upgradable from: 5.7.3+dfsg-1.8ubuntu3.18.10.1]
libsnmp30/disco 5.7.3+dfsg-5ubuntu1 amd64
libsnmp30/now 5.7.3+dfsg-1.8ubuntu3.18.10.1 amd64 [installed,upgradable to: 5.7.3+dfsg-5ubuntu1.2]

Any help or hints would be appreciated. Thanks!

---

### Post by pchaffey on 2020-03-07
> **kkovach said:**
> Same problem here. I don't know what to do with the following...

kkovach@frost:~$ sudo apt list --upgradable -a
Listing... Done
libsnmp30/disco-updates 5.7.3+dfsg-5ubuntu1.2 amd64 [upgradable from: 5.7.3+dfsg-1.8ubuntu3.18.10.1]
libsnmp30/disco 5.7.3+dfsg-5ubuntu1 amd64
libsnmp30/now 5.7.3+dfsg-1.8ubuntu3.18.10.1 amd64 [installed,upgradable to: 5.7.3+dfsg-5ubuntu1.2]

Any help or hints would be appreciated. Thanks!

Did you get a response to this ? I have exactly the same problem

---

### Post by Impavidus on 2020-03-08
OP used Ubuntu 19.04. If you don't run that release, your problem appears not exactly the same. If you also run 19.04, you've got a different problem too, as 19.04 has now reached end of life. In that case, wipe it and try a fresh install of 19.10.

If you have a problem, start your own thread. That's how it's done on this forum.

---

