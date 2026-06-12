---
title: "Cannot Upgrade Computer"
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by jcjanko2 on 2015-05-03
I have been trying to find an answer to this question for almost an hour and cannot find anything (I have found similar issues but they were not exact and the solutions did not work), so I apologize if this has been answered. 

My daughter brought her computer to me and said she could not install her updates. I tried to manually upgrade through the terminal and here is what I got:

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 audacity : Depends: libavcodec54 (>= 6:9.1-1) but it is not installed or
                     libavcodec-extra-54 (>= 6:9.13) but it is not installed
 gstreamer1.0-libav : Depends: libavcodec54 (>= 6:9.1-1) but it is not installed or
                               libavcodec-extra-54 (>= 6:9.13) but it is not installed
 libavformat54 : Depends: libavcodec54 (>= 6:9.1-1) but it is not installed or
                          libavcodec-extra-54 (>= 6:9.18) but it is not installed
 libchromaprint0 : Depends: libavcodec54 (>= 6:9.1-1) but it is not installed or
                            libavcodec-extra-54 (>= 6:9.10) but it is not installed
 libopencv-highgui2.4 : Depends: libavcodec54 (>= 6:9.1-1) but it is not installed or
                                 libavcodec-extra-54 (>= 6:9.10) but it is not installed
E: Unmet dependencies. Try using -f.

I cannot install or remove ANY programs on the computer, through the terminal or Software Center. She is using Xubuntu 14.04 64-bit on a Dell E6400. Any help would be appreciated before I just decide to wipe it clean. Thanks!

---

### Post by ian-weisser on 2015-05-03
Please show us the output of the following command:
```
apt-cache policy audacity
```

---

### Post by jcjanko2 on 2015-05-04
Thank you for the quick reply:

$ apt-cache policy audacity
audacity:
  Installed: 2.0.5-1ubuntu3.2
  Candidate: 2.0.5-1ubuntu3.2
  Version table:
 *** 2.0.5-1ubuntu3.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.0.5-1ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages

---

### Post by matt_symes on 2015-05-04
Hi

> **jcjanko2 said:**
> Thank you for the quick reply:

$ apt-cache policy audacity
audacity:
  Installed: 2.0.5-1ubuntu3.2
  Candidate: 2.0.5-1ubuntu3.2
  Version table:
 *** 2.0.5-1ubuntu3.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.0.5-1ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages

That looks alright.

Can we next check her sources. Can you post the output of this.

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

The package system needs either libavcodec54 or libavcodec-extra-54, both of which are in the universe repositories at the versions needed to satisfy the package system.

However they conflict with each other so only one needs to be installed. Can you post the output of this command so we can take a look at what dpkg has to say about the packages.

```
dpkg -l libavcodec54 libavcodec-extra-54
```

Kind regards

---

### Post by kerry_s on 2015-05-04
why didn't you run the "sudo apt-get -f install" like it's telling you to do ?

---

### Post by matt_symes on 2015-05-04
Hi

> **kerry_s said:**
> why didn't you run the "sudo apt-get -f install" like it's telling you to do ?

The question is 'why is the system missing the libraries ?' you see. 

It should have already have one of them and it's prudent to do some background checking.

Kind regards

---

### Post by jcjanko2 on 2015-05-04
> **kerry_s said:**
> why didn't you run the "sudo apt-get -f install" like it's telling you to do ?

I think the better question is why you think I haven't tried that, instead of asking if I had :). I probably should have been more explicit:

```

$ sudo apt-get -f install
[sudo] password for lydia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libavcodec54
The following NEW packages will be installed:
  libavcodec54
0 upgraded, 1 newly installed, 0 to remove and 158 not upgraded.
Need to get 0 B/2,349 kB of archives.
After this operation, 6,276 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error: parsing file '/var/lib/dpkg/available' near line 45935 package 'qtchooser':
 `Replaces' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by jcjanko2 on 2015-05-04
> **matt_symes said:**
> Hi



That looks alright.

Can we next check her sources. Can you post the output of this.

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

The package system needs either libavcodec54 or libavcodec-extra-54, both of which are in the universe repositories at the versions needed to satisfy the package system.

However they conflict with each other so only one needs to be installed. Can you post the output of this command so we can take a look at what dpkg has to say about the packages.

```
dpkg -l libavcodec54 libavcodec-extra-54
```

Kind regards

```
$ grep -n "^[^#]" /etc/apt/sources.list{,.d/*}

/etc/apt/sources.list:1:deb cdrom:[Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723)]/ trusty main multiverse restricted universe
/etc/apt/sources.list:5:deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:6:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:10:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:11:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:16:deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:17:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:18:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:19:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:26:deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:27:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:28:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:29:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:37:deb http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:38:deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:39:deb http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:40:deb-src http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:41:deb http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:42:deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:48:deb http://archive.canonical.com/ubuntu trusty partner
/etc/apt/sources.list:49:deb-src http://archive.canonical.com/ubuntu trusty partner
/etc/apt/sources.list:53:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list:54:deb-src http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list.d/google-chrome.list:3:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:3:deb http://dl.google.com/linux/chrome/deb/ stable main
```

```
$ dpkg -l libavcodec54 libavcodec-extra-54

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/  Name           Version      Architecture Description
+++-==============-============-============-=================================
un  libavcodec-ext <none>       <none>       (no description available)
rc  libavcodec54:a 6:9.18-0ubun amd64        Libav codec library
```

Thank you again for all of the replies. I also have noticed her HDD is a little loud, but seems to be working fine otherwise. Not sure if it is going on her.

---

### Post by jcjanko2 on 2015-05-04
I apologize for the formatting of the post. I don't know how to get it more vertical.

---

### Post by matt_symes on 2015-05-04
Hi

The formatting of the post is fixed for you :)

This is what i think may have happened.

The library libavcodec-extra-54 has been uninstalled to satisfy the dependency of a newly installed program the requires libavcodec54. 

This operation cannot complete as your dpkg available file is corrupted. The information for the package qtchooser has a damaged replaces field. Hence the current problem.

Although this may not be the only problem with your package system, it is where the sticking point is at the moment.

To get things started you need to fix the available file.

This can either be attempted by editing the field or using the backup available file, either of which may be problematic.

The location of the backup available file is in the same location as the standard one.

```
matthew-laptop:/var/log:2 % ls /var/lib/dpkg/available*
/var/lib/dpkg/available  /var/lib/dpkg/available-old
matthew-laptop:/var/log:2 
```

In the first instance, let's try using the old one. We'll rename the current one .broken. Then we'll see if apt can fix itself.

```

sudo mv /var/lib/dpkg/available{,.broken}
sudo mv /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo apt-get -f install
```

Post back any and all errors.

If this does not work then we'll take it from there. Maybe try to fix the errors returned or try to fix the broken file using sed.

I am away from keyboard until tomorrow some time and i'm based in the UK so, if she's in a rush and needs it back, someone else can help. If not i'll be online at some point tomorrow.

Kind regards

---

### Post by jcjanko2 on 2015-05-05
> **matt_symes said:**
> Hi

The formatting of the post is fixed for you :)

This is what i think may have happened.

The library libavcodec-extra-54 has been uninstalled to satisfy the dependency of a newly installed program the requires libavcodec54. 

This operation cannot complete as your dpkg available file is corrupted. The information for the package qtchooser has a damaged replaces field. Hence the current problem.

Although this may not be the only problem with your package system, it is where the sticking point is at the moment.

To get things started you need to fix the available file.

This can either be attempted by editing the field or using the backup available file, either of which may be problematic.

The location of the backup available file is in the same location as the standard one.

```
matthew-laptop:/var/log:2 % ls /var/lib/dpkg/available*
/var/lib/dpkg/available  /var/lib/dpkg/available-old
matthew-laptop:/var/log:2 
```

In the first instance, let's try using the old one. We'll rename the current one .broken. Then we'll see if apt can fix itself.

```

sudo mv /var/lib/dpkg/available{,.broken}
sudo mv /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo apt-get -f install
```

Post back any and all errors.

If this does not work then we'll take it from there. Maybe try to fix the errors returned or try to fix the broken file using sed.

I am away from keyboard until tomorrow some time and i'm based in the UK so, if she's in a rush and needs it back, someone else can help. If not i'll be online at some point tomorrow.

Kind regards
This did it! Everything is updating correctly and running smoothly. Thank you so much for your help.

---

