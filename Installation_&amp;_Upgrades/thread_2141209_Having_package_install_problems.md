---
title: "Having package install problems"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by jb0nez on 2013-05-02
I have a slightly complicated setup, let me explain first. I have an ssd I gave 10gb to linux. My hdd has an old 120GB linux partition. So I boot from the ssd and have home and tmp etc on there, but I bind mount as  much of the hard drive as I can so that programs gets installed there (ala Steam). I was running 12.10, saw that there was a new release, did do-release-upgrade, everything succeeded but on reboot mount couldn't find libraries. So I changed my fstab to not bind mount anything, did a new install of 13.04 onto the ssd without formatting. Then I remounted my bound dirs, everything was working fine, could run my old and new apps. Then I went to set it up so I could use my Nexus 7 via file manager. I went and added a ppa and installed some packages, mtpfs I think and one more. Problem is they were for 12.10.
Here's my fstab at the moment:
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=0b115957-998c-492f-83f0-2f0bc0cdd62a /               ext4    errors=remount-ro 0       1
# /mnt/linux was on /dev/sdb5 during installation
UUID=c165c7b3-f5aa-4379-94c8-9fb25830909e /mnt/linux      ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=6de58d89-f303-4f63-8784-76748f960e20 none            swap    sw              0       0
##RAMDISK##
none /tmp tmpfs defaults 0 0
#my bind mounts
/mnt/linux/bin /bin none bind 0 0
/mnt/linux/usr /usr none bind 0 0 
/mnt/linux/opt /opt none bind 0 0
/mnt/linux/var /var none bind 0 0
#/mnt/linux/lib32 /lib32 none bind 0 0
#/mnt/linux/lib64 /lib64 none bind 0 0
#/mnt/linux/lib /lib none bind 0 0



```
I used to have the last 3 uncommented but couldn't boot, something about libc6 again. So commented those out, not much will install there anyway, and was able to boot.

Anyway when I installed the mtpfs files I guess they replaced a lib with an earlier version cause all hell broke loose. Unbootable system, mountall would say bad file descriptors. I fixed that by linking some libraries and also not bind mounting /lib. Also gave my linux partition 5gb more via gparted, extending to the left, which it warned might cause boot problems. It did, using a live cd I got through everything, made use of boot-repair.

So that's many hours of work but I'm booting ok, and I figured since I'd had /usr and /lib etc bind mounted when I first upgraded to 13.04, then when I installed 13.04 completely on the SSD, I figured all libraries should be up to date - 13.04 was on the SSD and HDD. 
Anyway after I installed those mtpfs programs I can't do ANYtHING in package manager/synaptic. I have two broken packages on my system per synaptic: libc6-i386 and libudev1. I mark them for reinstallation and it wants to upgrade "libc6" and "libc6:i386" and re-install "libc6-i386" and "libudev1". I hit apply and get this:
E: Internal Error, No file name for libudev1:amd64
I think my libraries are messed up - synaptic says libc6  is version 2.15-0ubuntu20.1 but will be upgraded to version 2.17-0ubuntu5. I'm pretty sure raring needs 2.17.

Ok next, at the command line, I can't apt-get anything. 
sudo apt-get -f install:
```
justin@justin-FX6831:/lib/i386-linux-gnu$ sudo apt-get -f install
[sudo] password for justin: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
justin@justin-FX6831:/lib/i386-linux-gnu$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  dh-apparmor html2text libavahi-client-dev libavahi-common-dev libgnutls-openssl27 libgnutlsxx27 libgpg-error-dev libgssrpc4 libieee1284-3-dev libjbig-dev libjpeg62 libjs-jquery libkadm5clnt-mit8
  libkadm5srv-mit8 libkdb5-6 libltdl-dev liblzma-dev libmail-sendmail-perl libp11-kit-dev libsensors4-dev libsnmp-perl libssl-doc libsys-hostname-long-perl libtasn1-3-dev libtiffxx5 libv4l-dev libwrap0-dev
  libxml-parser-perl python-scour
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6 libc6:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 0 newly installed, 0 to remove and 1229 not upgraded.
11 not fully installed or removed.
Need to get 0 B/8,784 kB of archives.
After this operation, 110 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 141140 files and directories currently installed.)
Preparing to replace libc6:amd64 2.15-0ubuntu20.1 (using .../libc6_2.17-0ubuntu5_amd64.deb) ...
De-configuring libc6:i386 ...
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...done.




A copy of the C library was found in an unexpected directory:
  '/lib/x86_64-linux-gnu/libc-2.17.so'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/x86_64-linux-gnu' and try again.


dpkg: error processing /var/cache/apt/archives/libc6_2.17-0ubuntu5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Preparing to replace libc6:i386 2.15-0ubuntu20.1 (using .../libc6_2.17-0ubuntu5_i386.deb) ...
De-configuring libc6:amd64 ...
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...done.




A copy of the C library was found in an unexpected directory:
  '/lib/i386-linux-gnu/libc-2.17.so'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/i386-linux-gnu' and try again.


dpkg: error processing /var/cache/apt/archives/libc6_2.17-0ubuntu5_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.17-0ubuntu5_amd64.deb
 /var/cache/apt/archives/libc6_2.17-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I get that error about the C library when I try to do ANYTHING with apt-get. I've done clean, remove, autoclean, etc, and yet somehow anytime I try to install a package I'll get the error about dependencies on that C library. Once I removed that library by mv'ing like it said and I suddenly couldn't even ls or sudo. Obviously an important library. 

Output of "sudo apt-get autoremove"
```
justin@justin-FX6831:/lib/i386-linux-gnu$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6-i386 : Depends: libc6 (= 2.17-0ubuntu5) but 2.15-0ubuntu20.1 is installed
 libudev1 : Depends: libc6 (>= 2.17) but 2.15-0ubuntu20.1 is installed
E: Unmet dependencies. Try using -f.


```

Here's some directory listing showing I'm already USING libc6 2.17:
```
ustin@justin-FX6831:/var/cache/apt/archives$ ls -l /lib/x86_64-linux-gnu/libc*-rwxr-xr-x 1 root root 1848024 Apr 18 01:21 /lib/x86_64-linux-gnu/libc-2.17.so
lrwxrwxrwx 1 root root      14 Jan 18 11:50 /lib/x86_64-linux-gnu/libcap.so.2 -> libcap.so.2.22
-rw-r--r-- 1 root root   18952 Jan 18 11:50 /lib/x86_64-linux-gnu/libcap.so.2.22
-rw-r--r-- 1 root root  194968 Apr 18 01:21 /lib/x86_64-linux-gnu/libcidn-2.17.so
lrwxrwxrwx 1 root root      15 Apr 30 21:02 /lib/x86_64-linux-gnu/libcidn.so.1 -> libcidn-2.17.so
lrwxrwxrwx 1 root root      17 Apr 30 21:02 /lib/x86_64-linux-gnu/libcom_err.so.2 -> libcom_err.so.2.1
-rw-r--r-- 1 root root   14592 Jan  2 01:26 /lib/x86_64-linux-gnu/libcom_err.so.2.1
-rw-r--r-- 1 root root   43368 Apr 18 01:21 /lib/x86_64-linux-gnu/libcrypt-2.17.so
-rw-r--r-- 1 root root 1930656 Mar 19 09:13 /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
lrwxrwxrwx 1 root root      16 Apr 30 21:02 /lib/x86_64-linux-gnu/libcrypt.so.1 -> libcrypt-2.17.so
lrwxrwxrwx 1 root root      12 Apr 30 21:02 /lib/x86_64-linux-gnu/libc.so.6 -> libc-2.17.so
justin@justin-FX6831:/var/cache/apt/archives$ cd /lib/x86_64-linux-gnu/
justin@justin-FX6831:/lib/x86_64-linux-gnu$ ls -l libc-2.17.so 
-rwxr-xr-x 1 root root 1848024 Apr 18 01:21 libc-2.17.so
justin@justin-FX6831:/lib/x86_64-linux-gnu$ ls -l libc.so.6 
lrwxrwxrwx 1 root root 12 Apr 30 21:02 libc.so.6 -> libc-2.17.so
justin@justin-FX6831:/lib/x86_64-linux-gnu$ 

```

But check this out:
```
justin@justin-FX6831:~$ dpkg -l libc6Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                           Version                      Architecture                 Description
+++-==============================================-============================-============================-=================================================================================================
ii  libc6:amd64                                    2.15-0ubuntu20.1             amd64                        Embedded GNU C Library: Shared libraries
ii  libc6:i386                                     2.15-0ubuntu20.1             i386                         Embedded GNU C Library: Shared libraries
justin@justin-FX6831:~$ 



```
I'm using the newest llbc6 but dpkg thinks I still  have the old 2.15 installed. And since 2.17 is a dependency for just about everything, apt-get ALWAYS wants to download and install it. But I can't even install 2.17 due to that error:
```
justin@justin-FX6831:/var/cache/apt/archives$ sudo dpkg -i *deb(Reading database ... 141140 files and directories currently installed.)
Preparing to replace libc6:amd64 2.15-0ubuntu20.1 (using libc6_2.17-0ubuntu5_amd64.deb) ...
De-configuring libc6:i386 ...
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...done.




A copy of the C library was found in an unexpected directory:
  '/lib/x86_64-linux-gnu/libc-2.17.so'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/x86_64-linux-gnu' and try again.


dpkg: error processing libc6_2.17-0ubuntu5_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libc6:i386 2.15-0ubuntu20.1 (using libc6_2.17-0ubuntu5_i386.deb) ...
De-configuring libc6:amd64 ...
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...done.




A copy of the C library was found in an unexpected directory:
  '/lib/i386-linux-gnu/libc-2.17.so'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/i386-linux-gnu' and try again.


dpkg: error processing libc6_2.17-0ubuntu5_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 libc6_2.17-0ubuntu5_amd64.deb
 libc6_2.17-0ubuntu5_i386.deb
justin@justin-FX6831:/var/cache/apt/archives$ 

```

tl;dr - I get that same error above about libc not being safe to upgrade when I try to do ANYTHING with apt-get. Blocking me from installing anything. So what do I do at this point to fix my apt-get/dpkg?

---

### Post by jb0nez on 2013-05-02
This has become a nightmare, I figured if I installed 13.04 off a CD onto the HDD /dev/sdb5, that would ensure all libs and mounts of it are consistent with a raring system. didn't format, but that doesn't seem to matter as  the installer destroyed all installed packages anyway. Now I see why people make a separate partition for /var and /opt. On first reboot lightdm bombed out leaving me in text mode. Went to my home dir and installed catalyst 13,4, Rebooted but no error messages, just went straight to a text login prompt, did sudo startx and KDE started fine.

Also tried booting off the SSD, Not even an error message, nothing on the screen but a blinking cursor. So now I'm reinstalling (again) onto the SSD, then I'll setup my bind mountpoints, and see if the lib versions all match so I can use apt-get.  Then the hours long process of resinstalling all my software, getting dropbox configured to not use my home dir, getting netflix working again, etc etc
The lesson I separate partitions for  /var and /opt. The reason I like just one big / is so I don't have to constantly resize partitions as my needs change, let everything share the same space pool. But I see that partitioning might let me do OS upgrades without losing everything. Will have to google a partition scheme that lets me do that. Also will remove bind points before I ever do-release-upgrade again, then boot to hard drive and do-release-upgrade there.

Here's hoping KDE starts on the SSD. All bind mounts are gone for now. At least (knocking on wood) my Win 7 partition is still functional after all this.  
 
count so far: OS reinstalls 3, do-release-upgrade 1. Hours wasted: at least ten.

---

