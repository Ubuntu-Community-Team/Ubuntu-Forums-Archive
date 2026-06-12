---
title: "Can't intall - unmet dependencies that have actually been installed"
date: 2014-12-02
forum: Installation &amp; Upgrades
---

### Post by astarmathsandphysics on 2014-12-02
I am trying to install some apache2 modules and got this from the terminal.

sudo apt-get install libapache2-mod-spamhaus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libapache2-mod-spamhaus : Depends: apache2.2-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
root@server11362:~# sudo apt-get install apache2.2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2.2-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@server11362:~# 

As you see the spamhaus module depends on apache2.2-common but this is already installed.
How to fix?

---

### Post by gifford on 2014-12-02
Try using synaptic package manager to see if it will fix the problem. Open it up and under sections choose custom filters. It will show the broken packages, just go to edit and choose fix broken packages.
Hope it works for you.

---

### Post by astarmathsandphysics on 2014-12-02
Am on a terminal to remote server
Tried all the usual stuff
sudo apt-get clean
sudo apt-get autoremove
etc

---

### Post by gifford on 2014-12-02
Will this work?: sudo apt-get install -f

---

### Post by astarmathsandphysics on 2014-12-02
Nope that doesnt work either

---

### Post by ian-weisser on 2014-12-02
> **astarmathsandphysics said:**
> 
The following packages have unmet dependencies:
 libapache2-mod-spamhaus : Depends: apache2.2-common but it is not going to be installed
...
apache2.2-common is already the newest version.


Take a look at the source(s) of your apache2.2-common.
Please post the output of:
```
apt-cache policy apache2.2-common
```

---

### Post by astarmathsandphysics on 2014-12-03
Here it is

root@server11362:~# apt-cache policy apache2.2-common
apache2.2-common:
  Installed: 2.4.10-1+deb.sury.org~precise+1
  Candidate: 2.4.10-1+deb.sury.org~precise+1
  Version table:
 *** 2.4.10-1+deb.sury.org~precise+1 0
        500 [http://ppa.launchpad.net/ondrej/php5/ubuntu/](http://ppa.launchpad.net/ondrej/php5/ubuntu/) precise/main amd64 Packages
        100 /var/lib/dpkg/status
     2.2.22-1ubuntu1.7 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main amd64 Packages
     2.2.22-1ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages
root@server11362:~# mod_deflate test
mod_deflate: command not found
root@server11362:~#

---

### Post by ian-weisser on 2014-12-03
> **astarmathsandphysics said:**
> Installed: 2.4.10-1+deb.sury.org~precise+1
  Candidate: 2.4.10-1+deb.sury.org~precise+1
  Version table:
 *** 2.4.10-1+deb.sury.org~precise+1 0
        500 [http://ppa.launchpad.net/ondrej/php5/ubuntu/](http://ppa.launchpad.net/ondrej/php5/ubuntu/) precise/main amd64 Packages

Ah, you are using a version of Apache from a PPA instead of the Ubuntu repositories.
That's probably important.

Please show us the output of:
```
apt-cache show libapache2-mod-spamhaus
apt-cache show apache2.2-common
```

---

### Post by ian-weisser on 2014-12-03
> **astarmathsandphysics said:**
> Package: libapache2-mod-spamhaus
**Version: 0.7-1**
Depends: libc6 (>= 2.4), apache2.2-common

Package: apache2.2-common
Version: 2.4.10-1+deb.sury.org~precise+1
Breaks: ..., **libapache2-mod-spamhaus (<< 0.7-1.1)**, ...

Package: apache2.2-common
Version: 2.2.22-1ubuntu1.7
(No Breaks)

Package: apache2.2-common
Version: 2.2.22-1ubuntu1
(No Breaks)

Okay, here's what seems to be the problem:
Your version of Apache (2.4.10) is too advanced for the version of mod-spamhaus.
The package manager has an impossible situation. So it kicks the problem over to you.


I see four options:

1) You can downgrade Apache back to 2.2. Then mod-spamhaus should install easily.
This means uninstalling all the PPA software, disabling that PPA, and reinstalling Apache 2.2 from the Ubuntu repositories. This is a supported path - returning to the supported software versions in the supported repositories.

2) You can upgrade your version of Ubuntu to 14.04 for Apache 2.4.7 or to Ubuntu 14.10 for Apache 2.4.10.
Like #1, this means uninstalling all the PPA software and disabling that PPA. The PPA uses a rather unfortunate versioning scheme, and may cause a package management conflict that will break the upgrade. After the upgrade, install Apache from the Ubuntu repositories, not the PPA. This is also a supported path.

3) You can keep the Apache 2.4 PPA, and find a compatible version of mod-spamhaus out in the wild. This is not a supported solution.

4) You can contact the PPA maintainer for advice, since it's the PPA causing the problem.

---

### Post by astarmathsandphysics on 2014-12-04
I think I will upgrade ubuntu.
It is on my list of things to do anyway.

---

