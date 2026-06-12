---
title: "ap-get upgrade 3 not upgraded"
date: 2022-01-27
forum: Installation &amp; Upgrades
---

### Post by Krischu on 2022-01-27
I'm trying to bring an ubuntu 18.04.6 system up to date. (it's still a 32 bit system but I have no choice at the moment).

After running

apt-get update
apt-get upgrade

I'm getting:

```

root@me:~# apt-get update
Hit:1 http://ppa.launchpad.net/certbot/certbot/ubuntu bionic InRelease
Hit:2 http://archive.ubuntu.com/ubuntu bionic InRelease                                                 
Hit:3 http://archive.ubuntu.com/ubuntu bionic-updates InRelease                                         
Hit:4 http://de.archive.ubuntu.com/ubuntu bionic InRelease                                              
Hit:5 http://ppa.launchpad.net/vbernat/haproxy-1.8/ubuntu bionic InRelease                              
Hit:6 http://security.ubuntu.com/ubuntu bionic-security InRelease                                     
Reading package lists... Done                                                   
root@me:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
root@me:~# 

```

How can I find out the cause and how to repair the situation?

Also I would like to find out whether the recent polkit (pkexec) security flaw has been eliminated with the upgrade, in outer words,
is there a change log or release remarks on every update. Kind of a verbose upgrade?

---

### Post by ActionParsnip on 2022-01-27
What is the output of
```

apt-cache policy linux-generic linux-headers-generic linux-image-generic

```

Packages are "kept back" until their dependant packages and versions are met, then they will install.

---

### Post by guiverc on 2022-01-27
There are cases where `apt upgrade` will **not**install all upgrades; that is intentional as gives the operator more control on when to apply upgrades that may require a reboot or require removal of packages (*that could impact running programs*).

from `man apt` on my release is the following

>        full-upgrade (apt-get(8))

           full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.


Have you tried that? or checked for holds (`apt-mark showhold`)

---

### Post by Krischu on 2022-01-27
> **ActionParsnip said:**
> What is the output of
```

apt-cache policy linux-generic linux-headers-generic linux-image-generic

```

Packages are "kept back" until their dependant packages and versions are met, then they will install.

```

root@me:~# apt-cache policy linux-generic linux-headers-generic linux-image-generic
linux-generic:
  Installed: 4.15.0.163.152
  Candidate: 4.15.0.166.155
  Version table:
     4.15.0.166.155 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
 *** 4.15.0.163.152 100
        100 /var/lib/dpkg/status
     4.15.0.20.23 500
        500 http://archive.ubuntu.com/ubuntu bionic/main i386 Packages
        500 http://de.archive.ubuntu.com/ubuntu bionic/main i386 Packages
linux-headers-generic:
  Installed: 4.15.0.163.152
  Candidate: 4.15.0.166.155
  Version table:
     4.15.0.166.155 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
 *** 4.15.0.163.152 100
        100 /var/lib/dpkg/status
     4.15.0.20.23 500
        500 http://archive.ubuntu.com/ubuntu bionic/main i386 Packages
        500 http://de.archive.ubuntu.com/ubuntu bionic/main i386 Packages
linux-image-generic:
  Installed: 4.15.0.163.152
  Candidate: 4.15.0.166.155
  Version table:
     4.15.0.166.155 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
 *** 4.15.0.163.152 100
        100 /var/lib/dpkg/status
     4.15.0.20.23 500
        500 http://archive.ubuntu.com/ubuntu bionic/main i386 Packages
        500 http://de.archive.ubuntu.com/ubuntu bionic/main i386 Packages
root@me:~# 


```

On the other machine I'm getting:

```

root@mail:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  php
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@mail:~# 

```

dpkg --list shows that I have several php versions up to php8 installed. Why is this "php" without version left over.
I'm a bit hesitant to do a "full upgrade". Can I do this fearlessly?

---

### Post by schragge on 2022-01-27
> **Krischu said:**
> I'm a bit hesitant to do a "full upgrade". Can I do this fearlessly?
Not only you can. You are *supposed* to do this when you see the "kept back" message. Have you read the man page **guiverc** quoted? BTW, it's [FONT=monospace]**full-upgrade**[/FONT] (note the dash).

> **Krischu said:**
> Why is this "php" without version left over.
From the package description:
> This package is a dependency package, which depends on latest stable PHP version
See [15.2.1. Meta-Packages or Fake Packages]("https://www.debian.org/doc/manuals/debian-handbook/sect.building-first-package.en.html#id-1.18.5.2") in *The Debian Administrator's Handbook* as well as [uhelp]community/MetaPackages[/uhelp].

*Full Circle #47* ran [this question]("http://dl.fullcirclemagazine.org/issue47_en.pdf#page=35") in their Q&A section:
> [SIZE=+2]**[COLOR=#e27743]Q[/COLOR]**[/SIZE] In the Ubuntu repositories, there are files listed by the Synaptic Package Manager as &#8220;place holders&#8221;, and some called &#8220;transitional dummy packages&#8221;. What are these files, and how are they used?

[SIZE=+2]**A**[/SIZE] You can think of those files as pointers, pointing to the real packages, which probably have more complicatd names. So, for example, if you install &#8220;apache2,&#8221; you get all the components you need in order to run the current version of Apache2.

You'll lose nothing by upgrading or not upgrading such a dummy package. It's there just for your convenience, so that you don't have to remember what the latest stable PHP version is.

---

