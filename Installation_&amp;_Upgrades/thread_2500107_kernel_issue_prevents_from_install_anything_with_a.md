---
title: "kernel issue prevents from install anything with apt-get install"
date: 2024-08-23
forum: Installation &amp; Upgrades
---

### Post by ndresse on 2024-08-23
Hi, I am facing an issue similar to the one here : [https://ubuntuforums.org/showthread.php?t=2499832](https://ubuntuforums.org/showthread.php?t=2499832)
I tried to follow the instructions given, but when I did it I could not boot my machine anymore, the kernel version was 6.8.0.41
Then I booted with kernel version 6.8.0.39 and the boot was successful, I am back at the same point as the beginning : I can't install anything using apt-get install.

Here is what I get when I try : 
```
awadmin@ProtoI9-13900E:~$ sudo apt-get install -y libavcodec-dev libavformat-dev libavutil-dev libavfilter-dev
[sudo] password for awadmin: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
libavcodec-dev is already the newest version (7:6.1.1-3ubuntu5).
libavformat-dev is already the newest version (7:6.1.1-3ubuntu5).
libavutil-dev is already the newest version (7:6.1.1-3ubuntu5).
libavfilter-dev is already the newest version (7:6.1.1-3ubuntu5).
The following packages were automatically installed and are no longer required:
  debsuryorg-archive-keyring linux-headers-6.8.0-40
  linux-headers-6.8.0-40-generic linux-image-6.8.0-40-generic
  linux-modules-6.8.0-40-generic linux-modules-extra-6.8.0-40-generic
  linux-tools-6.8.0-40 linux-tools-6.8.0-40-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-headers-6.8.0-41-generic (6.8.0-41.41) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-41-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-41-generic KERNELRELEASE=6.8.0-41-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-41-generic (x86_64)
Consult /var/lib/dkms/blackmagic-io/12.6a15/build/make.log for more information.
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-41-generic KERNELRELEASE=6.8.0-41-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-41-generic (x86_64)
Consult /var/lib/dkms/blackmagic/12.6a15/build/make.log for more information.
dkms autoinstall on 6.8.0-41-generic/x86_64 failed for blackmagic-io(10) blackmagic(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-41-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-41-generic (--configure):
 installed linux-headers-6.8.0-41-generic package post-installation script subprocess returned error exit status 11
Setting up linux-image-6.8.0-41-generic (6.8.0-41.41) ...
I: /boot/initrd.img is now a symlink to initrd.img-6.8.0-41-generic
Setting up linux-image-6.8.0-40-generic (6.8.0-40.40) ...
I: /boot/initrd.img.old is now a symlink to initrd.img-6.8.0-40-generic
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-6.8.0-41-generic; however:
  Package linux-headers-6.8.0-41-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up linux-headers-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-40-generic KERNELRELEASE=6.8.0-40-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/blackmagic-io/12.6a15/build/make.log for more information.
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-40-generic KERNELRELEASE=6.8.0-40-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/blackmagic/12.6a15/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for blackmagic-io(10) blackmagic(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-40-generic (--configure):
 installed linux-headers-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.8.0-41.41); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for linux-image-6.8.0-41-generic (6.8.0-41.41) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-41-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-41-generic KERNELRELEASE=6.8.0-41-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-41-generic (x86_64)
Consult /var/lib/dkms/blackmagic-io/12.6a15/build/make.log for more information.
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-41-generic KERNELRELEASE=6.8.0-41-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-41-generic (x86_64)
Consult /var/lib/dkms/blackmagic/12.6a15/build/make.log for more information.
dkms autoinstall on 6.8.0-41-generic/x86_64 failed for blackmagic-io(10) blackmagic(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-41-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.8.0-41-generic (--configure):
 installed linux-image-6.8.0-41-generic package post-installation script subprocess returned error exit status 11
No apport report written because MaxReports is reached already
                                                              Processing triggers for linux-image-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-40-generic KERNELRELEASE=6.8.0-40-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/blackmagic-io/12.6a15/build/make.log for more information.
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-40-generic KERNELRELEASE=6.8.0-40-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/blackmagic/12.6a15/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for blackmagic-io(10) blackmagic(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.8.0-40-generic (--configure):
 installed linux-image-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-6.8.0-41-generic
 linux-headers-generic
 linux-headers-6.8.0-40-generic
 linux-generic
 linux-image-6.8.0-41-generic
 linux-image-6.8.0-40-generic
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

On my previous try (on kernel 6.8.0.41 before the reboot fail), I only did this, accordingly to the issue [https://ubuntuforums.org/showthread.php?t=2499832](https://ubuntuforums.org/showthread.php?t=2499832)
sudo rm -rf /var/lib/dkms/blackmagic/12.6a15/source/dkms.conf

Can please anyone take a look and help me out ?

---

### Post by currentshaft on 2024-08-23
upd3ate

---

### Post by ndresse on 2024-08-23
Doing this, the blackmagic-12.6a15 module was completely deleted from the DKMS tree but when I get to the sudo apt-get install --reinstall linux-headers-$(uname -r), still have the same problem :

```
awadmin@ProtoI9-13900E:~$ sudo apt-get install --reinstall linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  debsuryorg-archive-keyring linux-headers-6.8.0-40 linux-headers-6.8.0-40-generic linux-image-6.8.0-40-generic linux-modules-6.8.0-40-generic
  linux-modules-extra-6.8.0-40-generic linux-tools-6.8.0-40 linux-tools-6.8.0-40-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 54 not upgraded.
6 not fully installed or removed.
Need to get 3890 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 linux-headers-6.8.0-39-generic amd64 6.8.0-39.39 [3890 kB]
Fetched 3890 kB in 0s (19.0 MB/s)                      
debconf: delaying package configuration, since apt-utils is not installed
(Reading database ... 214264 files and directories currently installed.)
Preparing to unpack .../linux-headers-6.8.0-39-generic_6.8.0-39.39_amd64.deb ...
Unpacking linux-headers-6.8.0-39-generic (6.8.0-39.39) over (6.8.0-39.39) ...
Setting up linux-headers-6.8.0-41-generic (6.8.0-41.41) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-41-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-41-generic KERNELRELEASE=6.8.0-41-generic...(bad exit status: 2)
Error! Bad return status for module build on kernel: 6.8.0-41-generic (x86_64)
Consult /var/lib/dkms/blackmagic-io/12.6a15/build/make.log for more information.
dkms autoinstall on 6.8.0-41-generic/x86_64 failed for blackmagic-io(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-41-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-41-generic (--configure):
 installed linux-headers-6.8.0-41-generic package post-installation script subprocess returned error exit status 11
Setting up linux-image-6.8.0-41-generic (6.8.0-41.41) ...
I: /boot/initrd.img is now a symlink to initrd.img-6.8.0-41-generic
Setting up linux-image-6.8.0-40-generic (6.8.0-40.40) ...
I: /boot/initrd.img.old is now a symlink to initrd.img-6.8.0-40-generic
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-6.8.0-41-generic; however:
  Package linux-headers-6.8.0-41-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up linux-headers-6.8.0-39-generic (6.8.0-39.39) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-39-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-39-generic KERNELRELEASE=6.8.0-39-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-39-generic (x86_64)
Consult /var/lib/dkms/blackmagic-io/12.6a15/build/make.log for more information.
dkms autoinstall on 6.8.0-39-generic/x86_64 failed for blackmagic-io(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-39-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-39-generic (--configure):
 installed linux-headers-6.8.0-39-generic package post-installation script subprocess returned error exit status 11
Setting up linux-headers-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-40-generic KERNELRELEASE=6.8.0-40-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/blackmagic-io/12.6a15/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for blackmagic-io(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-40-generic (--configure):
 installed linux-headers-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.8.0-41.41); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for linux-image-6.8.0-41-generic (6.8.0-41.41) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-41-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-41-generic KERNELRELEASE=6.8.0-41-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-41-generic (x86_64)
Consult /var/lib/dkms/blackmagic-io/12.6a15/build/make.log for more information.
dkms autoinstall on 6.8.0-41-generic/x86_64 failed for blackmagic-io(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-41-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.8.0-41-generic (--configure):
 installed linux-image-6.8.0-41-generic package post-installation script subprocess returned error exit status 11
No apport report written because MaxReports is reached already
                                                              Processing triggers for linux-image-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j32 KERNELRELEASE=6.8.0-40-generic KERNELRELEASE=6.8.0-40-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/desktopvideo.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/blackmagic-io/12.6a15/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for blackmagic-io(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.8.0-40-generic (--configure):
 installed linux-image-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-6.8.0-41-generic
 linux-headers-generic
 linux-headers-6.8.0-39-generic
 linux-headers-6.8.0-40-generic
 linux-generic
 linux-image-6.8.0-41-generic
 linux-image-6.8.0-40-generic
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by currentshaft on 2024-08-23
log

---

### Post by ndresse on 2024-08-23
A lot of errors and a warning saying the compiler differs from the one used to build the kernel  (gcc-13 vs x86_64-linux-gnu-gcc-13)

Here is the file : 
```
DKMS make.log for blackmagic-io-12.6a15 for kernel 6.8.0-40-generic (x86_64)
Fri Aug 23 14:47:17 UTC 2024
touch .blackmagic.o.cmd
make -C /lib/modules/6.8.0-40-generic/build M=/var/lib/dkms/blackmagic-io/12.6a15/build
make[1]: Entering directory '/usr/src/linux-headers-6.8.0-40-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0
  You are using:           gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bmio_client.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bmio_dev.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bmio_device.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bmio_driver.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bmio_serial.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bmio_export.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bmio_pci_ids.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bm_pci.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bm_util.o
  COPY    /var/lib/dkms/blackmagic-io/12.6a15/build/blackmagic.o
  CC [M]  /var/lib/dkms/blackmagic-io/12.6a15/build/bmio_audio.o
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.c: In function &#8216;bm_mutex_alloc&#8217;:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.c:178:9: error: implicit declaration of function &#8216;mutex_init&#8217;; did you mean &#8216;bm_util_init&#8217;? [-Werror=implicit-function-declaration]
  178 |         mutex_init(mutex);
      |         ^~~~~~~~~~
      |         bm_util_init
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.c: In function &#8216;bm_mutex_lock&#8217;:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.c:189:9: error: implicit declaration of function &#8216;mutex_lock&#8217;; did you mean &#8216;bm_mutex_lock&#8217;? [-Werror=implicit-function-declaration]
  189 |         mutex_lock(mutex);
      |         ^~~~~~~~~~
      |         bm_mutex_lock
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.c: In function &#8216;bm_mutex_trylock&#8217;:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.c:194:17: error: implicit declaration of function &#8216;mutex_trylock&#8217;; did you mean &#8216;bm_mutex_trylock&#8217;? [-Werror=implicit-function-declaration]
  194 |         return (mutex_trylock(mutex) != 0);
      |                 ^~~~~~~~~~~~~
      |                 bm_mutex_trylock
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.c: In function &#8216;bm_mutex_unlock&#8217;:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.c:199:9: error: implicit declaration of function &#8216;mutex_unlock&#8217;; did you mean &#8216;bm_mutex_unlock&#8217;? [-Werror=implicit-function-declaration]
  199 |         mutex_unlock(mutex);
      |         ^~~~~~~~~~~~
      |         bm_mutex_unlock
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_util.c: In function &#8216;bm_alloc_aligned&#8217;:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_util.c:140:37: error: &#8216;MAX_ORDER&#8217; undeclared (first use in this function)
  140 |         if (get_order(alloc_size) < MAX_ORDER)
  
  /var/lib/dkms/blackmagic-io/12.6a15/build/bm_util.c:140:37: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_util.c: At top level:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_util.c:535:13: warning: no previous prototype for &#8216;get_event&#8217; [-Wmissing-prototypes]
  535 | bm_event_t* get_event(void* event, bool create)
      |             ^~~~~~~~~
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_util.c:575:6: warning: no previous prototype for &#8216;put_event&#8217; [-Wmissing-prototypes]
  575 | void put_event(bm_event_t* ev)
      |      ^~~~~~~~~
make[3]: *** [scripts/Makefile.build:243: /var/lib/dkms/blackmagic-io/12.6a15/build/bm_util.o] Error 1
make[3]: *** Waiting for unfinished jobs....
cc1: some warnings being treated as errors
make[3]: *** [scripts/Makefile.build:243: /var/lib/dkms/blackmagic-io/12.6a15/build/bm_locks.o] Error 1
In file included from ./include/linux/pci.h:2695,
                 from /var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.c:31:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.c: In function &#8216;bm_dma_sg_bus_map&#8217;:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.c:240:84: warning: implicit conversion from &#8216;bm_dma_direction_t&#8217; {aka &#8216;enum bm_dma_direction&#8217;} to &#8216;enum dma_data_direction&#8217; [-Wenum-conversion]
  240 |         int nents = dma_map_sg(&pci->pdev->dev, sgTable->sgl, sgTable->orig_nents, dir);
      |                                                                                    ^~~
./include/linux/dma-mapping.h:419:58: note: in definition of macro &#8216;dma_map_sg&#8217;
  419 | #define dma_map_sg(d, s, n, r) dma_map_sg_attrs(d, s, n, r, 0)
      |                                                          ^
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.c: In function &#8216;bm_dma_sg_bus_unmap&#8217;:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.c:257:74: warning: implicit conversion from &#8216;bm_dma_direction_t&#8217; {aka &#8216;enum bm_dma_direction&#8217;} to &#8216;enum dma_data_direction&#8217; [-Wenum-conversion]
  257 |         dma_unmap_sg(&pci->pdev->dev, sgTable->sgl, sgTable->orig_nents, dir);
      |                                                                          ^~~
./include/linux/dma-mapping.h:420:62: note: in definition of macro &#8216;dma_unmap_sg&#8217;
  420 | #define dma_unmap_sg(d, s, n, r) dma_unmap_sg_attrs(d, s, n, r, 0)
      |                                                              ^
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.c: In function &#8216;bm_dma_bus_map_kernel_subpage&#8217;:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.c:344:72: warning: implicit conversion from &#8216;bm_dma_direction_t&#8217; {aka &#8216;enum bm_dma_direction&#8217;} to &#8216;enum dma_data_direction&#8217; [-Wenum-conversion]
  344 |         subpage->busAddr = dma_map_single(&pci->pdev->dev, addr, size, dir);
      |                                                                        ^~~
./include/linux/dma-mapping.h:417:66: note: in definition of macro &#8216;dma_map_single&#8217;
  417 | #define dma_map_single(d, a, s, r) dma_map_single_attrs(d, a, s, r, 0)
      |                                                                  ^
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.c: In function &#8216;bm_dma_bus_unmap_kernel_subpage&#8217;:
/var/lib/dkms/blackmagic-io/12.6a15/build/bm_mm.c:357:76: warning: implicit conversion from &#8216;bm_dma_direction_t&#8217; {aka &#8216;enum bm_dma_direction&#8217;} to &#8216;enum dma_data_direction&#8217; [-Wenum-conversion]
  357 |         dma_unmap_single(&pci->pdev->dev, subpage->busAddr, subpage->size, dir);
      |                                                                            ^~~
./include/linux/dma-mapping.h:418:70: note: in definition of macro &#8216;dma_unmap_single&#8217;
  418 | #define dma_unmap_single(d, a, s, r) dma_unmap_single_attrs(d, a, s, r, 0)
        |                                                                      ^
/var/lib/dkms/blackmagic-io/12.6a15/build/bmio_serial.c:180:18: error: initialization of &#8216;ssize_t (*)(struct tty_struct *, const u8 *, size_t)&#8217; {aka &#8216;long int (*)(struct tty_struct *, const unsigned char *, long unsigned int)&#8217;} from incompatible pointer type &#8216;int (*)(struct tty_struct *, const unsigned char *, int)&#8217; [-Werror=incompatible-pointer-types]
  180 |         .write = serial_write,
      |                  ^~~~~~~~~~~~
/var/lib/dkms/blackmagic-io/12.6a15/build/bmio_serial.c:180:18: note: (near initialization for &#8216;serial_ops.write&#8217;)
cc1: some warnings being treated as errors
make[3]: *** [scripts/Makefile.build:243: /var/lib/dkms/blackmagic-io/12.6a15/build/bmio_serial.o] Error 1
make[2]: *** [/usr/src/linux-headers-6.8.0-40-generic/Makefile:1926: /var/lib/dkms/blackmagic-io/12.6a15/build] Error 2
make[1]: *** [Makefile:240: __sub-make] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-6.8.0-40-generic'
make: *** [Makefile:47: all] Error 2
```

---

