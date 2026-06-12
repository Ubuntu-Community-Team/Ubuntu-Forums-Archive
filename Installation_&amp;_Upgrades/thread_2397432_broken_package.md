---
title: "broken package"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by rcrahul60 on 2018-07-29
when i run --fix-broken install the output is:

pkg: error processing archive /var/cache/apt/archives/libglx-mesa0_18.0.5-0ubuntu0~18.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libGLX_indirect.so.0', which is also in package nvidia-396 396.37-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/libglx-mesa0_18.0.5-0ubuntu0~18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Problem is how can i remove and install again to fix this file?

---

### Post by Frogs Hair on 2018-07-29
Post the output of the following. ```
sudo apt update
```

---

### Post by rcrahul60 on 2018-07-30
it does't work

---

### Post by Frogs Hair on 2018-07-30
No error or output at all ?

---

### Post by rcrahul60 on 2018-07-31
a**pt update showing no error but while ****i**** try to install anything:**
tbosss@tbosss:~/Downloads/platform-tools_r28.0.0-linux(1)/platform-tools$ sudo apt install android-tools-adb android-tools-fastboot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 android-tools-adb : Depends: adb but it is not going to be installed
 android-tools-fastboot : Depends: fastboot but it is not going to be installed
 libglx-mesa0 : Depends: libglapi-mesa (= 18.0.0~rc5-1ubuntu1) but 18.0.5-0ubuntu0~18.04.1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

**while running --fix-broken install:**

tbosss@tbosss:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libglx-mesa0
The following packages will be upgraded:
  libglx-mesa0
1 upgraded, 0 newly installed, 0 to remove and 101 not upgraded.
5 not fully installed or removed.
Need to get 0 B/132 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 209349 files and directories currently installed.)
Preparing to unpack .../libglx-mesa0_18.0.5-0ubuntu0~18.04.1_amd64.deb ...
Unpacking libglx-mesa0:amd64 (18.0.5-0ubuntu0~18.04.1) over (18.0.0~rc5-1ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libglx-mesa0_18.0.5-0ubuntu0~18.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libGLX_indirect.so.0', which is also in package nvidia-396 396.37-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/libglx-mesa0_18.0.5-0ubuntu0~18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rcrahul60 on 2018-07-31
found the solution need to force overwrite.

thanks

---

### Post by siloria on 2018-10-15
sudo apt-get -o Dpkg::Options::="--force-overwrite"install--fix-broken

hope it helps..

---

