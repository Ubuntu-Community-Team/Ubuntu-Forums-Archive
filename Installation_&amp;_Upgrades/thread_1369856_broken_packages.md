---
title: "broken packages"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by joedoe47 on 2010-01-01
hey there, this is my first post here on the ubuntu forums. although I am a noob on the forum I'm not new to linux.

after following a guide to sync my ipod touch (3.1.2) and it 'seemed' to work but there were originally 3 broken packages and after trying to run "sudo apt-get auto-remove" and "sudo apt-get -f install" and "sudo dpkg --configure --pending". I even cleared the cached packages that synaptic has, I got it down to 2 left broken packages, without knowing what the heck happened :confused: and was wondering if anyone here could help out.:guitar:

synaptic outputs this when I try to automatically fix broken packages...
> E: /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb: trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0
E: /var/cache/apt/archives/usbmuxd_1.0.1-0ubuntu1~k_amd64.deb: trying to overwrite '/usr/sbin/usbmuxd', which is also in package libusbmux0 0

and what I receive when I try to do this via terminal
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libusbmuxd1 usbmuxd
The following NEW packages will be installed:
  libusbmuxd1 usbmuxd
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
joedoe47@joedoe47-laptop:~$ sudo apt-get -f  install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libusbmuxd1 usbmuxd
The following NEW packages will be installed:
  libusbmuxd1 usbmuxd
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/40.8kB of archives.
After this operation, 213kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 187747 files and directories currently installed.)
Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Unpacking usbmuxd (from .../usbmuxd_1.0.1-0ubuntu1~k_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/usbmuxd_1.0.1-0ubuntu1~k_amd64.deb (--unpack):
 trying to overwrite '/usr/sbin/usbmuxd', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb
 /var/cache/apt/archives/usbmuxd_1.0.1-0ubuntu1~k_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I've read this may be 4-5 times and get confused when I try to read and follow what is being done. Hope to get this fixed somehow...:mad:

*edit:
here are the sites I used as a guide and made it seem to work, but not really cuz of the broken packages
[http://www.mexlinux.com/how-to-sync-music-between-iphone-and-ubuntu/](http://www.mexlinux.com/how-to-sync-music-between-iphone-and-ubuntu/)
[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)

---

### Post by joedoe47 on 2010-01-01
btw, I hope I posted in the right area... if I didn't if a mod could move it to where it's supposed to go.

---

### Post by Soul-Sing on 2010-01-01
libusbmuxd1_1.0.1-0ubuntu1
usbmuxd_1.0.1-0ubuntu1

```
gksudo nautilus
```
navigate via nautilus to:

/var/cache/apt/archives
and remove the above mentioned packages

```
sudo apt-get update
```

---

### Post by joedoe47 on 2010-01-01
idk, I got rid of them and updated  but when I go to fix the dependencies I still get the same error...

---

### Post by joedoe47 on 2010-01-01
never mind I resolved the issue. I first un-installed all of the programs that were broken (mind you this also un-installed ifuse, rhythmbox, gtkpod, libpod, and a couple I don't remember) however then I logout out and logged back in, started the process all over again and for some reason it worked.

heh. another reason to love ubuntu... you can have a bunch of errors and still be able to run and fix it (like to see windows do that)

---

### Post by tim.inman on 2010-01-05
I have the same problem.  I believe that this was triggered by an update.  I haven't been able to fix mine yet.

---

### Post by Vince N on 2010-02-01
SOunds like there might be an older package that is causing a conflict.  Try removing libusbmux0 first and then install usbmuxd

---

