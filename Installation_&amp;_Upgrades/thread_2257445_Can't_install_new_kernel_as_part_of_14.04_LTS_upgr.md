---
title: "Can't install new kernel as part of 14.04 LTS upgrade"
date: 2014-12-19
forum: Installation &amp; Upgrades
---

### Post by mike-g2 on 2014-12-19
I'm trying to complete an upgrade to my laptop.  Unfortunately, there was an error during the upgrade process and the new kernel didn't install completely.  I can boot to an older 3.2 kernel but can't install any newer kernels. 

Here's what happens when I try to install linux-generic-lts-trusty which I assume will install all necessary kernels.

```

[mike@host ~]$ sudo apt-get install linux-generic-lts-trusty
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-generic linux-headers-generic linux-image-3.13.0-43-generic
  linux-image-extra-3.13.0-43-generic linux-image-generic
Suggested packages:
  linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-generic linux-generic-lts-trusty linux-headers-generic
  linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic
  linux-image-generic
0 upgraded, 6 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/51.9 MB of archives.
After this operation, 194 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Selecting previously unselected package linux-image-3.13.0-43-generic.
(Reading database ... 401775 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Selecting previously unselected package linux-image-extra-3.13.0-43-generic.
Preparing to unpack .../linux-image-extra-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Unpacking linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-image-generic (3.13.0.43.50) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../linux-headers-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.43.50) ...
Selecting previously unselected package linux-generic.
Preparing to unpack .../linux-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-generic (3.13.0.43.50) ...
Selecting previously unselected package linux-generic-lts-trusty.
Preparing to unpack .../linux-generic-lts-trusty_3.13.0.43.50_amd64.deb ...
Unpacking linux-generic-lts-trusty (3.13.0.43.50) ...
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-No apport report written because the error message indicates its a followup error from a previous failure.
  No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                            generic (3.13.0.43.50) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-trusty:
 linux-generic-lts-trusty depends on linux-generic; however:
  Package linux-generic is not configured yet.

dpkg: error processing package linux-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
 linux-generic-lts-trusty
E: Sub-process /usr/bin/dpkg returned an error code (1)
[mike@host ~]$ 

```

I'd appreciate any help I can get solving this issue.

Thanks,

Mike

---

### Post by fantab on 2014-12-19
Post the output of:
```
sudo df -h
```

---

### Post by mike-g2 on 2014-12-19
Here's the output. Note I do not have a separate /boot partition.

```
$ sudo df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        33G   18G   14G  57% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           779M  1.2M  778M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  692K  3.8G   1% /run/shm
none            100M   68K  100M   1% /run/user
/dev/sda1        56G   45G   11G  81% /windows
/dev/sda6       580G  215G  335G  40% /home
```

---

### Post by Bucky Ball on 2014-12-19
Do this:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report back any errors that throws. If there is a new kernel available, that should install. If it doesn't it will throw an error.

If you upgraded via the net only yesterday, though, that should have dragged in the latest kernel. Do:

```
uname -a
```

The current 14.04 kernel is 3.13.0-43.

---

### Post by mike-g2 on 2014-12-20
Output from  $ sudo apt-get autoremove

> 
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-trusty:
 linux-generic-lts-trusty depends on linux-generic; however:
  Package linux-generic is not configured yet.

dpkg: error processing package linux-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic-lts-trusty
E: Sub-process /usr/bin/dpkg returned an error code (1)




---

### Post by mike-g2 on 2014-12-20
output from $ sudo apt-get update

> 
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease
Ign [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty InRelease
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages
Ign [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-updates InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
Ign [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Ign [http://cran.case.edu](http://cran.case.edu) precise/ InRelease
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty/non-free amd64 Packages
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages
Get:1 [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-updates Release.gpg [933 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib amd64 Packages
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://cran.case.edu](http://cran.case.edu) precise/ Release.gpg
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages
Get:2 [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-updates Release [62.0 kB]
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty/non-free i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
Hit [http://cran.case.edu](http://cran.case.edu) precise/ Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages
.
.
.
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [229 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [387 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [9,356 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [8,861 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [230 kB]
Get:21 [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-updates/multiverse i386 Packages [9,539 B]
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-updates/main Translation-en
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-updates/multiverse Translation-en
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-updates/restricted Translation-en
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-updates/universe Translation-en
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [379 kB]
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/main Sources
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/restricted Sources
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/universe Sources
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/multiverse Sources
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/main amd64 Packages
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/restricted amd64 Packages
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/universe amd64 Packages
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/multiverse amd64 Packages
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/main i386 Packages
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/restricted i386 Packages
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,539 B]
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/universe i386 Packages
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/multiverse i386 Packages
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [8,832 B]
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/main Translation-en
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/multiverse Translation-en
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
Hit [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Ign [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty/main Translation-en_US
Ign [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty/multiverse Translation-en_US
Ign [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty/restricted Translation-en_US
Ign [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Fetched 2,900 kB in 16s (171 kB/s)
Reading package lists...


---

### Post by Bucky Ball on 2014-12-20
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

One after the other, please. No need to post the whole output, only the errors. ;)

The update looked fine. Let's see what the upgrade and dist-upgrade drag up. 

And please use [code] tags for code. See the last link in my signature for how. Neater, space-saving and easier to read. Thanks.

---

### Post by mike-g2 on 2014-12-20
```
$ sudo apt-get upgrade
```

and

```
$ sudo apt-get dist-upgrade 
```

both give similar results.

Here's the `upgrade` output.
 ```


[mikeg@cheoah Green]$ sudo apt-get upgrade
[sudo] password for mikeg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnuplot-nox gnuplot-x11
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not cNo apport report written because the error message indicates its a followup error from a previous failure.
   No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                             No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
                                                                                            onfigured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-trusty:
 linux-generic-lts-trusty depends on linux-generic; however:
  Package linux-generic is not configured yet.

dpkg: error processing package linux-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
 linux-generic-lts-trusty
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What is depmod

---

### Post by mike-g2 on 2014-12-20
I get similar message for apt-get update and apt-get -f install.

---

### Post by Bucky Ball on 2014-12-20
Please use [code] tags for code, as requested. I have added them to your last post. Thanks.

I have to go out, but will have a look later. ;)

---

### Post by mike-g2 on 2014-12-20
Thanks. I will use [CODE] tags in future posts.

---

### Post by mike-g2 on 2014-12-21
```

[mikeg@host Green]$ uname -a
Linux host 3.2.0-74-generic #109-Ubuntu SMP Tue Dec 9 16:45:49 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by mike-g2 on 2014-12-21
Was able to purge all of the 3.13-x kernels, but no updates were available either using `apt-get upgrade' or `apt-get dist-upgrade'.  So I tried 
```

[mike@host Green]$ sudo apt-get install linux-image-generic linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-generic linux-image-3.13.0-43-generic
  linux-image-extra-3.13.0-43-generic
Suggested packages:
  linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-generic linux-headers-generic linux-image-3.13.0-43-generic
  linux-image-extra-3.13.0-43-generic linux-image-generic
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/51.9 MB of archives.
After this operation, 194 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Selecting previously unselected package linux-image-3.13.0-43-generic.
(Reading database ... 401709 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Selecting previously unselected package linux-image-extra-3.13.0-43-generic.
Preparing to unpack .../linux-image-extra-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Unpacking linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-image-generic (3.13.0.43.50) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../linux-headers-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.43.50) ...
Selecting previously unselected package linux-generic.
Preparing to unpack .../linux-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-generic (3.13.0.43.50) ...
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                   No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                generic (3.13.0.43.50) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I then tried running,
```

[mike@host Green]$ sudo apt-get purge linux-image-generic linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-generic
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  linux-generic* linux-image-generic*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 57.3 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 406536 files and directories currently installed.)
Removing linux-generic (3.13.0.43.50) ...
Removing linux-image-generic (3.13.0.43.50) ...
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
[mikeg@cheoah Green]$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-generic
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Looking at these errors I see there's reference to two different kernels under generic:  3.13.0-43.72 for the image-extra and 3.13.0.43.50 for the linux-image-generic. e.g.
```

...
Unpacking linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-image-generic (3.13.0.43.50) ...

```
Could this be part of the problem?

---

### Post by fantab on 2014-12-21
> Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
 linux-generic-lts-trusty

You'll have to remove the above packages first:
```

sudo dpkg --purge linux-image-3.13.0-43-generic
sudo apt-get remove --purge linux-image-3.13.0-43-generic
sudo dpkg --purge linux-image-extra-3.13.0-43-generic
sudo apt-get remove --purge  linux-image-extra-3.13.0-43-generic
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

Report back the errors, if any, after 'apt-get update' and 'apt-get dist-upgrade'.

---

### Post by mike-g2 on 2014-12-21
Kernels and images purged.  upgrade and dist-upgrade said I had no packages that needed upgrading.

---

### Post by fantab on 2014-12-21
Alright.

```
uname -r
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

With 'uname -r' you will note down the kernel in use.
with the second command you will purge all the kernel on the machine except the one with 'uname -r'.

If there are no errors reported:
```
sudo apt-get update
sudo apt-get install linux
```

---

### Post by mike-g2 on 2014-12-21
> **fantab said:**
> Alright.

```

sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

That's a beautiful command.

I was able to purge all linux-*, but when I try
```

[mike@host Green]$ sudo apt-get install linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux

```
Was it suppsed to be
```

sudo apt-get install linux-*

```?

---

### Post by fantab on 2014-12-21
If I remember correctly 'linux' used to be a metapackage.
Anyway:
```
sudo apt-get install linux-generic linux-headers-generic linux-image-generic
```

Even if you don't run the above, 'Software updater' will find the necessary upgrades soon. Shutdown and restart ubuntu.
You are good.

Post the output of:
```
cat /etc/apt/sources.list
```
to see if all the relevant sources point to 'trusty'.

---

### Post by mike-g2 on 2014-12-22
Unfortunately, even after rebooting and updating the software center I get the same ol' errors
```

[mike@host ~]$ sudo apt-get install linux-generic linux-headers-generic linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.13.0-43 linux-headers-3.13.0-43-generic
  linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic
Suggested packages:
  linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-generic linux-headers-3.13.0-43 linux-headers-3.13.0-43-generic
  linux-headers-generic linux-image-3.13.0-43-generic
  linux-image-extra-3.13.0-43-generic linux-image-generic
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.5 MB of archives.
After this operation, 271 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-3.13.0-43-generic amd64 3.13.0-43.72 [15.1 MB]
Get:2 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-extra-3.13.0-43-generic amd64 3.13.0-43.72 [36.7 MB]
Get:3 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-generic amd64 3.13.0.43.50 [2,788 B]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.13.0-43 all 3.13.0-43.72 [8,907 kB]
Get:5 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.13.0-43-generic amd64 3.13.0-43.72 [731 kB]
Get:6 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-generic amd64 3.13.0.43.50 [2,784 B]
Get:7 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-generic amd64 3.13.0.43.50 [1,780 B]
Fetched 61.5 MB in 1min 54s (537 kB/s)                                         
Selecting previously unselected package linux-image-3.13.0-43-generic.
(Reading database ... 376897 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Selecting previously unselected package linux-image-extra-3.13.0-43-generic.
Preparing to unpack .../linux-image-extra-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Unpacking linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-image-generic (3.13.0.43.50) ...
Selecting previously unselected package linux-headers-3.13.0-43.
Preparing to unpack .../linux-headers-3.13.0-43_3.13.0-43.72_all.deb ...
Unpacking linux-headers-3.13.0-43 (3.13.0-43.72) ...
Selecting previously unselected package linux-headers-3.13.0-43-generic.
Preparing to unpack .../linux-headers-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Unpacking linux-headers-3.13.0-43-generic (3.13.0-43.72) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../linux-headers-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.43.50) ...
Selecting previously unselected package linux-generic.
Preparing to unpack .../linux-generic_3.13.0.43.50_amd64.deb ...
Unpacking linux-generic (3.13.0.43.50) ...
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.13.0-43 (3.13.0-43.72) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Setting up linux-headers-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
Setting up linux-headers-generic (3.13.0.43.50) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have purged the 3.13 kernels and related packages a second time but get the same results.

I'm still confused as to why  running depmod fails.

---

### Post by mike-g2 on 2014-12-22
I have unchecked the standard Canonical repositories for trusty and reactivated the precise ones.  I then tried installing a 3.2 kernel but got essentially the same errors:
```

(synaptic:13151): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
Selecting previously unselected package linux-image-3.2.0-23-generic.
(Reading database ... 372749 files and directories currently installed.)
Preparing to unpack .../linux-image-3.2.0-23-generic_3.2.0-23.36_amd64.deb ...
Done.
Unpacking linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_3.2.0.23.25_amd64.deb ...
Unpacking linux-image-generic (3.2.0.23.25) ...
Selecting previously unselected package linux-image.
Preparing to unpack .../linux-image_3.2.0.23.25_amd64.deb ...
Unpacking linux-image (3.2.0.23.25) ...
Selecting previously unselected package linux.
Preparing to unpack .../linux_3.2.0.23.25_amd64.deb ...
Unpacking linux (3.2.0.23.25) ...
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.2.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-23-generic; however:
  Package linux-image-3.2.0-23-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 3.2.0.23.25); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 3.2.0.23.25); however:
  Package linux-image is not configured yet.

dpkg: error processing package linux (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  Errors were encountered while processing:
 linux-image-3.2.0-23-generic
 linux-image-generic
 linux-image
 linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.2.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-23-generic; however:
  Package linux-image-3.2.0-23-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 3.2.0.23.25); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 3.2.0.23.25); however:
  Package linux-image is not configured yet.

dpkg: error processing package linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-23-generic
 linux-image-generic
 linux-image
 linux

```

Any what files to look at to get more info on why depmod fails?

---

### Post by fantab on 2014-12-22
try:
```
sudo apt-get autoremove
sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update 
sudo apt-get -f install
sudo apt-get dist-upgrade
```

The idea is to remove the packages that are causing the problem and re-installing.

---

### Post by mike-g2 on 2014-12-23
Sorry if I wasn't clear before, but I was able to remove the offending packages, but I can't get the newer (>3.2) kernels to install afterwards.  I get the same errors as before.

For example,  using:
```

sudo apt-get purge linux-generic linux-headers-generic linux-image-generic linux-headers-3.13.0-24* linux-image-3.13* linux-image.extra-3.13*

```
and variants thereof.

Executing
```

[mike@host ~]$ sudo rm /var/lib/apt/lists/* -vf
removed ‘/var/lib/apt/lists/archive.canonical.com_dists_trusty_partner_binary-amd64_Packages’
removed ‘/var/lib/apt/lists/archive.canonical.com_dists_trusty_partner_binary-i386_Packages’
.
.
.
removed ‘/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en’
removed ‘/var/lib/apt/lists/lock’
rm: cannot remove ‘/var/lib/apt/lists/partial’: Is a directory
[mike@host ~]$ sudo rmdir  /var/lib/apt/lists/partial
[mike@host ~]$ sudo apt-get update
Ign http://archive.canonical.com trusty InRelease
Ign http://archive.ubuntu.com trusty InRelease
Get:1 http://archive.canonical.com trusty Release.gpg [933 B]
Get:2 http://archive.ubuntu.com trusty Release.gpg [933 B] 
Get:3 http://archive.canonical.com trusty Release [9,359 B]
.
.
.

Get:15 http://archive.ubuntu.com trusty/universe Translation-en [4,089 kB]     
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US  
Fetched 19.4 MB in 40s (480 kB/s)                                              
Reading package lists... Done
[mike@host ~]$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```
So I interpret this as everything that was causing problems being removed. 

As I mentioned above, if I try to install a new kernel I get the same ol' errors.  For example,

```

[mike@host ~]$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[mikeg@cheoah ~]$ sudo apt-get install linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux
[mike@host ~]$ sudo apt-get install linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-headers-generic linux-image-3.13.0-24-generic
  linux-image-extra-3.13.0-24-generic linux-image-generic
Suggested packages:
  linux-doc-3.13.0 linux-source-3.13.0
The following NEW packages will be installed:
  linux-generic linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-headers-generic linux-image-3.13.0-24-generic
  linux-image-extra-3.13.0-24-generic linux-image-generic
0 upgraded, 7 newly installed, 0 to remove and 1 not upgraded.
Need to get 61.2 MB of archives.
After this operation, 270 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main linux-image-3.13.0-24-generic amd64 3.13.0-24.46 [15.0 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main linux-image-extra-3.13.0-24-generic amd64 3.13.0-24.46 [36.6 MB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty/main linux-image-generic amd64 3.13.0.24.28 [2,326 B]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty/main linux-headers-3.13.0-24 all 3.13.0-24.46 [8,869 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/main linux-headers-3.13.0-24-generic amd64 3.13.0-24.46 [710 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty/main linux-headers-generic amd64 3.13.0.24.28 [2,314 B]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/main linux-generic amd64 3.13.0.24.28 [1,786 B]
Fetched 61.2 MB in 2min 25s (420 kB/s)                                         
Selecting previously unselected package linux-image-3.13.0-24-generic.
(Reading database ... 372835 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-24-generic_3.13.0-24.46_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-24-generic (3.13.0-24.46) ...
Selecting previously unselected package linux-image-extra-3.13.0-24-generic.
Preparing to unpack .../linux-image-extra-3.13.0-24-generic_3.13.0-24.46_amd64.deb ...
Unpacking linux-image-extra-3.13.0-24-generic (3.13.0-24.46) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_3.13.0.24.28_amd64.deb ...
Unpacking linux-image-generic (3.13.0.24.28) ...
Selecting previously unselected package linux-headers-3.13.0-24.
Preparing to unpack .../linux-headers-3.13.0-24_3.13.0-24.46_all.deb ...
Unpacking linux-headers-3.13.0-24 (3.13.0-24.46) ...
Selecting previously unselected package linux-headers-3.13.0-24-generic.
Preparing to unpack .../linux-headers-3.13.0-24-generic_3.13.0-24.46_amd64.deb ...
Unpacking linux-headers-3.13.0-24-generic (3.13.0-24.46) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../linux-headers-generic_3.13.0.24.28_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.24.28) ...
Selecting previously unselected package linux-generic.
Preparing to unpack .../linux-generic_3.13.0.24.28_amd64.deb ...
Unpacking linux-generic (3.13.0.24.28) ...
Setting up linux-image-3.13.0-24-generic (3.13.0-24.46) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.13.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-24-generic:
 linux-image-extra-3.13.0-24-generic depends on linux-image-3.13.0-24-generic; however:
  Package linux-image-3.13.0-24-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-24-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-24-generic; however:
  Package linux-image-3.13.0-24-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-24-generic; however:
  Package linux-image-extra-3.13.0-24-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.13.0-24 (3.13.0-24.46) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Setting up linux-headers-3.13.0-24-generic (3.13.0-24.46) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
Setting up linux-headers-generic (3.13.0.24.28) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.24.28); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.13.0-24-generic
 linux-image-extra-3.13.0-24-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Tomy_St-Aubin on 2014-12-23
I have exactly the same problem...
that's is my result after your proposal... (sorry for my english... it's not very good)


sudo apt-get purge linux-generic linux-headers-generic linux-image-generic linux-headers-3.13.0-24* linux-image-3.13* linux-image.extra-3.13*
[sudo] password for tom: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Note : sélection de linux-headers-3.13.0-29-generic pour l'expression rationnelle « linux-headers-3.13.0-24* »
Note : sélection de linux-headers-3.13.0-27-generic pour l'expression rationnelle « linux-headers-3.13.0-24* »
Note : sélection de linux-headers-3.13.0-24 pour l'expression rationnelle « linux-headers-3.13.0-24* »
Note : sélection de linux-headers-3.13.0-27 pour l'expression rationnelle « linux-headers-3.13.0-24* »
Note : sélection de linux-headers-3.13.0-29 pour l'expression rationnelle « linux-headers-3.13.0-24* »
Note : sélection de linux-headers-3.13.0-27-lowlatency pour l'expression rationnelle « linux-headers-3.13.0-24* »
Note : sélection de linux-headers-3.13.0-24-lowlatency pour l'expression rationnelle « linux-headers-3.13.0-24* »
Note : sélection de linux-headers-3.13.0-24-generic pour l'expression rationnelle « linux-headers-3.13.0-24* »
Note : sélection de linux-headers-3.13.0-29-lowlatency pour l'expression rationnelle « linux-headers-3.13.0-24* »
Note : sélection de linux-image-3.13.0-27-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-36-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.16.0-25-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-41-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-37-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-34-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-43-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-34-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-32-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-41-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-27-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-30-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-43-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-39-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.16.0-26-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-39-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.16.0-28-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-40-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-36-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-37-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.16.0-26-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-33-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-29-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-35-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-30-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-24-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.16.0-28-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-33-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-24-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.16.0-25-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-35-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-40-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-32-lowlatency pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-3.13.0-29-generic pour l'expression rationnelle « linux-image-3.13* »
Note : sélection de linux-image-extra-3.13.0-27-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-36-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-34-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-43-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-32-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-41-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-30-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-39-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.16.0-25-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-37-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-35-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-24-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-33-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.16.0-28-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-40-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.16.0-26-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Note : sélection de linux-image-extra-3.13.0-29-generic pour l'expression rationnelle « linux-image.extra-3.13* »
Package 'linux-headers-3.13.0-24' is not installed, so not removed
Package 'linux-headers-3.13.0-24-generic' is not installed, so not removed
Package 'linux-headers-3.13.0-24-lowlatency' is not installed, so not removed
Package 'linux-headers-3.13.0-27' is not installed, so not removed
Package 'linux-headers-3.13.0-27-generic' is not installed, so not removed
Package 'linux-headers-3.13.0-27-lowlatency' is not installed, so not removed
Package 'linux-headers-3.13.0-29' is not installed, so not removed
Package 'linux-headers-3.13.0-29-generic' is not installed, so not removed
Package 'linux-headers-3.13.0-29-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-24-generic' is not installed, so not removed
Package 'linux-image-3.13.0-24-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-27-generic' is not installed, so not removed
Package 'linux-image-3.13.0-27-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-29-generic' is not installed, so not removed
Package 'linux-image-3.13.0-29-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-30-generic' is not installed, so not removed
Package 'linux-image-3.13.0-30-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-32-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-33-generic' is not installed, so not removed
Package 'linux-image-3.13.0-33-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-34-generic' is not installed, so not removed
Package 'linux-image-3.13.0-34-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-35-generic' is not installed, so not removed
Package 'linux-image-3.13.0-35-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-36-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-37-generic' is not installed, so not removed
Package 'linux-image-3.13.0-37-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-39-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-40-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-41-generic' is not installed, so not removed
Package 'linux-image-3.13.0-41-lowlatency' is not installed, so not removed
Package 'linux-image-3.13.0-43-lowlatency' is not installed, so not removed
Package 'linux-image-3.16.0-25-generic' is not installed, so not removed
Package 'linux-image-3.16.0-25-lowlatency' is not installed, so not removed
Package 'linux-image-3.16.0-26-generic' is not installed, so not removed
Package 'linux-image-3.16.0-26-lowlatency' is not installed, so not removed
Package 'linux-image-3.16.0-28-generic' is not installed, so not removed
Package 'linux-image-3.16.0-28-lowlatency' is not installed, so not removed
Package 'linux-image-extra-3.13.0-24-generic' is not installed, so not removed
Package 'linux-image-extra-3.13.0-27-generic' is not installed, so not removed
Package 'linux-image-extra-3.13.0-29-generic' is not installed, so not removed
Package 'linux-image-extra-3.13.0-30-generic' is not installed, so not removed
Package 'linux-image-extra-3.13.0-33-generic' is not installed, so not removed
Package 'linux-image-extra-3.13.0-34-generic' is not installed, so not removed
Package 'linux-image-extra-3.13.0-35-generic' is not installed, so not removed
Package 'linux-image-extra-3.13.0-37-generic' is not installed, so not removed
Package 'linux-image-extra-3.13.0-41-generic' is not installed, so not removed
Package 'linux-image-extra-3.16.0-25-generic' is not installed, so not removed
Package 'linux-image-extra-3.16.0-26-generic' is not installed, so not removed
Package 'linux-image-extra-3.16.0-28-generic' is not installed, so not removed
Les paquets suivants seront ENLEVÉS :
  linux-generic* linux-headers-3.13.0-36 linux-headers-generic*
  linux-image-3.13.0-32-generic* linux-image-3.13.0-36-generic*
  linux-image-3.13.0-39-generic* linux-image-3.13.0-40-generic*
  linux-image-3.13.0-43-generic* linux-image-extra-3.13.0-32-generic*
  linux-image-extra-3.13.0-36-generic* linux-image-extra-3.13.0-39-generic*
  linux-image-extra-3.13.0-40-generic* linux-image-extra-3.13.0-43-generic*
  linux-image-generic*
0 mis à jour, 0 nouvellement installés, 14 à enlever et 0 non mis à jour.
1 partiellement installés ou enlevés.
Après cette opération, 646 Mo d'espace disque seront libérés.
Souhaitez-vous continuer ? [O/n] o
dpkg : avertissement : le fichier contenant la liste des fichiers du paquet « liburl-dispatcher1:amd64 » étant manquant, il est considéré qu'aucun fichier du paquet n'est actuellement installé
dpkg : avertissement : le fichier contenant la liste des fichiers du paquet « liburi-perl » étant manquant, il est considéré qu'aucun fichier du paquet n'est actuellement installé
dpkg : avertissement : le fichier contenant la liste des fichiers du paquet « libusb-1.0-0:amd64 » étant manquant, il est considéré qu'aucun fichier du paquet n'est actuellement installé
dpkg : avertissement : le fichier contenant la liste des fichiers du paquet « libusbmuxd2 » étant manquant, il est considéré qu'aucun fichier du paquet n'est actuellement installé
dpkg : avertissement : le fichier contenant la liste des fichiers du paquet « libusb-0.1-4:amd64 » étant manquant, il est considéré qu'aucun fichier du paquet n'est actuellement installé
dpkg : avertissement : le fichier contenant la liste des fichiers du paquet « libustr-1.0-1:amd64 » étant manquant, il est considéré qu'aucun fichier du paquet n'est actuellement installé
(Lecture de la base de données... 307174 fichiers et répertoires déjà installés.)
Suppression de linux-headers-3.13.0-36 (3.13.0-36.63) ...
dpkg: error processing package linux-headers-3.13.0-36 (--remove):
 impossible de supprimer « /usr/src/linux-headers-3.13.0-36/arch/blackfin/mach-bf537/boards/Kconfig » de façon sûre.: N'est pas un dossier
Des erreurs ont été rencontrées pendant l'exécution :
 linux-headers-3.13.0-36
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Tomy_St-Aubin on 2014-12-23
i resolve my trouble with this solution: 

sudo rm -fr linux-headers-3.13.0-36

As you adjust the command , replacing the number [FONT=inherit]version [/FONT][FONT=inherit] that corresponds to your header packets that it make trouble.[/FONT]

---

