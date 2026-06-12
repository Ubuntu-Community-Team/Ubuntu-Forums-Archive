---
title: "Anbox prevents upgrade to 19.10"
date: 2019-10-23
forum: Installation &amp; Upgrades
---

### Post by Hasimir on 2019-10-23
Hi.

I'm running Ubuntu 19.04 and received the message asking me to upgrade to 19.10.
I happily agreed, but the process keeps aborting with this message:
[B]The upgrade will continue but the 'anbox-modules-dkms' package may not be in a working state.
[/B]
I tried uninstalling the package and its linked elements, but I seem unable to do it properly.
How can I scrape **anbox** away from my system?
(if I'm not mistaken it's only used for Android emulation, something I don't need right now)

Thanks for the help :)

---

### Post by Skaperen on 2019-10-23
what means did you use to do "uninstalling the package and its linked elements"?  what exact error message(s) did you get?

---

### Post by Holger_Gehrke on 2019-10-23
Have you tried the [procedure given on the Anbox-site]("https://docs.anbox.io/userguide/install.html#uninstall-anbox") for uninstalling ?

Holger

---

### Post by Hasimir on 2019-10-23
The remove anbox command says that anbox is not installed.

When I then run ppa-purge I get this error:
> ERROR (dkms apport): kernel package linux-headers-5.3.7-050307-generic is not supported
Error! Bad return status for module build on kernel: 5.3.7-050307-generic (x86_6
4)
Consult /var/lib/dkms/anbox/1/build/make.log for more information.
dpkg: error processing package anbox-modules-dkms (--configure):
 installed anbox-modules-dkms package post-installation script subprocess return
ed error exit status 10
Errors were encountered while processing:
 anbox-modules-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by #&amp;thj^% on 2019-10-23
Have a look in "/var/lib/dkms/anbox/1/build/make.log "

---

### Post by Hasimir on 2019-10-23
```
DKMS make.log for anbox-1 for kernel 5.3.7-050307-generic (x86_64)
Mi 23. Okt 22:17:15 CEST 2019
make: Entering directory '/var/lib/dkms/anbox/1/build/ashmem'
make -C /lib/modules/5.3.7-050307-generic/build V=0 M=$PWD
make[1]: Entering directory '/usr/src/linux-headers-5.3.7-050307-generic'
  CC [M]  /var/lib/dkms/anbox/1/build/ashmem/deps.o
  CC [M]  /var/lib/dkms/anbox/1/build/ashmem/ashmem.o
  LD [M]  /var/lib/dkms/anbox/1/build/ashmem/ashmem_linux.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /var/lib/dkms/anbox/1/build/ashmem/ashmem_linux.mod.o
  LD [M]  /var/lib/dkms/anbox/1/build/ashmem/ashmem_linux.ko
make[1]: Leaving directory '/usr/src/linux-headers-5.3.7-050307-generic'
make: Leaving directory '/var/lib/dkms/anbox/1/build/ashmem'
make: Entering directory '/var/lib/dkms/anbox/1/build/binder'
make -C /lib/modules/5.3.7-050307-generic/build V=0 M=$PWD
make[1]: Entering directory '/usr/src/linux-headers-5.3.7-050307-generic'
  CC [M]  /var/lib/dkms/anbox/1/build/binder/deps.o
  CC [M]  /var/lib/dkms/anbox/1/build/binder/binder.o
/var/lib/dkms/anbox/1/build/binder/binder.c:3382:11: error: initialization of ‘vm_fault_t (*)(struct vm_fault *)’ {aka ‘unsigned int (*)(struct vm_fault *)’} from incompatible pointer type ‘int (*)(struct vm_fault *)’ [-Werror=incompatible-pointer-types]
 3382 |  .fault = binder_vm_fault,
      |           ^~~~~~~~~~~~~~~
/var/lib/dkms/anbox/1/build/binder/binder.c:3382:11: note: (near initialization for ‘binder_vm_ops.fault’)
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:280: /var/lib/dkms/anbox/1/build/binder/binder.o] Error 1
make[1]: *** [Makefile:1626: _module_/var/lib/dkms/anbox/1/build/binder] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.3.7-050307-generic'
make: *** [Makefile:8: all] Error 2
make: Leaving directory '/var/lib/dkms/anbox/1/build/binder'


```

---

### Post by #&amp;thj^% on 2019-10-23
First lets see if we get anywhere with:
```
sudo apt install libelf-dev libelf-devel
```
Paste back so we all can see that return. 
So far one other poster had a fix for himself: [https://github.com/anbox/anbox-modules/issues/28](https://github.com/anbox/anbox-modules/issues/28)

---

### Post by Hasimir on 2019-10-23
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libelf-devel
```

---

### Post by #&amp;thj^% on 2019-10-23
How about just:
```
sudo apt install libelf-dev
```

---

### Post by Hasimir on 2019-10-23
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  elementary-theme example-content fonts-raleway-elementary g++-8 geoclue
  geoclue-ubuntu-geoip gir1.2-mutter-4 golang-1.10-go
  golang-1.10-race-detector-runtime golang-1.10-src libavdevice57
  libclang-8-dev libclang-common-8-dev libclang1-8 libdouble-conversion1
  libept1.5.0 libfdk-aac1 libgeoclue0 libgnome-desktop-3-17 libigdgmm5
  libllvm8 libllvm8:i386 liblouisutdml8 libmbedcrypto1 libmbedtls10 libmp4v2-2
  libmutter-4-0 libmysqlclient20 libobjc-9-dev libpoppler85 libpython3.6
  libpython3.6-minimal libpython3.6-stdlib libx265-165 linux-headers-5.0.0-32
  linux-headers-5.0.0-32-generic linux-tools-5.0.0-32
  linux-tools-5.0.0-32-generic pppconfig pppoeconf python-fasteners
  python-monotonic python3-evdev
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed
  libelf-dev
0 to upgrade, 1 to newly install, 0 to remove and 1 not to upgrade.
1 not fully installed or removed.
Need to get 56,8 kB of archives.
After this operation, 367 kB of additional disk space will be used.
Get:1 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) eoan/main amd64 libelf-dev amd64 0.176-1.1 [56,8 kB]
Fetched 56,8 kB in 0s (295 kB/s)     
Selecting previously unselected package libelf-dev:amd64.
(Reading database ... 474464 files and directories currently installed.)
Preparing to unpack .../libelf-dev_0.176-1.1_amd64.deb ...
Unpacking libelf-dev:amd64 (0.176-1.1) ...
Setting up libelf-dev:amd64 (0.176-1.1) ...
Setting up anbox-modules-dkms (13) ...
Removing old anbox-1 DKMS files...


------------------------------
Deleting module version: 1
completely from the DKMS tree.
------------------------------
Done.
Loading new anbox-1 DKMS files...
Building for 5.3.7-050307-generic
Building initial module for 5.3.7-050307-generic
ERROR (dkms apport): kernel package linux-headers-5.3.7-050307-generic is not su
pported
Error! Bad return status for module build on kernel: 5.3.7-050307-generic (x86_6
4)
Consult /var/lib/dkms/anbox/1/build/make.log for more information.
dpkg: error processing package anbox-modules-dkms (--configure):
 installed anbox-modules-dkms package post-installation script subprocess return
ed error exit status 10
Errors were encountered while processing:
 anbox-modules-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by #&amp;thj^% on 2019-10-23
What is:
```
uname -r
```

---

### Post by Hasimir on 2019-10-23
5.3.7-050307-generic

---

### Post by #&amp;thj^% on 2019-10-23
That baby is dug-in deep, I need to run a few tests. (Give me a sec.)
EDIT: This is what I had in mind, have a look: [https://askubuntu.com/questions/919083/dkms-does-not-automatically-rebuild-after-kernel-upgrade](https://askubuntu.com/questions/919083/dkms-does-not-automatically-rebuild-after-kernel-upgrade)

---

### Post by Hasimir on 2019-10-23
> **1fallen said:**
> That baby is dug-in deep, I need to run a few tests. (Give me a sec.)

Thanks <3

---

### Post by #&amp;thj^% on 2019-10-23
Check my previous post, and then please add:
```
ls -1 /dev/{ashmem,binder}
```

---

### Post by Hasimir on 2019-10-23
ls: cannot access '/dev/ashmem': No such file or directory
ls: cannot access '/dev/binder': No such file or directory

---

### Post by #&amp;thj^% on 2019-10-23
I'm starting to think I'm in over my skills, but:
```
sudo dkms status
```

---

### Post by Hasimir on 2019-10-23
Question... was I supposed to run the commands from the linked page?

Anyway, the last command returns this:
anbox, 1: added

---

### Post by Hasimir on 2019-10-23
I'm doing this...

**$ ls -la /var/lib/dkms/**
total 16
drwxr-xr-x  3 root root 4096 Okt 23 23:27 .
drwxr-xr-x 85 root root 4096 Okt 23 19:40 ..
drwxr-xr-x  3 root root 4096 Okt 23 23:27 anbox
-rw-r--r--  1 root root    6 Mai  6 19:16 dkms_dbversion

**$ lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 19.10
Release:    19.10
Codename:    eoan

**$ apt list dkms -a**
Listing... Done
dkms/eoan,eoan,now 2.7.1-4ubuntu2 all [installed,automatic]

**$ sudo dkms status**
anbox, 1: added

---

### Post by #&amp;thj^% on 2019-10-23
Now let's go for broke:
```

sudo modprobe ashmem_linux
sudo modprobe binder_linux
```
Stop on any error.

---

### Post by Hasimir on 2019-10-23
**$ sudo modprobe ashmem_linux**
modprobe: FATAL: Module ashmem_linux not found in directory /lib/modules/5.3.7-050307-generic

**$ sudo modprobe binder_linux**
modprobe: FATAL: Module binder_linux not found in directory /lib/modules/5.3.7-050307-generic

---

### Post by #&amp;thj^% on 2019-10-23
Interesting, try:
```
sudo apt install -y linux-headers-generic
```

---

### Post by Hasimir on 2019-10-23
**$ sudo apt install -y linux-headers-generic**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version (5.3.0.19.22).
The following packages were automatically installed and are no longer required:
  elementary-theme example-content fonts-raleway-elementary g++-8 geoclue
  geoclue-ubuntu-geoip gir1.2-mutter-4 golang-1.10-go
  golang-1.10-race-detector-runtime golang-1.10-src libavdevice57
  libclang-8-dev libclang-common-8-dev libclang1-8 libdouble-conversion1
  libept1.5.0 libfdk-aac1 libgeoclue0 libgnome-desktop-3-17 libigdgmm5
  libllvm8 libllvm8:i386 liblouisutdml8 libmbedcrypto1 libmbedtls10 libmp4v2-2
  libmutter-4-0 libmysqlclient20 libobjc-9-dev libpoppler85 libpython3.6
  libpython3.6-minimal libpython3.6-stdlib libx265-165 linux-headers-5.0.0-32
  linux-headers-5.0.0-32-generic linux-tools-5.0.0-32
  linux-tools-5.0.0-32-generic pppconfig pppoeconf python-fasteners
  python-monotonic python3-evdev
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up anbox-modules-dkms (13) ...
Removing old anbox-1 DKMS files...


------------------------------
Deleting module version: 1
completely from the DKMS tree.
------------------------------
Done.
Loading new anbox-1 DKMS files...
Building for 5.3.7-050307-generic
Building initial module for 5.3.7-050307-generic
ERROR (dkms apport): kernel package linux-headers-5.3.7-050307-generic is not su
pported
Error! Bad return status for module build on kernel: 5.3.7-050307-generic (x86_6
4)
Consult /var/lib/dkms/anbox/1/build/make.log for more information.
dpkg: error processing package anbox-modules-dkms (--configure):
 installed anbox-modules-dkms package post-installation script subprocess return
ed error exit status 10
Errors were encountered while processing:
 anbox-modules-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by #&amp;thj^% on 2019-10-23
Now I'm on a personal quest to solve this:mad: :)
```
sudo ls -la /usr/src/
```

---

### Post by Hasimir on 2019-10-24
**$ sudo ls -la /usr/src/**
total 44
drwxr-xr-x 11 root root 4096 Okt 23 23:34 .
drwxr-xr-x 15 root root 4096 Apr  4  2019 ..
drwxr-xr-x  4 root root 4096 Okt 17 12:58 anbox-1
drwxr-xr-x  3 root root 4096 Okt  3  2018 libdvd-pkg
drwxr-xr-x 24 root root 4096 Mai  9  2018 linux-headers-4.16.8-041608
drwxr-xr-x 25 root root 4096 Okt 17 11:44 linux-headers-5.0.0-32
drwxr-xr-x  8 root root 4096 Okt 17 11:44 linux-headers-5.0.0-32-generic
drwxr-xr-x 24 root root 4096 Okt 23 19:39 linux-headers-5.3.0-19
drwxr-xr-x  7 root root 4096 Okt 23 19:39 linux-headers-5.3.0-19-generic
drwxr-xr-x 23 root root 4096 Okt 19 23:59 linux-headers-5.3.7-050307
drwxr-xr-x  7 root root 4096 Okt 19 23:58 linux-headers-5.3.7-050307-generic

---

### Post by #&amp;thj^% on 2019-10-24
I just can't reproduce your symptoms, but it really sounds like a "possible" fix would be to boot to kernel "5.0.0-32-generic" then try the suggested UN-install procedure.
You are not getting anywhere with kernel "5.3.7-050307-generic".
I have a 12 hour day at work so I won't be around today.
Good Luck.

---

### Post by Hasimir on 2019-10-24
I'll try that.
Thanks for all the help you gave me!
I'll keep you posted on the results ;)

---

### Post by Hasimir on 2019-10-24
Nope.
I installed and switched to the older kernel...
[B]
$ uname -r[/B]5.0.2-050002-generic

But I keep getting the same results when running the uninstall procedures ( [https://docs.anbox.io/userguide/install.html#uninstall-anbox](https://docs.anbox.io/userguide/install.html#uninstall-anbox) ) T_T

---

### Post by Hasimir on 2019-10-24
SUCCESS! :D
I was trying to remove an ooold version of Skype... and was failing... and ended up opening the Synaptic manager to see if something showed up there. And it did. And I removed it. But still I got errors come up in relation to anbox!

So I thought: what will turn up if I search for "anbox" in Synaptic?
Turns out there was a module.
I marked it for complete removal.
And it worked! :D
No my updates are error free :D

---

### Post by #&amp;thj^% on 2019-10-27
Yep I figured that there was something more to all this. Congrats and good work. :)
Sorry for the delay, my old bones can't handle my work load, hour wise.

---

