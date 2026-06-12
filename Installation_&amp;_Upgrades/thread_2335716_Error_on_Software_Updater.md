---
title: "Error on Software Updater"
date: 2016-08-31
forum: Installation &amp; Upgrades
---

### Post by scpatl4now on 2016-08-31
I am getting a broken package error when trying to do software update. When I tried to fix I got this

```
Reading package lists... Done 
W: There is no public key available for the following key IDs:
1397BC53640DB551
scott@Gscott-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.13.0-96-generic; however:
  Package linux-headers-3.13.0-96-generic is not installed.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic

```

How do I fix this?
(previous command was sudo apt-get update)

---

### Post by scpatl4now on 2016-08-31
More info...when I go to pkg manager I get

```
(synaptic:11993): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 1687082 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-96_3.13.0-96.143_all.deb ...
Unpacking linux-headers-3.13.0-96 (3.13.0-96.143) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-96_3.13.0-96.143_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-96/arch/x86/Makefile.um.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-96/arch/x86/Makefile.um'): No space left on device
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-headers-3.13.0-96-generic_3.13.0-96.143_amd64.deb ...
Unpacking linux-headers-3.13.0-96-generic (3.13.0-96.143) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-96-generic_3.13.0-96.143_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-96-generic/include/config/radio/saa7706h.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-96-generic/include/config/radio/saa7706h.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-96_3.13.0-96.143_all.deb
 /var/cache/apt/archives/linux-headers-3.13.0-96-generic_3.13.0-96.143_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.13.0-96-generic; however:
  Package linux-headers-3.13.0-96-generic is not installed.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic


```

It spits out this error

```
E: /var/cache/apt/archives/linux-headers-3.13.0-96_3.13.0-96.143_all.deb: unable to create `/usr/src/linux-headers-3.13.0-96/arch/ia64/uv/kernel/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-96/arch/ia64/uv/kernel/Makefile'): No space left on device
E: /var/cache/apt/archives/linux-headers-3.13.0-96-generic_3.13.0-96.143_amd64.deb: unable to create `/usr/src/linux-headers-3.13.0-96-generic/include/config/radio/maxiradio.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-96-generic/include/config/radio/maxiradio.h'): No space left on device

```

df gives me

```
scott@Gscott-desktop:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1979908        12   1979896   1% /dev
tmpfs             404736      2072    402664   1% /run
/dev/sda8       26875956  17019292   8468376  67% /
none                   4         0         4   0% /sys/fs/cgroup
none                5120         0      5120   0% /run/lock
none             2023668       672   2022996   1% /run/shm
none              102400        68    102332   1% /run/user
/dev/sdb1      244197340 174538736  69658604  72% /media/BigOlE
/dev/sda1       50910876  12612780  35688896  27% /home
```



I have plenty of space

---

### Post by howefield on 2016-08-31
The first error can be fixed with..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1397BC53640DB551
```

For the second, try this see if it makes some space, although it'll likely take more to fix.
 
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```

---

### Post by Impavidus on 2016-08-31
In addition to running out of disk space, you may also run out of inodes (=slots in the index table of the partition). It may give the same error message. To check, run```
df -i
```

---

### Post by scpatl4now on 2016-08-31
This was the result...still getting the error


```
scott@Gscott-desktop:~$ sudo apt-get clean
scott@Gscott-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.13.0-96-generic but it is not installed
E: Unmet dependencies. Try using -f.
scott@Gscott-desktop:~$ sudo apt-get autoremove -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.13.0-96 linux-headers-3.13.0-96-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-96 linux-headers-3.13.0-96-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 9,562 kB of archives.
After this operation, 76.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main linux-headers-3.13.0-96 all 3.13.0-96.143 [8,865 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main linux-headers-3.13.0-96-generic amd64 3.13.0-96.143 [698 kB]
Fetched 9,562 kB in 6s (1,574 kB/s)                                            
(Reading database ... 1687082 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-96_3.13.0-96.143_all.deb ...
Unpacking linux-headers-3.13.0-96 (3.13.0-96.143) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-96_3.13.0-96.143_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-96/arch/x86/include/asm/io_apic.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-96/arch/x86/include/asm/io_apic.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-headers-3.13.0-96-generic_3.13.0-96.143_amd64.deb ...
Unpacking linux-headers-3.13.0-96-generic (3.13.0-96.143) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-96-generic_3.13.0-96.143_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-96-generic/include/config/megaraid/mailbox.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-96-generic/include/config/megaraid/mailbox.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-96_3.13.0-96.143_all.deb
 /var/cache/apt/archives/linux-headers-3.13.0-96-generic_3.13.0-96.143_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by scpatl4now on 2016-08-31
Ok...how do I fix this?

```
scott@Gscott-desktop:~$ df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             494977     566   494411    1% /dev
tmpfs            505917     657   505260    1% /run
/dev/sda8       1716960 1713061     3899  100% /
none             505917       2   505915    1% /sys/fs/cgroup
none             505917       3   505914    1% /run/lock
none             505917       9   505908    1% /run/shm
none             505917      33   505884    1% /run/user
/dev/sdb1      69756908   77931 69678977    1% /media/BigOlE
/dev/sda1       3244032   76981  3167051    3% /home

```

---

### Post by scpatl4now on 2016-08-31
Ok...so I am out of inodes...
how do I fix this.  The are probably lots of small files hiding somewhere...but how do I locate the ones to remove?

---

### Post by scpatl4now on 2016-08-31
the problem seems to be in /usr folder (it was over 789,000 and counting...I am still at a loss over what to do...anyone?

---

### Post by howefield on 2016-09-01
Good call Impavidus, 

I'd have a look at papibes post here

[https://ubuntuforums.org/showthread.php?t=2325064&page=3&p=13492477&viewfull=1#post13492477](https://ubuntuforums.org/showthread.php?t=2325064&page=3&p=13492477&viewfull=1#post13492477)

---

