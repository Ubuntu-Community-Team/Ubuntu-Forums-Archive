---
title: "lots of stuff broken after X upgrade"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by herot on 2006-08-30
one of the updates upgraded my X11 system... and then i noticed very degraded performance in 3d games... also amarok wont launch anymore nor will synaptic!!

i cant even do a 'apt-get dist-upgrade' now...

this is the error i get...
```

root@Armagh:/home/herot# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
The following NEW packages will be installed:
  compiz-core compiz-plugins
The following packages have been kept back:
  totem
The following packages will be upgraded:
  compiz compiz-gnome libdrm2 libgl1-mesa libgl1-mesa-dri libglu1-mesa
  libkrb53 libmagick9 libtag1c2a libtheora0 mesa-utils wine xserver-xorg-core
13 upgraded, 2 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 103kB/27.8MB of archives.
After unpacking 21.3MB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Get:1 http://archive.ubuntu.com dapper-backports/main libtag1c2a 1.4-4~dapper1 [103kB]
Fetched 103kB in 1s (93.4kB/s)
(Reading database ... 111820 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Armagh:/home/herot#

```

---

### Post by mlind on 2006-08-30
Could you post the output of
```

dpkg -S /usr/lib/libGL.so.1

```

---

### Post by herot on 2006-08-30
root@Armagh:/home/herot# dpkg -S /usr/lib/libGL.so.1
diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1
diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.xlibmesa
libgl1-mesa: /usr/lib/libGL.so.1
root@Armagh:/home/herot#

---

### Post by herot on 2006-08-31
can anyone help??

---

### Post by herot on 2006-09-01
please help meee

---

### Post by mlind on 2006-09-02
You probably need to manually resolve this error which is caused by xorg-driver-fglrx diversion. I'm not sure why pacakge manager wants this package removed, isn't that the binary ATI driver?

Try removing it manually first, then doing apt-get upgrade
```

sudo dpkg -P xorg-driver-fglrx

```

If same error remains, you must manually rename offending /usr/lib/libGL.so.1. Could you post the output of
```

ls /usr/lib/libGL.so.1*

```

---

### Post by herot on 2006-09-03
```

root@Armagh:/home/herot# sudo dpkg -P xorg-driver-fglrx
(Reading database ... 111820 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
root@Armagh:/home/herot#

```

and here is the output of the other command...

```
root@Armagh:/home/herot# ls /usr/lib/libGL.so.1*
/usr/lib/libGL.so.1
root@Armagh:/home/herot#

```

---

### Post by mlind on 2006-09-04
You should be able to solve this issue by temorarily renaming /usr/lib/libGL.so.1 file or move it to some backup folder.
If you **don't** have **libgl1-mesa** package installed, then you can completely remove libGL.so.1. Otherwise remember to rename/copy file back after you've removed xorg-driver-fglrx package.

This problem is caused diversion which dpkg can't resolve for some reason (buggy removal script in ati's xorg-driver-fglrx package). 
Diversion is used when two different packages want to install a file with same name.

---

