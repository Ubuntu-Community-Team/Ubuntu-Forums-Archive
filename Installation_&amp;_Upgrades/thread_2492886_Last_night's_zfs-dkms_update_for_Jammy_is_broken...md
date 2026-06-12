---
title: "Last night's zfs-dkms update for Jammy is broken..."
date: 2023-11-26
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2023-11-26
If you have ZFS installed on Jammy 22.04, and you see an update for package zfs-dkms 2.1.5-1ubuntu6~22.04.2... Hold off on that update for at least a few days... It seems to be broken.

If you have already and it crashes dpkg on the update, then join this bug as affected (upper left link):
[https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044630](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044630)

It doesn't seem to affect Lunar, Mantic nor DEV Noble. I don't think it will affect Focal, as the kernel series, even for HWE, is below where the cause of the crash is.

I'll update this thread, when it gets resolved.

---

### Post by #&amp;thj^% on 2023-11-26
It happens on Mantic as well.
NOTE: This was a upgrade from jammy to Mantic.

---

### Post by aljames2 on 2023-11-26
```

aljms@b550a-rzn:~$ apt list zfs-dkms
Listing... Done
zfs-dkms/jammy-updates,jammy-security 2.1.5-1ubuntu6~22.04.2 all
N: There is 1 additional version. Please use the '-a' switch to see it

```

I have taken the new update however, I have no crash reports.  My manual root on ZFS install is on Desktop Jammy though, not sure if that is relevant..

I am on Kernel 5.15.0-89-generic.

---

### Post by #&amp;thj^% on 2023-11-27
Tried two more times on install jammy, make it current on updates, ad "sed to Mantic" and failed boots with a updated kernel "6.5.0.13"

Now the proper way would be, Clean install and not upgraded, all is good on Noble:
```
apt show zfs-dkms
Package: zfs-dkms
Version: 2.2.0-0ubuntu3
Priority: extra
Section: universe/kernel
Source: zfs-linux
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ZFS on Linux maintainers <pkg-zfsonlinux-devel@alioth-lists.debian.net>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 18.8 MB
Provides: zfs-modules
Depends: dkms (>> 2.1.1.2-5), file, libc6-dev | libc-dev, lsb-release, python3-distutils | libpython3-stdlib (<< 3.6.4), debconf (>= 0.5) | debconf-2.0, perl:any
Recommends: zfs-zed, zfsutils-linux (>= 2.2.0-0ubuntu3), linux-libc-dev (<< 6.6~), linux-libc-dev (>= 3.10~)
Suggests: debhelper
Breaks: spl-dkms (<< 0.8.0~rc1)
Replaces: spl-dkms
Homepage: https://zfsonlinux.org/
Download-Size: 2,445 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
Description: OpenZFS filesystem kernel modules for Linux
 OpenZFS is a storage platform that encompasses the functionality of
 traditional filesystems and volume managers. It supports data checksums,
 compression, encryption, snapshots, and more.
 .
 This DKMS package includes the SPA, DMU, ZVOL, and ZPL components of
 OpenZFS.


```
I was able to import my rpool back, for my data.
I need to manage a better ZFS back-up or snapshot plan. I do rsnyc for /home and that mostly works. (snapshots on failed boots or even emergency mode is worthless)
```
System:
  Host: me-noble Kernel: 6.5.0-9-generic arch: x86_64 bits: 64 Desktop: Xfce
    v: 4.18.1 Distro: Ubuntu 24.04 (Noble Numbat)
Machine:
  Type: Laptop System: LENOVO product: 20R10010US v: ThinkPad X1 Carbon 7th
    serial: <superuser required>
  Mobo: LENOVO model: 20R10010US v: SDK0J40697 WIN
    serial: <superuser required> UEFI: LENOVO v: N2QET53W(1.47 )
    date: 07/19/2023

```
dkms versions:
```
zfs-dkms | 2.1.2-1ubuntu3         | jammy/universe           | all
 zfs-dkms | 2.1.5-1ubuntu6~22.04.2 | jammy-security/universe  | all
 zfs-dkms | 2.1.5-1ubuntu6~22.04.2 | jammy-updates/universe   | all
 zfs-dkms | 2.1.9-2ubuntu1         | lunar/universe           | all
 zfs-dkms | 2.1.9-2ubuntu1.2       | lunar-security/universe  | all
 zfs-dkms | 2.1.9-2ubuntu1.2       | lunar-updates/universe   | all
 zfs-dkms | 2.2.0~rc3-0ubuntu4     | mantic/universe          | all
 zfs-dkms | 2.2.0-0ubuntu1~23.10   | mantic-proposed/universe | all
 zfs-dkms | 2.2.0-0ubuntu3         | noble/universe           | all

```

---

### Post by #&amp;thj^% on 2023-11-28
Spoke to soon, after 4 successful reboots yesterday all worked.
Today a cold Boot same as before.
NOTE: This is on jammy LVM2/ext4 trying to recover my data
```

sudo update-grub
[sudo] password for me: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found background: /boot/grub_linux_lite.png
Found background image: /boot/grub_linux_lite.png
Found linux image: /boot/vmlinuz-5.15.0-89-generic
Found initrd image: /boot/initrd.img-5.15.0-89-generic
Found linux image: /boot/vmlinuz-5.15.0-82-generic
Found initrd image: /boot/initrd.img-5.15.0-82-generic
Some pools couldn't be imported and will be ignored:
cannot import 'rpool': unsupported version or feature
This pool uses the following feature(s) not supported by this system:
	com.klarasystems:vdev_zaps_v2
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Adding boot menu entry for UEFI Firmware Settings ...
```
And this:
```
The following NEW packages will be installed:
  zfs-dkms
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 2,345 kB of archives.
After this operation, 18.0 MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 zfs-dkms all 2.1.5-1ubuntu6~22.04.2 [2,345 kB]
Fetched 2,345 kB in 3s (707 kB/s)     
Preconfiguring packages ...
Selecting previously unselected package zfs-dkms.
(Reading database ... 470104 files and directories currently installed.)
Preparing to unpack .../zfs-dkms_2.1.5-1ubuntu6~22.04.2_all.deb ...
Unpacking zfs-dkms (2.1.5-1ubuntu6~22.04.2) ...
Setting up zfs-dkms (2.1.5-1ubuntu6~22.04.2) ...
Loading new zfs-2.1.5 DKMS files...
Building for 5.15.0-89-generic
Building initial module for 5.15.0-89-generic
<string>:1: DeprecationWarning: The distutils package is deprecated and slated f
or removal in Python 3.12. Use setuptools or check PEP 632 for potential alterna
tives
<string>:1: DeprecationWarning: The distutils.sysconfig module is deprecated, us
e sysconfig instead
<string>:1: DeprecationWarning: The distutils package is deprecated and slated f
or removal in Python 3.12. Use setuptools or check PEP 632 for potential alterna
tives
<string>:1: DeprecationWarning: The distutils.sysconfig module is deprecated, us
e sysconfig instead
<stdin>:4: DeprecationWarning: The distutils package is deprecated and slated fo
r removal in Python 3.12. Use setuptools or check PEP 632 for potential alternat
ives
<stdin>:4: DeprecationWarning: The distutils.sysconfig module is deprecated, use
 sysconfig instead
<stdin>:3: DeprecationWarning: The distutils package is deprecated and slated fo
r removal in Python 3.12. Use setuptools or check PEP 632 for potential alternat
ives
<stdin>:3: DeprecationWarning: The distutils.sysconfig module is deprecated, use
 sysconfig instead
<stdin>:2: DeprecationWarning: The distutils package is deprecated and slated fo
r removal in Python 3.12. Use setuptools or check PEP 632 for potential alternat
ives
<stdin>:2: DeprecationWarning: The distutils.sysconfig module is deprecated, use
 sysconfig instead
<string>:1: DeprecationWarning: The distutils package is deprecated and slated f
or removal in Python 3.12. Use setuptools or check PEP 632 for potential alterna
tives
<string>:1: DeprecationWarning: The distutils.sysconfig module is deprecated, us
e sysconfig instead
<string>:1: DeprecationWarning: The distutils package is deprecated and slated f
or removal in Python 3.12. Use setuptools or check PEP 632 for potential alterna
tives
<string>:1: DeprecationWarning: The distutils.sysconfig module is deprecated, us
e sysconfig instead
<string>:1: DeprecationWarning: The distutils package is deprecated and slated f
or removal in Python 3.12. Use setuptools or check PEP 632 for potential alterna
tives
<string>:1: DeprecationWarning: The distutils.sysconfig module is deprecated, us
e sysconfig instead

Progress: [ 60%] [##################################........................] 


```
This is off jammy LVM/ext4
```
apt policy zfs-dkms
zfs-dkms:
  Installed: 2.1.5-1ubuntu6~22.04.2
  Candidate: 2.1.5-1ubuntu6~22.04.2
  Version table:
 *** 2.1.5-1ubuntu6~22.04.2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/universe i386 Packages
        100 /var/lib/dpkg/status
     2.1.2-1ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe i386 Packages

```
Now no pools can be imported:
```
sudo zpool import -f rpool
[sudo] password for me: 
This pool uses the following feature(s) not supported by this system:
	com.klarasystems:vdev_zaps_v2
cannot import 'rpool': unsupported version or feature

```
So now 
```
sudo zpool upgrade
This system supports ZFS pool feature flags.

All pools are formatted using feature flags.

Every feature flags pool has all supported and requested features enabled.

```
This is the biggest disadvantage of ZFS - you are completely powerless

---

### Post by MAFoElffen on 2023-11-28
It looks like you can get/set that feature:
```

     
vdev_zaps_v2

    GUID
        com.klarasystems:vdev_zaps_v2
    READ-ONLY COMPATIBLE
        no

    This feature creates a ZAP object for the root vdev.

    This feature becomes active after the next zpool import or zpool reguid. Properties can be retrieved or set on the root vdev using zpool get and zpool set with root as the vdev name which is an alias for root-0.

```
But dang, how to reset that without importing it? Can you temp import it to something using -R /mnt to disable that feature, then export it, to try import it again?

EDIT: I don't have that feature in any of my pools...

---

### Post by #&amp;thj^% on 2023-11-28
> **MAFoElffen said:**
> It looks like you can get/set that feature:
```

     
vdev_zaps_v2

    GUID
        com.klarasystems:vdev_zaps_v2
    READ-ONLY COMPATIBLE
        no

    This feature creates a ZAP object for the root vdev.

    This feature becomes active after the next zpool import or zpool reguid. Properties can be retrieved or set on the root vdev using zpool get and zpool set with root as the vdev name which is an alias for root-0.

```
But dang, how to reset that without importing it? Can you temp import it to something using -R /mnt to disable that feature, then export it, to try import it again?

I noticed that as well but no joy yet here is some history from today:
```
101  sudo zpool import rpool
  103  sudo zpool import rpool/USERDATA/me_0god1o
  104  sudo zpool import rpool/me_0god1o
  105  sudo zpool import rpool 0god1o
  208  sudo zpool import -d
  209  sudo zpool import -d bpool
  212  zpool status
  213  sudo zpool import -d rpool
  251  sudo zpool status
  252  sudo zpool import -d rpool
  275  zpool status
  276  sudo zpool import -d rpool
  277  sudo zpool export -d rpool
  278  sudo zpool export -f rpool
  279  sudo zpool export rpool
  285  sudo zpool import -f rpool
  287  sudo zpool status
  288  sudo zpool import -o readonly=on content-pool
  289  sudo zpool import -o readonly=on content-rpool

```
 It flat hates me today...:lolflag:
Bleeding edge denote bloodshed, it just took mine LOL
```
sudo zpool import  -R /mnt  rpool
[sudo] password for me: 
cannot import 'rpool': pool was previously in use from another system.
Last accessed by me-noble (hostid=cb2d7d) at Mon Nov 27 19:29:00 2023
The pool can be imported, use 'zpool import -f' to import the pool.
*me*&#57520;*~*&#57520;*1*&#57520;*sudo zpool import  -f /mnt  rpool
cannot import '/mnt': no such pool available
*me*&#57520;*~*&#57520;*1*&#57520;*sudo zpool import  -f -R /mnt  rpool
This pool uses the following feature(s) not supported by this system:
	com.klarasystems:vdev_zaps_v2
cannot import 'rpool': unsupported version or feature

```

---

### Post by MAFoElffen on 2023-11-28
<edited>
Sorry. Posted instructions for a ZFS Performance thread in "General", in this thread. Dang. LOL

I have TB's of extra external HDD drives. You don't want to know what "I am thinking about doing". (LMFAO) But i have this laptop static as part of that Bug report. (Which no-one has responded to yet from launchpad itself.)

---

### Post by aljames2 on 2023-11-28
I found this YT video, guy talks about kernel updates breaking zfs-dkms.  Sounds like he monitors kernel changes & tests in a vm before moving to production.  I’m 90% lost listening to him but maybe useful..

[https://m.youtube.com/watch?v=A19XRbN1OG4&pp=ygUIWmZzLWRrbXM%3D](https://m.youtube.com/watch?v=A19XRbN1OG4&pp=ygUIWmZzLWRrbXM%3D)

---

### Post by #&amp;thj^% on 2023-11-28
EDIT: to all my posts above: Took the propose zfs-dkms 
```
 zfs-dkms | 2.2.1-0ubuntu1         | noble-proposed/universe  | all

```
So far this has lasted over 5 reboots, and Two cold boots, one was a 15 min shutdown the next was a 1hour shutdown.
Looking OK so far.
NOTE: Not suggested or Advised, will keep this post current with my findings.

---

