---
title: "linux-images and hwe not (fully) installed 16.04"
date: 2017-06-11
forum: Installation &amp; Upgrades
---

### Post by crazybear on 2017-06-11
OK. Was forced off of Ubuntu 12.04 in which all worked fine by end of  support to same. Moved, with great difficulty, most of what I had to  16.04. Was aware of problems 16.04 had with AMD GPUs [I have a Radeon 7970]. And  [sometimes - about one boot in ten] my 3 head system would have either  one monitor flickering/blurry or simply black.  
  In effort to fix this I tried after some research on answers to upgrade to *linux-generic-hwe-16.04* and add *linux-image-4.8.0-53* and *54*.
Now, the entire system is messed up pretty well and with command sudo dpkg --configure -a I just got the following:

  [note - had to leave out much I wanted to post as system said was  'spam'. I forgot how to post text that scrolled to save space.]

```
  dpkg: dependency problems prevent configuration of linux-generic-hwe-16.04:
 linux-generic-hwe-16.04 depends on linux-image-generic-hwe-16.04 (= 4.8.0.54.25); however:
  Package linux-image-generic-hwe-16.04 is not configured yet.

dpkg: error processing package linux-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-virtual-hwe-16.04:
 linux-image-extra-virtual-hwe-16.04 depends on linux-image-generic-hwe-16.04 (= 4.8.0.54.25); however:
  Package linux-image-generic-hwe-16.04 is not configured yet.

dpkg: error processing package linux-image-extra-virtual-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-4.4.0-79-generic
 linux-image-4.8.0-53-generic
 linux-image-extra-4.4.0-79-generic
 linux-image-4.8.0-54-generic
 linux-image-extra-4.8.0-53-generic
 linux-image-generic
 linux-image-extra-4.8.0-54-generic
 linux-image-generic-hwe-16.04
 linux-generic
 linux-generic-lts-vivid
 linux-generic-hwe-16.04
 linux-image-extra-virtual-hwe-16.04
```

---

### Post by Impavidus on 2017-06-11
The vital part of the error message, usually the first error reported, is missing. I understand you posted this first on ask ubuntu. You should be able to post the entire message here, in [noparse]```
code tags
```[/noparse], for readability.

---

### Post by crazybear on 2017-06-11
Ok, will try again, see two posts above for explanation. I don't know which is the cart and which the horse...but I also can't update grub. [cause or effect?]

```

$ sudo dpkg --configure -a
[sudo] password for crazybear: 
Setting up linux-image-4.4.0-79-generic (4.4.0-79.100) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-79-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-79-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-4.8.0-53-generic (4.8.0-53.56~16.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.8.0-53-generic.postinst line 1052.
dpkg: error processing package linux-image-4.8.0-53-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-79-generic:
 linux-image-extra-4.4.0-79-generic depends on linux-image-4.4.0-79-generic; however:
  Package linux-image-4.4.0-79-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-79-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.8.0-54-generic.postinst line 1052.
dpkg: error processing package linux-image-4.8.0-54-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.8.0-53-generic:
 linux-image-extra-4.8.0-53-generic depends on linux-image-4.8.0-53-generic; however:
  Package linux-image-4.8.0-53-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.8.0-53-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-79-generic; however:
  Package linux-image-4.4.0-79-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-79-generic; however:
  Package linux-image-extra-4.4.0-79-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.8.0-54-generic:
 linux-image-extra-4.8.0-54-generic depends on linux-image-4.8.0-54-generic; however:
  Package linux-image-4.8.0-54-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.8.0-54-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-hwe-16.04:
 linux-image-generic-hwe-16.04 depends on linux-image-4.8.0-54-generic; however:
  Package linux-image-4.8.0-54-generic is not configured yet.
 linux-image-generic-hwe-16.04 depends on linux-image-extra-4.8.0-54-generic; however:
  Package linux-image-extra-4.8.0-54-generic is not configured yet.

dpkg: error processing package linux-image-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.79.85); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-vivid:
 linux-generic-lts-vivid depends on linux-generic; however:
  Package linux-generic is not configured yet.

dpkg: error processing package linux-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-hwe-16.04:
 linux-generic-hwe-16.04 depends on linux-image-generic-hwe-16.04 (= 4.8.0.54.25); however:
  Package linux-image-generic-hwe-16.04 is not configured yet.

dpkg: error processing package linux-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-virtual-hwe-16.04:
 linux-image-extra-virtual-hwe-16.04 depends on linux-image-generic-hwe-16.04 (= 4.8.0.54.25); however:
  Package linux-image-generic-hwe-16.04 is not configured yet.

dpkg: error processing package linux-image-extra-virtual-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-4.4.0-79-generic
 linux-image-4.8.0-53-generic
 linux-image-extra-4.4.0-79-generic
 linux-image-4.8.0-54-generic
 linux-image-extra-4.8.0-53-generic
 linux-image-generic
 linux-image-extra-4.8.0-54-generic
 linux-image-generic-hwe-16.04
 linux-generic
 linux-generic-lts-vivid
 linux-generic-hwe-16.04
 linux-image-extra-virtual-hwe-16.04

```

---

### Post by Impavidus on 2017-06-11
> **crazybear said:**
> Ok, will try again, see two posts above for explanation. I don't know which is the cart and which the horse...but I also can't update grub. [cause or effect?]

```

...
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
...

```

Found this: [https://ubuntuforums.org/showthread.php?t=2355841](https://ubuntuforums.org/showthread.php?t=2355841)
Interestingly, it's your own thread of three months ago. That was a hard one to fix, but you managed last time. This seems to be a problem related to grub-customizer.

---

### Post by crazybear on 2017-06-12
I just went through that old and long thread and tried some of the steps used then, but did not fix anything. all grub entries are 'ii', and the magic formula [I thought] last time did not work - in fact would not run: [but I may be confused...and no doubt am]
$ dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
dpkg: error: --purge needs at least one package name argument


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !

I'm stuck, unable to remove problem kernels or install ones I need. Help again, please.

```

$ ls -al /usr/src/
total 88
drwxr-xr-x 22 root root 4096 Jun 12 06:39 .
drwxr-xr-x 14 root root 4096 Apr 28  2016 ..
drwxr-xr-x  3 root root 4096 May 15  2016 libdvd-pkg
drwxr-xr-x 24 root root 4096 Jun 25  2015 linux-headers-3.13.0-57
drwxr-xr-x  7 root root 4096 Jun 25  2015 linux-headers-3.13.0-57-generic
drwxr-xr-x 27 root root 4096 Apr 28  2016 linux-headers-4.4.0-21
drwxr-xr-x  7 root root 4096 Apr 28  2016 linux-headers-4.4.0-21-generic
drwxr-xr-x 27 root root 4096 May 18  2016 linux-headers-4.4.0-22
drwxr-xr-x  7 root root 4096 May 18  2016 linux-headers-4.4.0-22-generic
drwxr-xr-x 27 root root 4096 May 28 05:20 linux-headers-4.4.0-78
drwxr-xr-x  7 root root 4096 May 28 05:20 linux-headers-4.4.0-78-generic
drwxr-xr-x 27 root root 4096 Jun  7 19:08 linux-headers-4.4.0-79
drwxr-xr-x  7 root root 4096 Jun  7 19:08 linux-headers-4.4.0-79-generic
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3
drwxr-xr-x  8 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3-generic
drwxr-xr-x 27 root root 4096 Jun  6 12:53 linux-headers-4.8.0-53
drwxr-xr-x  7 root root 4096 Jun  6 12:53 linux-headers-4.8.0-53-generic
drwxr-xr-x 27 root root 4096 Jun  7 19:08 linux-headers-4.8.0-54
drwxr-xr-x  7 root root 4096 Jun  7 19:08 linux-headers-4.8.0-54-generic
drwxr-xr-x  6 root root 4096 Jun 11 13:11 oem-audio-hda-daily-lts-xenial-0.201706100731~ubuntu16.04.1
drwxr-xr-x 12 root root 4096 May 12 05:55 virtualbox-5.0.40

```

```

$ dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                               amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                                  4.0ubuntu1                                           all          Linux image base package
ii  linux-firmware                                              1.157.10                                             all          Firmware for Linux kernel drivers
iU  linux-generic                                               4.4.0.79.85                                          amd64        Complete Generic Linux kernel and headers
iU  linux-generic-hwe-16.04                                     4.8.0.54.25                                          amd64        Complete Generic Linux kernel and headers
iU  linux-generic-lts-vivid                                     4.4.0.79.85                                          amd64        Complete Generic Linux kernel and headers (dummy transitional package)
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-22                                      4.4.0-22.40                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-22-generic                              4.4.0-22.40                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-78                                      4.4.0-78.99                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-78-generic                              4.4.0-78.99                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-79                                      4.4.0-79.100                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-79-generic                              4.4.0-79.100                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600                                  4.6.0-040600.201605151930                            all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3                               4.6.0-040600rc3.201604120934                         all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3-generic                       4.6.0-040600rc3.201604120934                         amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-53                                      4.8.0-53.56~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-53-generic                              4.8.0-53.56~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-54                                      4.8.0-54.57~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-54-generic                              4.8.0-54.57~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.79.85                                          amd64        Generic Linux kernel headers
ii  linux-headers-generic-hwe-16.04                             4.8.0.54.25                                          amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic                                4.4.0-22.40                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-72-generic                                4.4.0-72.93                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-75-generic                                4.4.0-75.96                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-77-generic                                4.4.0-77.98                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-78-generic                                4.4.0-78.99                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-79-generic                                4.4.0-79.100                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.8.0-53-generic                                4.8.0-53.56~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
iF  linux-image-4.8.0-54-generic                                4.8.0-54.57~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-22-generic                          4.4.0-22.40                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-72-generic                          4.4.0-72.93                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-75-generic                          4.4.0-75.96                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-77-generic                          4.4.0-77.98                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic                          4.4.0-78.99                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-79-generic                          4.4.0-79.100                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.8.0-53-generic                          4.8.0-53.56~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-4.8.0-54-generic                          4.8.0-54.57~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-virtual-hwe-16.04                         4.8.0.54.25                                          amd64        Extra drivers for Virtual Linux kernel image
iU  linux-image-generic                                         4.4.0.79.85                                          amd64        Generic Linux kernel image
iU  linux-image-generic-hwe-16.04                               4.8.0.54.25                                          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-79.100                                         amd64        Linux Kernel Headers for development
ii  linux-lts-vivid-tools-common                                3.19.0-18.18~14.04.1                                 all          Linux kernel version specific tools for version 3.19.0
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                                 all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                                all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                                 amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Impavidus on 2017-06-12
My suspicion last time, although I can't be completely sure about it, is that the scripts used to update grub were somehow damaged by grub-customizer. Do you still use it? It might help if you reset it to some simple default settings. I've never used grub-customizer. If it wasn't that, something else damaged the scripts to update grub.

---

### Post by crazybear on 2017-06-12
No, I'm almost certain that grub-customizer is NOT the problem. It was working fine with it before. It only got broken when I tried to add the new kernels, as with last time. Yes, I use it and it has never given a problem except these two occasions I was trying to add several new kernels at the same time. In 12.04 and 14.04 [as well as all the time I little used 16.04 except these two occasions mentioned] grub-customizer has worked fine for years. It is just a GUI interface for grub.

But following the general plan of last time, this time I have not been sucessful in clearing things up. Help would be appreciated to know what to do/try first, second, etc.

I spent about two hours last night going over the suggestions and methods used in [https://ubuntuforums.org/showthread.php?t=2355841](https://ubuntuforums.org/showthread.php?t=2355841), but nothing worked and nothing much changed except I had a very difficult time booting up this morning...but I'm back in. I had grub customizer on 12.04 for five years and it never gave me a day or hour of trouble. I had it on 14.04 for a long time without problems too - and on 16.04 and only now does it 'appear' to be problematic - but I think as a result, not as a cause. Anyway, to humor those who think it is a problem I tried to remove it, but now I can NOT remove or add anything. Ideas how to proceed? This morning was also a day when one of my three monitors was not working - on a VERY powerful AMD Radeon GPU - the reason I was trying to put in these new kernels and stack, when things got messed up. I have only one working kernel now and am very worried. 12.04 is not working, nor is 14.04 [can not get internet - network conf files all messed up!].....please help before I loose the ability to do anything on the computer. Thanks.

Ah...Please folks, I really need to fix my Ubuntu 16.04. Again, I have only one kernel working and often when I boot up one of my three monitors goes crazy. I assume it is the well-known problem 16.04  has with AMD GPUs. I read that the new hwe and the newer kernels [4.8] often solved this problem [my GPU is not old and is quite powerful..but it is AMD Radeon], and that is how I got from a stable system to the mess I'm in now somehow. A 'fresh install' for me is a full month's work due to how my system is set up, so that is not an option - or one that I view as close to death and/or torture. I'd really appreciate some advice on how to get things installed and stable again! Again, while something similar happened a few months ago, following what I was instructed to do and did then is NOT working now - not at all. Thanks in advance.

```

$ dpkg -l | grep linux-image*
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic                                4.4.0-22.40                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-72-generic                                4.4.0-72.93                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-75-generic                                4.4.0-75.96                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-77-generic                                4.4.0-77.98                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-78-generic                                4.4.0-78.99                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-79-generic                                4.4.0-79.100                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.8.0-53-generic                                4.8.0-53.56~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
iF  linux-image-4.8.0-54-generic                                4.8.0-54.57~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-22-generic                          4.4.0-22.40                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-72-generic                          4.4.0-72.93                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-75-generic                          4.4.0-75.96                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-77-generic                          4.4.0-77.98                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic                          4.4.0-78.99                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-79-generic                          4.4.0-79.100                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.8.0-53-generic                          4.8.0-53.56~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-4.8.0-54-generic                          4.8.0-54.57~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-virtual-hwe-16.04                         4.8.0.54.25                                          amd64        Extra drivers for Virtual Linux kernel image
iU  linux-image-generic                                         4.4.0.79.85                                          amd64        Generic Linux kernel image
iU  linux-image-generic-hwe-16.04                               4.8.0.54.25                                          amd64        Generic Linux kernel image

$ ls /boot
abi-4.4.0-21-generic  abi-4.8.0-54-generic     config-4.8.0-53-generic      initrd.img-4.4.0-22-generic  memtest86+.bin               System.map-4.4.0-78-generic  vmlinuz-4.4.0-22-generic
abi-4.4.0-22-generic  config-4.4.0-21-generic  config-4.8.0-54-generic      initrd.img-4.4.0-78-generic  memtest86+.elf               System.map-4.4.0-79-generic  vmlinuz-4.4.0-78-generic
abi-4.4.0-78-generic  config-4.4.0-22-generic  grub                         initrd.img-4.4.0-79-generic  memtest86+_multiboot.bin     System.map-4.8.0-53-generic  vmlinuz-4.4.0-79-generic
abi-4.4.0-79-generic  config-4.4.0-78-generic  grub.bak                     initrd.img-4.8.0-53-generic  System.map-4.4.0-21-generic  System.map-4.8.0-54-generic  vmlinuz-4.8.0-53-generic
abi-4.8.0-53-generic  config-4.4.0-79-generic  initrd.img-4.4.0-21-generic  initrd.img-4.8.0-54-generic  System.map-4.4.0-22-generic  vmlinuz-4.4.0-21-generic     vmlinuz-4.8.0-54-generic

$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs   12G     0   12G   0% /dev
tmpfs          tmpfs     2.4G   19M  2.4G   1% /run
/dev/sdc1      ext4      909G  736G  127G  86% /
tmpfs          tmpfs      12G  333M   12G   3% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs      12G     0   12G   0% /sys/fs/cgroup
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     2.4G   12K  2.4G   1% /run/user/125
tmpfs          tmpfs     2.4G  100K  2.4G   1% /run/user/1000

```

I just noticed that the 4.8 kernels are listed as 16.04.1, and I have, I believe 16.04.2....not sure if this is a problem or not and what makes it one or the other.

---

### Post by Bashing-om on 2017-06-16
crazybear; Hey hey - we meet once more.

[INDENT]crazybear has requested my presence - here I am[/INDENT]

Willing to see what we can do, but, 1st is to determine what we are going to do.
How does " linux-image-extra-virtual-hwe-16.04" - " drwxr-xr-x 12 root root 4096 May 12 05:55 virtualbox-5.0.40" - play into this ? Are we running on bare metal here ?
What is the reason that you are attempting to install HWE ? Is there a demonstrated need for the later kernels and stack ?
To compound the problem there is " linux-generic-lts-vivid depends on linux-generic; however:" as vivid is no longer supported . That needs to go; somehow .

And experimental stuff ?? what prompts the installation of " linux-headers-4.6.0-040600rc3  " and others ?

As you can see there is a lot of work to do .. will take a lot of time and effort - no matter how we look at this . Are you willing to put forth this time and effort ? Keeping in mind that a fresh clean install only takes a matter of minutes .

[INDENT][INDENT]'buntu - fixable - 
[/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-17
> **Bashing-om said:**
> crazybear; Hey hey - we meet once more.[INDENT]crazybear has requested my presence - here I am[/INDENT]

Willing to see what we can do, but, 1st is to determine what we are going to do.
How does " linux-image-extra-virtual-hwe-16.04" - " drwxr-xr-x 12 root root 4096 May 12 05:55 virtualbox-5.0.40" - play into this ? Are we running on bare metal here ?
What is the reason that you are attempting to install HWE ? Is there a demonstrated need for the later kernels and stack ?
To compound the problem there is " linux-generic-lts-vivid depends on linux-generic; however:" as vivid is no longer supported . That needs to go; somehow .

And experimental stuff ?? what prompts the installation of " linux-headers-4.6.0-040600rc3  " and others ?

As you can see there is a lot of work to do .. will take a lot of time and effort - no matter how we look at this . Are you willing to put forth this time and effort ? Keeping in mind that a fresh clean install only takes a matter of minutes .[INDENT][INDENT]'buntu - fixable - 
[/INDENT]
[/INDENT]


As I said above, a 'clean-install' for me means a month of work after the 'clean-install' - so that is the very last thing I want to try. As I also mentioned above, often when I boot up into 16.04 one of my three monitors will not work or is so blurry it can not be used - and I must reboot [sometimes several times until it is stable]. From researching, I think the problem is that I have an AMD Radeon 7970 Tahiti GPU and the AMD drivers don't work with 16.04 [and the linux AMD drivers don't always work so well]. Others said they solved the problem with similar GPUs by adding the new stack and the newer kernels - that was why I tried to add them. As for virtualbox, I'm confused exactly what you are referring to. I have virtualbox installed and plan to use it sometime, but have NOT set it up yet and it shouldn't [I thought] be attached to anything - it is a separate program, no? I do not remember adding the 'experimental stuff' - at least not on purpose. I only tried to add the 4.8 kernel and the new stack [hwe] to try to solve the problem with my three head system - which worked FINE in 12.04; but now that 12.04 is not supported, it doesn't work anymore, sadly.

Anyway, thanks for coming by to try to help.

---

### Post by Bashing-om on 2017-06-17
crazybear; Ho Kay !

I am all for fixing . Be aware - my experience with multi-monitors with AMD is less than stellar .

Let's reduce to simplest terms at this point and work with a single monitor .
1st up is to try and remove the vivid kernel .
```

sudo dpkg -P linux-generic-lts-vivid linux-lts-vivid-tools-common 

```
Where I do expect and anticipate the package manager to scream and holler .
Show me and we see just how dirty this operation may become.

[INDENT][INDENT]roll up our sleeves
[INDENT][INDENT][INDENT]and go to work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Impavidus on 2017-06-17
I was busy with some other things a few days, but good to have some help. This may be a complex issue.

What seems to be the problem – at least, triggers the error message – is that zz-update-grub, the tool that updates grub after installing or uninstalling a kernel, encounters a broken script or config file. zz-update-grub runs update-grub, update-grub runs grub-mkconfig, grub-mkconfig runs grub-probe and grub-probe gives an error. The root cause for this problem may be more difficult to find.

It might be interesting to see these config files.```
cat /etc/default/grub
ls /etc/grub.d
grep 'unicode.pf2GRUB_GFX' /etc/grub.d/*
```
That last command is based on my guess (hope) that the strange line in the error message can be found in one of the files processed by update-grub.

I've got no experience with multiple monitors and my only experience with ATI/AMD graphics is on an old computer that has always worked fine with the open source drivers – even on 6.06.

---

### Post by crazybear on 2017-06-17
That file was purged with no screaming from the system! It is VERY strange it was there. I NEVER had that version of Ubuntu - ever!

```

ls -al /usr/src/
total 88
drwxr-xr-x 22 root root 4096 Jun 16 22:54 .
drwxr-xr-x 14 root root 4096 Apr 28  2016 ..
drwxr-xr-x  3 root root 4096 May 15  2016 libdvd-pkg
drwxr-xr-x 24 root root 4096 Jun 25  2015 linux-headers-3.13.0-57
drwxr-xr-x  7 root root 4096 Jun 25  2015 linux-headers-3.13.0-57-generic
drwxr-xr-x 27 root root 4096 Apr 28  2016 linux-headers-4.4.0-21
drwxr-xr-x  7 root root 4096 Apr 28  2016 linux-headers-4.4.0-21-generic
drwxr-xr-x 27 root root 4096 May 18  2016 linux-headers-4.4.0-22
drwxr-xr-x  7 root root 4096 May 18  2016 linux-headers-4.4.0-22-generic
drwxr-xr-x 27 root root 4096 May 28 05:20 linux-headers-4.4.0-78
drwxr-xr-x  7 root root 4096 May 28 05:20 linux-headers-4.4.0-78-generic
drwxr-xr-x 27 root root 4096 Jun  7 19:08 linux-headers-4.4.0-79
drwxr-xr-x  7 root root 4096 Jun  7 19:08 linux-headers-4.4.0-79-generic
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3
drwxr-xr-x  8 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3-generic
drwxr-xr-x 27 root root 4096 Jun  6 12:53 linux-headers-4.8.0-53
drwxr-xr-x  7 root root 4096 Jun  6 12:53 linux-headers-4.8.0-53-generic
drwxr-xr-x 27 root root 4096 Jun  7 19:08 linux-headers-4.8.0-54
drwxr-xr-x  7 root root 4096 Jun  7 19:08 linux-headers-4.8.0-54-generic
drwxr-xr-x  6 root root 4096 Jun 16 22:54 oem-audio-hda-daily-lts-xenial-0.201706161031~ubuntu16.04.1
drwxr-xr-x 12 root root 4096 May 12 05:55 virtualbox-5.0.40

~$ dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                               amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                                  4.0ubuntu1                                           all          Linux image base package
ii  linux-firmware                                              1.157.11                                             all          Firmware for Linux kernel drivers
iU  linux-generic                                               4.4.0.79.85                                          amd64        Complete Generic Linux kernel and headers
iU  linux-generic-hwe-16.04                                     4.8.0.54.25                                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-22                                      4.4.0-22.40                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-22-generic                              4.4.0-22.40                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-78                                      4.4.0-78.99                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-78-generic                              4.4.0-78.99                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-79                                      4.4.0-79.100                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-79-generic                              4.4.0-79.100                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600                                  4.6.0-040600.201605151930                            all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3                               4.6.0-040600rc3.201604120934                         all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3-generic                       4.6.0-040600rc3.201604120934                         amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-53                                      4.8.0-53.56~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-53-generic                              4.8.0-53.56~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-54                                      4.8.0-54.57~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-54-generic                              4.8.0-54.57~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.79.85                                          amd64        Generic Linux kernel headers
ii  linux-headers-generic-hwe-16.04                             4.8.0.54.25                                          amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic                                4.4.0-22.40                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-72-generic                                4.4.0-72.93                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-75-generic                                4.4.0-75.96                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-77-generic                                4.4.0-77.98                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-78-generic                                4.4.0-78.99                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-79-generic                                4.4.0-79.100                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.8.0-53-generic                                4.8.0-53.56~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
iF  linux-image-4.8.0-54-generic                                4.8.0-54.57~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-22-generic                          4.4.0-22.40                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-72-generic                          4.4.0-72.93                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-75-generic                          4.4.0-75.96                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-77-generic                          4.4.0-77.98                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic                          4.4.0-78.99                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-79-generic                          4.4.0-79.100                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.8.0-53-generic                          4.8.0-53.56~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-4.8.0-54-generic                          4.8.0-54.57~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-virtual-hwe-16.04                         4.8.0.54.25                                          amd64        Extra drivers for Virtual Linux kernel image
iU  linux-image-generic                                         4.4.0.79.85                                          amd64        Generic Linux kernel image
iU  linux-image-generic-hwe-16.04                               4.8.0.54.25                                          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-79.100                                         amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                                 all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                                all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                                 amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

So what do you suggest next?

---

### Post by Bashing-om on 2017-06-17
crazybear; well.

depends now on what you want to do . complete the HWE package installs - or remove it ?
what is the present situation ?
```

uname -r
df -h
df -i

```

[INDENT][INDENT]all them depends
[/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-17
I would think to install the hwe, as this new stack seems to better accommodate AMD GPUs.

```

$ uname -r
4.4.0-78-generic

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             12G     0   12G   0% /dev
tmpfs           2.4G   35M  2.4G   2% /run
/dev/sdc1       909G  746G  117G  87% /
tmpfs            12G  510M   12G   5% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            12G     0   12G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           2.4G   12K  2.4G   1% /run/user/125
tmpfs           2.4G  120K  2.4G   1% /run/user/1000


$ df -i
Filesystem        Inodes   IUsed     IFree IUse% Mounted on
udev             3080589     749   3079840    1% /dev
tmpfs            3085927    1291   3084636    1% /run
/dev/sdc1       60473344 2077675  58395669    4% /
tmpfs            3085927     443   3085484    1% /dev/shm
tmpfs            3085927       9   3085918    1% /run/lock
tmpfs            3085927      18   3085909    1% /sys/fs/cgroup
cgmfs            3085927      14   3085913    1% /run/cgmanager/fs
tmpfs            3085927      13   3085914    1% /run/user/125
tmpfs            3085927      47   3085880    1% /run/user/1000

```

---

### Post by Bashing-om on 2017-06-17
crazybear; well;

try :
```

sudo apt install --reinstall-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial

```
keeping in mind there are several broken kernel packages .

If no errors - reboot and see what we have :
```

ls -al /vmlinuz* /initrd.img*

```

Then we go to work to remove the old kernels .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-18
E: Command line option --reinstall-recommends is not understood in combination with the other options

but, I found that if I tried each one separately I got something like:

```

$ sudo apt-get install --reinstall --install-recommends xserver-xorg-core-lts-xenial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libmircommon5
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  linux-image-4.4.0-72-generic linux-image-4.4.0-75-generic linux-image-4.4.0-77-generic linux-image-extra-4.4.0-21-generic
  linux-image-extra-4.4.0-22-generic linux-image-extra-4.4.0-72-generic linux-image-extra-4.4.0-75-generic
  linux-image-extra-4.4.0-77-generic
The following NEW packages will be installed:
  xserver-xorg-core-lts-xenial
0 upgraded, 1 newly installed, 8 to remove and 3 not upgraded.
20 not fully installed or removed.
Need to get 0 B/2,056 B of archives.
After this operation, 981 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 760722 files and directories currently installed.)
Removing linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-72-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Error! Your kernel headers for kernel 4.4.0-72-generic cannot be found.
Please install the linux-headers-4.4.0-72-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-72-generic cannot be found.
Please install the linux-headers-4.4.0-72-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic
WARNING: missing /lib/modules/4.4.0-72-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-72-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_usYfeS/lib/modules/4.4.0-72-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_usYfeS/lib/modules/4.4.0-72-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-72-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-72-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-72-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-75-generic (4.4.0-75.96) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-75-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Error! Your kernel headers for kernel 4.4.0-75-generic cannot be found.
Please install the linux-headers-4.4.0-75-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-75-generic cannot be found.
Please install the linux-headers-4.4.0-75-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-75-generic
WARNING: missing /lib/modules/4.4.0-75-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-75-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_u9lH4s/lib/modules/4.4.0-75-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_u9lH4s/lib/modules/4.4.0-75-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-75-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-75-generic (4.4.0-75.96) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-75-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-75-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-75-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-77-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Error! Your kernel headers for kernel 4.4.0-77-generic cannot be found.
Please install the linux-headers-4.4.0-77-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-77-generic cannot be found.
Please install the linux-headers-4.4.0-77-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-77-generic
WARNING: missing /lib/modules/4.4.0-77-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-77-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_DW1mWk/lib/modules/4.4.0-77-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_DW1mWk/lib/modules/4.4.0-77-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-77-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-77-generic (4.4.0-77.98) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-77-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-77-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-21-generic (4.4.0-21.37) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-21-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-22-generic (4.4.0-22.40) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-22-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-72-generic
 linux-image-4.4.0-72-generic
 linux-image-extra-4.4.0-75-generic
 linux-image-4.4.0-75-generic
 linux-image-extra-4.4.0-77-generic
 linux-image-4.4.0-77-generic
 linux-image-extra-4.4.0-21-generic
 linux-image-extra-4.4.0-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2017-06-18
crazybear' Umphhh

do that as :
```

sudo apt install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial

```
where it is now " install-recommends" .

[INDENT][INDENT]all things are not equal :(
[/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-18
NOPE...nothing happened.

```

$ sudo apt install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial
[sudo] password for peter-and-crazybear: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-72-generic linux-image-4.4.0-75-generic linux-image-4.4.0-77-generic
  linux-image-extra-4.4.0-21-generic linux-image-extra-4.4.0-22-generic linux-image-extra-4.4.0-72-generic
  linux-image-extra-4.4.0-75-generic linux-image-extra-4.4.0-77-generic
The following NEW packages will be installed:
  libwayland-egl1-mesa-lts-xenial linux-generic-lts-xenial xserver-xorg-core-lts-xenial
  xserver-xorg-input-all-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial
0 upgraded, 6 newly installed, 8 to remove and 3 not upgraded.
20 not fully installed or removed.
Need to get 0 B/12.1 kB of archives.
After this operation, 981 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 760718 files and directories currently installed.)
Removing linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-72-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Error! Your kernel headers for kernel 4.4.0-72-generic cannot be found.
Please install the linux-headers-4.4.0-72-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-72-generic cannot be found.
Please install the linux-headers-4.4.0-72-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic
WARNING: missing /lib/modules/4.4.0-72-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-72-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_sM4kOn/lib/modules/4.4.0-72-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_sM4kOn/lib/modules/4.4.0-72-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-72-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-72-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-72-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-75-generic (4.4.0-75.96) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-75-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Error! Your kernel headers for kernel 4.4.0-75-generic cannot be found.
Please install the linux-headers-4.4.0-75-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-75-generic cannot be found.
Please install the linux-headers-4.4.0-75-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-75-generic
WARNING: missing /lib/modules/4.4.0-75-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-75-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_rjHM75/lib/modules/4.4.0-75-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_rjHM75/lib/modules/4.4.0-75-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-75-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-75-generic (4.4.0-75.96) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-75-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-75-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-75-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-77-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Error! Your kernel headers for kernel 4.4.0-77-generic cannot be found.
Please install the linux-headers-4.4.0-77-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-77-generic cannot be found.
Please install the linux-headers-4.4.0-77-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-77-generic
WARNING: missing /lib/modules/4.4.0-77-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-77-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_7ygbZi/lib/modules/4.4.0-77-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_7ygbZi/lib/modules/4.4.0-77-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-77-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-77-generic (4.4.0-77.98) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-77-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-77-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-21-generic (4.4.0-21.37) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-21-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-22-generic (4.4.0-22.40) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-22-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-72-generic
 linux-image-4.4.0-72-generic
 linux-image-extra-4.4.0-75-generic
 linux-image-4.4.0-75-generic
 linux-image-extra-4.4.0-77-generic
 linux-image-4.4.0-77-generic
 linux-image-extra-4.4.0-21-generic
 linux-image-extra-4.4.0-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2017-06-18
crazybear; Welp;

We have 2 courses of action we can take.
1) give the package manager what it wants - and later remove them;
2) Get real dirty and remove the offensive kernels at this time .

I am all for getting real real dirty and clean up the mess .

to that end, what are you booting with now ?
```

uname -r

```
That ^ kernel we do not mess with !

How does ;
> 
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.

play into this ? 
Show :
```

cat /etc/default/grub

```

What is set for booting ?
```

ls -al /vmlinuz* /initrd.img*

```

And what are we going to rm ?
Show me a new listings :
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot
dpkg -l | grep linux-

```

With the end goal after all the clean up to get ya up on HWE .

[INDENT][INDENT][INDENT]work work work
[/INDENT][/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-18
Why would we get rid of any fully installed [ii] kernel at this point, unless it was quite old? I have exclusively been booting up onto 4.4.0-78.

```

$ uname -r
4.4.0-78-generic

$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="16"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="plymouth:debug usbhid.quirks=0x1B1C:0x1B11:0x408 drm.debug=0xe"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


export GRUB_COLOR_NORMAL="black/black"
export GRUB_COLOR_HIGHLIGHT="magenta/black"
export GRUB_MENU_PICTURE="/media/peter-and-crazybear/SURVIVORUSB/Transfer Folder/45.jpg"
GRUB_FONT="/boot/grub/unicode.pf2"GRUB_GFXPAYLOAD_LINUX=None
GRUB_GFXPAYLOAD_LINUX=None
peter-and-crazybear@peterandcrazybear-GA-X58A-UD7:~$ ls -al /vmlinuz* /initrd.img*
lrwxrwxrwx 1 root root 32 Jun 18 11:32 /initrd.img -> boot/initrd.img-4.8.0-54-generic
lrwxrwxrwx 1 root root 32 Jun 18 11:32 /initrd.img.old -> boot/initrd.img-4.8.0-53-generic
lrwxrwxrwx 1 root root 29 Jun 18 11:32 /vmlinuz -> boot/vmlinuz-4.8.0-54-generic
lrwxrwxrwx 1 root root 29 Jun 18 11:32 /vmlinuz.old -> boot/vmlinuz-4.8.0-53-generic

$ ls -al /usr/src/
total 88
drwxr-xr-x 22 root root 4096 Jun 16 22:54 .
drwxr-xr-x 14 root root 4096 Apr 28  2016 ..
drwxr-xr-x  3 root root 4096 May 15  2016 libdvd-pkg
drwxr-xr-x 24 root root 4096 Jun 25  2015 linux-headers-3.13.0-57
drwxr-xr-x  7 root root 4096 Jun 25  2015 linux-headers-3.13.0-57-generic
drwxr-xr-x 27 root root 4096 Apr 28  2016 linux-headers-4.4.0-21
drwxr-xr-x  7 root root 4096 Apr 28  2016 linux-headers-4.4.0-21-generic
drwxr-xr-x 27 root root 4096 May 18  2016 linux-headers-4.4.0-22
drwxr-xr-x  7 root root 4096 May 18  2016 linux-headers-4.4.0-22-generic
drwxr-xr-x 27 root root 4096 May 28 05:20 linux-headers-4.4.0-78
drwxr-xr-x  7 root root 4096 May 28 05:20 linux-headers-4.4.0-78-generic
drwxr-xr-x 27 root root 4096 Jun  7 19:08 linux-headers-4.4.0-79
drwxr-xr-x  7 root root 4096 Jun  7 19:08 linux-headers-4.4.0-79-generic
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3
drwxr-xr-x  8 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3-generic
drwxr-xr-x 27 root root 4096 Jun  6 12:53 linux-headers-4.8.0-53
drwxr-xr-x  7 root root 4096 Jun  6 12:53 linux-headers-4.8.0-53-generic
drwxr-xr-x 27 root root 4096 Jun  7 19:08 linux-headers-4.8.0-54
drwxr-xr-x  7 root root 4096 Jun  7 19:08 linux-headers-4.8.0-54-generic
drwxr-xr-x  6 root root 4096 Jun 16 22:54 oem-audio-hda-daily-lts-xenial-0.201706161031~ubuntu16.04.1
drwxr-xr-x 12 root root 4096 May 12 05:55 virtualbox-5.0.40

$ ls -al /lib/modules/
total 60
drwxr-xr-x 15 root root 4096 Jun 12 06:39 .
drwxr-xr-x 30 root root 4096 Mar 24 18:43 ..
drwxr-xr-x  2 root root 4096 May  1 09:39 3.13.0-57-generic
drwxr-xr-x  2 root root 4096 May  1 09:39 3.13.0-59-generic
drwxr-xr-x  2 root root 4096 May  1 09:39 3.13.0-62-generic
drwxr-xr-x  2 root root 4096 May  1 09:39 3.13.0-63-generic
drwxr-xr-x  2 root root 4096 May  1 09:39 3.13.0-79-generic
drwxr-xr-x  2 root root 4096 May  1 09:39 3.19.0-51-generic
drwxr-xr-x  6 root root 4096 Jun 18 11:32 4.4.0-21-generic
drwxr-xr-x  6 root root 4096 Jun 18 11:32 4.4.0-22-generic
drwxr-xr-x  6 root root 4096 Jun 16 22:58 4.4.0-78-generic
drwxr-xr-x  6 root root 4096 Jun 18 11:32 4.4.0-79-generic
drwxr-xr-x  2 root root 4096 Jun  8  2016 4.6.0-040600rc3-generic
drwxr-xr-x  6 root root 4096 Jun 18 11:32 4.8.0-53-generic
drwxr-xr-x  6 root root 4096 Jun 18 11:32 4.8.0-54-generic

$ ls -al /boot
total 265272
drwxr-xr-x  4 root root    12288 Jun 18 11:33 .
drwxr-xr-x 26 root root     4096 Jun 18 11:32 ..
-rw-r--r--  1 root root  1239577 Apr 19  2016 abi-4.4.0-21-generic
-rw-r--r--  1 root root  1239612 May 13  2016 abi-4.4.0-22-generic
-rw-r--r--  1 root root  1246312 Apr 27 20:24 abi-4.4.0-78-generic
-rw-r--r--  1 root root  1246311 May 18 00:09 abi-4.4.0-79-generic
-rw-r--r--  1 root root  1408605 May 16 05:53 abi-4.8.0-53-generic
-rw-r--r--  1 root root  1408813 May 24 22:48 abi-4.8.0-54-generic
-rw-r--r--  1 root root   189412 Apr 19  2016 config-4.4.0-21-generic
-rw-r--r--  1 root root   189520 May 13  2016 config-4.4.0-22-generic
-rw-r--r--  1 root root   190355 Apr 27 20:24 config-4.4.0-78-generic
-rw-r--r--  1 root root   190356 May 18 00:09 config-4.4.0-79-generic
-rw-r--r--  1 root root   199564 May 16 05:53 config-4.8.0-53-generic
-rw-r--r--  1 root root   199564 May 24 22:48 config-4.8.0-54-generic
drwxr-xr-x  6 root root     4096 Jun 18 11:33 grub
drwxr-xr-x  5 root root     4096 May  9  2016 grub.bak
-rw-r--r--  1 root root 14868853 Jun 18 11:32 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 14872303 Jun 18 11:32 initrd.img-4.4.0-22-generic
-rw-r--r--  1 root root 40286369 Jun 16 22:55 initrd.img-4.4.0-78-generic
-rw-r--r--  1 root root 40282639 Jun 18 11:32 initrd.img-4.4.0-79-generic
-rw-r--r--  1 root root 42634563 Jun 18 11:32 initrd.img-4.8.0-53-generic
-rw-r--r--  1 root root 42651699 Jun 18 11:33 initrd.img-4.8.0-54-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3853719 Apr 19  2016 System.map-4.4.0-21-generic
-rw-------  1 root root  3855781 May 13  2016 System.map-4.4.0-22-generic
-rw-------  1 root root  3882872 Apr 27 20:24 System.map-4.4.0-78-generic
-rw-------  1 root root  3883279 May 18 00:09 System.map-4.4.0-79-generic
-rw-------  1 root root  4066743 May 16 05:53 System.map-4.8.0-53-generic
-rw-------  1 root root  4067832 May 24 22:48 System.map-4.8.0-54-generic
-rw-------  1 root root  7013968 Apr 19  2016 vmlinuz-4.4.0-21-generic
-rw-------  1 root root  7015440 May 13  2016 vmlinuz-4.4.0-22-generic
-rw-------  1 root root  7089552 Apr 27 20:24 vmlinuz-4.4.0-78-generic
-rw-------  1 root root  7091696 May 18 00:09 vmlinuz-4.4.0-79-generic
-rw-------  1 root root  7308416 May 16 05:53 vmlinuz-4.8.0-53-generic
-rw-------  1 root root  7311584 May 24 22:48 vmlinuz-4.8.0-54-generic

$ dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                               amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                                  4.0ubuntu1                                           all          Linux image base package
ii  linux-firmware                                              1.157.11                                             all          Firmware for Linux kernel drivers
iU  linux-generic                                               4.4.0.79.85                                          amd64        Complete Generic Linux kernel and headers
iU  linux-generic-hwe-16.04                                     4.8.0.54.25                                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-22                                      4.4.0-22.40                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-22-generic                              4.4.0-22.40                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-78                                      4.4.0-78.99                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-78-generic                              4.4.0-78.99                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-79                                      4.4.0-79.100                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-79-generic                              4.4.0-79.100                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600                                  4.6.0-040600.201605151930                            all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3                               4.6.0-040600rc3.201604120934                         all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3-generic                       4.6.0-040600rc3.201604120934                         amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-53                                      4.8.0-53.56~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-53-generic                              4.8.0-53.56~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-54                                      4.8.0-54.57~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-54-generic                              4.8.0-54.57~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.79.85                                          amd64        Generic Linux kernel headers
ii  linux-headers-generic-hwe-16.04                             4.8.0.54.25                                          amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic                                4.4.0-22.40                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-72-generic                                4.4.0-72.93                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-75-generic                                4.4.0-75.96                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-77-generic                                4.4.0-77.98                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-78-generic                                4.4.0-78.99                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-79-generic                                4.4.0-79.100                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.8.0-53-generic                                4.8.0-53.56~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
iF  linux-image-4.8.0-54-generic                                4.8.0-54.57~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-22-generic                          4.4.0-22.40                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-72-generic                          4.4.0-72.93                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-75-generic                          4.4.0-75.96                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-77-generic                          4.4.0-77.98                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic                          4.4.0-78.99                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-79-generic                          4.4.0-79.100                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.8.0-53-generic                          4.8.0-53.56~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-4.8.0-54-generic                          4.8.0-54.57~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-virtual-hwe-16.04                         4.8.0.54.25                                          amd64        Extra drivers for Virtual Linux kernel image
iU  linux-image-generic                                         4.4.0.79.85                                          amd64        Generic Linux kernel image
iU  linux-image-generic-hwe-16.04                               4.8.0.54.25                                          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-79.100                                         amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                                 all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                                all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                                 amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by deadflowr on 2017-06-18
> Why would we get rid of any fully installed [ii] kernel at this point, unless it was quite old? I have exclusively been booting up onto 4.4.0-78.
As to why you would want to be running an upgraded kernel beyond the 4.4.0-78 version:
[https://www.ubuntu.com/usn/usn-3312-1/]("https://www.ubuntu.com/usn/usn-3312-1/")

---

### Post by Bashing-om on 2017-06-18
crazybear; Whew .. tall orders here to respond to .

Most depends on what you want to do . all I can do is render my best opinion and offer advise to proceed in the direction you choose.
You are presently bumping the head of disk space usage . 87% is getting tight - not much left for overhead - we need to reclaim disk space . At about 90% capacity journaling starts to fail . On a service machine all we really want is the latest kernel and ONE backup kernel - there is no need for any others to my think'n .
We do want to get this system restored to a booting condition - to that end is what is booting ?
grub has set to boot :
> 
/vmlinuz -> boot/vmlinuz-4.8.0-54-generic
/vmlinuz.old -> boot/vmlinuz-4.8.0-53-generic

But for some unknown reason the booting kernel is :
> 
4.4.0-78-generic


Now just why ?
How does the boot parameters:
> 
GRUB_CMDLINE_LINUX_DEFAULT="plymouth:debug usbhid.quirks=0x1B1C:0x1B11:0x408 drm.debug=0xe"

play into this ? What functions do they serve ?

Then there is the non-supported mode :
> 
GRUB_GFXPAYLOAD_LINUX=None

That needs to be set correctly if in fact it does need to be set :
see: [https://www.gnu.org/software/grub/manual/html_node/gfxpayload.html](https://www.gnu.org/software/grub/manual/html_node/gfxpayload.html)


It is a mystery at this time why " iU  linux-image-extra-4.8.0-53-generic  and -54 " are not fully installed >> iU  linux-image-generic-hwe-16.04 that maybe related to booting the 4.4.0-78-generic kernel vice this latest !

-------------------------

We can try and stay within the package manager - will not hurt to try:
```

sudo dpkg -P linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic

```
As a gentle poke at it .. see what bites back and maybe do the same for the other partial installs ??

So long as we do not mess with what is booting and what we want to boot .. we can poke and prod .

[INDENT][INDENT]what to do
[INDENT][INDENT]OH what to do
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-18
> **Bashing-om said:**
> crazybear; Whew .. tall orders here to respond to .

Most depends on what you want to do . all I can do is render my best opinion and offer advise to proceed in the direction you choose.
You are presently bumping the head of disk space usage . 87% is getting tight - not much left for overhead - we need to reclaim disk space . At about 90% capacity journaling starts to fail . On a service machine all we really want is the latest kernel and ONE backup kernel - there is no need for any others to my think'n .
We do want to get this system restored to a booting condition - to that end is what is booting ?
grub has set to boot :

But for some unknown reason the booting kernel is :


Now just why ?
How does the boot parameters:

play into this ? What functions do they serve ?

Then there is the non-supported mode :

That needs to be set correctly if in fact it does need to be set :
see: [https://www.gnu.org/software/grub/manual/html_node/gfxpayload.html](https://www.gnu.org/software/grub/manual/html_node/gfxpayload.html)


It is a mystery at this time why " iU  linux-image-extra-4.8.0-53-generic  and -54 " are not fully installed >> iU  linux-image-generic-hwe-16.04 that maybe related to booting the 4.4.0-78-generic kernel vice this latest !

-------------------------

We can try and stay within the package manager - will not hurt to try:
```

sudo dpkg -P linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic

```
As a gentle poke at it .. see what bites back and maybe do the same for the other partial installs ??

So long as we do not mess with what is booting and what we want to boot .. we can poke and prod .[INDENT][INDENT]what to do[INDENT][INDENT]OH what to do
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
 

```

$ sudo dpkg -P linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
[sudo] password for peter-and-crazybear: 
dpkg: warning: ignoring request to remove linux-headers-4.4.0-72 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.4.0-72-generic which isn't installed
(Reading database ... 760718 files and directories currently installed.)
Removing linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-72-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-72-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-72-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Error! Your kernel headers for kernel 4.4.0-72-generic cannot be found.
Please install the linux-headers-4.4.0-72-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-72-generic cannot be found.
Please install the linux-headers-4.4.0-72-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic
WARNING: missing /lib/modules/4.4.0-72-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-72-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_52Kphn/lib/modules/4.4.0-72-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_52Kphn/lib/modules/4.4.0-72-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-4.4.0-72-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-4.4.0-72-generic
 linux-image-extra-4.4.0-72-generic

```

- The extra boot parameters have never given me trouble in 12.04, 14.04 nor 16.04. They allow my fancy Corsair keyboard to function in Linux [was only supported by Corsair in Windows]. There is a driver installed that runs the keyboard in Ubuntu built by some private person.

- It is very easy for me to move some big files off of the disk. I have enourmous storage capacity and tend to fill up disks fast - but that is NO problemo - but will take a day or so to find where they belong. It is now at 80% and I can in some days make that even lower or switch to a 2GB drive.

- I have since this tangle with the kernels NOT been able to do a grub-update, which may explain why it points to one kernel, yet I boot with another. I physically choose among those listed and NOT all installed [properly - ii] are even listed at the moment.

- As to the GRUB_GFXPAYLOAD_LINUX[COLOR=#000000][FONT=&quot]&#8217; - I know nothing about it and didn't intentionally set it. However, there are no visual problems with the boot up phase - if there is visual problem with one of the 3 monitors [it varies which one], that is after I log in - and those times I reboot and hope it is stable [about 3/4 times it is].[/FONT][/COLOR]

---

### Post by Bashing-om on 2017-06-18
crazybear; Welp ---

Looks to me like our best course of action here now is to take that real dirty path ,, and then try and clean up the mess we make when we seriously break the package manager .

I could be wrong about that best course - I have been wrong at least once before in my life .
If ya want to try and dpkg some of the other half installed kernels, by all means give it a whirl . I can not see that it can hurt to try . 

I would fix that :
> 
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.

now, just to get the garbage out of the way .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-18
> **Bashing-om said:**
> crazybear; Welp ---

Looks to me like our best course of action here now is to take that real dirty path ,, and then try and clean up the mess we make when we seriously break the package manager .

I could be wrong about that best course - I have been wrong at least once before in my life .
If ya want to try and dpkg some of the other half installed kernels, by all means give it a whirl . I can not see that it can hurt to try . 

I would fix that :

now, just to get the garbage out of the way .
[INDENT][INDENT]maybe yes[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

fix it how? the GRUB_GFXPAYLOAD_LINUX[COLOR=#000000][FONT=&quot]’ line?[/FONT][/COLOR]

---

### Post by deadflowr on 2017-06-18
You need to erase the GRUB_GFXPAYLOAD_LINUX=NONE from the line:
```
GRUB_FONT="/boot/grub/unicode.pf2"GRUB_GFXPAYLOAD_LINUX=None
```
so it looks like this:
```
GRUB_FONT="/boot/grub/unicode.pf2"
```

---

### Post by Bashing-om on 2017-06-18
crazybear; Hey;

> 
fix it how? the GRUB_GFXPAYLOAD_LINUX’ line?

In your /etc/default/grub file is the line:
> 
GRUB_GFXPAYLOAD_LINUX=None

where "none" is not valid. [https://www.gnu.org/software/grub/manual/html_node/gfxpayload.html](https://www.gnu.org/software/grub/manual/html_node/gfxpayload.html)
for advise on what is supported -

[INDENT][INDENT]getting our ducks all in a row
[/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-19
There are two of you suggesting I do things. Neither is [to me] very clear. There are TWO LINES in the file with that term! I hope I did the right thing in removing it entirely in the longer line and changing 'none' to 'keep' in the shorter line. If not, I'll not be able to boot. The explanations online about this term are confusing [to me]. It says it controls in what form the boot is done graphically; also seems to indicate it is generated by something [in my case perhaps by grub-configure?]. As I think you are both in the US and I'm in Europe and time zones are off, I hope I get word before I shut down my computer! Thanks.

The two lines are now:
GRUB_FONT="/boot/grub/unicode.pf2
GRUB_GFXPAYLOAD_LINUX=keep

---

### Post by deadflowr on 2017-06-19
Yeah, the error you saw
> /usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None.
referred to the fact that there is and never has been a file called */boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None.*
there is a */boot/grub/unicode.pf2* file though, which is more likely what it should have been.
Seems like the gfxpayload line what doubled up somehow and then one of those lines got backspaced into the Grub font entry.
Removing that should stop that error from happening, at least.

(I note that the entry you've posted shows it without closing quotes:
```
GRUB_FONT="/boot/grub/unicode.pf2  << no quote
```
Make sure you put a quote at the end of the GRUB_FONT line like
```
GRUB_FONT="/boot/grub/unicode.pf2" << added quote at end
```
so it doesn't cause any odd syntax errors.)

You can always see if any of the entries are wrong by running
```
sudo update-grub
```
any errors will show or make themselves known.
At least as far as grub is concerned.

As for the GRUB_GFXPAYLOAD_LINUX= line, I know nothing about it.
I don't have it and do not need it.
So I'm not sure what importance it has or if it's important at all.

Hope something here makes sense.

---

### Post by crazybear on 2017-06-19
> **deadflowr said:**
> Yeah, the error you saw

referred to the fact that there is and never has been a file called */boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None.*
there is a */boot/grub/unicode.pf2* file though, which is more likely what it should have been.
Seems like the gfxpayload line what doubled up somehow and then one of those lines got backspaced into the Grub font entry.
Removing that should stop that error from happening, at least.

(I note that the entry you've posted shows it without closing quotes:
```
GRUB_FONT="/boot/grub/unicode.pf2  << no quote
```
Make sure you put a quote at the end of the GRUB_FONT line like
```
GRUB_FONT="/boot/grub/unicode.pf2" << added quote at end
```
so it doesn't cause any odd syntax errors.)

You can always see if any of the entries are wrong by running
```
sudo update-grub
```
any errors will show or make themselves known.
At least as far as grub is concerned.

As for the GRUB_GFXPAYLOAD_LINUX= line, I know nothing about it.
I don't have it and do not need it.
So I'm not sure what importance it has or if it's important at all.

Hope something here makes sense.

done....I'll know when I next boot, won't I....the 4.8 kernels are also listed now and the highest one is pointed to to boot into by default!~

> **deadflowr said:**
> As to why you would want to be running an upgraded kernel beyond the 4.4.0-78 version:
[https://www.ubuntu.com/usn/usn-3312-1/](https://www.ubuntu.com/usn/usn-3312-1/)
[U]
This is VERY important in my situation[/U]. I have state actor(s) who have attacked me in the past, and likely look to at the present from time to time. I know they have the highest level of ability - and are the most difficult to protect against, but I must do what I can to avoid vulnerabilities.

> [COLOR=#000000]*As for the GRUB_GFXPAYLOAD_LINUX= line, I know nothing about it.*[/COLOR]
[COLOR=#000000]*I don't have it and do not need it.*[/COLOR]
[COLOR=#000000]*So I'm not sure what importance it has or if it's important at all.*[/COLOR]

I also don't know. I have looked at several webpages on this, but as with so many Linux 'explanations' they are clearly understood by those who wrote them and less-than-intelligible to those who are new to them. I have a three monitor system and also have an AMD Radeon 7970 - which is reported to [and does have] problems with 16.04 at times. I hope how it is now set will at least boot....I'll know soon.

---

### Post by Impavidus on 2017-06-19
OK, you guys identified and fixed the faulty line in /etc/default/grub. You won't notice a change at the next boot directly, as /etc/default/grub isn't used during boot. It is however used for updating grub, which happens whenever you install or uninstall a kernel (or whenever you run update-grub manually). This faulty line blocked all attempts to (un-)install kernels. So with /etc/default/grub fixed, it should be possible to get those kernels properly installed or uninstalled.

To get the packages in a consistent state:```
sudo apt install -f
```
Then you should be able to reboot and get into kernel 4.8.0-54 and uninstall old stuff. You should have enough headroom on your hard drive to manage.

As to how that faulty line got into your /etc/default/grub, it must have been inserted by you, a buggy tool or someone else. My bet is on the buggy tool.

---

### Post by crazybear on 2017-06-19
> **Impavidus said:**
> OK, you guys identified and fixed the faulty line in /etc/default/grub. You won't notice a change at the next boot directly, as /etc/default/grub isn't used during boot. It is however used for updating grub, which happens whenever you install or uninstall a kernel (or whenever you run update-grub manually). This faulty line blocked all attempts to (un-)install kernels. So with /etc/default/grub fixed, it should be possible to get those kernels properly installed or uninstalled.

To get the packages in a consistent state:```
sudo apt install -f
```
Then you should be able to reboot and get into kernel 4.8.0-54 and uninstall old stuff. You should have enough headroom on your hard drive to manage.

As to how that faulty line got into your /etc/default/grub, it must have been inserted by you, a buggy tool or someone else. My bet is on the buggy tool.

Well, that seemed to help a LOT! I ran sudo apt install-f and there were no error messages.

Here is the current state of the kernels:

```

$ dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
[sudo] password for peter-and-crazybear: 
(Reading database ... 758620 files and directories currently installed.)
Removing linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Purging configuration files for linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Removing linux-image-4.4.0-75-generic (4.4.0-75.96) ...
Purging configuration files for linux-image-4.4.0-75-generic (4.4.0-75.96) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Removing linux-image-4.4.0-77-generic (4.4.0-77.98) ...
Purging configuration files for linux-image-4.4.0-77-generic (4.4.0-77.98) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Removing linux-image-extra-4.4.0-21-generic (4.4.0-21.37) ...
Purging configuration files for linux-image-extra-4.4.0-21-generic (4.4.0-21.37) ...
Removing linux-image-extra-4.4.0-22-generic (4.4.0-22.40) ...
Purging configuration files for linux-image-extra-4.4.0-22-generic (4.4.0-22.40) ...
Removing linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
Purging configuration files for linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
Removing linux-image-extra-4.4.0-75-generic (4.4.0-75.96) ...
Purging configuration files for linux-image-extra-4.4.0-75-generic (4.4.0-75.96) ...
Removing linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
Purging configuration files for linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
Removing unison-gtk (2.48.3-1ubuntu1) ...
Purging configuration files for unison-gtk (2.48.3-1ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...

$ dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                               amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                                  4.0ubuntu1                                           all          Linux image base package
ii  linux-firmware                                              1.157.11                                             all          Firmware for Linux kernel drivers
ii  linux-generic                                               4.4.0.79.85                                          amd64        Complete Generic Linux kernel and headers
ii  linux-generic-hwe-16.04                                     4.8.0.54.25                                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-22                                      4.4.0-22.40                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-22-generic                              4.4.0-22.40                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-78                                      4.4.0-78.99                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-78-generic                              4.4.0-78.99                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-79                                      4.4.0-79.100                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-79-generic                              4.4.0-79.100                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600                                  4.6.0-040600.201605151930                            all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3                               4.6.0-040600rc3.201604120934                         all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3-generic                       4.6.0-040600rc3.201604120934                         amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-53                                      4.8.0-53.56~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-53-generic                              4.8.0-53.56~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-54                                      4.8.0-54.57~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-54-generic                              4.8.0-54.57~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.79.85                                          amd64        Generic Linux kernel headers
ii  linux-headers-generic-hwe-16.04                             4.8.0.54.25                                          amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-78-generic                                4.4.0-78.99                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-79-generic                                4.4.0-79.100                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-53-generic                                4.8.0-53.56~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-54-generic                                4.8.0-54.57~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic                          4.4.0-78.99                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-79-generic                          4.4.0-79.100                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-53-generic                          4.8.0-53.56~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-54-generic                          4.8.0-54.57~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-virtual-hwe-16.04                         4.8.0.54.25                                          amd64        Extra drivers for Virtual Linux kernel image
ii  linux-image-generic                                         4.4.0.79.85                                          amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-16.04                               4.8.0.54.25                                          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-79.100                                         amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                                 all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                                all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                                 amd64        Bootloader for Linux/i386 using MS-DOS floppies



```

Why, however, does a different list of **installed** linux-headers appear in Synaptic Package Manager? [wanted to upload a jpg, but see I can not unless it is on the internet].

Anything more that should be trimmed out?
Am I go to go? I'll certainly know if the new hwe and higher kernels work to solve the problem with the GPU!
So, the real problem was the two crazy mistakes on the grub file [which I certainly did NOT enter manually].
Anyway, seem to have made progress and can likely now install normal updates too.

---

### Post by crazybear on 2017-06-19
Addendum: Have booted into 4.8.0-54 a few times and not once [yet] has there been any distortion with the monitors [so far so good on that], but a little annoying was it doesn't do the usual boot [with a circle with light moving around], but shows me a dialogue list of everything it is doing including a 1 min 30 sec pause labelled something like upstart job scheduled in 1 min 30 sec [which is a long waste of time]. What is causing this? It did finally [after about three minutes] come to the log-in screen, but it was not attractive and needlessly long.

---

### Post by Bashing-om on 2017-06-19
crazybear; Hey !

Making good progress ! .. See, I told you so :)

Now if you are booting and all looks good - less that long pause - let's consider removing the old kernels.

What results :
```

sudo apt -s autoremove

```
where 's' is (S)imilate . will advise what it would do if told .
Make sure that the linux-image-4.8.0-54-generic is the booting kernel .

[INDENT][INDENT]not done 'til the paper work is done
[/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-20
> **Bashing-om said:**
> crazybear; Hey !

Making good progress ! .. See, I told you so :)

Now if you are booting and all looks good - less that long pause - let's consider removing the old kernels.

What results :
```

sudo apt -s autoremove

```
where 's' is (S)imilate . will advise what it would do if told .
Make sure that the linux-image-4.8.0-54-generic is the booting kernel .[INDENT][INDENT]not done 'til the paper work is done
[/INDENT]
[/INDENT]


There were a lot of needed updates - not sure if all kernels are the exact same as before.
```

$ dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                               amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                                  4.0ubuntu1                                           all          Linux image base package
ii  linux-firmware                                              1.157.11                                             all          Firmware for Linux kernel drivers
ii  linux-generic                                               4.4.0.81.87                                          amd64        Complete Generic Linux kernel and headers
ii  linux-generic-hwe-16.04                                     4.8.0.56.27                                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-22                                      4.4.0-22.40                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-22-generic                              4.4.0-22.40                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-78                                      4.4.0-78.99                                          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-78-generic                              4.4.0-78.99                                          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-79                                      4.4.0-79.100                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-79-generic                              4.4.0-79.100                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-81                                      4.4.0-81.104                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-81-generic                              4.4.0-81.104                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600                                  4.6.0-040600.201605151930                            all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3                               4.6.0-040600rc3.201604120934                         all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3-generic                       4.6.0-040600rc3.201604120934                         amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-53                                      4.8.0-53.56~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-53-generic                              4.8.0-53.56~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-54                                      4.8.0-54.57~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-54-generic                              4.8.0-54.57~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-56                                      4.8.0-56.61~16.04.1                                  all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-56-generic                              4.8.0-56.61~16.04.1                                  amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.81.87                                          amd64        Generic Linux kernel headers
ii  linux-headers-generic-hwe-16.04                             4.8.0.56.27                                          amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-78-generic                                4.4.0-78.99                                          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-79-generic                                4.4.0-79.100                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-81-generic                                4.4.0-81.104                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-53-generic                                4.8.0-53.56~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-54-generic                                4.8.0-54.57~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-56-generic                                4.8.0-56.61~16.04.1                                  amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic                          4.4.0-78.99                                          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-79-generic                          4.4.0-79.100                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-81-generic                          4.4.0-81.104                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-53-generic                          4.8.0-53.56~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-54-generic                          4.8.0-54.57~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-56-generic                          4.8.0-56.61~16.04.1                                  amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-virtual-hwe-16.04                         4.8.0.56.27                                          amd64        Extra drivers for Virtual Linux kernel image
ii  linux-image-generic                                         4.4.0.81.87                                          amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-16.04                               4.8.0.56.27                                          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-81.104                                         amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                                 all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                                all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                                 amd64        Bootloader for Linux/i386 using MS-DOS floppies

$ sudo apt -s autoremove
[sudo] password for peter-and-crazybear: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic linux-headers-4.4.0-79 linux-headers-4.4.0-79-generic linux-headers-4.8.0-53
  linux-headers-4.8.0-53-generic linux-image-4.4.0-78-generic linux-image-4.4.0-79-generic linux-image-4.8.0-53-generic
  linux-image-extra-4.4.0-78-generic linux-image-extra-4.4.0-79-generic linux-image-extra-4.8.0-53-generic
0 upgraded, 0 newly installed, 12 to remove and 1 not upgraded.
Remv linux-headers-4.4.0-78-generic [4.4.0-78.99]
Remv linux-headers-4.4.0-78 [4.4.0-78.99]
Remv linux-headers-4.4.0-79-generic [4.4.0-79.100]
Remv linux-headers-4.4.0-79 [4.4.0-79.100]
Remv linux-headers-4.8.0-53-generic [4.8.0-53.56~16.04.1]
Remv linux-headers-4.8.0-53 [4.8.0-53.56~16.04.1]
Remv linux-image-extra-4.4.0-78-generic [4.4.0-78.99]
Remv linux-image-4.4.0-78-generic [4.4.0-78.99]
Remv linux-image-extra-4.4.0-79-generic [4.4.0-79.100]
Remv linux-image-4.4.0-79-generic [4.4.0-79.100]
Remv linux-image-extra-4.8.0-53-generic [4.8.0-53.56~16.04.1]
Remv linux-image-4.8.0-53-generic [4.8.0-53.56~16.04.1]

```

To my eye, that is a bit more than I want to eliminate at this time! The kernel 4.8.0-54-generic along with the new hwe seems to be very stable thus far and very stable with my GPU! [**so anyone else having problems with AMD GPU's might keep that in mind!**]. Why does it not want to autoremove the 4.6 or older 4.4 kernels? It wants to remove even the 4.8.0-53! Aha, I see it just added a new 4.8.0-56 [which I've not yet tried].

---

### Post by Impavidus on 2017-06-20
Autoremove doesn't always work as it should, in particular when your package manager has been broken. You can uninstall the old kernels manually:```
sudo apt purge linux-image-4.4.0-78-generic linux-image-extra-4.4.0-78-generic
```Similar for the other kernels.

You can speed it up a bit by using shell expansions:```
sudo apt purge linux-image{,-extra}-4.4.0-{78,79,81}-generic
```
That will remove 3 old kernels at a time.

Also remove the old header packages, listed in your post above (linux-headers-4.4.0-21 etc.). They can take quite a lot of inodes, sometimes this can cause trouble if you never clean them.

---

### Post by crazybear on 2017-06-20
What about the following - do they have reason to remain and/or newer equivalents? **I assume they should remain**.
> 
linux-firmware                                             1.157.11   

linux-libc-dev:amd64     4.4.0-81.104  

Everything else is now 4.8.0 and I'll delete some of them when I'm sure the latest ones are working well [but they sure seem to be!].

---

### Post by deadflowr on 2017-06-20
I'd keep both.
You may actually need the linux-firmware package.
Not sure about the linux-libc-dev package, though.
But better safe than sorry.

---

### Post by crazybear on 2017-06-23
Hmmmm. I did mark this solved, as I certainly got the kernels installed. There have been no video problems, as before before these new kernels and the new stack; but, there have been a number of times when the OS just froze up.....don't know why.... It froze three times yesterday and I had to reboot...but perhaps that is another issue [?].

---

### Post by Bashing-om on 2017-06-23
crazybear; Ouch !

I do not see a freeze as related to this thread . Start a new thread on this new issue.
How are you able to restart the system when the freeze occurs ?
When the system freezes do you still have keyboard input ?
Magic SysRq key method: hold down the Alt+SysRq keys and slowly run through the sequence R,E,I,S,U,B - after the B, your system will reboot (or if you want to shut it down, make the last letter o). For systems without a SysRq label on the key, it's the Prt Scr key.
As we do want a graceful resumption of service . Else real bad things can happen .

In this new thread show:
```

lspci -k|grep -iEA5 'vga|3d'
sudo lshw -C display

```
Make sure it is not the graphics causing the freeze.

[INDENT][INDENT]sometimes this
[INDENT][INDENT][INDENT]other times that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by crazybear on 2017-06-26
New thread is here: [https://ubuntuforums.org/showthread.php?t=2364634&p=13659614#post13659614](https://ubuntuforums.org/showthread.php?t=2364634&p=13659614#post13659614)

---

