---
title: "Update issue after 14.04 LTS upgrade"
date: 2014-09-29
forum: Installation &amp; Upgrades
---

### Post by Jetze_Mellema on 2014-09-29
Upgraded from 12.04 LTS to 14.04 LTS, something went wrong (not sure what). Now I can no longer update te server. The errors I see:```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
Setting up linux-cloud-tools-common (3.13.0-36.63) ...
start: Job failed to start
invoke-rc.d: initscript hv-kvp-daemon, action "start" failed.
dpkg: error processing package linux-cloud-tools-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-34:
 linux-cloud-tools-3.13.0-34 depends on linux-cloud-tools-common; however:
  Package linux-cloud-tools-common is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-34 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-34-generic:
 linux-cloud-tools-3.13.0-34-generic depends on linux-cloud-tools-3.13.0-34; however:
  Package linux-cloud-tools-3.13.0-34 is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-34-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-36:
 linux-cloud-tools-3.13.0No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                   No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                                            No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                                                                                                           No apport report written because MaxReports is reached already
                                                                                                                                                                                         No apport report written because MaxReports is reached already
          -36 depends on linux-cloud-tools-common; however:
  Package linux-cloud-tools-common is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-36 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-36-generic:
 linux-cloud-tools-3.13.0-36-generic depends on linux-cloud-tools-3.13.0-36; however:
  Package linux-cloud-tools-3.13.0-36 is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-virtual:
 linux-cloud-tools-virtual depends on linux-cloud-tools-3.13.0-36-generic; however:
  Package linux-cloud-tools-3.13.0-36-generic is not configured yet.


dpkg: error processing package linux-cloud-tools-virtual (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hv-kvp-daemon-init:
 hv-kvp-daemon-init depends on linux-cloud-tools-virtual | linux-cloud-tools; however:
  Package linux-cloud-tools-virtual is not configured yet.
  Package linux-cloud-tools is not installed.
  Package linux-cloud-tools-virtual which provides linux-cloud-tools is not configured yet.


dpkg: error processing package hv-kvp-daemon-init (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-cloud-tools-common
 linux-cloud-tools-3.13.0-34
 linux-cloud-tools-3.13.0-34-generic
 linux-cloud-tools-3.13.0-36
 linux-cloud-tools-3.13.0-36-generic
 linux-cloud-tools-virtual
 hv-kvp-daemon-init
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

I am not very experience with Linux troubleshooting so I really could use some help to find what is causing this.

---

### Post by ibjsb4 on 2014-09-29
I do not run linux-cloud, but you could also try:
```
sudo dpkg --configure -a
```
**--configure** _package_...|**-a**|**--pending**               Configure  a  package  which  has  been  unpacked  but  not  yet               configured.  If **-a** or **--pending** is given instead of _package_, all               unpacked but unconfigured packages are configured.
[http://manpages.ubuntu.com/manpages/trusty/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/dpkg.1.html)
and
```
sudo apt-get -f install
```
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Jetze_Mellema on 2014-09-30
Thanks for your answer. Both commands do not fix the issue, the output is similar to what I copied in my startpost.

---

### Post by ibjsb4 on 2014-09-30
And your running the right kernel

```
uname -r
```

---

### Post by Jetze_Mellema on 2014-09-30
3.13.0-36-generic

---

### Post by Bashing-om on 2014-09-30
Jetze_Mellema; Hi !

I do not know what is actually going on, as:
> 
 apt-cache show linux-cloud-tools
N: Can't select versions from package 'linux-cloud-tools' as it is purely virtual
N: No packages found

But, we can at least try a direct application of the 'configure' command and see what results, maybe get some additional info .
```

sudo dpkg-reconfigure linux-cloud-tools-3.13.0-34

```

[INDENT][INDENT]just a nudge along the path
[/INDENT][/INDENT]

---

### Post by Jetze_Mellema on 2014-10-01
Thanks, appreciate it! Unfortunately this didn't work:
/usr/sbin/dpkg-reconfigure: linux-cloud-tools-3.13.0-34 is broken or not fully installed

---

### Post by Bashing-om on 2014-10-01
Jetze_Mellema; Well !

Let's take the package manager's hint:
> 
/usr/sbin/dpkg-reconfigure: linux-cloud-tools-3.13.0-34 is broken or [color=red]not fully installed[/color]

And see what results if we (re-)install it.
```

sudo apt-get install linux-cloud-tools-3.13.0-34

```
Keeping in mind we are working to resolve this :
> 
Package linux-cloud-tools-common is not configured yet.


So ->
[INDENT][INDENT][INDENT]a work in progress
[/INDENT][/INDENT][/INDENT]

---

### Post by Fernando_Nunes on 2014-10-16
Hey guys, I'm having the same exact issue, and also on Ubuntu 14.04.1 LTS but with latest kernel (3.13.0-37-generic). It started on the package update to latest kernel, and stuck ever since, for now I removed all related packages ! Here is the list:
hv-kvp-daemon-init
linux-cloud-tools-3.13.0-37 linux-cloud-tools-3.13.0-37-generic linux-cloud-tools-common linux-cloud-tools-virtual
walinuxagent

---

### Post by Bashing-om on 2014-10-16
Fernando_Nunes; Hi ! Welcome to the forum .

The basis of all things; " what does the package manager think ?: ->
So, lets see what the package manager thinks.

Post pack - between code tags - the output of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C 

``` and let's see
[INDENT][INDENT][INDENT]what tale gets told
[/INDENT][/INDENT][/INDENT]

---

### Post by Jetze_Mellema on 2014-11-19
Thank you!
```
myuser@server:~$ sudo apt-get updateIgn http://security.ubuntu.com trusty-security InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://security.ubuntu.com trusty-security Release [62.0 kB]
Get:3 http://security.ubuntu.com trusty-security/main Sources [49.5 kB]
Get:4 http://security.ubuntu.com trusty-security/universe Sources [13.5 kB]
Get:5 http://security.ubuntu.com trusty-security/main amd64 Packages [153 kB]
Get:6 http://security.ubuntu.com trusty-security/universe amd64 Packages [61.7 kB]
Get:7 http://security.ubuntu.com trusty-security/main i386 Packages [147 kB]
Get:8 http://security.ubuntu.com trusty-security/universe i386 Packages [61.7 kB]
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://azure.archive.ubuntu.com trusty InRelease
Ign http://azure.archive.ubuntu.com trusty-updates InRelease
Hit http://azure.archive.ubuntu.com trusty Release.gpg
Hit http://azure.archive.ubuntu.com trusty-updates Release.gpg
Hit http://azure.archive.ubuntu.com trusty Release
Hit http://azure.archive.ubuntu.com trusty-updates Release
Hit http://azure.archive.ubuntu.com trusty/main Sources
Hit http://azure.archive.ubuntu.com trusty/universe Sources
Hit http://azure.archive.ubuntu.com trusty/main amd64 Packages
Hit http://azure.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://azure.archive.ubuntu.com trusty/main i386 Packages
Hit http://azure.archive.ubuntu.com trusty/universe i386 Packages
Hit http://azure.archive.ubuntu.com trusty/main Translation-en
Hit http://azure.archive.ubuntu.com trusty/universe Translation-en
Hit http://azure.archive.ubuntu.com trusty-updates/main Sources
Hit http://azure.archive.ubuntu.com trusty-updates/universe Sources
Hit http://azure.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://azure.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://azure.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://azure.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://azure.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://azure.archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://azure.archive.ubuntu.com trusty/main Translation-en_US
Ign http://azure.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 549 kB in 15s (35.4 kB/s)
Reading package lists... Done
myuser@server:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-cloud-tools-virtual linux-headers-generic linux-headers-virtual
  linux-image-extra-virtual linux-image-generic linux-image-virtual
  linux-virtual
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-cloud-tools-common (3.13.0-39.66) ...
start: Job failed to start
invoke-rc.d: initscript hv-kvp-daemon, action "start" failed.
dpkg: error processing package linux-cloud-tools-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-34:
 linux-cloud-tools-3.13.0-34 depends on linux-cloud-tools-common; however:
  Package linux-cloud-tools-common is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-34 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-36:
 linux-cloud-tools-3.13.0-36 depends on linux-cloud-tools-common; however:
  Package linux-cloud-tools-common is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-36 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-36-generic:
 linux-cloud-tools-3.13.0-36-generic depends onNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                         No apport report written because the error message indicates its a followup error from a previous failure.
                   No apport report written because MaxReports is reached already
 No apport report written because MaxReports is reached already
                                                               No apport report written because MaxReports is reached already
                                              linux-cloud-tools-3.13.0-36; however:
  Package linux-cloud-tools-3.13.0-36 is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-virtual:
 linux-cloud-tools-virtual depends on linux-cloud-tools-3.13.0-36-generic; however:
  Package linux-cloud-tools-3.13.0-36-generic is not configured yet.


dpkg: error processing package linux-cloud-tools-virtual (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hv-kvp-daemon-init:
 hv-kvp-daemon-init depends on linux-cloud-tools-virtual | linux-cloud-tools; however:
  Package linux-cloud-tools-virtual is not configured yet.
  Package linux-cloud-tools is not installed.
  Package linux-cloud-tools-virtual which provides linux-cloud-tools is not configured yet.


dpkg: error processing package hv-kvp-daemon-init (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-cloud-tools-common
 linux-cloud-tools-3.13.0-34
 linux-cloud-tools-3.13.0-36
 linux-cloud-tools-3.13.0-36-generic
 linux-cloud-tools-virtual
 hv-kvp-daemon-init
E: Sub-process /usr/bin/dpkg returned an error code (1)
myuser@server:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-cloud-tools-common (3.13.0-39.66) ...
start: Job failed to start
invoke-rc.d: initscript hv-kvp-daemon, action "start" failed.
dpkg: error processing package linux-cloud-tools-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-34:
 linux-cloud-tools-3.13.0-34 depends on linux-cloud-tools-common; however:
  Package linux-cloud-tools-common is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-34 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-36:
 linux-cloud-tools-3.13.0-36 depends on linux-cloud-tools-common; however:
  Package linux-cloud-tools-common is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-36 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-36-generic:
 linux-cloud-tools-3.13.0-36-generic depends on linux-cloud-tools-3.13.0-36; however:
  Package linux-cloud-tools-3.13.0-36 is not configured yet.


dpkg: error processing package linux-cloud-tools-3.13.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-clNo apport report written because the error message indicates its a followup error from a previous failure.
     No apport report written because the error message indicates its a followup error from a previous failure.
                               No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         oud-tools-virtual:
 linux-cloud-tools-virtual depends on linux-cloud-tools-3.13.0-36-generic; however:
  Package linux-cloud-tools-3.13.0-36-generic is not configured yet.


dpkg: error processing package linux-cloud-tools-virtual (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hv-kvp-daemon-init:
 hv-kvp-daemon-init depends on linux-cloud-tools-virtual | linux-cloud-tools; however:
  Package linux-cloud-tools-virtual is not configured yet.
  Package linux-cloud-tools is not installed.
  Package linux-cloud-tools-virtual which provides linux-cloud-tools is not configured yet.


dpkg: error processing package hv-kvp-daemon-init (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-cloud-tools-common
 linux-cloud-tools-3.13.0-34
 linux-cloud-tools-3.13.0-36
 linux-cloud-tools-3.13.0-36-generic
 linux-cloud-tools-virtual
 hv-kvp-daemon-init
E: Sub-process /usr/bin/dpkg returned an error code (1)
myuser@server:~$ sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-cloud-tools-3.13.0-36-generic Linux kernel version specific cloud tools
 linux-cloud-tools-virtual This package will always depend on the latest minima
 linux-cloud-tools-3.13.0-36 Linux kernel version specific cloud tools for vers
 linux-cloud-tools-3.13.0-34 Linux kernel version specific cloud tools for vers
 hv-kvp-daemon-init   Transitional Package for Hyper-V tools


The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-cloud-tools-common Linux kernel version specific cloud tools for version


The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 module-init-tools    transitional dummy package (module-init-tools to kmod)
 libjson0:amd64       JSON manipulation library (transitional package)


myuser@server:~$

```

---

### Post by Bashing-om on 2014-11-19
Jetze_Mellema; Welp ;

Did you install "cloud" from an alternate source ?
I see:
> 
dpkg: error processing package linux-cloud-tools-3.13.0-34 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-cloud-tools-3.13.0-36:
 linux-cloud-tools-3.13.0-36 depends on linux-cloud-tools-common; however:
  Package linux-cloud-tools-common is not configured yet.


Two different versions, conflicting.
What are we working with ? Please show:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Try and see what it will take to remove and then install the proper version for your system.

I show:
> 
sysop@1404mini:~$ apt-cache search linux-cloud-tools-3.13.0-36
linux-cloud-tools-3.13.0-36 - Linux kernel version specific cloud tools for version 3.13.0-36
linux-cloud-tools-3.13.0-36-generic - Linux kernel version specific cloud tools for version 3.13.0-36
linux-cloud-tools-3.13.0-36-lowlatency - Linux kernel version specific cloud tools for version 3.13.0-36
sysop@1404mini:~$
-bk-

Version: 3.13.0-36.63
Depends: libc6 (>= 2.14), linux-cloud-tools-common
Filename: pool/main/l/linux/linux-cloud-tools-3.13.0-36_3.13.0-36.63_amd64.deb

the correct version for release 14.04 .

[INDENT][INDENT]small steps, but[/INDENT][/INDENT]
[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by Jetze_Mellema on 2014-11-19
Thanks for your help, I really appreciate it!

Did not use another source to update or upgrade the server, although the package was already in my pre-configured Azure virtual machine. I did not build this server from scratch.

```
~$ cat -n /etc/apt/sources.list     1  ## Note, this file is written by cloud-init on first boot of an instance
     2  ## modifications made here will not survive a re-bundle.
     3  ## if you wish to make changes you can:
     4  ## a.) add 'apt_preserve_sources_list: true' to /etc/cloud/cloud.cfg
     5  ##     or do the same in user-data
     6  ## b.) add sources in /etc/apt/sources.list.d
     7  ## c.) make changes to template file /etc/cloud/templates/sources.list.tmpl
     8  #
     9
    10  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    11  # newer versions of the distribution.
    12  deb http://azure.archive.ubuntu.com/ubuntu trusty main
    13  deb-src http://azure.archive.ubuntu.com/ubuntu trusty main
    14
    15  ## Major bug fix updates produced after the final release of the
    16  ## distribution.
    17  deb http://azure.archive.ubuntu.com/ubuntu trusty-updates main
    18  deb-src http://azure.archive.ubuntu.com/ubuntu trusty-updates main
    19
    20  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    21  ## team. Also, please note that software in universe WILL NOT receive any
    22  ## review or updates from the Ubuntu security team.
    23  deb http://azure.archive.ubuntu.com/ubuntu trusty universe
    24  deb-src http://azure.archive.ubuntu.com/ubuntu trusty universe
    25  deb http://azure.archive.ubuntu.com/ubuntu trusty-updates universe
    26  deb-src http://azure.archive.ubuntu.com/ubuntu trusty-updates universe
    27
    28  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    29  ## team, and may not be under a free licence. Please satisfy yourself as to
    30  ## your rights to use the software. Also, please note that software in
    31  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    32  ## security team.
    33  # deb http://azure.archive.ubuntu.com/ubuntu precise multiverse
    34  # deb-src http://azure.archive.ubuntu.com/ubuntu precise multiverse
    35  # deb http://azure.archive.ubuntu.com/ubuntu precise-updates multiverse
    36  # deb-src http://azure.archive.ubuntu.com/ubuntu precise-updates multiverse
    37
    38  ## Uncomment the following two lines to add software from the 'backports'
    39  ## repository.
    40  ## N.B. software from this repository may not have been tested as
    41  ## extensively as that contained in the main release, although it includes
    42  ## newer versions of some applications which may provide useful features.
    43  ## Also, please note that software in backports WILL NOT receive any review
    44  ## or updates from the Ubuntu security team.
    45  # deb http://azure.archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    46  # deb-src http://azure.archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    47
    48  ## Uncomment the following two lines to add software from Canonical's
    49  ## 'partner' repository.
    50  ## This software is not part of Ubuntu, but is offered by Canonical and the
    51  ## respective vendors as a service to Ubuntu users.
    52  # deb http://archive.canonical.com/ubuntu precise partner
    53  # deb-src http://archive.canonical.com/ubuntu precise partner
    54
    55  deb http://security.ubuntu.com/ubuntu trusty-security main
    56  deb-src http://security.ubuntu.com/ubuntu trusty-security main
    57  deb http://security.ubuntu.com/ubuntu trusty-security universe
    58  deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    59  # deb http://security.ubuntu.com/ubuntu precise-security multiverse
    60  # deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

```
The /etc/apt/sources.list.d/ on my server is empty.
> **Bashing-om said:**
> Jetze_Mellema; Welp ;

Try and see what it will take to remove and then install the proper version for your system.

I'm sorry, but can you please provide detailed steps? I'm not a Linux guy and this whole troubleshooting process is a bit overwhelming.

---

### Post by Bashing-om on 2014-11-19
Jetze_Mellema; Humm ..

Looks good to me; Let's try:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
Becuase we have this:
> 
The following packages have been kept back:

only
Then if the package manager is still screaming and hollering, let's try :
```

sudo apt-get purge linux-cloud-tools-common
sudo apt-get purge linux-cloud-tools-3.13.0-34
sudo apt-get install linux-cloud-tools-common
sudo aptget install --reinstall linux-cloud-tools-3.13.0-36

```

[INDENT][INDENT]maybe then YES
[/INDENT][/INDENT]

---

### Post by Jetze_Mellema on 2014-11-21
sudo apt-get purge linux-cloud-tools-3.13.0-34 said something about it not being installed so can't remove it. And sudo apt-get install linux-cloud-tools-common gave this:
```
[COLOR=#222222][FONT=Verdana]Reading package lists... Done[/FONT][/COLOR]Building dependency tree
Reading state information... Done
Package 'linux-cloud-tools-3.13.0-34' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
azureuser@qftest:/data/backup$ sudo apt-get install linux-cloud-tools-common
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  linux-cloud-tools-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/43.0 kB of archives.
After this operation, 221 kB of additional disk space will be used.
Selecting previously unselected package linux-cloud-tools-common.
(Reading database ... 149994 files and directories currently installed.)
Preparing to unpack .../linux-cloud-tools-common_3.13.0-39.66_all.deb ...
Unpacking linux-cloud-tools-common (3.13.0-39.66) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up linux-cloud-tools-common (3.13.0-39.66) ...
start: Job failed to start
invoke-rc.d: initscript hv-kvp-daemon, action "start" failed.
dpkg: error processing package linux-cloud-tools-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 linux-cloud-tools-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I guess we're back where we started, aren't we?

---

### Post by Bashing-om on 2014-11-21
Jetze_Mellema; Welp;

3 steps forward and but one back.
My think'n;
If that package resides on the system - and it is corrupted:
```

ls -al /var/cache/apt/archives/linux-cloud-tools-common

```
Let's try and "remove" it and download it once more.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

