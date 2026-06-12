---
title: "linux-image-5.3.0-7625-generic failed to upgrade"
date: 2020-01-05
forum: Installation &amp; Upgrades
---

### Post by gandhi-s-anger-translator on 2020-01-05
I'm a newbie to the Linux environment. Please tell me if I missed out on anything important and sorry if the English is sub par.

apt upgrade didn't finish


At the time of installation, I had some traces of anbox(only anbox-modules-dkms and dkms)

Here's what happened at first :


```
$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-generic linux-headers-5.3.0-7625 linux-headers-5.3.0-7625-generic linux-headers-generic linux-image-5.3.0-7625-generic
  linux-image-generic linux-libc-dev linux-modules-5.3.0-7625-generic linux-modules-extra-5.3.0-7625-generic
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 74.8 MB of archives.
After this operation, 7,168 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 linux-modules-5.3.0-7625-generic amd64 5.3.0-7625.27~1576774585~18.04~c7868f8 [14.1 MB]
Get:2 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 linux-generic amd64 5.3.0-7625.27~1576774585~18.04~c7868f8 [175 kB]
Get:3 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 linux-image-generic amd64 5.3.0-7625.27~1576774585~18.04~c7868f8 [176 kB]
Get:4 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 linux-image-5.3.0-7625-generic amd64 5.3.0-7625.27~1576774585~18.04~c7868f8 [8,902 kB]
Get:5 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 linux-modules-extra-5.3.0-7625-generic amd64 5.3.0-7625.27~1576774585~18.04~c7868f8 [37.7 MB]
Get:6 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 linux-headers-5.3.0-7625 all 5.3.0-7625.27~1576774585~18.04~c7868f8 [11.1 MB]
Get:7 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 linux-headers-generic amd64 5.3.0-7625.27~1576774585~18.04~c7868f8 [175 kB]
Get:8 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 linux-headers-5.3.0-7625-generic amd64 5.3.0-7625.27~1576774585~18.04~c7868f8 [1,279 kB]
Get:9 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 linux-libc-dev amd64 5.3.0-7625.27~1576774585~18.04~c7868f8 [1,233 kB]
Fetched 74.8 MB in 8min 28s (147 kB/s)                                                                                               
(Reading database ... 358901 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-5.3.0-7625-generic_5.3.0-7625.27~1576774585~18.04~c7868f8_amd64.deb ...
Unpacking linux-modules-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) over (5.3.0-7625.27~1576337086~18.04~787b29e) ...
Preparing to unpack .../1-linux-generic_5.3.0-7625.27~1576774585~18.04~c7868f8_amd64.deb ...
Unpacking linux-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) over (5.3.0-7625.27~1576337086~18.04~787b29e) ...
Preparing to unpack .../2-linux-image-generic_5.3.0-7625.27~1576774585~18.04~c7868f8_amd64.deb ...
Unpacking linux-image-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) over (5.3.0-7625.27~1576337086~18.04~787b29e) ...
Preparing to unpack .../3-linux-image-5.3.0-7625-generic_5.3.0-7625.27~1576774585~18.04~c7868f8_amd64.deb ...
Unpacking linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) over (5.3.0-7625.27~1576337086~18.04~787b29e) ...
Preparing to unpack .../4-linux-modules-extra-5.3.0-7625-generic_5.3.0-7625.27~1576774585~18.04~c7868f8_amd64.deb ...
Unpacking linux-modules-extra-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) over (5.3.0-7625.27~1576337086~18.04~787b29e) ...
Preparing to unpack .../5-linux-headers-5.3.0-7625_5.3.0-7625.27~1576774585~18.04~c7868f8_all.deb ...
Unpacking linux-headers-5.3.0-7625 (5.3.0-7625.27~1576774585~18.04~c7868f8) over (5.3.0-7625.27~1576337086~18.04~787b29e) ...
Preparing to unpack .../6-linux-headers-generic_5.3.0-7625.27~1576774585~18.04~c7868f8_amd64.deb ...
Unpacking linux-headers-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) over (5.3.0-7625.27~1576337086~18.04~787b29e) ...
Preparing to unpack .../7-linux-headers-5.3.0-7625-generic_5.3.0-7625.27~1576774585~18.04~c7868f8_amd64.deb ...
Unpacking linux-headers-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) over (5.3.0-7625.27~1576337086~18.04~787b29e) ...
Preparing to unpack .../8-linux-libc-dev_5.3.0-7625.27~1576774585~18.04~c7868f8_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.3.0-7625.27~1576774585~18.04~c7868f8) over (5.3.0-7625.27~1576337086~18.04~787b29e) ...
Setting up linux-modules-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Setting up linux-libc-dev:amd64 (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Setting up linux-headers-5.3.0-7625 (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Setting up linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Setting up linux-headers-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.3.0-7625-generic

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -j4 -C ashmem KERNEL_SRC=/lib/modules/5.3.0-7625-generic/build && make -j4 -C binder KERNEL_SRC=/lib/modules/5.3.0-7625-generic/build.....(bad exit status: 2)
ERROR (dkms apport): kernel package linux-headers-5.3.0-7625-generic is not supported
Error! Bad return status for module build on kernel: 5.3.0-7625-generic (x86_64)
Consult /var/lib/dkms/anbox/1/build/make.log for more information.
   ...done.
Setting up linux-headers-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Setting up linux-modules-extra-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Setting up linux-image-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Setting up linux-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Processing triggers for linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.3.0-7625-generic

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -j4 -C ashmem KERNEL_SRC=/lib/modules/5.3.0-7625-generic/build && make -j4 -C binder KERNEL_SRC=/lib/modules/5.3.0-7625-generic/build....(bad exit status: 2)
ERROR (dkms apport): kernel package linux-headers-5.3.0-7625-generic is not supported
Error! Bad return status for module build on kernel: 5.3.0-7625-generic (x86_64)
Consult /var/lib/dkms/anbox/1/build/make.log for more information.
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-7625-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 34: /etc/default/grub: -----------: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.3.0-7625-generic (--configure):
 installed linux-image-5.3.0-7625-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.3.0-7625-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I had anbox  installed at one point in time, I thought I removed all traces.

I then proceeded to remove, the ppa for anbox-support using ppa-purge(I didn't remove the anbox-modules-dkms first. I really hope this isn't the part where I screwed up). which showed the following:

```
Updating packages lists
PPA to be removed: morphis anbox-support
Package revert list generated:
 anbox-modules-dkms-

Disabling morphis PPA from 
/etc/apt/sources.list.d/morphis-ubuntu-anbox-support-bionic.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  anbox-modules-dkms
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 212 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 358906 files and directories currently installed.)
Removing anbox-modules-dkms (13) ...

-------- Uninstall Beginning --------
Module:  anbox
Version: 1
Kernel:  4.15.0-65-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ashmem_linux.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


binder_linux.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 1
completely from the DKMS tree.
------------------------------
Done.
Setting up linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Processing triggers for linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.3.0-7625-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-7625-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 34: /etc/default/grub: -----------: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.3.0-7625-generic (--configure):
 installed linux-image-5.3.0-7625-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.3.0-7625-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
/usr/sbin/ppa-purge: line 191: aptitude: command not found
Warning:  Something went wrong, packages may not have been reverted

```
 
After which, I removed anbox-modules-dkms, and then purge it... here's the output(I believe the output is similar. I'll just post the output for purge):

```

$ sudo apt purge anbox-modules-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  anbox-modules-dkms*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
(Reading database ... 358884 files and directories currently installed.)
Purging configuration files for anbox-modules-dkms (13) ...
Processing triggers for linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.3.0-7625-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-7625-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 34: /etc/default/grub: -----------: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.3.0-7625-generic (--configure):
 installed linux-image-5.3.0-7625-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.3.0-7625-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Like any good netizen would do, I went straight to duckduckgo and did a quick search or two...
I have tried doing the following commands to fix it:
```
$sudo dpkg --configure -a
```
```
Setting up linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Processing triggers for linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.3.0-7625-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-7625-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 34: /etc/default/grub: -----------: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.3.0-7625-generic (--configure):
 installed linux-image-5.3.0-7625-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.3.0-7625-generic
```
```
$ sudo apt-get -f install
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
Processing triggers for linux-image-5.3.0-7625-generic (5.3.0-7625.27~1576774585~18.04~c7868f8) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-7625-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 34: /etc/default/grub: -----------: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.3.0-7625-generic (--configure):
 installed linux-image-5.3.0-7625-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.3.0-7625-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



Can anyone point me towards the right plan of action and perhaps hint me of my faults?

---

### Post by webaake on 2020-01-06
Seems that  /etc/default/grub is  missing and Grub needs it. I don't know why but here's a link that might help you: 


[https://askubuntu.com/questions/1092012/missing-etc-default-grub-file-need-to-edit-boot-order-grub-reinstall-doesnt](https://askubuntu.com/questions/1092012/missing-etc-default-grub-file-need-to-edit-boot-order-grub-reinstall-doesnt)

---

### Post by gandhi-s-anger-translator on 2020-01-06
I did have the file... which was what made me worried

I found a link that was able to help from this very forum, that was able to help
[https://ubuntuforums.org/showthread.php?p=10707336#poststop](https://ubuntuforums.org/showthread.php?p=10707336#poststop)

Done as adviced by drs305

---

