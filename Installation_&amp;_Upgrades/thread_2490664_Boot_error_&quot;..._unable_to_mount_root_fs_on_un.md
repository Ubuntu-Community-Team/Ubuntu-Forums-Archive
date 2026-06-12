---
title: "Boot error &quot;... unable to mount root fs on unknown-block(0,0)&quot;"
date: 2023-09-12
forum: Installation &amp; Upgrades
---

### Post by javastarchild on 2023-09-12
How do I fix this boot error.  Thanks in advance.  Hope I didn't paste in too much stuff :(

Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)
.
.
.

I tried boot-repair and get this (partial)

```
~$ sudo apt install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dctrl-tools dh-dkms docker-scan-plugin gcc-12-base:i386 gir1.2-mutter-11 gir1.2-nma-1.0 libabsl20210324 libbpf0 libcfitsio9 libcupsfilters1 libflac8 libfontembed1
  libfwupdplugin7 libgdal31 libgeos3.11.0 libgs9-common libgssdp-1.2-0 libgupnp-1.2-1 libicu71 libicu71:i386 libjavascriptcoregtk-5.0-0 libldap-2.5-0 liblerc3 libmpdec3
  libmutter-11-0 libpcre3 libpoppler123 libprotobuf23 libpython3.10 libpython3.10-minimal libpython3.10-stdlib libqpdf28 libreoffice-ogltrans libreoffice-pdfimport
  librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2 librygel-server-2.6-2 libtbb2 libtiff5 libtiffxx5 libwebkit2gtk-5.0-0 netkit-telnet python3.10
  python3.10-minimal
.... stuff removed ...
... all seems normal removed, then ...

Hunk #1 succeeded at 118 (offset 47 lines).


Building module:
Cleaning build area...(bad exit status: 2)
unset ARCH; [ ! -h /usr/bin/cc ] && export CC=/usr/bin/gcc; env NV_VERBOSE=1 'make' -j16 NV_EXCLUDE_BUILD_MODULES='' KERNEL_UNAME=6.2.0-32-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC
_MISMATCH=1 SYSSRC=/lib/modules/6.2.0-32-generic/build LD=/usr/bin/ld.bfd modules...........(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-kernel-source-520.0.crash'
Error! Bad return status for module build on kernel: 6.2.0-32-generic (x86_64)
Consult /var/lib/dkms/nvidia/520.61.05/build/make.log for more information.
dkms autoinstall on 6.2.0-32-generic/x86_64 failed for nvidia(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.2.0-32-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.2.0-32-generic (--configure):
 installed linux-headers-6.2.0-32-generic package post-installation script subprocess returned error exit status 1
Setting up boot-sav (4ppa203) ...
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-6.2.0-32-generic; however:
  Package linux-headers-6.2.0-32-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up boot-sav-extra (4ppa203) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up boot-repair (4ppa203) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.2.0.32.32); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for man-db (2.11.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu5) ...
Processing triggers for gnome-menus (3.36.0-1.1ubuntu1) ...
Processing triggers for linux-image-6.2.0-32-generic (6.2.0-32.32) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-32-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
applying patch disable_fstack-clash-protection_fcf-protection.patch...patching file Kbuild
Hunk #1 succeeded at 118 (offset 47 lines).


Building module:
Cleaning build area...(bad exit status: 2)
unset ARCH; [ ! -h /usr/bin/cc ] && export CC=/usr/bin/gcc; env NV_VERBOSE=1 'make' -j16 NV_EXCLUDE_BUILD_MODULES='' KERNEL_UNAME=6.2.0-32-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC
_MISMATCH=1 SYSSRC=/lib/modules/6.2.0-32-generic/build LD=/usr/bin/ld.bfd modules........(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-kernel-source-520.0.crash'
Error! Bad return status for module build on kernel: 6.2.0-32-generic (x86_64)
Consult /var/lib/dkms/nvidia/520.61.05/build/make.log for more information.
dkms autoinstall on 6.2.0-32-generic/x86_64 failed for nvidia(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.2.0-32-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.2.0-32-generic (--configure):
 installed linux-image-6.2.0-32-generic package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-6.2.0-32-generic
 linux-headers-generic
 linux-generic
 linux-image-6.2.0-32-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Rubi1200 on 2023-09-12
Hi and welcome to the forums :-)

Did you run this from the liveUSB?

If not, that is what you need to do.

See the boot info script in my signature and follow the instructions to install and run on a USB. Then paste the link to the report here for others to view and diagnose.

---

### Post by yancek on 2023-09-12
Also, more information such as which Ubuntu version you are using and whether this is a new problem?  Did the system ever boot properly?  Did you make some changes that may have caused this problem?  If so, what did you change?  Boot file entries, partition changes, etc.??

---

### Post by MAFoElffen on 2023-09-13
TRY these in succession until one works:

- At the Grub2 Boot menu, choose "Advanced Options" > Select an earlier version kernel and try to boot... It may boot to the Graphical Login. Start a terminal session.

- At the Boot Menu, press the <E> Key to get into edit mode.  <Arrow-Down> to the line that starts with "linux".  <Arrow-Right> until after where it says "quiet splash" and append  with the word "nomodeset". That will prevent the NVidia drivers from loading and may  boot in safe-graphics mode. Start a terminal session.

- At the Grub2 Boot menu, choose Advanced Options > Select an earlier kernel with a Rescue option, and try to boot... It may boot to a Rescue Menu. Then select "network" to enable networking and then "root" to drop to a root prompt.

- At the Boot Menu, press the <E> Key to get into edit mode.  <Arrow-Down> to the line that starts with "linux".  <Arrow-Right> until after where it says "quiet splash" and replace those two words with "-- 3". It should boot to a VTTY where your can enter your credentials to login to a console.

If any of those boot, and you are at a command prompt, then do
```

sudo apt update
sudo apt remove --purge nvidia-driver-*
sudo ubuntu-drivers list

```
Choose a driver version that it finds as potentially compatible with your GPU. 

Let's say it lists "nvidia-driver-530"... Then to install it do:
```

sudo apt install nvidia-driver-530 nvidia-dkms-530

```

---

### Post by javastarchild on 2023-09-16
re: MAFoElffen That worked!!!  Thanks.

The advanced boot options and selecting the previous kernel version had been working for months - that's where I got the error text from originally. Using this command "[COLOR=#000000][FONT=&amp]sudo apt install nvidia-driver-535 nvidia-dkms-535"[/FONT][/COLOR] caused the screen to go blank, but waiting a bit and rebooting - then it booted on default (latest) kernel all seems to be good now.

re: yancek That computer has been working for a few years w/o issues until an update a few months ago and it started failing on latest kernel boot. Ubuntu: 23.04, Kernel Version: Linux 6.2.0-32-generic, GPU: Nvidia GeForce RTX 3060, Computer: Dell XPS 8940, Firmware Version: 2.10.0.  That PC is a dual boot Win11/Ubuntu.  Maybe that info will help someone else.

re: Rubi1200 Didn't have to do the USB boot - but thanks for feed back

Thanks all!!

---

### Post by Rubi1200 on 2023-09-16
Glad to hear you got it sorted out :-)

Please use Thread Tools at the top right of your first post to mark this as Solved so others can benefit from the solution.

---

### Post by MAFoElffen on 2023-09-17
Glad that worked.

Having used NVidia GPU's with Unix and Linux for over 13 years now have taught me, that when things update (especially on a kernel update), that it is going to happen sometimes. I think because the drivers are closed source, the left hand doesn't always know what the right hand is doing and how it will affect each other. I sort of expect that as a way of life, when using NVidia GPU's.

**Explanation for others down the road reading this:** The error in the title indicated that it failed in the nvidia dkms module build process, when it went to update the initramfs image... So later, on boot, it got a "unable to mount root fs" error.

Please keep these instructions handy for if or when it happens again.

---

