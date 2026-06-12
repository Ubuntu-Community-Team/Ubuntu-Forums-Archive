---
title: "How to mount samba share?"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by digidrag on 2005-11-08
Hi
before someone says that I have not searched for this topic, I have searched for it.

I have just installed Ubuntu 5.10 on a local machine without internet.
I want to connect/mount the local directory /mnt/myshare to the network share \\Fileserver\myshare

After I tried
"Mount -t smbfs ..." I get
[I]wrong fs type, bad option, bad superblock on //fileserver/share,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
[/I]

So I searched in the forum and got some threads, 
The answer was to install the package smbfs,but

"sudo apt-get install smbfs"
returns
[I]Package smbfs is not available, but referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has not installation candidate
[/I]


So my question is 
**How do I get the package smbfs?**

---

### Post by Arktis on 2005-11-08
Strange... the package 'smbfs' exists for me.  Here is my sources.list

```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 

deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ breezy universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu/ breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe 
```

---

### Post by digidrag on 2005-11-08
Can it be that it loads the package via internet, if it is requested?
I don't have an internet connection...

---

### Post by Arktis on 2005-11-08
Yeah, you probably need to download the package, save it and then transfer it to your computer at home on a disk and install it with dpkg.

---

### Post by digidrag on 2005-11-08
Problem is that i have not found this package in the package list..
Do you have another link I can try to find Ubuntu packages?

---

### Post by Arktis on 2005-11-08
Assuming you have breezy, [here](http://packages.ubuntu.com/breezy/otherosfs/smbfs) is a link to the smbfs package.

---

### Post by digidrag on 2005-11-09
many thanks, will try that

---

