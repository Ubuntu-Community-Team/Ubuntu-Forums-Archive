---
title: "i can't upgrade kernel"
date: 2018-12-18
forum: MINT
---

### Post by bernnt on 2018-12-18
**sudo apt-get upgrade**
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-extra-4.13.0-43-generic linux-image-extra-4.13.0-45-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 334 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 637228 files and directories currently installed.)
Removing linux-image-extra-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-43-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Error! echo
Your kernel headers for kernel 4.13.0-43-generic cannot be found at
/lib/modules/4.13.0-43-generic/build or /lib/modules/4.13.0-43-generic/source.
Error! echo
Your kernel headers for kernel 4.13.0-43-generic cannot be found at
/lib/modules/4.13.0-43-generic/build or /lib/modules/4.13.0-43-generic/source.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-43-generic
Warning: No support for locale: en_US.utf8
depmod: WARNING: could not open /var/tmp/mkinitramfs_2ricfY/lib/modules/4.13.0-43-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_2ricfY/lib/modules/4.13.0-43-generic/modules.builtin: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-43-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-43-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.13.0-45-generic (4.13.0-45.50~16.04.1) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
Error! echo
Your kernel headers for kernel 4.13.0-45-generic cannot be found at
/lib/modules/4.13.0-45-generic/build or /lib/modules/4.13.0-45-generic/source.
Error! echo
Your kernel headers for kernel 4.13.0-45-generic cannot be found at
/lib/modules/4.13.0-45-generic/build or /lib/modules/4.13.0-45-generic/source.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-45-generic
Warning: No support for locale: en_US.utf8
depmod: WARNING: could not open /var/tmp/mkinitramfs_ZyqP1M/lib/modules/4.13.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ZyqP1M/lib/modules/4.13.0-45-generic/modules.builtin: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-45-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.13.0-43-generic
 linux-image-extra-4.13.0-45-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```




[B]
sudo apt-get dist-upgrade[/B]

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-image-4.13.0-43-generic linux-image-4.13.0-45-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 41,7 MB/105 MB of archives.
After this operation, 145 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ftp.ntua.gr/ubuntu](http://ftp.ntua.gr/ubuntu) xenial-updates/main amd64 linux-image-4.13.0-43-generic amd64 4.13.0-43.48~16.04.1 [20,9 MB]
Get:2 [http://ftp.ntua.gr/ubuntu](http://ftp.ntua.gr/ubuntu) xenial-updates/main amd64 linux-image-4.13.0-45-generic amd64 4.13.0-45.50~16.04.1 [20,9 MB]                                                                         
Fetched 41,7 MB in 17s (2340 kB/s)                                                                                                                                                                   
Selecting previously unselected package linux-image-4.13.0-43-generic.
(Reading database ... 637229 files and directories currently installed.)
Preparing to unpack .../linux-image-4.13.0-43-generic_4.13.0-43.48~16.04.1_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Done.
Unpacking linux-image-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.13.0-43-generic_4.13.0-43.48~16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.13.0-43-generic' to '/boot/vmlinuz-4.13.0-43-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Selecting previously unselected package linux-image-4.13.0-45-generic.
Preparing to unpack .../linux-image-4.13.0-45-generic_4.13.0-45.50~16.04.1_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
Done.
Unpacking linux-image-4.13.0-45-generic (4.13.0-45.50~16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.13.0-45-generic_4.13.0-45.50~16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.13.0-45-generic' to '/boot/System.map-4.13.0-45-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.13.0-43-generic_4.13.0-43.48~16.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-4.13.0-45-generic_4.13.0-45.50~16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
[B]


uname -r
[/B]
```
4.15.0-38-generic
```


**df**
```

Filesystem                1K-blocks      Used Available Use% Mounted on
udev                        3894220         0   3894220   0% /dev
tmpfs                        785168      9588    775580   2% /run
/dev/mapper/mint--vg-root 222142116 166234788  44600116  79% /
tmpfs                       3925820    115612   3810208   3% /dev/shm
tmpfs                          5120         4      5116   1% /run/lock
tmpfs                       3925820         0   3925820   0% /sys/fs/cgroup
/dev/sda1                    482922    471010         0 100% /boot
cgmfs                           100         0       100   0% /run/cgmanager/fs
tmpfs                        785168        84    785084   1% /run/user/1000
/home/polykarpos/.Private 222142116 166234788  44600116  79% /home/polykarpos
```



**ls -la /boot**

```
total 283631
drwxr-xr-x  5 root root     4096 Dec 18 10:09 .
drwxr-xr-x 24 root root     4096 Oct 23 11:36 ..
-rw-r--r--  1 root root  1537455 Aug 16 00:00 abi-4.15.0-33-generic
-rw-r--r--  1 root root  1537610 Aug 28 16:28 abi-4.15.0-34-generic
-rw-r--r--  1 root root  1537821 Sep 25 16:42 abi-4.15.0-36-generic
-rw-r--r--  1 root root  1537997 Oct 11 05:52 abi-4.15.0-38-generic
-rw-r--r--  1 root root   216913 Aug 16 00:00 config-4.15.0-33-generic
-rw-r--r--  1 root root   216913 Aug 28 16:28 config-4.15.0-34-generic
-rw-r--r--  1 root root   216962 Sep 25 16:42 config-4.15.0-36-generic
-rw-r--r--  1 root root   216991 Oct 11 05:52 config-4.15.0-38-generic
drwxr-xr-x  5 root root     1024 Dec 18 09:55 grub
-rw-r--r--  1 root root 58249180 Sep  8 16:03 initrd.img-4.15.0-33-generic
-rw-r--r--  1 root root 58260525 Sep 12 09:22 initrd.img-4.15.0-34-generic
-rw-r--r--  1 root root 58264815 Oct  4 15:33 initrd.img-4.15.0-36-generic
-rw-r--r--  1 root root 58267076 Oct 23 11:36 initrd.img-4.15.0-38-generic
drwx------  2 root root    12288 Mar 15  2018 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root        0 Aug 16 00:00 retpoline-4.15.0-33-generic
-rw-r--r--  1 root root        0 Aug 28 16:28 retpoline-4.15.0-34-generic
-rw-r--r--  1 root root        0 Sep 25 16:42 retpoline-4.15.0-36-generic
-rw-r--r--  1 root root        0 Oct 11 05:52 retpoline-4.15.0-38-generic
-rw-------  1 root root  4041375 Aug 16 00:00 System.map-4.15.0-33-generic
-rw-------  1 root root  4043167 Aug 28 16:28 System.map-4.15.0-34-generic
-rw-------  1 root root  4045599 Sep 25 16:42 System.map-4.15.0-36-generic
-rw-------  1 root root  4046116 Oct 11 05:52 System.map-4.15.0-38-generic
drwx------  4 root root     1024 Oct 25 10:21 .Trash-0
-rw-------  1 root root  8108600 Aug 16 21:58 vmlinuz-4.15.0-33-generic
-rw-------  1 root root  8114136 Aug 29 17:23 vmlinuz-4.15.0-34-generic
-rw-------  1 root root  8119672 Sep 26 18:58 vmlinuz-4.15.0-36-generic
-rw-------  1 root root  8120984 Oct 11 16:03 vmlinuz-4.15.0-38-generic
```


[B]
dpkg -l | grep linux-[/B]

```
ii  linux-base                                                  4.5ubuntu1~16.04.1                           all          Linux image base package
iF  linux-firmware                                              1.157.21                                     all          Firmware for Linux kernel drivers
ii  linux-headers-4.10.0-38                                     4.10.0-38.42~16.04.1                         all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-38-generic                             4.10.0-38.42~16.04.1                         amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-37                                     4.13.0-37.42~16.04.1                         all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-37-generic                             4.13.0-37.42~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-38                                     4.13.0-38.43~16.04.1                         all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-38-generic                             4.13.0-38.43~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-39                                     4.13.0-39.44~16.04.1                         all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-39-generic                             4.13.0-39.44~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-41                                     4.13.0-41.46~16.04.1                         all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-41-generic                             4.13.0-41.46~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-43                                     4.13.0-43.48~16.04.1                         all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-43-generic                             4.13.0-43.48~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-45                                     4.13.0-45.50~16.04.1                         all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-45-generic                             4.13.0-45.50~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-24                                     4.15.0-24.26~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-24-generic                             4.15.0-24.26~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-29                                     4.15.0-29.31~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-29-generic                             4.15.0-29.31~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-33                                     4.15.0-33.36~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-33-generic                             4.15.0-33.36~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-34                                     4.15.0-34.37~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-34-generic                             4.15.0-34.37~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-36                                     4.15.0-36.39~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-36-generic                             4.15.0-36.39~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-38                                     4.15.0-38.41~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-38-generic                             4.15.0-38.41~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-39                                     4.15.0-39.42~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-39-generic                             4.15.0-39.42~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-38-generic                               4.10.0-38.42~16.04.1                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-37-generic                               4.13.0-37.42~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-38-generic                               4.13.0-38.43~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-39-generic                               4.13.0-39.44~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-41-generic                               4.13.0-41.46~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ic  linux-image-4.13.0-43-generic                               4.13.0-43.48~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ic  linux-image-4.13.0-45-generic                               4.13.0-45.50~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.15.0-24-generic                               4.15.0-24.26~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-4.15.0-29-generic                               4.15.0-29.31~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-4.15.0-33-generic                               4.15.0-33.36~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-4.15.0-34-generic                               4.15.0-34.37~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-4.15.0-36-generic                               4.15.0-36.39~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-4.15.0-38-generic                               4.15.0-38.41~16.04.1                         amd64        Signed kernel image generic
rc  linux-image-extra-4.10.0-38-generic                         4.10.0-38.42~16.04.1                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
iF  linux-image-extra-4.13.0-41-generic                         4.13.0-41.46~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rH  linux-image-extra-4.13.0-43-generic                         4.13.0-43.48~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rH  linux-image-extra-4.13.0-45-generic                         4.13.0-45.50~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                        4.4.0-140.166                                amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-24-generic                             4.15.0-24.26~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-29-generic                             4.15.0-29.31~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-33-generic                             4.15.0-33.36~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-34-generic                             4.15.0-34.37~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-36-generic                             4.15.0-36.39~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-38-generic                             4.15.0-38.41~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-39-generic                             4.15.0-39.42~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-24-generic                       4.15.0-24.26~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-29-generic                       4.15.0-29.31~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-33-generic                       4.15.0-33.36~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-34-generic                       4.15.0-34.37~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-36-generic                       4.15.0-36.39~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-38-generic                       4.15.0-38.41~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-39-generic                       4.15.0-39.42~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-utils                                              3:6.03+dfsg-11ubuntu1                        amd64        collection of bootloaders (utilities)
```

---

### Post by coffeecat on 2018-12-18
@bernnt. you posted to the *Packaging and Compiling Programs* sub-forum which is for help with compiling programs and creating deb packages, and is inappropriate for your problem. This from your df output:

> ```
/dev/mapper/mint--vg-root 
```

tells us that you are running Linux Mint in an LVM. Therefore, I have moved this to the Mint sub-forum.

Your df output also tells us that your boot partition is 100% full, which explains at least part of your problem. There are other errors that suggest this may not be the only problem. Have you already attempted to remove anything? Please describe anything you may have already done so that forum members may be able to help you. What version of Mint are you running?

---

### Post by bernnt on 2018-12-18
i have tried anything i have found on the forum, including reinstalling files that create the problem, trying to delete them, purge them, anything. also the problem create a conflict when i try to free boot space.

**cat /etc/linuxmint/info**

RELEASE=18.3
CODENAME=sylvia
EDITION="Cinnamon 64-bit"
DESCRIPTION="Linux Mint 18.3 Sylvia"
DESKTOP=Gnome
TOOLKIT=GTK
NEW_FEATURES_URL=http://www.linuxmint.com/rel_sylvia_cinnamon_whatsnew.php
RELEASE_NOTES_URL=http://www.linuxmint.com/rel_sylvia_cinnamon.php
USER_GUIDE_URL=help:linuxmint
GRUB_TITLE=Linux Mint 18.3 Cinnamon 64-bit

---

### Post by ubname on 2018-12-18
Hi,

removing old kernels usually solve this kind of problem, one way to do that is using the "mint software" "Kernel" menu and remove all kernels *not* marked as "active".

Another way is to use the below simple script one line, to try if above do not work, *Use at your risk* it worked for me.

```
sudo dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

---

### Post by bernnt on 2018-12-18
**sudo dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge**

```
[sudo] password for polykarpos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc-dev-bin libclang-common-3.8-dev libfile-stripnondeterminism-perl libllvm3.8 po-debconf
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  alien* clang* clang-3.8* debhelper* dh-autoreconf* dh-strip-nondeterminism* g++* g++-5* libc6-dev* libclang1-3.8* libstdc++-5-dev* libtool* libusb-dev* linux-headers-4.10.0-38*
  linux-headers-4.10.0-38-generic* linux-headers-4.13.0-37* linux-headers-4.13.0-37-generic* linux-headers-4.13.0-38* linux-headers-4.13.0-38-generic* linux-headers-4.13.0-39*
  linux-headers-4.13.0-39-generic* linux-headers-4.13.0-41* linux-headers-4.13.0-41-generic* linux-headers-4.13.0-43* linux-headers-4.13.0-43-generic* linux-headers-4.13.0-45*
  linux-headers-4.13.0-45-generic* linux-headers-4.15.0-24* linux-headers-4.15.0-24-generic* linux-headers-4.15.0-29* linux-headers-4.15.0-29-generic* linux-headers-4.15.0-33*
  linux-headers-4.15.0-33-generic* linux-headers-4.15.0-34* linux-headers-4.15.0-34-generic* linux-headers-4.15.0-36* linux-headers-4.15.0-36-generic* linux-headers-4.15.0-39*
  linux-headers-4.15.0-39-generic* linux-image-4.13.0-39-generic* linux-image-4.13.0-41-generic* linux-image-4.15.0-24-generic* linux-image-4.15.0-29-generic* linux-image-4.15.0-33-generic*
  linux-image-4.15.0-34-generic* linux-image-4.15.0-36-generic* linux-image-extra-4.13.0-41-generic* linux-image-extra-4.13.0-43-generic linux-image-extra-4.13.0-45-generic linux-libc-dev*
  linux-modules-4.15.0-24-generic* linux-modules-4.15.0-29-generic* linux-modules-4.15.0-33-generic* linux-modules-4.15.0-34-generic* linux-modules-4.15.0-36-generic*
  linux-modules-extra-4.15.0-24-generic* linux-modules-extra-4.15.0-29-generic* linux-modules-extra-4.15.0-33-generic* linux-modules-extra-4.15.0-34-generic* linux-modules-extra-4.15.0-36-generic*
0 upgraded, 0 newly installed, 60 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 3152 MB disk space will be freed.
(Reading database ... 637228 files and directories currently installed.)
Removing linux-image-extra-4.13.0-41-generic (4.13.0-41.46~16.04.1) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-41-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-41-generic /boot/vmlinuz-4.13.0-41-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-41-generic /boot/vmlinuz-4.13.0-41-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-41-generic /boot/vmlinuz-4.13.0-41-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-41-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-41-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-41-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.13.0-41-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by bernnt on 2018-12-21
again the same problem

```
sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-extra-4.13.0-41-generic linux-image-extra-4.13.0-43-generic linux-image-extra-4.13.0-45-generic
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 500 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 632329 files and directories currently installed.)
Removing linux-image-extra-4.13.0-41-generic (4.13.0-41.46~16.04.1) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-41-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-41-generic /boot/vmlinuz-4.13.0-41-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-41-generic /boot/vmlinuz-4.13.0-41-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-41-generic /boot/vmlinuz-4.13.0-41-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-41-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-41-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-41-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-43-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Error! echo
Your kernel headers for kernel 4.13.0-43-generic cannot be found at
/lib/modules/4.13.0-43-generic/build or /lib/modules/4.13.0-43-generic/source.
Error! echo
Your kernel headers for kernel 4.13.0-43-generic cannot be found at
/lib/modules/4.13.0-43-generic/build or /lib/modules/4.13.0-43-generic/source.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-43-generic
Warning: No support for locale: en_US.utf8
depmod: WARNING: could not open /var/tmp/mkinitramfs_OqMPyW/lib/modules/4.13.0-43-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_OqMPyW/lib/modules/4.13.0-43-generic/modules.builtin: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-43-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-43-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.13.0-45-generic (4.13.0-45.50~16.04.1) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
Error! echo
Your kernel headers for kernel 4.13.0-45-generic cannot be found at
/lib/modules/4.13.0-45-generic/build or /lib/modules/4.13.0-45-generic/source.
Error! echo
Your kernel headers for kernel 4.13.0-45-generic cannot be found at
/lib/modules/4.13.0-45-generic/build or /lib/modules/4.13.0-45-generic/source.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-45-generic
Warning: No support for locale: en_US.utf8
depmod: WARNING: could not open /var/tmp/mkinitramfs_w2MTpa/lib/modules/4.13.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_w2MTpa/lib/modules/4.13.0-45-generic/modules.builtin: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-45-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.13.0-41-generic
 linux-image-extra-4.13.0-43-generic
 linux-image-extra-4.13.0-45-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by bernnt on 2019-01-11
```
sudo apt-get -y dist-upgrade


[sudo] password for polykarpos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-image-4.13.0-43-generic linux-image-4.13.0-45-generic
The following packages will be upgraded:
  exiv2 libexiv2-14 libpam-systemd libsystemd0 libudev1 libudev1:i386 systemd
  udev
8 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0 B/143 MB of archives.
After this operation, 145 MB of additional disk space will be used.
(Reading database ... 632333 files and directories currently installed.)
Preparing to unpack .../linux-image-4.13.0-43-generic_4.13.0-43.48~16.04.1_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Done.
Unpacking linux-image-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.13.0-43-generic_4.13.0-43.48~16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.13.0-43-generic' to '/boot/vmlinuz-4.13.0-43-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Preparing to unpack .../linux-image-4.13.0-45-generic_4.13.0-45.50~16.04.1_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
Done.
Unpacking linux-image-4.13.0-45-generic (4.13.0-45.50~16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.13.0-45-generic_4.13.0-45.50~16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.13.0-45-generic' to '/boot/System.map-4.13.0-45-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-45-generic /boot/vmlinuz-4.13.0-45-generic
Preparing to unpack .../libsystemd0_229-4ubuntu21.15_amd64.deb ...
Unpacking libsystemd0:amd64 (229-4ubuntu21.15) over (229-4ubuntu21.10) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.13.0-43-generic_4.13.0-43.48~16.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-4.13.0-45-generic_4.13.0-45.50~16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

