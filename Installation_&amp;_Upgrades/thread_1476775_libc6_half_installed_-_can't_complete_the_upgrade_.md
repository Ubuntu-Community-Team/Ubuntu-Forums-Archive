---
title: "libc6 half installed - can't complete the upgrade to lucid"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by jlord87 on 2010-05-08
Hi guys,

yesterday I've decided to upgrade ubuntu from hardy to lucid on my poweredge server.

unfortunately, I've found an error that I'm not able to solve:

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc-bin: Breaks: libc6 (< 2.10) but 2.7-10ubuntu5 is installed
  libc-dev-bin: Depends: libc6 (> 2.11) but 2.7-10ubuntu5 is installed
                Recommends: manpages-dev but it is not installed
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7) but 2.7-10ubuntu5 is installed
  libc6-i386: Depends: libc6 (= 2.11.1-0ubuntu7) but 2.7-10ubuntu5 is installed
  locales: Depends: libc6 (>= 2.9-0ubuntu10) but 2.7-10ubuntu5 is installed or
                    libc6.1 (>= 2.9-0ubuntu10) but it is not installable
E: Unmet dependencies. Try using -f.
``````
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 324 not upgraded.
5 not fully installed or removed.
Need to get 0B/4,249kB of archives.
After this operation, 1,167kB disk space will be freed.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 54185 files and directories currently installed.)
Preparing to replace libc6 2.7-10ubuntu5 (using .../libc6_2.11.1-0ubuntu7_amd64.deb) ...
Died at /usr/sbin/update-rc.d line 57.
dpkg: error processing /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```This is the dpkg log:

```
2010-05-07 21:53:16 startup archives unpack
2010-05-07 21:53:16 upgrade libc6 2.7-10ubuntu5 2.11.1-0ubuntu7
2010-05-07 21:53:16 status half-installed libc6 2.7-10ubuntu5
2010-05-07 21:53:16 status half-installed libc6 2.7-10ubuntu5
```Does anybody have an idea on how to fix this problem?

thanks a lot

---

### Post by P4man on 2010-05-08
I seem to recall someone with a similar problem that was caused by using a mirror not having all files (or not all up to date). Wouldnt hurt changing your apt mirror and running ```
dpkg --configure -a
```

---

### Post by tommcd on 2010-05-08
> **jlord87 said:**
> Does anybody have an idea on how to fix this problem?

The first part of the error is suggesting a possible solution:
```
You might want to run `apt-get -f install' to correct these.

```
So try:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade

```
and see if that fixes it. 

And welcome to the Ubuntu forums!

---

### Post by jlord87 on 2010-05-08
> **P4man said:**
> I seem to recall someone with a similar problem that was caused by using a mirror not having all files (or not all up to date). Wouldnt hurt changing your apt mirror and running ```
dpkg --configure -a
```

I've used apt-cacher...
but updating the repository doesn't solve the problem...

I've also tryied to configure manually the package (using dpkg --configure -a) but it doesn't work:

```
$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.11.1-0ubuntu7); however:
  Package libc6 is not installed.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc-dev-bin:
 libc-dev-bin depends on libc6 (>> 2.11); however:
  Package libc6 is not installed.
 libc-dev-bin depends on libc6 (<< 2.12); however:
  Package libc6 is not installed.
dpkg: error processing libc-dev-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.11.1-0ubuntu7); however:
  Package libc6 is not installed.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on libc6 (>= 2.9-0ubuntu10) | libc6.1 (>= 2.9-0ubuntu10); however:
  Package libc6 is not installed.
  Package libc6.1 is not installed.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglib2.0-0:
 libglib2.0-0 depends on libc6 (>= 2.9); however:
  Package libc6 is not installed.
 libglib2.0-0 depends on libpcre3 (>= 7.7); however:
  Version of libpcre3 on system is 7.4-1ubuntu2.1.
dpkg: error processing libglib2.0-0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
 libc-dev-bin
 libc6-i386
 locales
 libglib2.0-0

```

> **tommcd said:**
> The first part of the error is suggesting a  possible solution:
```
You might want to run `apt-get -f install' to correct these.

```So try:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade

```and see if that fixes it. 

And welcome to the Ubuntu forums!

as you can see in my first post, apt-get install -f doesn't work...

anyway, thanks for the reply :)

---

### Post by tommcd on 2010-05-08
> 
as you can see in my first post, apt-get install -f doesn't work...

Sorry, I missed that in your first post.
It seems that /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_amd64.deb may be corrupt.
Try renaming that file to: libc6_2.11.1-0ubuntu7_amd64.deb.bak
And then try to update and upgrade.

---

### Post by jlord87 on 2010-05-08
> **tommcd said:**
> Sorry, I missed that in your first post.
It seems that /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_amd64.deb may be corrupt.
Try renaming that file to: libc6_2.11.1-0ubuntu7_amd64.deb.bak
And then try to update and upgrade.

uff, no way...

```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libpcre3
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libpcre3
2 upgraded, 0 newly installed, 0 to remove and 322 not upgraded.
6 not fully installed or removed.
Need to get 4,249kB/4,465kB of archives.
After this operation, 1,114kB disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 http://it.archive.ubuntu.com/ubuntu/ lucid/main libc6 2.11.1-0ubuntu7 [4,249kB]
Fetched 4,249kB in 31s (135kB/s)                                               
Preconfiguring packages ...
(Reading database ... 54187 files and directories currently installed.)
Preparing to replace libc6 2.7-10ubuntu5 (using .../libc6_2.11.1-0ubuntu7_amd64.deb) ...
Died at /usr/sbin/update-rc.d line 57.
dpkg: error processing /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```if I try to install only that package with dpkg I'll get

```
$ sudo dpkg -i libc6_2.11.1-0ubuntu7_amd64.deb 
(Reading database ... 54187 files and directories currently installed.)
Preparing to replace libc6 2.7-10ubuntu5 (using libc6_2.11.1-0ubuntu7_amd64.deb) ...
Died at /usr/sbin/update-rc.d line 57.
dpkg: error processing libc6_2.11.1-0ubuntu7_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 libc6_2.11.1-0ubuntu7_amd64.deb
```the package was not corrupted:
```
$ md5sum libc6_2.11.1-0ubuntu7_amd64.deb
6e66c70ab7c8804b19264ebc1213c64c  libc6_2.11.1-0ubuntu7_amd64.deb
$ md5sum libc6_2.11.1-0ubuntu7_amd64.deb_backup 
6e66c70ab7c8804b19264ebc1213c64c  libc6_2.11.1-0ubuntu7_amd64.deb_backup

```At the moment I'm running the lucid kernel.
```
Linux r900 2.6.32-22-server #33-Ubuntu SMP Wed Apr 28 14:34:48 UTC 2010 x86_64 GNU/Linux
```May this be a problem?
Does rebooting the system with the old one have any sense to you?

---

### Post by tommcd on 2010-05-09
At this point it couldn't hurt to try an earlier kernel.
I don't think it will help to solve this dependency mess though.

I am about out of ideas on what else to try. Have you tried updating and upgrading using a different mirror?
Since you have verified that the libc6 package in question is not corrupt, this may be of little benefit.
If it were me, at this point I would consider doing a clean install of Ubuntu 10.04. Obviously this will mean taking your server off line for the time of the reinstall, so you will have to weigh the pros and cons of this for your situation.

---

### Post by mcframe on 2010-07-24
Just for the records in case someone should stumble about this error like I did some hours ago.

It turned out that this error message ```
Died at /usr/sbin/update-rc.d line 57
``` show up when the directory ```
/var/lib/update-rc.d
``` is missing.

To solve just 
```
sudo mkdir /var/lib/update-rc.d
sudo apt-get install -f 
```
and restart the update process.

:p

---

