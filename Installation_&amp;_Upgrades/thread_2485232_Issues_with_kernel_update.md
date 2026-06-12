---
title: "Issues with kernel update"
date: 2023-03-23
forum: Installation &amp; Upgrades
---

### Post by mdobrea on 2023-03-23
Hi, to everyone!
 
 
 I have a development board NavQ Plus (with an ARM Cortex-A53) supported by a Ubuntu 20.04.6 LTS.
 
 
 The actual situation is the following one:
  
```

$ uname -a
Linux imx8mpnavq 5.10.72-lts-5.10.y+gb1e11be1a78a #1 SMP PREEMPT Wed Jun 29 12:55:32 UTC 2022 aarch64 aarch64 aarch64 GNU/Linux

```

My problem is the requirement to have one of the following Ubuntu kernels 4.4, 4.8, 4.10, 4.13, 4.15, 4.18, 5.0, 5.3, 5.4, 5.13 or 5.15 active in order to install Intel RealSense SDK 2.0 and work with Depth Camera D435i.
                       

So, I tried to upgrade from kernel version 5.10 to version 5.4 or 5.15 by using the script ubuntu-mainline-kernel.sh (accordingly with [https://askubuntu.com/questions/1388115/how-do-i-update-my-kernel-to-the-latest-one](https://askubuntu.com/questions/1388115/how-do-i-update-my-kernel-to-the-latest-one)) or through {sudo apt install --install-recommends linux-generic-hwe-20.04} or {sudo apt install --reinstall --install-recommends linux-generic}.

                       
All was done without errors, but when I reboot and check the version of the &#8220;new&#8221; kernel (uname -r) I get the original version 5.10.
 So, my situation is as follow:
  
```

$ which ubuntu-drivers
/usr/bin/ubuntu-drivers
$ ubuntu-drivers list-oem
 
$ ls -l /boot/initrd.img*
 lrwxrwxrwx 1 root root       31 Mar 23 19:33 /boot/initrd.img -> initrd.img-5.4.0-050400-generic
 -rw-r--r-- 1 root root 73072530 Mar 23 18:27 /boot/initrd.img-5.15.0-67-generic
 -rw-r--r-- 1 root root 50401681 Mar 23 19:34 /boot/initrd.img-5.4.0-050400-generic
 -rw-r--r-- 1 root root 53085619 Mar 23 19:04 /boot/initrd.img-5.4.0-144-generic
 lrwxrwxrwx 1 root root       28 Mar 23 19:33 /boot/initrd.img.old -> initrd.img-5.4.0-144-generic

$ dpkg --list 'linux-*' | grep -v '^rc\|^un'
 Desired=Unknown/Install/Remove/Purge/Hold
 | Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
 |/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
 ||/ Name                                              Version                       Architecture Description
 +++-=================================================-=============================-============-============================================================
 ii  linux-base                                                                      4.5ubuntu3.7                  all          Linux image base package
 ii  linux-firmware                                                                1.187.36                      all          Firmware for Linux kernel drivers
 ii  linux-generic                                                                   5.4.0.144.142                 arm64        Complete Generic Linux kernel and headers
 ii  linux-generic-hwe-20.04                                                 5.15.0.67.74~20.04.28         arm64        Complete Generic Linux kernel and headers
 ii  linux-headers-5.15.0-67-generic                                    5.15.0-67.74~20.04.1          arm64        Linux kernel headers for version 5.15.0 on ARMv8 SMP
 ii  linux-headers-5.4.0-050400                                           5.4.0-050400.201911242031     all          Header files related to Linux kernel version 5.4.0
 ii  linux-headers-5.4.0-050400-generic                              5.4.0-050400.201911242031     arm64        Linux kernel headers for version 5.4.0 on ARMv8 SMP
 ii  linux-headers-5.4.0-144                                                 5.4.0-144.161                 all          Header files related to Linux kernel version 5.4.0
 ii  linux-headers-5.4.0-144-generic                                     5.4.0-144.161                 arm64        Linux kernel headers for version 5.4.0 on ARMv8 SMP
 ii  linux-headers-generic                                                     5.4.0.144.142                 arm64        Generic Linux kernel headers
 ii  linux-headers-generic-hwe-20.04                                   5.15.0.67.74~20.04.28         arm64        Generic Linux kernel headers
 ii  linux-hwe-5.15-headers-5.15.0-67                                  5.15.0-67.74~20.04.1          all          Header files related to Linux kernel version 5.15.0
 ii  linux-image-5.15.0-67-generic                                        5.15.0-67.74~20.04.1          arm64        Signed kernel image generic
 ii  linux-image-5.4.0-144-generic                                        5.4.0-144.161                 arm64        Signed kernel image generic
 ii  linux-image-generic                                                         5.4.0.144.142                 arm64        Generic Linux kernel image
 ii  linux-image-generic-hwe-20.04                                       5.15.0.67.74~20.04.28         arm64        Generic Linux kernel image
 ii  linux-image-unsigned-5.15.104-0515104-generic           5.15.104-0515104.202303220949 arm64        Linux kernel image for version 5.15.104 on ARMv8 SMP
 ii  linux-image-unsigned-5.15.104-0515104-generic-64k    5.15.104-0515104.202303220949 arm64        Linux kernel image for version 5.15.104 on ARMv8 SMP
 ii  linux-image-unsigned-5.4.0-050400-generic                   5.4.0-050400.201911242031     arm64        Linux kernel image for version 5.4.0 on ARMv8 SMP
 ii  linux-libc-dev:arm64                                                        5.4.0-144.161                 arm64        Linux Kernel Headers for development
 ii  linux-modules-5.15.0-67-generic                                     5.15.0-67.74~20.04.1          arm64        Linux kernel extra modules for version 5.15.0 on ARMv8 SMP
 ii  linux-modules-5.15.104-0515104-generic                       5.15.104-0515104.202303220949 arm64        Linux kernel extra modules for version 5.15.104 on ARMv8 SMP
 ii  linux-modules-5.15.104-0515104-generic-64k                5.15.104-0515104.202303220949 arm64        Linux kernel extra modules for version 5.15.104 on ARMv8 SMP
 ii  linux-modules-5.4.0-050400-generic                               5.4.0-050400.201911242031     arm64        Linux kernel extra modules for version 5.4.0 on ARMv8 SMP
 ii  linux-modules-5.4.0-144-generic                                     5.4.0-144.161                 arm64        Linux kernel extra modules for version 5.4.0 on ARMv8 SMP
 ii  linux-modules-extra-5.15.0-67-generic                            5.15.0-67.74~20.04.1          arm64        Linux kernel extra modules for version 5.15.0 on ARMv8 SMP
 ii  linux-modules-extra-5.4.0-144-generic                            5.4.0-144.161                 arm64        Linux kernel extra modules for version 5.4.0 on ARMv8 SMP
 ii  linux-sound-base                                                             1.0.25+dfsg-0ubuntu5          all          base package for ALSA and OSS sound systems

 $ sudo apt install linux-generic
 [sudo] password for user:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 linux-generic is already the newest version (5.4.0.144.142).
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 
$ uname -a
Linux imx8mpnavq 5.10.72-lts-5.10.y+gb1e11be1a78a #1 SMP PREEMPT Wed Jun 29 12:55:32 UTC 2022 aarch64 aarch64 aarch64 GNU/Linux
 
```
  
                       
So, PLEASE, can you help me to change the kernel version? Any idea is welcome! Thank you!

---

