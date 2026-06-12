---
title: "Cannot update 12.04"
date: 2015-08-18
forum: Installation &amp; Upgrades
---

### Post by vs-ruthless on 2015-08-18
Hi,

I've been running a 12.04 VPS server for a few years now with no major issue until today, for some reason I cannot update packages via webmin or update the server via apt-get. 

I'm getting the following error message: 

```
The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 3.2.0.88.102) but 3.2.0.89.103 is to be installed
 linux-image-generic : Depends: linux-image-3.2.0-88-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

What I've tried so far.

sudo apt-get -f install and I've also rm some old kernals as purge is not working either (updated grub)

Hopefully this is something simple?

Ruthless

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; Hello;

I will start this ball rolling.

As you did:
> 
 and I've also rm some old kernals as purge is not working either


Will not be so simple. Going behind the package manager's back is UNgood.

Let's take a look at what we are working with to get an idea of what we are going to do .

Do we have operating head room ?
What returns:
```

df -h
df -i

```

Now what is installed for the kernels and support ?
```

dpkg -l | grep linux-
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```

What kernel are you booting presently ?
```

uname -r
ls -al /vmlin*
ls -al /initrd*

```

[INDENT][INDENT][INDENT]clearing the deck
[INDENT][INDENT][INDENT]for action[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-18
Hi Bashing-om,

**Do we have operating head room ?**
```

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda3        49G   13G   34G  27% /
udev            490M  4.0K  490M   1% /dev
tmpfs           100M  256K  100M   1% /run
none            5.0M     0  5.0M   0% /run/lock
tmpfs           498M  4.0K  498M   1% /run/shm
/dev/vda1       461M  433M  4.8M  99% /boot

df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/vda3      3219456 945397 2274059   30% /
udev            125236    396  124840    1% /dev
tmpfs           127434    300  127134    1% /run
none            127434      2  127432    1% /run/lock
tmpfs           127434      2  127432    1% /run/shm
/dev/vda1       121920    318  121602    1% /boot

```

[B]Now what is installed for the kernels and support ?
[/B]```
dpkg -l | grep linux-
ii  linux-firmware                  1.79.18                               Firmware for Linux kernel drivers
iU  linux-generic                   3.2.0.88.102                          Complete Generic Linux kernel
ii  linux-headers-3.2.0-32          3.2.0-32.51                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-32-generic  3.2.0-32.51                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-34          3.2.0-34.53                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-34-generic  3.2.0-34.53                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-35          3.2.0-35.55                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-35-generic  3.2.0-35.55                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-36          3.2.0-36.57                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-36-generic  3.2.0-36.57                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-38          3.2.0-38.61                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-38-generic  3.2.0-38.61                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-39          3.2.0-39.62                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-39-generic  3.2.0-39.62                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-40          3.2.0-40.64                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-40-generic  3.2.0-40.64                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-44          3.2.0-44.69                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-44-generic  3.2.0-44.69                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-48          3.2.0-48.74                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-48-generic  3.2.0-48.74                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-52          3.2.0-52.78                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-52-generic  3.2.0-52.78                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-53          3.2.0-53.81                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-53-generic  3.2.0-53.81                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-54          3.2.0-54.82                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-54-generic  3.2.0-54.82                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-56          3.2.0-56.86                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-56-generic  3.2.0-56.86                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-57          3.2.0-57.87                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-57-generic  3.2.0-57.87                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-58          3.2.0-58.88                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-58-generic  3.2.0-58.88                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-59          3.2.0-59.90                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-59-generic  3.2.0-59.90                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-60          3.2.0-60.91                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-60-generic  3.2.0-60.91                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-63          3.2.0-63.95                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-63-generic  3.2.0-63.95                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-65          3.2.0-65.99                           Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-65-generic  3.2.0-65.99                           Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-67          3.2.0-67.101                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-67-generic  3.2.0-67.101                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-68          3.2.0-68.102                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-68-generic  3.2.0-68.102                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-69          3.2.0-69.103                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-69-generic  3.2.0-69.103                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-70          3.2.0-70.105                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-70-generic  3.2.0-70.105                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-75          3.2.0-75.110                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-75-generic  3.2.0-75.110                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-77          3.2.0-77.114                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-77-generic  3.2.0-77.114                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-79          3.2.0-79.115                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-79-generic  3.2.0-79.115                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-83          3.2.0-83.120                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-83-generic  3.2.0-83.120                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-88          3.2.0-88.126                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-88-generic  3.2.0-88.126                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-3.2.0-89          3.2.0-89.127                          Header files related to Linux kernel versio                                                n 3.2.0
ii  linux-headers-3.2.0-89-generic  3.2.0-89.127                          Linux kernel headers for version 3.2.0 on 6                                                4 bit x86 SMP
ii  linux-headers-generic           3.2.0.89.103                          Generic Linux kernel headers
ii  linux-image-3.2.0-31-generic    3.2.0-31.50                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-32-generic    3.2.0-32.51                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-34-generic    3.2.0-34.53                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-35-generic    3.2.0-35.55                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-36-generic    3.2.0-36.57                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-38-generic    3.2.0-38.61                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-39-generic    3.2.0-39.62                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-40-generic    3.2.0-40.64                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-44-generic    3.2.0-44.69                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-48-generic    3.2.0-48.74                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-52-generic    3.2.0-52.78                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-53-generic    3.2.0-53.81                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-54-generic    3.2.0-54.82                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-56-generic    3.2.0-56.86                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-57-generic    3.2.0-57.87                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-58-generic    3.2.0-58.88                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-59-generic    3.2.0-59.90                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-60-generic    3.2.0-60.91                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-63-generic    3.2.0-63.95                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-65-generic    3.2.0-65.99                           Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-67-generic    3.2.0-67.101                          Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-68-generic    3.2.0-68.102                          Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-69-generic    3.2.0-69.103                          Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-70-generic    3.2.0-70.105                          Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-75-generic    3.2.0-75.110                          Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-77-generic    3.2.0-77.114                          Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-79-generic    3.2.0-79.115                          Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-83-generic    3.2.0-83.120                          Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
ii  linux-image-3.2.0-89-generic    3.2.0-89.127                          Linux kernel image for version 3.2.0 on 64                                                 bit x86 SMP
iU  linux-image-generic             3.2.0.88.102                          Generic Linux kernel image
ii  linux-libc-dev                  3.2.0-87.125                          Linux Kernel Headers for development

ls -al /usr/src/
total 240
drwxr-xr-x 60 root root 4096 Aug 17 22:45 .
drwxr-xr-x 10 root root 4096 Sep 30  2012 ..
drwxr-xr-x 24 root root 4096 Oct 19  2012 linux-headers-3.2.0-32
drwxr-xr-x  7 root root 4096 Oct 19  2012 linux-headers-3.2.0-32-generic
drwxr-xr-x 24 root root 4096 Dec  7  2012 linux-headers-3.2.0-34
drwxr-xr-x  7 root root 4096 Dec  7  2012 linux-headers-3.2.0-34-generic
drwxr-xr-x 24 root root 4096 Jan  9  2013 linux-headers-3.2.0-35
drwxr-xr-x  7 root root 4096 Jan  9  2013 linux-headers-3.2.0-35-generic
drwxr-xr-x 24 root root 4096 Jan 28  2013 linux-headers-3.2.0-36
drwxr-xr-x  7 root root 4096 Jan 28  2013 linux-headers-3.2.0-36-generic
drwxr-xr-x 24 root root 4096 Feb 24  2013 linux-headers-3.2.0-38
drwxr-xr-x  7 root root 4096 Feb 24  2013 linux-headers-3.2.0-38-generic
drwxr-xr-x 24 root root 4096 Mar 24  2013 linux-headers-3.2.0-39
drwxr-xr-x  7 root root 4096 Mar 24  2013 linux-headers-3.2.0-39-generic
drwxr-xr-x 24 root root 4096 Apr 14  2013 linux-headers-3.2.0-40
drwxr-xr-x  7 root root 4096 Apr 14  2013 linux-headers-3.2.0-40-generic
drwxr-xr-x 24 root root 4096 May 30  2013 linux-headers-3.2.0-44
drwxr-xr-x  7 root root 4096 May 30  2013 linux-headers-3.2.0-44-generic
drwxr-xr-x 24 root root 4096 Jun 25  2013 linux-headers-3.2.0-48
drwxr-xr-x  7 root root 4096 Jun 25  2013 linux-headers-3.2.0-48-generic
drwxr-xr-x 24 root root 4096 Aug 22  2013 linux-headers-3.2.0-52
drwxr-xr-x  7 root root 4096 Aug 22  2013 linux-headers-3.2.0-52-generic
drwxr-xr-x 24 root root 4096 Sep 16  2013 linux-headers-3.2.0-53
drwxr-xr-x  7 root root 4096 Sep 16  2013 linux-headers-3.2.0-53-generic
drwxr-xr-x 24 root root 4096 Oct 19  2013 linux-headers-3.2.0-54
drwxr-xr-x  7 root root 4096 Oct 19  2013 linux-headers-3.2.0-54-generic
drwxr-xr-x 24 root root 4096 Nov 10  2013 linux-headers-3.2.0-56
drwxr-xr-x  7 root root 4096 Nov 10  2013 linux-headers-3.2.0-56-generic
drwxr-xr-x 24 root root 4096 Dec 24  2013 linux-headers-3.2.0-57
drwxr-xr-x  7 root root 4096 Dec 24  2013 linux-headers-3.2.0-57-generic
drwxr-xr-x 24 root root 4096 Jan 18  2014 linux-headers-3.2.0-58
drwxr-xr-x  7 root root 4096 Jan 18  2014 linux-headers-3.2.0-58-generic
drwxr-xr-x 24 root root 4096 Feb 28  2014 linux-headers-3.2.0-59
drwxr-xr-x  7 root root 4096 Feb 28  2014 linux-headers-3.2.0-59-generic
drwxr-xr-x 24 root root 4096 Mar 15  2014 linux-headers-3.2.0-60
drwxr-xr-x  7 root root 4096 Mar 15  2014 linux-headers-3.2.0-60-generic
drwxr-xr-x 24 root root 4096 Jun  2  2014 linux-headers-3.2.0-63
drwxr-xr-x  7 root root 4096 Jun  2  2014 linux-headers-3.2.0-63-generic
drwxr-xr-x 24 root root 4096 Aug 27  2014 linux-headers-3.2.0-65
drwxr-xr-x  7 root root 4096 Aug 27  2014 linux-headers-3.2.0-65-generic
drwxr-xr-x 24 root root 4096 Aug  2  2014 linux-headers-3.2.0-67
drwxr-xr-x  7 root root 4096 Aug  2  2014 linux-headers-3.2.0-67-generic
drwxr-xr-x 24 root root 4096 Sep 15  2014 linux-headers-3.2.0-68
drwxr-xr-x  7 root root 4096 Sep 15  2014 linux-headers-3.2.0-68-generic
drwxr-xr-x 24 root root 4096 Sep 27  2014 linux-headers-3.2.0-69
drwxr-xr-x  7 root root 4096 Sep 27  2014 linux-headers-3.2.0-69-generic
drwxr-xr-x 24 root root 4096 Nov 16  2014 linux-headers-3.2.0-70
drwxr-xr-x  7 root root 4096 Nov 16  2014 linux-headers-3.2.0-70-generic
drwxr-xr-x 24 root root 4096 Jan 28  2015 linux-headers-3.2.0-75
drwxr-xr-x  7 root root 4096 Jan 28  2015 linux-headers-3.2.0-75-generic
drwxr-xr-x 24 root root 4096 Mar 24 22:32 linux-headers-3.2.0-77
drwxr-xr-x  7 root root 4096 Mar 24 22:32 linux-headers-3.2.0-77-generic
drwxr-xr-x 24 root root 4096 Mar 24 22:31 linux-headers-3.2.0-79
drwxr-xr-x  7 root root 4096 Mar 24 22:31 linux-headers-3.2.0-79-generic
drwxr-xr-x 24 root root 4096 May 12 20:11 linux-headers-3.2.0-83
drwxr-xr-x  7 root root 4096 May 12 20:11 linux-headers-3.2.0-83-generic
drwxr-xr-x 24 root root 4096 Jul 27 18:10 linux-headers-3.2.0-88
drwxr-xr-x  7 root root 4096 Jul 27 18:10 linux-headers-3.2.0-88-generic
drwxr-xr-x 24 root root 4096 Aug 17 22:45 linux-headers-3.2.0-89
drwxr-xr-x  7 root root 4096 Aug 17 22:45 linux-headers-3.2.0-89-generic

ls -al /etc/modules/
ls: cannot access /etc/modules/: Not a directory

ls -al /boot/
total 428328
drwxr-xr-x  4 root root     8192 Aug 18 19:07 .
drwxr-xr-x 24 root root     4096 Aug 18 19:07 ..
-rw-r--r--  1 root root   795365 Jul 26  2013 abi-3.2.0-52-generic
-rw-r--r--  1 root root   795539 Aug 22  2013 abi-3.2.0-53-generic
-rw-r--r--  1 root root   795539 Sep 10  2013 abi-3.2.0-54-generic
-rw-r--r--  1 root root   795686 Oct 23  2013 abi-3.2.0-56-generic
-rw-r--r--  1 root root   795751 Nov 12  2013 abi-3.2.0-57-generic
-rw-r--r--  1 root root   795751 Dec  3  2013 abi-3.2.0-58-generic
-rw-r--r--  1 root root   795751 Jan  7  2014 abi-3.2.0-59-generic
-rw-r--r--  1 root root   795743 Feb 19  2014 abi-3.2.0-60-generic
-rw-r--r--  1 root root   795911 May 16  2014 abi-3.2.0-63-generic
-rw-r--r--  1 root root   795911 Jul  4  2014 abi-3.2.0-65-generic
-rw-r--r--  1 root root   795963 Jul 15  2014 abi-3.2.0-67-generic
-rw-r--r--  1 root root   795963 Aug 12  2014 abi-3.2.0-68-generic
-rw-r--r--  1 root root   795963 Sep  2  2014 abi-3.2.0-69-generic
-rw-r--r--  1 root root   796014 Sep 24  2014 abi-3.2.0-70-generic
-rw-r--r--  1 root root   796535 Dec 16  2014 abi-3.2.0-75-generic
-rw-r--r--  1 root root   796597 Mar 10 17:50 abi-3.2.0-77-generic
-rw-r--r--  1 root root   796660 Mar 12 14:57 abi-3.2.0-79-generic
-rw-r--r--  1 root root   796660 Apr 29 17:01 abi-3.2.0-83-generic
-rw-r--r--  1 root root   796660 Jul 28 11:24 abi-3.2.0-89-generic
-rw-r--r--  1 root root   140629 Jul 26  2013 config-3.2.0-52-generic
-rw-r--r--  1 root root   140629 Aug 22  2013 config-3.2.0-53-generic
-rw-r--r--  1 root root   140629 Sep 10  2013 config-3.2.0-54-generic
-rw-r--r--  1 root root   140629 Oct 23  2013 config-3.2.0-56-generic
-rw-r--r--  1 root root   140629 Nov 12  2013 config-3.2.0-57-generic
-rw-r--r--  1 root root   140629 Dec  3  2013 config-3.2.0-58-generic
-rw-r--r--  1 root root   140629 Jan  7  2014 config-3.2.0-59-generic
-rw-r--r--  1 root root   140612 Feb 19  2014 config-3.2.0-60-generic
-rw-r--r--  1 root root   140640 May 16  2014 config-3.2.0-63-generic
-rw-r--r--  1 root root   140640 Jul  4  2014 config-3.2.0-65-generic
-rw-r--r--  1 root root   140641 Jul 15  2014 config-3.2.0-67-generic
-rw-r--r--  1 root root   140675 Aug 12  2014 config-3.2.0-68-generic
-rw-r--r--  1 root root   140675 Sep  2  2014 config-3.2.0-69-generic
-rw-r--r--  1 root root   140705 Sep 24  2014 config-3.2.0-70-generic
-rw-r--r--  1 root root   140790 Dec 16  2014 config-3.2.0-75-generic
-rw-r--r--  1 root root   140790 Mar 10 17:50 config-3.2.0-77-generic
-rw-r--r--  1 root root   140790 Mar 12 14:57 config-3.2.0-79-generic
-rw-r--r--  1 root root   140790 Apr 29 17:01 config-3.2.0-83-generic
-rw-r--r--  1 root root   140790 Jul 28 11:24 config-3.2.0-89-generic
drwxr-xr-x  3 root root     7168 Aug 18 19:10 grub
-rw-r--r--  1 root root 14247121 Aug 22  2013 initrd.img-3.2.0-52-generic
-rw-r--r--  1 root root 14248664 Sep 16  2013 initrd.img-3.2.0-53-generic
-rw-r--r--  1 root root 14248505 Oct 19  2013 initrd.img-3.2.0-54-generic
-rw-r--r--  1 root root 14249585 Nov 10  2013 initrd.img-3.2.0-56-generic
-rw-r--r--  1 root root 14250547 Dec 24  2013 initrd.img-3.2.0-57-generic
-rw-r--r--  1 root root 14249884 Jan 18  2014 initrd.img-3.2.0-58-generic
-rw-r--r--  1 root root 14249621 Feb 28  2014 initrd.img-3.2.0-59-generic
-rw-r--r--  1 root root 14250828 Apr  6  2014 initrd.img-3.2.0-60-generic
-rw-r--r--  1 root root 14251460 Jun  2  2014 initrd.img-3.2.0-63-generic
-rw-r--r--  1 root root 14235453 Aug 27  2014 initrd.img-3.2.0-65-generic
-rw-r--r--  1 root root 14234550 Aug 27  2014 initrd.img-3.2.0-67-generic
-rw-r--r--  1 root root 14233683 Sep 15  2014 initrd.img-3.2.0-68-generic
-rw-r--r--  1 root root 14234420 Sep 27  2014 initrd.img-3.2.0-69-generic
-rw-r--r--  1 root root 14234429 Nov 16  2014 initrd.img-3.2.0-70-generic
-rw-r--r--  1 root root 14233928 Feb 22 09:32 initrd.img-3.2.0-75-generic
-rw-r--r--  1 root root 14233938 Mar 24 22:32 initrd.img-3.2.0-77-generic
-rw-r--r--  1 root root 14233374 Mar 24 22:31 initrd.img-3.2.0-79-generic
-rw-r--r--  1 root root 14236253 May 12 20:11 initrd.img-3.2.0-83-generic
-rw-r--r--  1 root root 14235101 Aug 18 19:07 initrd.img-3.2.0-89-generic
drwx------  2 root root    12288 Sep 30  2012 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2893555 Jul 26  2013 System.map-3.2.0-52-generic
-rw-------  1 root root  2894361 Aug 22  2013 System.map-3.2.0-53-generic
-rw-------  1 root root  2894535 Sep 10  2013 System.map-3.2.0-54-generic
-rw-------  1 root root  2895053 Oct 23  2013 System.map-3.2.0-56-generic
-rw-------  1 root root  2895166 Nov 12  2013 System.map-3.2.0-57-generic
-rw-------  1 root root  2895308 Dec  3  2013 System.map-3.2.0-58-generic
-rw-------  1 root root  2895419 Jan  7  2014 System.map-3.2.0-59-generic
-rw-------  1 root root  2895229 Feb 19  2014 System.map-3.2.0-60-generic
-rw-------  1 root root  2896164 May 16  2014 System.map-3.2.0-63-generic
-rw-------  1 root root  2896866 Jul  4  2014 System.map-3.2.0-65-generic
-rw-------  1 root root  2896997 Jul 15  2014 System.map-3.2.0-67-generic
-rw-------  1 root root  2897193 Aug 12  2014 System.map-3.2.0-68-generic
-rw-------  1 root root  2897193 Sep  2  2014 System.map-3.2.0-69-generic
-rw-------  1 root root  2897281 Sep 24  2014 System.map-3.2.0-70-generic
-rw-------  1 root root  2898003 Dec 16  2014 System.map-3.2.0-75-generic
-rw-------  1 root root  2898503 Mar 10 17:50 System.map-3.2.0-77-generic
-rw-------  1 root root  2899324 Mar 12 14:57 System.map-3.2.0-79-generic
-rw-------  1 root root  2899357 Apr 29 17:01 System.map-3.2.0-83-generic
-rw-------  1 root root  2899603 Jul 28 11:24 System.map-3.2.0-89-generic
-rw-------  1 root root  4978224 Jul 26  2013 vmlinuz-3.2.0-52-generic
-rw-------  1 root root  4980336 Aug 22  2013 vmlinuz-3.2.0-53-generic
-rw-------  1 root root  4980272 Sep 10  2013 vmlinuz-3.2.0-54-generic
-rw-------  1 root root  4980752 Oct 23  2013 vmlinuz-3.2.0-56-generic
-rw-------  1 root root  4981040 Nov 12  2013 vmlinuz-3.2.0-57-generic
-rw-------  1 root root  4983216 Dec  3  2013 vmlinuz-3.2.0-58-generic
-rw-------  1 root root  4983888 Jan  7  2014 vmlinuz-3.2.0-59-generic
-rw-------  1 root root  4981616 Feb 19  2014 vmlinuz-3.2.0-60-generic
-rw-------  1 root root  4985488 May 16  2014 vmlinuz-3.2.0-63-generic
-rw-------  1 root root  4987152 Jul  4  2014 vmlinuz-3.2.0-65-generic
-rw-------  1 root root  4986960 Jul 15  2014 vmlinuz-3.2.0-67-generic
-rw-------  1 root root  4988144 Aug 12  2014 vmlinuz-3.2.0-68-generic
-rw-------  1 root root  4988176 Sep  2  2014 vmlinuz-3.2.0-69-generic
-rw-------  1 root root  4988848 Sep 24  2014 vmlinuz-3.2.0-70-generic
-rw-------  1 root root  4991088 Dec 16  2014 vmlinuz-3.2.0-75-generic
-rw-------  1 root root  4991152 Mar 10 17:50 vmlinuz-3.2.0-77-generic
-rw-------  1 root root  4991568 Mar 12 14:57 vmlinuz-3.2.0-79-generic
-rw-------  1 root root  4991856 Apr 29 17:01 vmlinuz-3.2.0-83-generic
-rw-------  1 root root  4994544 Jul 28 11:24 vmlinuz-3.2.0-89-generic

```

**What kernel are you booting presently ?**
```

uname -r
3.2.0-89-generic
ls -al /vmlin*
lrwxrwxrwx 1 root root 29 Aug 18 19:07 /vmlinuz -> boot/vmlinuz-3.2.0-89-generic
lrwxrwxrwx 1 root root 29 May 12 20:11 /vmlinuz.old -> boot/vmlinuz-3.2.0-83-generic
ls -al /initrd*
lrwxrwxrwx 1 root root 33 Aug 18 19:07 /initrd.img -> /boot/initrd.img-3.2.0-89-generic
lrwxrwxrwx 1 root root 33 May 12 20:11 /initrd.img.old -> /boot/initrd.img-3.2.0-83-generic

```

Here you go.

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; Hey !

We do have the root cause identified:
> 
/dev/vda1       461M  433M  4.8M  99% /boot

as the /boot partition full and no operating head room .
The solution to. as you know, remove the old kernels .
I do require a bit more info to make sure we have all our ducks in a row. I made an error "ls -al /etc/modules/
ls: cannot access /etc/modules/: Not a directory" ; A true statement - I had my mind set to a incorrect directory. Correct the path to the requested info to be:
```

ls -al /lib/modules/

```

We can do this
[INDENT][INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-18
```

ls -al /lib/modules/
total 128
drwxr-xr-x 32 root root 4096 Aug 17 22:45 .
drwxr-xr-x 20 root root 4096 Jul 11 19:37 ..
drwxr-xr-x  4 root root 4096 Nov  2  2012 3.2.0-31-generic
drwxr-xr-x  4 root root 4096 Oct 19  2012 3.2.0-32-generic
drwxr-xr-x  4 root root 4096 Dec  7  2012 3.2.0-34-generic
drwxr-xr-x  4 root root 4096 Jan  9  2013 3.2.0-35-generic
drwxr-xr-x  4 root root 4096 Jan 28  2013 3.2.0-36-generic
drwxr-xr-x  4 root root 4096 Feb 24  2013 3.2.0-38-generic
drwxr-xr-x  4 root root 4096 Mar 24  2013 3.2.0-39-generic
drwxr-xr-x  4 root root 4096 Apr 14  2013 3.2.0-40-generic
drwxr-xr-x  4 root root 4096 May 30  2013 3.2.0-44-generic
drwxr-xr-x  4 root root 4096 Jun 25  2013 3.2.0-48-generic
drwxr-xr-x  4 root root 4096 Aug 22  2013 3.2.0-52-generic
drwxr-xr-x  4 root root 4096 Sep 16  2013 3.2.0-53-generic
drwxr-xr-x  4 root root 4096 Oct 19  2013 3.2.0-54-generic
drwxr-xr-x  4 root root 4096 Nov 10  2013 3.2.0-56-generic
drwxr-xr-x  4 root root 4096 Dec 24  2013 3.2.0-57-generic
drwxr-xr-x  4 root root 4096 Jan 18  2014 3.2.0-58-generic
drwxr-xr-x  4 root root 4096 Feb 28  2014 3.2.0-59-generic
drwxr-xr-x  4 root root 4096 Mar 15  2014 3.2.0-60-generic
drwxr-xr-x  4 root root 4096 Jun  2  2014 3.2.0-63-generic
drwxr-xr-x  4 root root 4096 Aug 27  2014 3.2.0-65-generic
drwxr-xr-x  4 root root 4096 Aug 27  2014 3.2.0-67-generic
drwxr-xr-x  4 root root 4096 Sep 15  2014 3.2.0-68-generic
drwxr-xr-x  4 root root 4096 Sep 27  2014 3.2.0-69-generic
drwxr-xr-x  4 root root 4096 Nov 16  2014 3.2.0-70-generic
drwxr-xr-x  4 root root 4096 Jan 28  2015 3.2.0-75-generic
drwxr-xr-x  4 root root 4096 Mar 24 22:32 3.2.0-77-generic
drwxr-xr-x  4 root root 4096 Mar 24 22:31 3.2.0-79-generic
drwxr-xr-x  4 root root 4096 May 12 20:11 3.2.0-83-generic
drwxr-xr-x  2 root root 4096 Jul 27 18:10 3.2.0-88-generic
drwxr-xr-x  4 root root 4096 Aug 18 19:07 3.2.0-89-generic

```

Well this something I've learnt tonight, time for some house keeping!

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; OK;

Let's "TRY" and do this as cleanly as possible - we do have a mess on our hands.

Let's poke at it and see if it bites:
```

sudo dpkg --purge linux-image-3.2.0-32-generic

```

Depending on what the package manager does with this 'test' is how we proceed. I do want to do this in a clean fashion, keeping the package manager happy. IF we have to, we can get dirty and clean up the mess afterward.

most likely
[INDENT][INDENT][INDENT]not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-18
```

(Reading database ... 813363 files and directories currently installed.)
Removing linux-image-3.2.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-89-generic
Found initrd image: /boot/initrd.img-3.2.0-89-generic
Found linux image: /boot/vmlinuz-3.2.0-83-generic
Found initrd image: /boot/initrd.img-3.2.0-83-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic

```

No issues so far

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; Pleasantly surprised;

How about:
```

sudo dpkg --purge linux-headers-3.2.0-32-generic
sudo dpkg --purge linux-headers-3.2.0-32

```
If that files, we try and batch purge some more of the kernels .

[INDENT]making progress slowly
[/INDENT]

---

### Post by vs-ruthless on 2015-08-18
```

(Reading database ... 801090 files and directories currently installed.)
Removing linux-headers-3.2.0-32 ...

```

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; K

Look'n promising:
Try :
```

sudo dpkg -P linux-image-3.2.0-{34,36,38,39,40,44,48}-generic
sudo dpkg -P linux-headers-3.2.0-{34,36,38,39,40,44,48}-generic
sudo dpkg -P linux-headers-3.2.0-{34,36,38,39,40,44,48}

```
Note we still have -31 and -35 hanging. not sure yet how we are going to deal with them - yet/ Will know more later.

If these run clean and are 'Purged', we purge the remainder of the old kernels then do some clean up.
Maybe we get out light, and this is all we need to do.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-18
No issues, that ran OK.

Must mention, I really appreciate your help!

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; Wow ; outstanding :

Still pleasantly surprised, we are getting out of this, this light.

Let's run:
```

sudo dpkg -P linux-image-3.2.0-{52,53,54,56,57,58,59,60,63,65,67,68,69,70,75,77,79}-generic
sudo dpkg -P linux-headers-3.2.0-{52,53,54,56,57,58,59,60,63,65,67,68,69,70,75,77,79}-generic
sudo dpkg -P linux-headers-3.2.0-{52,53,54,56,57,58,59,60,63,65,67,68,69,70,75,77,79}

```
Still hanging the -31 and -35 kernels .

Look'n
[INDENT][INDENT]promise'n
[/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-18
Snap all good!

Ready and waiting...

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; K;

Let's see what we can do about the -31 and -35 kernels.
Need to know what we look like for overall after removing the kernel images that we have:
```

dpkg -l | grep linux-
ls -al /usr/src/
ls -al /lib/modules/

```
I do expect to do this dirty and clean up the mess.

[INDENT][INDENT]moving along right smartly
[/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-18
```

dpkg -l | grep linux-
ii  linux-firmware                  1.79.18                               Firmware for Linux kernel drivers
iU  linux-generic                   3.2.0.88.102                          Complete Generic Linux kernel
ii  linux-headers-3.2.0-34          3.2.0-34.53                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic  3.2.0-34.53                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-35          3.2.0-35.55                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic  3.2.0-35.55                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-36          3.2.0-36.57                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic  3.2.0-36.57                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-38          3.2.0-38.61                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic  3.2.0-38.61                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-39          3.2.0-39.62                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-generic  3.2.0-39.62                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-40          3.2.0-40.64                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic  3.2.0-40.64                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-44          3.2.0-44.69                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic  3.2.0-44.69                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48          3.2.0-48.74                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic  3.2.0-48.74                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52          3.2.0-52.78                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic  3.2.0-52.78                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53          3.2.0-53.81                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic  3.2.0-53.81                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-54          3.2.0-54.82                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic  3.2.0-54.82                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-56          3.2.0-56.86                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-56-generic  3.2.0-56.86                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-57          3.2.0-57.87                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-generic  3.2.0-57.87                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-58          3.2.0-58.88                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic  3.2.0-58.88                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-59          3.2.0-59.90                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic  3.2.0-59.90                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-60          3.2.0-60.91                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic  3.2.0-60.91                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-63          3.2.0-63.95                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-63-generic  3.2.0-63.95                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-65          3.2.0-65.99                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-65-generic  3.2.0-65.99                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-67          3.2.0-67.101                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic  3.2.0-67.101                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-68          3.2.0-68.102                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-68-generic  3.2.0-68.102                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-69          3.2.0-69.103                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-69-generic  3.2.0-69.103                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-70          3.2.0-70.105                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-70-generic  3.2.0-70.105                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-75          3.2.0-75.110                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-75-generic  3.2.0-75.110                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-77          3.2.0-77.114                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-77-generic  3.2.0-77.114                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-79          3.2.0-79.115                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-79-generic  3.2.0-79.115                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-83          3.2.0-83.120                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic  3.2.0-83.120                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-88          3.2.0-88.126                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-88-generic  3.2.0-88.126                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-89          3.2.0-89.127                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-89-generic  3.2.0-89.127                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic           3.2.0.89.103                          Generic Linux kernel headers
ii  linux-image-3.2.0-31-generic    3.2.0-31.50                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35-generic    3.2.0-35.55                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-83-generic    3.2.0-83.120                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-89-generic    3.2.0-89.127                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-generic             3.2.0.88.102                          Generic Linux kernel image
ii  linux-libc-dev                  3.2.0-87.125                          Linux Kernel Headers for development

ls -al /usr/src/
total 232
drwxr-xr-x 58 root root 4096 Aug 18 22:41 .
drwxr-xr-x 10 root root 4096 Sep 30  2012 ..
drwxr-xr-x 24 root root 4096 Dec  7  2012 linux-headers-3.2.0-34
drwxr-xr-x  7 root root 4096 Dec  7  2012 linux-headers-3.2.0-34-generic
drwxr-xr-x 24 root root 4096 Jan  9  2013 linux-headers-3.2.0-35
drwxr-xr-x  7 root root 4096 Jan  9  2013 linux-headers-3.2.0-35-generic
drwxr-xr-x 24 root root 4096 Jan 28  2013 linux-headers-3.2.0-36
drwxr-xr-x  7 root root 4096 Jan 28  2013 linux-headers-3.2.0-36-generic
drwxr-xr-x 24 root root 4096 Feb 24  2013 linux-headers-3.2.0-38
drwxr-xr-x  7 root root 4096 Feb 24  2013 linux-headers-3.2.0-38-generic
drwxr-xr-x 24 root root 4096 Mar 24  2013 linux-headers-3.2.0-39
drwxr-xr-x  7 root root 4096 Mar 24  2013 linux-headers-3.2.0-39-generic
drwxr-xr-x 24 root root 4096 Apr 14  2013 linux-headers-3.2.0-40
drwxr-xr-x  7 root root 4096 Apr 14  2013 linux-headers-3.2.0-40-generic
drwxr-xr-x 24 root root 4096 May 30  2013 linux-headers-3.2.0-44
drwxr-xr-x  7 root root 4096 May 30  2013 linux-headers-3.2.0-44-generic
drwxr-xr-x 24 root root 4096 Jun 25  2013 linux-headers-3.2.0-48
drwxr-xr-x  7 root root 4096 Jun 25  2013 linux-headers-3.2.0-48-generic
drwxr-xr-x 24 root root 4096 Aug 22  2013 linux-headers-3.2.0-52
drwxr-xr-x  7 root root 4096 Aug 22  2013 linux-headers-3.2.0-52-generic
drwxr-xr-x 24 root root 4096 Sep 16  2013 linux-headers-3.2.0-53
drwxr-xr-x  7 root root 4096 Sep 16  2013 linux-headers-3.2.0-53-generic
drwxr-xr-x 24 root root 4096 Oct 19  2013 linux-headers-3.2.0-54
drwxr-xr-x  7 root root 4096 Oct 19  2013 linux-headers-3.2.0-54-generic
drwxr-xr-x 24 root root 4096 Nov 10  2013 linux-headers-3.2.0-56
drwxr-xr-x  7 root root 4096 Nov 10  2013 linux-headers-3.2.0-56-generic
drwxr-xr-x 24 root root 4096 Dec 24  2013 linux-headers-3.2.0-57
drwxr-xr-x  7 root root 4096 Dec 24  2013 linux-headers-3.2.0-57-generic
drwxr-xr-x 24 root root 4096 Jan 18  2014 linux-headers-3.2.0-58
drwxr-xr-x  7 root root 4096 Jan 18  2014 linux-headers-3.2.0-58-generic
drwxr-xr-x 24 root root 4096 Feb 28  2014 linux-headers-3.2.0-59
drwxr-xr-x  7 root root 4096 Feb 28  2014 linux-headers-3.2.0-59-generic
drwxr-xr-x 24 root root 4096 Mar 15  2014 linux-headers-3.2.0-60
drwxr-xr-x  7 root root 4096 Mar 15  2014 linux-headers-3.2.0-60-generic
drwxr-xr-x 24 root root 4096 Jun  2  2014 linux-headers-3.2.0-63
drwxr-xr-x  7 root root 4096 Jun  2  2014 linux-headers-3.2.0-63-generic
drwxr-xr-x 24 root root 4096 Aug 27  2014 linux-headers-3.2.0-65
drwxr-xr-x  7 root root 4096 Aug 27  2014 linux-headers-3.2.0-65-generic
drwxr-xr-x 24 root root 4096 Aug  2  2014 linux-headers-3.2.0-67
drwxr-xr-x  7 root root 4096 Aug  2  2014 linux-headers-3.2.0-67-generic
drwxr-xr-x 24 root root 4096 Sep 15  2014 linux-headers-3.2.0-68
drwxr-xr-x  7 root root 4096 Sep 15  2014 linux-headers-3.2.0-68-generic
drwxr-xr-x 24 root root 4096 Sep 27  2014 linux-headers-3.2.0-69
drwxr-xr-x  7 root root 4096 Sep 27  2014 linux-headers-3.2.0-69-generic
drwxr-xr-x 24 root root 4096 Nov 16  2014 linux-headers-3.2.0-70
drwxr-xr-x  7 root root 4096 Nov 16  2014 linux-headers-3.2.0-70-generic
drwxr-xr-x 24 root root 4096 Jan 28  2015 linux-headers-3.2.0-75
drwxr-xr-x  7 root root 4096 Jan 28  2015 linux-headers-3.2.0-75-generic
drwxr-xr-x 24 root root 4096 Mar 24 22:32 linux-headers-3.2.0-77
drwxr-xr-x  7 root root 4096 Mar 24 22:32 linux-headers-3.2.0-77-generic
drwxr-xr-x 24 root root 4096 Mar 24 22:31 linux-headers-3.2.0-79
drwxr-xr-x  7 root root 4096 Mar 24 22:31 linux-headers-3.2.0-79-generic
drwxr-xr-x 24 root root 4096 May 12 20:11 linux-headers-3.2.0-83
drwxr-xr-x  7 root root 4096 May 12 20:11 linux-headers-3.2.0-83-generic
drwxr-xr-x 24 root root 4096 Jul 27 18:10 linux-headers-3.2.0-88
drwxr-xr-x  7 root root 4096 Jul 27 18:10 linux-headers-3.2.0-88-generic
drwxr-xr-x 24 root root 4096 Aug 17 22:45 linux-headers-3.2.0-89
drwxr-xr-x  7 root root 4096 Aug 17 22:45 linux-headers-3.2.0-89-generic

ls -al /lib/modules/
total 124
drwxr-xr-x 31 root root 4096 Aug 18 22:40 .
drwxr-xr-x 20 root root 4096 Jul 11 19:37 ..
drwxr-xr-x  4 root root 4096 Nov  2  2012 3.2.0-31-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:12 3.2.0-34-generic
drwxr-xr-x  4 root root 4096 Jan  9  2013 3.2.0-35-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:12 3.2.0-36-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:12 3.2.0-38-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:12 3.2.0-39-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:12 3.2.0-40-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:12 3.2.0-44-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:12 3.2.0-48-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-52-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-53-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-54-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-56-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-57-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-58-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-59-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-60-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-63-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-65-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-67-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-68-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:39 3.2.0-69-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:40 3.2.0-70-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:40 3.2.0-75-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:40 3.2.0-77-generic
drwxr-xr-x  2 root root 4096 Aug 18 23:40 3.2.0-79-generic
drwxr-xr-x  4 root root 4096 May 12 20:11 3.2.0-83-generic
drwxr-xr-x  2 root root 4096 Jul 27 18:10 3.2.0-88-generic
drwxr-xr-x  4 root root 4096 Aug 18 19:07 3.2.0-89-generic


```

I'm a little confused as this is still showing old kernal?

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; Yikes !

I am a bit more than confused . Should have removed them judging from the initial results that you provided ! You are working from within the VM,yes ?

[INDENT][INDENT]all I can think of for a reason is that the commands are directed toward the host ?
[/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-18
I believe so, it's a VPS.

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; Sheesssh ....

I honestly do not know . We do have :
> 
Purging configuration files for linux-image-3.2.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-geneeric

Clearly showing the image was removed. I have to assume the other 'P' - upper case "P" for purge went as well .

I can not explain why they are not removed . 
Any hints in the outputs ?

Will consider and see what I might come up with .

[INDENT][INDENT][INDENT]sometimes I do wonder 
[/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-18
Just ran it again and it states that all those we purged are nor available (example below)

```
 
Package `linux-image-3.2.0-65-generic' is not available.
Package `linux-headers-3.2.0-65-generic' is not available.
Package `linux-headers-3.2.0-65' is not available.

```

Is there a file that needs to be cleaned?

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; Hummm ...

Makes no sense to me why then those old kernels are still reflected in the outputs of :
```

dpkg -l | grep linux-
ls -al /usr/src/
ls -al /lib/modules/

```

Is it possible to reboot the server and get a fresh look ?

[INDENT][INDENT]just do not know
[/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-18
Did'nt realise the time will have to continue later up at 6am.

Once again thank you for all your help!!

Hopefully we will resolve this soon.

---

### Post by vs-ruthless on 2015-08-18
> **Bashing-om said:**
> vs-ruthless; Hummm ...

Makes no sense to me why then those old kernels are still reflected in the outputs of :
```

dpkg -l | grep linux-
ls -al /usr/src/
ls -al /lib/modules/

```

Is it possible to reboot the server and get a fresh look ?[INDENT][INDENT]just do not know
[/INDENT]
[/INDENT]


I thought the same, that was the output after the reboot.

---

### Post by Bashing-om on 2015-08-18
vs-ruthless; K;

We continue this tomorrow. In the meantime I will boot up an old 12.04 install; update it and remove the old kernels. Just so I am sure and certain as to what we "should" see as confirmations of removed kernels and what the system reports !

[INDENT][INDENT]confirmation is a good thing
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-08-19
vs-ruthless; Good morning !

I am back with my results after updating and purging old kernels in my 12.04;
My results:
```

sysop1@u1204:~$ dpkg -l | grep linux- // <- before
ii  linux-firmware                         1.79.18                                 Firmware for Linux kernel drivers
ii  linux-generic                          3.2.0.89.103                            Complete Generic Linux kernel
ii  linux-headers-3.2.0-60                 3.2.0-60.91                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic         3.2.0-60.91                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-61                 3.2.0-61.93                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-61-generic         3.2.0-61.93                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-70                 3.2.0-70.105                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-70-generic         3.2.0-70.105                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-79                 3.2.0-79.115                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-79-generic         3.2.0-79.115                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-83                 3.2.0-83.120                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic         3.2.0-83.120                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-89                 3.2.0-89.127                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-89-generic         3.2.0-89.127                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.89.103                            Generic Linux kernel headers
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-60-generic           3.2.0-60.91                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-61-generic           3.2.0-61.93                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-70-generic           3.2.0-70.105                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-79-generic           3.2.0-79.115                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-83-generic           3.2.0-83.120                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-89-generic           3.2.0-89.127                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.2.0.89.103                            Generic Linux kernel image
ii  linux-libc-dev                         3.2.0-89.127                            Linux Kernel Headers for development
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu1.1                  base package for ALSA and OSS sound systems
ii  syslinux-common                        2:4.05+dfsg-2                           collection of boot loaders (common files)
ii  syslinux-legacy                        2:3.63+dfsg-2ubuntu5                    Bootloader for Linux/i386 using MS-DOS floppies
sysop1@u1204:~$

sysop1@u1204:~$ ls -al /usr/src/  <-before
total 56
drwxr-xr-x 14 root root 4096 Aug 19 08:46 .
drwxr-xr-x 10 root root 4096 Aug 23  2012 ..
drwxr-xr-x 24 root root 4096 Apr 23  2014 linux-headers-3.2.0-60
drwxr-xr-x  7 root root 4096 Apr 23  2014 linux-headers-3.2.0-60-generic
drwxr-xr-x 24 root root 4096 May 13  2014 linux-headers-3.2.0-61
drwxr-xr-x  7 root root 4096 May 13  2014 linux-headers-3.2.0-61-generic
drwxr-xr-x 24 root root 4096 Nov 14  2014 linux-headers-3.2.0-70
drwxr-xr-x  7 root root 4096 Nov 14  2014 linux-headers-3.2.0-70-generic
drwxr-xr-x 24 root root 4096 Apr  3 22:00 linux-headers-3.2.0-79
drwxr-xr-x  7 root root 4096 Apr  3 22:00 linux-headers-3.2.0-79-generic
drwxr-xr-x 24 root root 4096 May 13 08:44 linux-headers-3.2.0-83
drwxr-xr-x  7 root root 4096 May 13 08:44 linux-headers-3.2.0-83-generic
drwxr-xr-x 24 root root 4096 Aug 19 08:46 linux-headers-3.2.0-89
drwxr-xr-x  7 root root 4096 Aug 19 08:46 linux-headers-3.2.0-89-generic
sysop1@u1204:~$ 

sysop1@u1204:~$ ls -al /lib/modules/  <-Before
total 36
drwxr-xr-x  9 root root 4096 Aug 19 08:45 .
drwxr-xr-x 22 root root 4096 Aug 19 08:42 ..
drwxr-xr-x  4 root root 4096 May 13  2014 3.2.0-29-generic
drwxr-xr-x  4 root root 4096 Apr 23  2014 3.2.0-60-generic
drwxr-xr-x  4 root root 4096 May 13  2014 3.2.0-61-generic
drwxr-xr-x  4 root root 4096 Nov 14  2014 3.2.0-70-generic
drwxr-xr-x  4 root root 4096 Apr  3 22:00 3.2.0-79-generic
drwxr-xr-x  4 root root 4096 May 13 08:44 3.2.0-83-generic
drwxr-xr-x  4 root root 4096 Aug 19 08:46 3.2.0-89-generic
sysop1@u1204:~$ 

Removal of 1 kerenl results:
sysop1@u1204:~$ sudo dpkg -P linux-image-3.2.0-29-generic

done
Purging configuration files for linux-image-3.2.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
sysop1@u1204:~$ 

sysop1@u1204:~$ sudo dpkg -P linux-headers-3.2.0-29-generic
dpkg: warning: there's no installed package matching linux-headers-3.2.0-29-generic
sysop1@u1204:~$ sudo dpkg -P linux-headers-3.2.0-29
dpkg: warning: there's no installed package matching linux-headers-3.2.0-29
sysop1@u1204:~$

Immediatly after - no reboot:
sysop1@u1204:~$ dpkg -l | grep linux-
ii  linux-firmware                         1.79.18                                 Firmware for Linux kernel drivers
ii  linux-generic                          3.2.0.89.103                            Complete Generic Linux kernel
ii  linux-headers-3.2.0-79                 3.2.0-79.115                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-79-generic         3.2.0-79.115                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-83                 3.2.0-83.120                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic         3.2.0-83.120                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-89                 3.2.0-89.127                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-89-generic         3.2.0-89.127                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.89.103                            Generic Linux kernel headers
ii  linux-image-3.2.0-79-generic           3.2.0-79.115                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-83-generic           3.2.0-83.120                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-89-generic           3.2.0-89.127                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.2.0.89.103                            Generic Linux kernel image
ii  linux-libc-dev                         3.2.0-89.127                            Linux Kernel Headers for development
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu1.1                  base package for ALSA and OSS sound systems
ii  syslinux-common                        2:4.05+dfsg-2                           collection of boot loaders (common files)
ii  syslinux-legacy                        2:3.63+dfsg-2ubuntu5                    Bootloader for Linux/i386 using MS-DOS floppies
sysop1@u1204:~$ 

sysop1@u1204:~$ ls -al /usr/src/
total 32
drwxr-xr-x  8 root root 4096 Aug 19 09:13 .
drwxr-xr-x 10 root root 4096 Aug 23  2012 ..
drwxr-xr-x 24 root root 4096 Apr  3 22:00 linux-headers-3.2.0-79
drwxr-xr-x  7 root root 4096 Apr  3 22:00 linux-headers-3.2.0-79-generic
drwxr-xr-x 24 root root 4096 May 13 08:44 linux-headers-3.2.0-83
drwxr-xr-x  7 root root 4096 May 13 08:44 linux-headers-3.2.0-83-generic
drwxr-xr-x 24 root root 4096 Aug 19 08:46 linux-headers-3.2.0-89
drwxr-xr-x  7 root root 4096 Aug 19 08:46 linux-headers-3.2.0-89-generic
sysop1@u1204:~$ 

sysop1@u1204:~$ ls -al /lib/modules/
total 20
drwxr-xr-x  5 root root 4096 Aug 19 09:13 .
drwxr-xr-x 22 root root 4096 Aug 19 08:42 ..
drwxr-xr-x  4 root root 4096 Apr  3 22:00 3.2.0-79-generic
drwxr-xr-x  4 root root 4096 May 13 08:44 3.2.0-83-generic
drwxr-xr-x  4 root root 4096 Aug 19 08:46 3.2.0-89-generic
sysop1@u1204:~$

```

As you can see, the results of removing kernels should be seen immediately . Presently, I do not know what to say.

[INDENT][INDENT]now this IS a thing
[/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-19
Evening Bashing-om,

I've gone through this topic again just encase I missed something, but to no avail.

**dpkg -l | grep linux- **is still showing everthing is still there, but when I run --purge  again I get a message saying that "Package `linux-headers-x.x.x-x' is not available." for eveyone that we purged.

Scratch head :?:

---

### Post by Bashing-om on 2015-08-19
vs-ruthless' Well ...

We can get real ruthless .. get very dirty --- and clean up the mess afterward .
But, it can get real messy and make a mess of the server - that possibility does exist !
Let's see what we can do dirtily:
show me the updated:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux

```
And we manually take matters into our own hands, and 'apt-get -f install' to 'fix' the system.

scary thought
[INDENT][INDENT][INDENT]but we can do that 
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-08-19
vs-ruthless; Hey !

See my last .
'Nother thought .
What does the package manager say about the state of the package manager system ?
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```


[INDENT][INDENT]if the package manager is not happy
[INDENT][INDENT][INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-19
Good News!

I found the issue why they did'nt remove, i pasted the command below all in one chunk.
```

sudo dpkg -P linux-image-3.2.0-{52,53,54,56,57,58,59,60,63,65,67,68,69,70,75,77,79}-generic
sudo dpkg -P linux-headers-3.2.0-{52,53,54,56,57,58,59,60,63,65,67,68,69,70,75,77,79}-generic
sudo dpkg -P linux-headers-3.2.0-{52,53,54,56,57,58,59,60,63,65,67,68,69,70,75,77,79}

```

Pasting separately has removed them - Hooray!!!

Now this is the status now:

```

ls -al /usr/src/
total 40
drwxr-xr-x 10 root root 4096 Aug 19 21:58 .
drwxr-xr-x 10 root root 4096 Sep 30  2012 ..
drwxr-xr-x 24 root root 4096 Jan  9  2013 linux-headers-3.2.0-35
drwxr-xr-x  7 root root 4096 Jan  9  2013 linux-headers-3.2.0-35-generic
drwxr-xr-x 24 root root 4096 May 12 20:11 linux-headers-3.2.0-83
drwxr-xr-x  7 root root 4096 May 12 20:11 linux-headers-3.2.0-83-generic
drwxr-xr-x 24 root root 4096 Jul 27 18:10 linux-headers-3.2.0-88
drwxr-xr-x  7 root root 4096 Jul 27 18:10 linux-headers-3.2.0-88-generic
drwxr-xr-x 24 root root 4096 Aug 17 22:45 linux-headers-3.2.0-89
drwxr-xr-x  7 root root 4096 Aug 17 22:45 linux-headers-3.2.0-89-generic

ls -al /lib/modules/
total 28
drwxr-xr-x  7 root root 4096 Aug 19 21:58 .
drwxr-xr-x 20 root root 4096 Jul 11 19:37 ..
drwxr-xr-x  4 root root 4096 Nov  2  2012 3.2.0-31-generic
drwxr-xr-x  4 root root 4096 Jan  9  2013 3.2.0-35-generic
drwxr-xr-x  4 root root 4096 May 12 20:11 3.2.0-83-generic
drwxr-xr-x  2 root root 4096 Jul 27 18:10 3.2.0-88-generic
drwxr-xr-x  4 root root 4096 Aug 18 19:07 3.2.0-89-generic

ls -al /boot/
total 45436
drwxr-xr-x  4 root root     8192 Aug 18 23:40 .
drwxr-xr-x 24 root root     4096 Aug 18 19:07 ..
-rw-r--r--  1 root root   796660 Apr 29 17:01 abi-3.2.0-83-generic
-rw-r--r--  1 root root   796660 Jul 28 11:24 abi-3.2.0-89-generic
-rw-r--r--  1 root root   140790 Apr 29 17:01 config-3.2.0-83-generic
-rw-r--r--  1 root root   140790 Jul 28 11:24 config-3.2.0-89-generic
drwxr-xr-x  3 root root     7168 Aug 18 23:40 grub
-rw-r--r--  1 root root 14236253 May 12 20:11 initrd.img-3.2.0-83-generic
-rw-r--r--  1 root root 14235101 Aug 18 19:07 initrd.img-3.2.0-89-generic
drwx------  2 root root    12288 Sep 30  2012 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2899357 Apr 29 17:01 System.map-3.2.0-83-generic
-rw-------  1 root root  2899603 Jul 28 11:24 System.map-3.2.0-89-generic
-rw-------  1 root root  4991856 Apr 29 17:01 vmlinuz-3.2.0-83-generic
-rw-------  1 root root  4994544 Jul 28 11:24 vmlinuz-3.2.0-89-generic

dpkg -l | grep linux
ii  libselinux1                     2.1.0-4.1ubuntu1                      SELinux runtime shared libraries
ii  linux-firmware                  1.79.18                               Firmware for Linux kernel drivers
iU  linux-generic                   3.2.0.88.102                          Complete Generic Linux kernel
ii  linux-headers-3.2.0-35          3.2.0-35.55                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic  3.2.0-35.55                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-83          3.2.0-83.120                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic  3.2.0-83.120                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-88          3.2.0-88.126                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-88-generic  3.2.0-88.126                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-89          3.2.0-89.127                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-89-generic  3.2.0-89.127                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic           3.2.0.89.103                          Generic Linux kernel headers
ii  linux-image-3.2.0-31-generic    3.2.0-31.50                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35-generic    3.2.0-35.55                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-83-generic    3.2.0-83.120                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-89-generic    3.2.0-89.127                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-generic             3.2.0.88.102                          Generic Linux kernel image
ii  linux-libc-dev                  3.2.0-87.125                          Linux Kernel Headers for development
ii  util-linux                      2.20.1-1ubuntu3.1                     Miscellaneous system utilities

```

He Smiles..

---

### Post by vs-ruthless on 2015-08-19
Just tried to update & upgrade.

Update no issues, upgrade I'm still getting my original message.

```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 3.2.0.88.102) but 3.2.0.89.103 is installed
 linux-image-generic : Depends: linux-image-3.2.0-88-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by Bashing-om on 2015-08-19
vs-ruthless; Hey hey ;

What a load off .

OK is the system in a happy state ?
rebooted and up and running on the -89 kernel ?

Do we even want to mess with the -21 and -35 kernel remnants ?

[INDENT][INDENT]wonders never cease
[/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-19
Rebooted

```

uname -r
3.2.0-89-generic

ls -al /vmlin*
lrwxrwxrwx 1 root root 29 Aug 18 19:07 /vmlinuz -> boot/vmlinuz-3.2.0-89-generic
lrwxrwxrwx 1 root root 29 May 12 20:11 /vmlinuz.old -> boot/vmlinuz-3.2.0-83-generic

ls -al /initrd*
lrwxrwxrwx 1 root root 33 Aug 18 19:07 /initrd.img -> /boot/initrd.img-3.2.0-89-generic
lrwxrwxrwx 1 root root 33 May 12 20:11 /initrd.img.old -> /boot/initrd.img-3.2.0-83-generic

dpkg -l | grep linux
ii  libselinux1                     2.1.0-4.1ubuntu1                      SELinux runtime shared libraries
ii  linux-firmware                  1.79.18                               Firmware for Linux kernel drivers
iU  linux-generic                   3.2.0.88.102                          Complete Generic Linux kernel
ii  linux-headers-3.2.0-35          3.2.0-35.55                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic  3.2.0-35.55                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-83          3.2.0-83.120                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic  3.2.0-83.120                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-88          3.2.0-88.126                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-88-generic  3.2.0-88.126                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-89          3.2.0-89.127                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-89-generic  3.2.0-89.127                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic           3.2.0.89.103                          Generic Linux kernel headers
ii  linux-image-3.2.0-31-generic    3.2.0-31.50                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35-generic    3.2.0-35.55                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-83-generic    3.2.0-83.120                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-89-generic    3.2.0-89.127                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-generic             3.2.0.88.102                          Generic Linux kernel image
ii  linux-libc-dev                  3.2.0-87.125                          Linux Kernel Headers for development
ii  util-linux                      2.20.1-1ubuntu3.1                     Miscellaneous system utilities

```

Question why is their 2 different kernals within this code below, isn't this what the error message is saying?

```

iU  linux-generic                   3.2.0.88.102                          Complete Generic Linux kernel
ii  linux-headers-generic           3.2.0.89.103                          Generic Linux kernel headers
iU  linux-image-generic             3.2.0.88.102                          Generic Linux kernel image

```

---

### Post by Bashing-om on 2015-08-19
vs-ruthless; Hey Hey .....

Look'n great !

As to " linux-generic  " That is the meta package to control installing kernels. And YES we do need to re-install it ( status iU ) .


Removing linux-generic will do no harm at all. It is only a "meta-package" depending on linux-image-generic and linux-headers-generic. Those two are themselves meta-packages depending on the respective latest image/headers packages.

You can see this for yourself by issuing apt-cache show linux-generic, apt-cache show linux-image-generic and apt-cache show linux-headers-generic.

The purpose of meta-packages is to pull-in the packages on which they depend, they have no functionality at all. On the other hand removing one will not remove it's dependencies - so no danger to the system.

After having fixed the original issue you can of course install linux-generic again. - which is what we are now going to do !

```

sudo apt-get install --reinstall linux-image-generic
sudo apt-get install --reinstall linux-generic

```


Now I personally prefer a 'clean' system . There is still the -31 and -35 remnants on the system.
Again, we can manually remove them .. but maybe the package manager will cope ?
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get of install
sudo dpkg -C

```

Slowly but surely (now)
[INDENT][INDENT][INDENT]a step at a time -> getting there
[/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-19
sudo apt-get install --reinstall linux-image-generic
sudo apt-get install --reinstall linux-generic

both failed, error below.
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.89.103) but 3.2.0.88.102 is to be installed
 linux-image-generic : Depends: linux-image-3.2.0-88-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Still she tests us, we will get there I'm sure.

---

### Post by Bashing-om on 2015-08-19
vs-ruthless; Hummm .....


Curious and curiouser !

OK, let's try:
```

sudo apt-get remove linux-image-generic
sudo apt get install linux-image-generic

```
If that flies do tha same for " linux-generic " package.

[INDENT][INDENT]were not for bad luck ->
[INDENT]but, we have not broke the server yet 
[/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-19
same error when I run - sudo apt-get remove linux-image-generic

```

Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.88.102) but it is not going to be installed
                 Depends: linux-headers-generic (= 3.2.0.88.102) but 3.2.0.89.103 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

That time again going to have to try again tomorrow.

---

### Post by Bashing-om on 2015-08-19
vs-ruthless; K !

I have an inkling of what is going on here:
we have the -88 headers installed:
> 
ii  linux-headers-3.2.0-83          3.2.0-83.120                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic  3.2.0-83.120                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-88          3.2.0-88.126                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-88-generic

But, but but
The -image-3.2.0-88 package is not installed !
> 
ii  linux-image-3.2.0-31-generic    3.2.0-31.50                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35-generic    3.2.0-35.55                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-83-generic    3.2.0-83.120                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-89-generic 


Let's see of we can make the package manager happy:
install it !
```

sudo apt-get install linux-image-3.2.0-88-generic

```

Maybe yes, 
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-20
Morning

No joy, same error

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 3.2.0.88.102) but 3.2.0.89.103 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Would it be easier to rm the latest kernel and go back to an old one? or can I manually upload the missing file?

---

### Post by Bashing-om on 2015-08-20
vs-ruthless; Morning;

We are making progress, and getting there.

We now have:
> 
linux-generic : Depends: linux-[color=green]headers-generic[/color] (= 3.2.0.88.102) but 3.2.0.89.103 is to be installed


And the verification:
> 
iU  linux-generic                   3.2.0.88.102
linux-headers-3.2.0-88          3.2.0-88.126

Let's try this to make the package manager happy:
```

sudo apt-get install linux-image-3.2.0-88-generic

```
see if the old .102 version gets over-ridden by the newer .126 version. Hopefully the " linux-headers-generic " 3.2.0-88 version will be picked up and installed. Which is the one we are missing.

Ultimately we want the -88 and -89 versions installed and all other kernels removed. The -89 as the booting kernel and the -88 as the backup.

Unless I am being real dense and missing something else. Your thoughts ?
As around and around we go to get the kernels straight.

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-08-20
vs-ruthless; YUK !

Nevermind my last thought, As I now see that is just what we just tried. Let me finish my coffee, and see if I can see this tree we are looking for in all this forest.
There must be a different way to make the kernel's files match up.

Think'n

[INDENT][INDENT]make the package manager happy
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-08-20
vs-ruthless; OK;

My think'n - for what it is worth.

There can be but ONE set of control files
a) linux-generic 
b) linux-headers-generic
c) linux-image-generic
These versions must match for the latest kernel that is installed.
So once more - with feeling - . let's see if we can make the version of " linux-generic" match that of " linux-headers-generic'
As " linux-headers-generic" is at the latest version, then "linux-generic" is the wrong version for the install.

Let's try a less invasive manner to remove and install:

Edited !
```

sudo dpkg -P linux-generic
sudo dpkg -P linux-image-generic
sudo apt-get install linux-generic
sudo apt-get install linux-image-generic

```

Depending now on what the system screams and hollers about is what we do to make it into a happy state.
There is no getting around the fact that these files must match version wise.

[INDENT][INDENT][INDENT]make it so
[/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-20
Good News it worked!

Status now, oh and I manged to update.

```

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda3        49G  6.4G   40G  14% /
udev            490M  4.0K  490M   1% /dev
tmpfs           100M  256K  100M   1% /run
none            5.0M     0  5.0M   0% /run/lock
tmpfs           498M  4.0K  498M   1% /run/shm
/dev/vda1       461M   59M  379M  14% /boot
df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/vda3      3219456 290622 2928834   10% /
udev            125236    395  124841    1% /dev
tmpfs           127434    294  127140    1% /run
none            127434      2  127432    1% /run/lock
tmpfs           127434      2  127432    1% /run/shm
/dev/vda1       121920    233  121687    1% /boot

dpkg -l | grep linux-
ii  linux-firmware                  1.79.18                               Firmware for Linux kernel drivers
ii  linux-generic                   3.2.0.89.103                          Complete Generic Linux kernel
ii  linux-headers-3.2.0-35          3.2.0-35.55                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic  3.2.0-35.55                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-83          3.2.0-83.120                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic  3.2.0-83.120                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-88          3.2.0-88.126                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-88-generic  3.2.0-88.126                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-89          3.2.0-89.127                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-89-generic  3.2.0-89.127                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic           3.2.0.89.103                          Generic Linux kernel headers
ii  linux-image-3.2.0-31-generic    3.2.0-31.50                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35-generic    3.2.0-35.55                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-83-generic    3.2.0-83.120                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-89-generic    3.2.0-89.127                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic             3.2.0.89.103                          Generic Linux kernel image
ii  linux-libc-dev                  3.2.0-89.127                          Linux Kernel Headers for development

ls -al /usr/src/
total 40
drwxr-xr-x 10 root root 4096 Aug 19 21:58 .
drwxr-xr-x 10 root root 4096 Sep 30  2012 ..
drwxr-xr-x 24 root root 4096 Jan  9  2013 linux-headers-3.2.0-35
drwxr-xr-x  7 root root 4096 Jan  9  2013 linux-headers-3.2.0-35-generic
drwxr-xr-x 24 root root 4096 May 12 20:11 linux-headers-3.2.0-83
drwxr-xr-x  7 root root 4096 May 12 20:11 linux-headers-3.2.0-83-generic
drwxr-xr-x 24 root root 4096 Jul 27 18:10 linux-headers-3.2.0-88
drwxr-xr-x  7 root root 4096 Jul 27 18:10 linux-headers-3.2.0-88-generic
drwxr-xr-x 24 root root 4096 Aug 17 22:45 linux-headers-3.2.0-89
drwxr-xr-x  7 root root 4096 Aug 17 22:45 linux-headers-3.2.0-89-generic

ls -al /lib/modules/
total 28
drwxr-xr-x  7 root root 4096 Aug 19 21:58 .
drwxr-xr-x 20 root root 4096 Jul 11 19:37 ..
drwxr-xr-x  4 root root 4096 Nov  2  2012 3.2.0-31-generic
drwxr-xr-x  4 root root 4096 Jan  9  2013 3.2.0-35-generic
drwxr-xr-x  4 root root 4096 May 12 20:11 3.2.0-83-generic
drwxr-xr-x  2 root root 4096 Jul 27 18:10 3.2.0-88-generic
drwxr-xr-x  4 root root 4096 Aug 18 19:07 3.2.0-89-generic
ls -al /boot/
total 45436
drwxr-xr-x  4 root root     8192 Aug 18 23:40 .
drwxr-xr-x 24 root root     4096 Aug 18 19:07 ..
-rw-r--r--  1 root root   796660 Apr 29 17:01 abi-3.2.0-83-generic
-rw-r--r--  1 root root   796660 Jul 28 11:24 abi-3.2.0-89-generic
-rw-r--r--  1 root root   140790 Apr 29 17:01 config-3.2.0-83-generic
-rw-r--r--  1 root root   140790 Jul 28 11:24 config-3.2.0-89-generic
drwxr-xr-x  3 root root     7168 Aug 18 23:40 grub
-rw-r--r--  1 root root 14236253 May 12 20:11 initrd.img-3.2.0-83-generic
-rw-r--r--  1 root root 14235101 Aug 18 19:07 initrd.img-3.2.0-89-generic
drwx------  2 root root    12288 Sep 30  2012 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2899357 Apr 29 17:01 System.map-3.2.0-83-generic
-rw-------  1 root root  2899603 Jul 28 11:24 System.map-3.2.0-89-generic
-rw-------  1 root root  4991856 Apr 29 17:01 vmlinuz-3.2.0-83-generic
-rw-------  1 root root  4994544 Jul 28 11:24 vmlinuz-3.2.0-89-generic

 dpkg -l | grep linux-
ii  linux-firmware                  1.79.18                               Firmware for Linux kernel drivers
ii  linux-generic                   3.2.0.89.103                          Complete Generic Linux kernel
ii  linux-headers-3.2.0-35          3.2.0-35.55                           Header files related to Linux kernel versio
ii  linux-headers-3.2.0-35-generic  3.2.0-35.55                           Linux kernel headers for version 3.2.0 on 6
ii  linux-headers-3.2.0-83          3.2.0-83.120                          Header files related to Linux kernel versio
ii  linux-headers-3.2.0-83-generic  3.2.0-83.120                          Linux kernel headers for version 3.2.0 on 6
ii  linux-headers-3.2.0-88          3.2.0-88.126                          Header files related to Linux kernel versio
ii  linux-headers-3.2.0-88-generic  3.2.0-88.126                          Linux kernel headers for version 3.2.0 on 6
ii  linux-headers-3.2.0-89          3.2.0-89.127                          Header files related to Linux kernel versio
ii  linux-headers-3.2.0-89-generic  3.2.0-89.127                          Linux kernel headers for version 3.2.0 on 6
ii  linux-headers-generic           3.2.0.89.103                          Generic Linux kernel headers
ii  linux-image-3.2.0-31-generic    3.2.0-31.50                           Linux kernel image for version 3.2.0 on 64
ii  linux-image-3.2.0-35-generic    3.2.0-35.55                           Linux kernel image for version 3.2.0 on 64
ii  linux-image-3.2.0-83-generic    3.2.0-83.120                          Linux kernel image for version 3.2.0 on 64
ii  linux-image-3.2.0-89-generic    3.2.0-89.127                          Linux kernel image for version 3.2.0 on 64
ii  linux-image-generic             3.2.0.89.103                          Generic Linux kernel image
ii  linux-libc-dev                  3.2.0-89.127                          Linux Kernel Headers for development

uname -r
3.2.0-89-generic

ls -al /vmlin*
lrwxrwxrwx 1 root root 29 Aug 18 19:07 /vmlinuz -> boot/vmlinuz-3.2.0-89-generic
lrwxrwxrwx 1 root root 29 May 12 20:11 /vmlinuz.old -> boot/vmlinuz-3.2.0-83-generic

ls -al /initrd*
lrwxrwxrwx 1 root root 33 Aug 18 19:07 /initrd.img -> /boot/initrd.img-3.2.0-89-generic
lrwxrwxrwx 1 root root 33 May 12 20:11 /initrd.img.old -> /boot/initrd.img-3.2.0-83-generic

```

I assume I still need to run the following?

```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get of install
sudo dpkg -C

```

---

### Post by Bashing-om on 2015-08-20
vs-ruthless; Yes !

What a load off .

Before we do the final cleanup, let's see what we can do about purging those kernel remnants.

Poke at it thusly:
```

sudo dpkg -P linux-image-3.2.0-31-generic

sudo dpkg -P linux-image-3.2.0-35-generic
sudo dpkg -P linux-headers-3.2.0-35-generic
sudo dpkg -P linux-headers-3.2.0-35

```

Why do we not see the -88 kernel on the /boot directory ???? IF the above runs and the -31 and -35 kernels are gone gone. Let's see what grub has to say about the -88 kernel:
```

sudo update-grub

```


I really think we best have the kernel issue at an end before we cleanup the system; paying real close attention to what 'autoremove' is going to remove ( that we might want, and thus re-install)

[INDENT][INDENT]I am as pleased as Punch
[/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-20
Just ran all the following commands and all the clean up commands and all looks good.

Is their any info you requie me to post up?

---

### Post by Bashing-om on 2015-08-20
vs-ruthless; Great !

So what has grub set up for us for booting ?
```

ls -al /vmlinuz*
ls -al /initrd*

```

[INDENT][INDENT][INDENT]put a smile on my face
[/INDENT][/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-20
Here you go.

```

ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 Aug 18 19:07 /vmlinuz -> boot/vmlinuz-3.2.0-89-generic
lrwxrwxrwx 1 root root 29 May 12 20:11 /vmlinuz.old -> boot/vmlinuz-3.2.0-83-generic
ls -al /initrd*
lrwxrwxrwx 1 root root 33 Aug 18 19:07 /initrd.img -> /boot/initrd.img-3.2.0-89-generic
lrwxrwxrwx 1 root root 33 May 12 20:11 /initrd.img.old -> /boot/initrd.img-3.2.0-83-generic

```

---

### Post by Bashing-om on 2015-08-20
vs-ruthless; I am not smiling !

Try:
```

sudo apt-get install --reinstall linux-image-3.2.0-88-generic

```

If that runs clean and installs:
for cheap insurance:
```

sudo update-grub

```

[INDENT][INDENT]get our ducks all in a row
[/INDENT][/INDENT]

---

### Post by vs-ruthless on 2015-08-20
Ducks aligned!

```

ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 Aug 20 22:34 /vmlinuz -> boot/vmlinuz-3.2.0-88-generic
lrwxrwxrwx 1 root root 29 Aug 18 19:07 /vmlinuz.old -> boot/vmlinuz-3.2.0-89-generic
ls -al /initrd*
lrwxrwxrwx 1 root root 33 Aug 20 22:34 /initrd.img -> /boot/initrd.img-3.2.0-88-generic
lrwxrwxrwx 1 root root 33 Aug 18 19:07 /initrd.img.old -> /boot/initrd.img-3.2.0-89-generic

```

Oh just to add i've just checked and webmin and I can now update packages as well.

I would like to thank you for your patients and your time that you have spend helping me fix my issue!

I'm over the moon that we have resolved this!

Thank you Bashing-om!!! Give yourself a MASSIVE pat on the back :D

---

### Post by Bashing-om on 2015-08-20
vs-ruthless; OutStanding !

Now there is a smile inplace . I can live with the fact that the newer kernel is now the backup kernel .

If you consider this matter settled, and are satisfied that there is resolution then signify as such:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


[INDENT][INDENT]job well done
[/INDENT][/INDENT]

---

