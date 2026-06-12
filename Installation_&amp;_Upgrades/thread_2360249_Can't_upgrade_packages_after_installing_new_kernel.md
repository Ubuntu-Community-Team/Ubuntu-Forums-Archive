---
title: "Can't upgrade packages after installing new kernel"
date: 2017-05-02
forum: Installation &amp; Upgrades
---

### Post by apeirohedra on 2017-05-02
Hi,

Ubuntu 16.04.2
Today I upgraded to  4.4.0-77-generic. After that...
I can't upgrade packages because of:

```
user@user:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  init
The following packages will be upgraded:
  init
1 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
1 not fully installed or removed.
Need to get 4,624 B of archives.
After this operation, 16.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://nz.archive.ubuntu.com/ubuntu xenial-updates/main amd64 init amd64 1.29ubuntu4 [4,624 B]
Fetched 4,624 B in 1s (4,200 B/s)
dpkg: unrecoverable fatal error, aborting:
 files list for package 'init' is not a regular file
E: Sub-process /usr/bin/dpkg returned an error code (2)
```


I have done a lot of tricks but nothing improved.

---

### Post by ajgreeny on 2017-05-02
That kernel seems to have some problems, though yours is not the same as the bug posted earlier today about wifi not connecting.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623)

However, just try booting to an earlier kernel eg 4.4.0-75, from grub to see if it solves your difficulty as well.

---

### Post by ian-weisser on 2017-05-02
> **apeirohedra said:**
> 
 files list for package 'init' is not a regular file

Tricks won't help - you must understand the problem and solve it.
Tricks rarely help with package problems, and sometimes make the problems worse.

The problem, according to your error message, is that the newly-downloaded 'init' package seems to be corrupt. 
Delete the corrupt package from your local cache, thereby forcing apt to download a fresh copy.

```
sudo apt clean init        # delete the corrupt copy of 'init' from your local cache
sudo apt update            # refresh your package database; optional, but a good habit before running 'upgrade'
sudo apt upgrade
```

---

### Post by apeirohedra on 2017-05-03
> However, just try booting to an earlier kernel eg 4.4.0-75, from grub to see if it solves your difficulty as well.

I've forgotten to mention that I purged all old kernels and only 4.4.0-77 left.

I have Internet connection.
I can't even install anything. After downloading manually and installing through Gdebi 4.4.0-75 kernel I got:

```
Failed to install package 'linux-image-4.4.0-75-generic amd64[65].deb
```

Is there a solution, except setting the system up from scratch?

---

### Post by ajgreeny on 2017-05-03
It is only wifi that is the main problem with this kernel, and it now appears according to that bug, that the problem is related to the additional packages for kernel 4.4.0-77 not being installed along with the linux-image package, ie the linux-image-extra and linux-header packages if updating was done using the update-manager.  Other methods of updating did not suffer in the same way, so if you used terminal commands or synaptic, those additional packages were installed as they should be.

For future reference it is strongly advised that you **always keep the two most recent kernel versions** installed on your computer just in case this sort of problem occurs again.

---

### Post by apeirohedra on 2017-05-03
I always update repositories and upgrade packages through terminal. Sometimes I leave at least two kernels. This time did not. 
I do never update through update-manager or synaptic. The second I have not installed though.
I can't install anything using terminal or anything else.
Anyway thank you, ajgreeny, very much.

---

### Post by ian-weisser on 2017-05-03
> **apeirohedra said:**
> Is there a solution, except setting the system up from scratch?

Check for typos on your input. There is no such package [COLOR=#000000][FONT=&amp]'linux-image-4.4.0-75-generic amd65.deb

Unless you have removed the package manager itself, or rendered the system unbootable, most problems are fairly easy to fix.
Your error messages above indicate a couple small problems, each with fairly easy fix.
 
[/FONT][/COLOR]

---

### Post by paul_h on 2017-05-03
> **ajgreeny said:**
> It is only wifi that is the main problem with this kernel, and it now appears according to that bug, that the problem is related to the additional packages for kernel 4.4.0-77 not being installed along with the linux-image package, ie the linux-image-extra and linux-header packages if updating was done using the update-manager.  Other methods of updating did not suffer in the same way, so if you used terminal commands or synaptic, those additional packages were installed as they should be.
     .......................... Cut ...................


The 4.4.0-77 kernel update, implemented by the Software Updater, caused problems to more than WIFI in my case. I lost WIFI, Ethernet, sound and USB mouse, and there were some small problem with writing to the screen.

The good news is that reverting to 4.4.0-75 through Grub recovered all those functions. With some hesitation, some 12+ hours later, I ran Software Updater to update to 4.4.0-77 successfully and everything is still working. In 11 years this is the only time I can recall having any problem updating Ubuntu. It really is an amazing OS and the community and Canonical support is outstanding!

---

### Post by apeirohedra on 2017-05-03
> **ian-weisser said:**
> [COLOR=#000000][FONT=&amp]
Unless you have removed the package manager itself, or rendered the system unbootable, most problems are fairly easy to fix.
Your error messages above indicate a couple small problems, each with fairly easy fix.
[/FONT][/COLOR]

Hope that in the future I will call it a small problem.

Ok to sum up, I will show You what I did and get:

1. Upgraded to newest linux-kernel 4.4.0-77.98
```
sudo apt upgrade
```

2. Removing all old packages... (Big mistake)
```
sudo apt purge linux-image-4.4.0-{66,67,70,71,72,75}-generic
sudo apt purge linux-image-extra-4.4.0-{66,67,70,71}-generic

```

3. Till now we have...
```
dpkg --list | grep linux-image
ii  linux-image-4.4.0-77-generic                                4.4.0-77.98                                      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-77-generic                          4.4.0-77.98                                      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                         4.4.0.77.83                                      amd64        Generic Linux kernel image

```

4. Checking for package manager...
```
sudo apt install apt
apt is already the newest version (1.2.20).

```

5. Trying to install any package, for example...
```
sudo apt install sl

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sl
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
Need to get 0 B/24.4 kB of archives.
After this operation, 86.0 kB of additional disk space will be used.
Selecting previously unselected package sl.
dpkg: unrecoverable fatal error, aborting:
 files list for package 'init' is not a regular file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by ian-weisser on 2017-05-03
Yes, see post #3 for how to fix it.
Don't fixate on this-kernel-or-that-kernel. The error is coming from apt, not the kernel.

---

### Post by apeirohedra on 2017-05-03
> **ian-weisser said:**
> Yes, see post #3 for how to fix it.


I did some tricks before my first post. Almost everything related to phrase:

```
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Using terminal:
```

[COLOR=#111111]sudo dpkg --configure -a[/COLOR]
[LEFT][COLOR=#111111][FONT=Consolas][COLOR=#000000]sudo apt autoclean[/COLOR]
[COLOR=#000000]sudo apt clean[/COLOR]
[/FONT][/COLOR][/LEFT]
 
```
to list a few. And then:
```
sudo apt clean init
```

Still the same:
```

sudo apt upgrade
(...)
Fetched 163 MB in 1min 30s (1,801 kB/s)                                                                                                                                                      
Extracting templates from packages: 100%
dpkg: unrecoverable fatal error, aborting:
 files list for package 'init' is not a regular file
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by ian-weisser on 2017-05-03
Please show us the complete contents of the file: /var/lib/dpkg/info/init.list
If the file won't open, please show us the complete error message.
It's owned by root, so you will need to use sudo.

---

### Post by apeirohedra on 2017-05-03
> **ian-weisser said:**
> Please show us the complete contents of the file: /var/lib/dpkg/info/init.list


In /var/lib/dpkg/info is only one dir
```
sudo ls -lh /var/lib/dpkg/info/
(...)
-rw-r--r-- 1 root        root          521 Jul 20  2016 info.list
-rw-r--r-- 1 root        root          418 Mar 12  2016 info.md5sums
-rwxr-xr-x 1 root        root          507 Mar 12  2016 info.postinst
-rwxr-xr-x 1 root        root          160 Mar 12  2016 info.postrm
-rwxr-xr-x 1 root        root          107 Mar 12  2016 info.prerm
drwxr-xr-x 2 root        root         4.0K Oct  8  2016 init.list
-rw-r--r-- 1 root        root          117 May  2 22:19 init.list-new
-rw-r--r-- 1 root        root          129 Nov 30 14:08 init.md5sums
-rw-r--r-- 1 root        root          358 Jan 13 15:49 initramfs-tools-bin.list
-rw-r--r-- 1 root        root          391 Jan  5 22:46 initramfs-tools-bin.md5sums
-rw-r--r-- 1 root        root          119 Jan  5 22:46 initramfs-tools.conffiles
(...)

```

And inside init.list two files
```
sudo ls -lh /var/lib/dpkg/info/init.list/

-rw-r--r-- 2 root root  55K Aug  3  2016 index.docbook
-rw-r--r-- 2 root root 3.6K Aug  3  2016 legal.xml

```

Just in case
```
sudo cat /var/lib/dpkg/info/init.list-new

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/init
/usr/share/doc/init/copyright
/usr/share/doc/init/changelog.gz

```

---

### Post by apeirohedra on 2017-05-04
> **ian-weisser said:**
> The problem, according to your error message, is that the newly-downloaded 'init' package seems to be corrupt.
Don't fixate on this-kernel-or-that-kernel. The error is coming from apt, not the kernel.

Right, got it. Thanks ian-weisser

I deleted init.list dir and renamed init.list-new file.

---

### Post by ian-weisser on 2017-05-04
Very happy to see that you figured it out. Well done.

---

