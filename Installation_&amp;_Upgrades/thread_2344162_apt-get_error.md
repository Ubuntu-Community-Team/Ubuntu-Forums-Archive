---
title: "apt-get error"
date: 2016-11-23
forum: Installation &amp; Upgrades
---

### Post by featheredseclude on 2016-11-23
So I went to install PlayonLinux and GPart.
Since those, I have been getting the error

```
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.
conf.d/' as it has an invalid filename extension
featheredseclude@featheredseclude-T900:~$ ls -l /etc/apt/apt.conf.d/
```

I've read on a solved thread under a very similar name, and those did not help my case.
This is the thread I viewed:
[https://ubuntuforums.org/showthread.php?t=1897475]("https://ubuntuforums.org/showthread.php?t=1897475")

When I go to remove the "50unattended..." file.

I get this:

```
rm: cannot remove '/etc/apt/apt.conf.d/50unattended-upgrades.distrib': No such file or directory
```

I did recently update from Kubuntu 15.10 to 16.04, if that has anything to do with it.
I try to keep it up-to-date.

I ran this command, as that thread read:
```
ls -l /etc/apt/apt.conf.d/
```

These are my results for this:

```
total 56
-rw-r--r-- 1 root root   49 nov 22  2016 00aptitude
-rw-r--r-- 1 root root   40 nov 22  2016 00trustcdrom
-rw-r--r-- 1 root root  769 nov  2 11:43 01autoremove
-r--r--r-- 1 root root 3343 nov 22  2016 01autoremove-kernels
-rw-r--r-- 1 root root   42 nov  2 11:43 01-vendor-ubuntu
-rw-r--r-- 1 root root  129 sep 17  2015 10periodic
-rw-r--r-- 1 root root  108 sep 17  2015 15update-stamp
-rw-r--r-- 1 root root   85 sep 17  2015 20archive
-rw-r--r-- 1 root root  243 dic 16  2009 20dbus
-rw-r--r-- 1 root root 1432 abr 18  2016 50appstream
-rw-r--r-- 1 root root 2331 ago 11  2015 50unattended-upgrades
-rw-r--r-- 1 root root 2367 nov 22  2016 50unattended-upgrades.ucf-dist
-rw-r--r-- 1 root root  182 ago 12  2015 70debconf
-rw-r--r-- 1 root root  305 may 24 11:48 99update-notifier
```

Any and all help to get this fixed would be greatly appreciated.
Thank you~

---

### Post by deadflowr on 2016-11-23
The remove error was right, you don't have that file.
Yours is 
```
50unattended-upgrades.ucf-dist
```
not
```
50unattended-upgrades.distrib
```
try again with your file name.

As to the meaning of the error, (not an error a warning, see:
[https://ubuntuforums.org/showthread.php?t=2342917]("https://ubuntuforums.org/showthread.php?t=2342917")

---

