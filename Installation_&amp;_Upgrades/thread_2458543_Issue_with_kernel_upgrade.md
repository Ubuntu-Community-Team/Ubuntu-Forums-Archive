---
title: "Issue with kernel upgrade"
date: 2021-02-26
forum: Installation &amp; Upgrades
---

### Post by daithi_dearg on 2021-02-26
Hope this is the place for this.

I have had alot of issues over the last few months with my kernel and I am booting off an old version of the kernel:
5.4.0-42-generic

I was following this:
[https://linuxhint.com/update_ubuntu_kernel_20_04/](https://linuxhint.com/update_ubuntu_kernel_20_04/)

Previous issues I had is that my WiFi wouldn't work as it was depending on an intel iwlwifi driver that didn't appear to be in later kernels.

The Hardwrae I have is:
Wireless-AC 9260

```
david@david-N7x0WU:/usr/local/bin$ sudo dpkg -i /home/david/Downloads/linux-headers-5.10.12-051012_5.10.12-051012.202101301330_all.deb 
(Reading database ... 319457 files and directories currently installed.)
Preparing to unpack .../linux-headers-5.10.12-051012_5.10.12-051012.202101301330_all.deb ...
Unpacking linux-headers-5.10.12-051012 (5.10.12-051012.202101301330) over (5.10.12-051012.202101301330) ...
Setting up linux-headers-5.10.12-051012 (5.10.12-051012.202101301330) ...

david@david-N7x0WU:/usr/local/bin$ sudo dpkg -i /home/david/Downloads/linux-modules-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb 
(Reading database ... 319457 files and directories currently installed.)
Preparing to unpack .../linux-modules-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb ...
Unpacking linux-modules-5.10.12-051012-generic (5.10.12-051012.202101301330) ...
dpkg: error processing archive /home/david/Downloads/linux-modules-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb (--install):
 unable to open '/lib/modules/5.10.12-051012-generic/kernel/drivers/net/ethernet/broadcom/tg3.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /home/david/Downloads/linux-modules-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb

david@david-N7x0WU:/usr/local/bin$ sudo dpkg -i /home/david/Downloads/linux-image-unsigned-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb 
(Reading database ... 319457 files and directories currently installed.)
Preparing to unpack .../linux-image-unsigned-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb ...
Unpacking linux-image-unsigned-5.10.12-051012-generic (5.10.12-051012.202101301330) over (5.10.12-051012.202101301330) ...
dpkg: dependency problems prevent configuration of linux-image-unsigned-5.10.12-051012-generic:
 linux-image-unsigned-5.10.12-051012-generic depends on linux-modules-5.10.12-051012-generic; however:
  Package linux-modules-5.10.12-051012-generic is not installed.

dpkg: error processing package linux-image-unsigned-5.10.12-051012-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-unsigned-5.10.12-051012-generic

david@david-N7x0WU:/usr/local/bin$ sudo ubuntu-mainline-kernel.sh -i
Finding latest version available on kernel.ubuntu.com
Latest version is: v5.11.2, continue? (y/N) 
Abort, the amd64 build has not succeeded
```

Any ideas?

---

### Post by grahammechanical on 2021-02-26
Are there issues with the 5.4 kernel that cause you to install the 5.10 kernel? I have Ubuntu 20.04 and it has received several kernel updates in recent weeks but the installation is still on 5.4 kernel. In fact it is now 5.4.0-66-generic. This is the case even though the install is 20.04.2 LTS. In theory it should be having the 5.8 kernel. Everything works, so I do not worry.

I have an install of Ubuntu 20.10 and that has the 5.8 kernel, I also have an install of Ubuntu 21.04 (development) and that is on the 5.10 kernel. 

What issues are you having that make an install of the 5.10 kernel desirable?

Regards.

---

### Post by daithi_dearg on 2021-02-27
I have to press esc and go into the grub menu to select kernel .42 and I have these versions:
-rw-r--r-- 1 root root 36301920 Feb 19 19:35 /boot/initrd.img-5.4.0-45-generic
-rw-r--r-- 1 root root 82539986 Feb 19 19:36 /boot/initrd.img-5.4.0-42-generic
-rw-r--r-- 1 root root 36311367 Feb 19 19:42 /boot/initrd.img-5.4.0-51-generic

I'm on version 20.04.2 LTS.

I know I can edit the grub menu to automatically pick the .42 kernel but was just a bit concerned that I was falling behind on the kernel and would be susceptible to Security Vulnerabilities.

---

### Post by dino99 on 2021-02-27
Why are you using that 'unsigned' kernel ? It is used on 64 bit x86 SMP: is it the case for you system ? If not, then purge your kernel(s), and use/install instead linux-image-generic package.

---

### Post by daithi_dearg on 2021-02-27
Are you saying I only need these:
linux-headers-5.10.12-051012_5.10.12-051012.202101301330_all.deb   
linux-modules-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb

If that's correct I get errors with modules install:
```
david@david-N7x0WU:~$ sudo dpkg -i /home/david/Downloads/linux-modules-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb 
(Reading database ... 350601 files and directories currently installed.)
Preparing to unpack .../linux-modules-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb ...
Unpacking linux-modules-5.10.12-051012-generic (5.10.12-051012.202101301330) ...
dpkg: error processing archive /home/david/Downloads/linux-modules-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb (--install):
 unable to open '/lib/modules/5.10.12-051012-generic/kernel/drivers/input/serio/pcips2.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /home/david/Downloads/linux-modules-5.10.12-051012-generic_5.10.12-051012.202101301330_amd64.deb
```

I also see a later kernel:
```
david@david-N7x0WU:~$ dpkg -l | grep 5.4.0-66
iU  linux-headers-5.4.0-66                        5.4.0-66.74                           all          Header files related to Linux kernel version 5.4.0
iU  linux-headers-5.4.0-66-generic                5.4.0-66.74                           amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
iU  linux-image-5.4.0-66-generic                  5.4.0-66.74                           amd64        Signed kernel image generic
iU  linux-modules-5.4.0-66-generic                5.4.0-66.74                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
```

Not sure why this later image isn't seen in initrd:
```
david@david-N7x0WU:~$ ls -ltr /boot/initrd.img*
lrwxrwxrwx 1 root root       27 Oct 21 08:11 /boot/initrd.img.old -> initrd.img-5.4.0-45-generic
lrwxrwxrwx 1 root root       27 Oct 21 08:11 /boot/initrd.img -> initrd.img-5.4.0-51-generic
-rw-r--r-- 1 root root 36301920 Feb 19 19:35 /boot/initrd.img-5.4.0-45-generic
-rw-r--r-- 1 root root 82539986 Feb 19 19:36 /boot/initrd.img-5.4.0-42-generic
-rw-r--r-- 1 root root 36311367 Feb 19 19:42 /boot/initrd.img-5.4.0-51-generic
```

---

### Post by daithi_dearg on 2021-02-27
Also don't see that image-linux-generic here but perhaps I'm looking in the wrong place:
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10.12/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10.12/)

```
david@david-N7x0WU:~$ uname -a
Linux david-N7x0WU 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Impavidus on 2021-02-27
Your hardware works with kernel 5.4.0-42, which means that it should work with all 5.4 kernels unless some contain a bug. There should be no need for 5.10 or 5.8 kernels. So why are you trying to install a 5.10 kernel? It's simpler to stay with the officially supported kernels for your Ubuntu release. For Ubuntu 20.04, that is 5.4 or 5.8.

The 5.4.0-66 kernel packages have been unpacked, but not fully installed. That's why they have no initrd.image files.

Can you show us a list of all currently installed kernel packages, including the partially installed packages?```
dpkg --list 'linux-*' | grep -v '^rc\|^un'
```Maybe your kernels after 5.4.0-42 don't work because they were only partially installed.

---

### Post by daithi_dearg on 2021-02-28
Kernels 45/51 load fine but the Intel Wireless Hardware doesn't work on these versions as I'm guessing the drivers are mising


```
david@david-N7x0WU:~$ dpkg --list 'linux-*' | grep -v '^rc\|^un'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture Description
+++-=============================================-===========================-============-===============================================================
ii  linux-base                                    4.5ubuntu3.1                all          Linux image base package
ii  linux-firmware                                1.187.9                     all          Firmware for Linux kernel drivers
iU  linux-generic                                 5.4.0.66.69                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.10.12-051012                  5.10.12-051012.202101301330 all          Header files related to Linux kernel version 5.10.12
ii  linux-headers-5.10.6-051006                   5.10.6-051006.202101091334  all          Header files related to Linux kernel version 5.10.6
ii  linux-headers-5.10.6-051006-generic           5.10.6-051006.202101091334  amd64        Linux kernel headers for version 5.10.6 on 64 bit x86 SMP
ii  linux-headers-5.10.6-051006-lowlatency        5.10.6-051006.202101091334  amd64        Linux kernel headers for version 5.10.6 on 64 bit x86 SMP
ii  linux-headers-5.11.0-051100                   5.11.0-051100.202102142330  all          Header files related to Linux kernel version 5.11.0
ii  linux-headers-5.11.0-051100-generic           5.11.0-051100.202102142330  amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-42                        5.4.0-42.46                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-45                        5.4.0-45.49                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-45-generic                5.4.0-45.49                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-51                        5.4.0-51.56                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-51-generic                5.4.0-51.56                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
iU  linux-headers-5.4.0-66                        5.4.0-66.74                 all          Header files related to Linux kernel version 5.4.0
iU  linux-headers-5.4.0-66-generic                5.4.0-66.74                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
iU  linux-headers-generic                         5.4.0.66.69                 amd64        Generic Linux kernel headers
ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-45-generic                  5.4.0-45.49                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-51-generic                  5.4.0-51.56                 amd64        Signed kernel image generic
iU  linux-image-5.4.0-66-generic                  5.4.0-66.74                 amd64        Signed kernel image generic
iU  linux-image-generic                           5.4.0.66.69                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          5.4.0-65.73                 amd64        Linux Kernel Headers for development
in  linux-modules-5.10.12-051012-generic          <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
ii  linux-modules-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-45-generic                5.4.0-45.49                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-51-generic                5.4.0-51.56                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
iU  linux-modules-5.4.0-66-generic                5.4.0-66.74                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-43-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-45-generic         <none>                      amd64        (no description available)
ii  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-66-generic          <none>                      amd64        (no description available)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5        all          base package for ALSA and OSS sound systems

```

---

### Post by Impavidus on 2021-02-28
The linux-modules-extra packages for kernel 5.4.0-45 and higher haven't been installed. I think that causes your wireless problem. They have been marked for installation.

Let's see how apt itself thinks this can be solved.```
sudo apt-get install -f --simulate
```If it doesn't show anything alarming, you can run it without the --simulate. If in doubt, show the output here. If you run the above command without the --simulate, show the output from the dpkg command from the previous post again, to see how that cleaned things up. And if you get any errors in any command, show command and full output.

Hope I didn't put too many conditionals in the above.

---

### Post by daithi_dearg on 2021-03-01
Getting following now:


```
avid@david-N7x0WU:~$ sudo apt-get install -f --simulate
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-modules-extra-5.4.0-66-generic
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-66-generic
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
11 not fully installed or removed.
Inst linux-modules-extra-5.4.0-66-generic (5.4.0-66.74 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])
Conf linux-modules-extra-5.4.0-66-generic (5.4.0-66.74 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])
Conf linux-image-5.4.0-66-generic (5.4.0-66.74 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])
Conf intel-microcode (3.20201110.0ubuntu0.20.04.2 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])
Conf linux-headers-generic (5.4.0.66.69 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])
Conf linux-image-generic (5.4.0.66.69 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])
Conf iucode-tool (2.3.1-1 Ubuntu:20.04/focal [amd64])
Conf linux-headers-5.4.0-66-generic (5.4.0-66.74 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])
Conf amd64-microcode (3.20191218.1ubuntu1 Ubuntu:20.04/focal [amd64])
Conf linux-modules-5.4.0-66-generic (5.4.0-66.74 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])
Conf linux-headers-5.4.0-66 (5.4.0-66.74 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [all])
Conf thermald (1.9.1-1ubuntu0.3 Ubuntu:20.04/focal-updates [amd64])
Conf linux-generic (5.4.0.66.69 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])

david@david-N7x0WU:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-modules-extra-5.4.0-66-generic
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-66-generic
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
11 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 350601 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-66-generic (5.4.0-66.74) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-66-generic/kernel/drivers/net/ethernet/3com/3c59x.ko.dpkg-new': Operation not permitted
Segmentation fault

david@david-N7x0WU:~$ dpkg --list 'linux-*' | grep -v '^rc\|^un'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture Description
+++-=============================================-===========================-============-===============================================================
ii  linux-base                                    4.5ubuntu3.1                all          Linux image base package
ii  linux-firmware                                1.187.9                     all          Firmware for Linux kernel drivers
iU  linux-generic                                 5.4.0.66.69                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.10.12-051012                  5.10.12-051012.202101301330 all          Header files related to Linux kernel version 5.10.12
ii  linux-headers-5.10.6-051006                   5.10.6-051006.202101091334  all          Header files related to Linux kernel version 5.10.6
ii  linux-headers-5.10.6-051006-generic           5.10.6-051006.202101091334  amd64        Linux kernel headers for version 5.10.6 on 64 bit x86 SMP
ii  linux-headers-5.10.6-051006-lowlatency        5.10.6-051006.202101091334  amd64        Linux kernel headers for version 5.10.6 on 64 bit x86 SMP
ii  linux-headers-5.11.0-051100                   5.11.0-051100.202102142330  all          Header files related to Linux kernel version 5.11.0
ii  linux-headers-5.11.0-051100-generic           5.11.0-051100.202102142330  amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-42                        5.4.0-42.46                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-45                        5.4.0-45.49                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-45-generic                5.4.0-45.49                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-51                        5.4.0-51.56                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-51-generic                5.4.0-51.56                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
iU  linux-headers-5.4.0-66                        5.4.0-66.74                 all          Header files related to Linux kernel version 5.4.0
iU  linux-headers-5.4.0-66-generic                5.4.0-66.74                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
iU  linux-headers-generic                         5.4.0.66.69                 amd64        Generic Linux kernel headers
ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-45-generic                  5.4.0-45.49                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-51-generic                  5.4.0-51.56                 amd64        Signed kernel image generic
iU  linux-image-5.4.0-66-generic                  5.4.0-66.74                 amd64        Signed kernel image generic
iU  linux-image-generic                           5.4.0.66.69                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          5.4.0-65.73                 amd64        Linux Kernel Headers for development
in  linux-modules-5.10.12-051012-generic          <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
ii  linux-modules-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-45-generic                5.4.0-45.49                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-51-generic                5.4.0-51.56                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
iU  linux-modules-5.4.0-66-generic                5.4.0-66.74                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-43-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-45-generic         <none>                      amd64        (no description available)
ii  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-66-generic          <none>                      amd64        (no description available)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5        all          base package for ALSA and OSS sound systems

```

---

### Post by Impavidus on 2021-03-01
> **daithi_dearg said:**
> Getting following now:

```

Unpacking linux-modules-extra-5.4.0-66-generic (5.4.0-66.74) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-66-generic/kernel/drivers/net/ethernet/3com/3c59x.ko.dpkg-new': Operation not permitted
Segmentation fault

```

At least there's an error message. Let's investigate. Why is that operation not permitted? Redownload the package files to rule out file corruption.```
ls -al /lib/modules/5.4.0-66-generic/kernel/drivers/net/ethernet/3com
sudo apt-get clean
sudo apt-get update
sudo apt-get install -f
```

---

### Post by daithi_dearg on 2021-03-01
Still not finding files in the /lib/modules directory.

Is there a deeper clean I can do or perhaps I could download the kernel files after 66.

```
david@david-N7x0WU:~$ ls -al /lib/modules/5.4.0-66-generic/kernel/drivers/net/ethernet/3com
ls: cannot access '/lib/modules/5.4.0-66-generic/kernel/drivers/net/ethernet/3com': No such file or directory
david@david-N7x0WU:~$ sudo apt-get clean
[sudo] password for david: 

david@david-N7x0WU:~$ sudo apt-get update
Hit:1 http://ie.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://ie.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:3 http://ie.archive.ubuntu.com/ubuntu focal-backports InRelease        
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease           
Reading package lists... Done                        

david@david-N7x0WU:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-modules-extra-5.4.0-66-generic
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-66-generic
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
11 not fully installed or removed.
Need to get 38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-extra-5.4.0-66-generic amd64 5.4.0-66.74 [38.6 MB]
Fetched 38.6 MB in 7s (5,157 kB/s)                                                                                                                                                                        
(Reading database ... 350601 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-66-generic (5.4.0-66.74) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-66-generic/kernel/drivers/media/pci/mantis/mantis.ko.dpkg-new': Operation not permitted
Segmentation fault (core dumped)

david@david-N7x0WU:~$ ls -al /lib/modules/5.4.0-66-generic/kernel/
arch/             crypto/           drivers/          fs/               lib/              net/              sound/            virtualbox-guest/ wireguard/        zfs/  
```

---

### Post by Impavidus on 2021-03-01
It's a bit weird that you get an "operation not permitted" error (which is different from the "permission denied" error). I may have found one lead: [https://askubuntu.com/questions/898606/operation-not-permitted-while-installing-linux-headers-4-8-0-45](https://askubuntu.com/questions/898606/operation-not-permitted-while-installing-linux-headers-4-8-0-45)
Bug report: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1685984](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1685984)

---

### Post by daithi_dearg on 2021-03-01
I was able to disable my AV and I now see .66 when I go into the grub menu but still have the issue with the Wifi card.

Commands I did are as follows:
sudo systemctl stop clamav-freshclam.service
sudo apt-get install -f  (Prompted me to run command below)
sudo dpkg --configure -a

Differences in /lib/modules for 42 versus 66 if that helps

```
david@david-N7x0WU:~$ ls /lib/modules/5.4.0-42-generic/kernel/drivers/net/wireless/intel/
ipw2x00  iwlegacy  iwlwifi
david@david-N7x0WU:~$ ls /lib/modules/5.4.0-66-generic/kernel/drivers/net/
bonding  dummy.ko  ethernet  geneve.ko  ifb.ko  macvlan.ko  mdio.ko  netconsole.ko    ppp   tap.ko   virtio_net.ko  vxlan.ko
caif     eql.ko    fddi      hyperv     ipvlan  macvtap.ko  mii.ko   net_failover.ko  slip  veth.ko  vmxnet3        xen-netback

```

---

### Post by Impavidus on 2021-03-02
Have all packages been installed now, as far as the package manager can tell?```
dpkg --list 'linux-*' | grep -v '^rc\|^un'
```
Which kernel are you now running?```
uname -a
```

---

### Post by daithi_dearg on 2021-03-02
Output of command:
```
david@david-N7x0WU:~$ dpkg --list 'linux-*' | grep -v '^rc\|^un'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture Description
+++-=============================================-===========================-============-===============================================================
ii  linux-base                                    4.5ubuntu3.1                all          Linux image base package
ii  linux-firmware                                1.187.9                     all          Firmware for Linux kernel drivers
iU  linux-generic                                 5.4.0.66.69                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.10.12-051012                  5.10.12-051012.202101301330 all          Header files related to Linux kernel version 5.10.12
ii  linux-headers-5.10.6-051006                   5.10.6-051006.202101091334  all          Header files related to Linux kernel version 5.10.6
ii  linux-headers-5.10.6-051006-generic           5.10.6-051006.202101091334  amd64        Linux kernel headers for version 5.10.6 on 64 bit x86 SMP
ii  linux-headers-5.10.6-051006-lowlatency        5.10.6-051006.202101091334  amd64        Linux kernel headers for version 5.10.6 on 64 bit x86 SMP
ii  linux-headers-5.11.0-051100                   5.11.0-051100.202102142330  all          Header files related to Linux kernel version 5.11.0
ii  linux-headers-5.11.0-051100-generic           5.11.0-051100.202102142330  amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-42                        5.4.0-42.46                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-45                        5.4.0-45.49                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-45-generic                5.4.0-45.49                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-51                        5.4.0-51.56                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-51-generic                5.4.0-51.56                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-66                        5.4.0-66.74                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-66-generic                5.4.0-66.74                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                         5.4.0.66.69                 amd64        Generic Linux kernel headers
ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-45-generic                  5.4.0-45.49                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-51-generic                  5.4.0-51.56                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-66-generic                  5.4.0-66.74                 amd64        Signed kernel image generic
iU  linux-image-generic                           5.4.0.66.69                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          5.4.0-65.73                 amd64        Linux Kernel Headers for development
in  linux-modules-5.10.12-051012-generic          <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
ii  linux-modules-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-45-generic                5.4.0-45.49                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-51-generic                5.4.0-51.56                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-66-generic                5.4.0-66.74                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-43-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-45-generic         <none>                      amd64        (no description available)
ii  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
iHR linux-modules-extra-5.4.0-66-generic          5.4.0-66.74                 amd64        (no description available)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5        all          base package for ALSA and OSS sound systems
```

uname -a points at .66 but the Wifi card doesn't work on this version.

---

### Post by Impavidus on 2021-03-02
Your linux-modules-extra-5.4.0-66-generic still hasn't been properly installed. dpkg --configure -a did something, but not all that had to be done.

Maybe a few apt-get install -f and dpkg --configure -a will help. Run```
sudo apt-get install -f
```If it asks you to run some other commands, run those too, followed by another apt-get install -f. You may have to reinstall linux-modules-extra-5.4.0-66-generic:```
sudo apt install --reinstall  linux-modules-extra-5.4.0-66-generic
```

---

### Post by ajgreeny on 2021-03-02
It looks as if there is still a problem with the ***linux-modules-extra-5.4.0-66-generic*** package which I think is only partly configured so it may be worth trying firstly to reconfigure that with ```
sudo dpkg-reconfigure linux-modules-extra-5.4.0-66-generic
``` and if that does not work you may need to reinstall that package.

First you should remove the .deb package from your cache in case it is corrupt with ```
sudo rm /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic
``` and then reinstall the package with
```
sudo apt install --reinstall linux-modules-extra-5.4.0-66-generic
```

---

### Post by daithi_dearg on 2021-03-03
Still no joy. Here are the commands I ran:

```
david@david-N7x0WU:~$ sudo systemctl status clamav-freshclam.service
[sudo] password for david: 
&#9679; clamav-freshclam.service - ClamAV virus database updater
     Loaded: loaded (/lib/systemd/system/clamav-freshclam.service; disabled; ve>
     Active: inactive (dead)
       Docs: man:freshclam(1)
             man:freshclam.conf(5)
             https://www.clamav.net/documents
david@david-N7x0WU:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.

david@david-N7x0WU:~$ sudo dpkg --configure -a

david@david-N7x0WU:~$ sudo apt install --reinstall  linux-modules-extra-5.4.0-66-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-66-generic
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
Need to get 0 B/38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
(Reading database ... 319452 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.d
eb ...
Unpacking linux-modules-extra-5.4.0-66-generic (5.4.0-66.74) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0
-66-generic_5.4.0-66.74_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-66-generic/kernel/drivers/net/ethernet/intel
/ixgb/ixgb.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.
deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

david@david-N7x0WU:~$ sudo dpkg-reconfigure linux-modules-extra-5.4.0-66-generic
/usr/sbin/dpkg-reconfigure: linux-modules-extra-5.4.0-66-generic is not installed

david@david-N7x0WU:~$ sudo rm /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic
rm: cannot remove '/var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic': No such file or directory

david@david-N7x0WU:~$ dpkg --list 'linux-*' | grep -v '^rc\|^un'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture Description
+++-=============================================-===========================-============-===============================================================
ii  linux-base                                    4.5ubuntu3.1                all          Linux image base package
ii  linux-firmware                                1.187.9                     all          Firmware for Linux kernel drivers
ii  linux-headers-5.10.12-051012                  5.10.12-051012.202101301330 all          Header files related to Linux kernel version 5.10.12
ii  linux-headers-5.10.6-051006                   5.10.6-051006.202101091334  all          Header files related to Linux kernel version 5.10.6
ii  linux-headers-5.10.6-051006-generic           5.10.6-051006.202101091334  amd64        Linux kernel headers for version 5.10.6 on 64 bit x86 SMP
ii  linux-headers-5.10.6-051006-lowlatency        5.10.6-051006.202101091334  amd64        Linux kernel headers for version 5.10.6 on 64 bit x86 SMP
ii  linux-headers-5.11.0-051100                   5.11.0-051100.202102142330  all          Header files related to Linux kernel version 5.11.0
ii  linux-headers-5.11.0-051100-generic           5.11.0-051100.202102142330  amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-42                        5.4.0-42.46                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-51                        5.4.0-51.56                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-51-generic                5.4.0-51.56                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-66                        5.4.0-66.74                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-66-generic                5.4.0-66.74                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-51-generic                  5.4.0-51.56                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-66-generic                  5.4.0-66.74                 amd64        Signed kernel image generic
ii  linux-libc-dev:amd64                          5.4.0-65.73                 amd64        Linux Kernel Headers for development
in  linux-modules-5.10.12-051012-generic          <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
ii  linux-modules-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-51-generic                5.4.0-51.56                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-66-generic                5.4.0-66.74                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-5.6.14-050614-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-43-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-45-generic         <none>                      amd64        (no description available)
ii  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-66-generic          <none>                      amd64        (no description available)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5        all          base package for ALSA and OSS sound systems
```

---

### Post by ajgreeny on 2021-03-03
Strange, but let's see if you are running short of either disk or inode space with the two commands ```
df -h
df -i
```

---

### Post by daithi_dearg on 2021-03-03
Looks like my inodes are full. I'll have to look at how to recover from this

```
david@david-N7x0WU:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.8G     0  3.8G   0% /dev
tmpfs                        784M  1.9M  783M   1% /run
/dev/mapper/ubuntu--vg-root  456G  146G  287G  34% /
tmpfs                        3.9G   20K  3.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0                   9.2M  9.2M     0 100% /snap/canonical-livepatch/94
/dev/loop3                    99M   99M     0 100% /snap/core/10823
/dev/loop2                   138M  138M     0 100% /snap/chromium/1479
/dev/loop4                    56M   56M     0 100% /snap/core18/1944
/dev/loop5                    98M   98M     0 100% /snap/core/10583
/dev/loop6                    56M   56M     0 100% /snap/core18/1988
/dev/loop7                   138M  138M     0 100% /snap/chromium/1497
/dev/loop1                   9.2M  9.2M     0 100% /snap/canonical-livepatch/95
/dev/loop8                   141M  141M     0 100% /snap/gnome-3-26-1604/98
/dev/loop9                   141M  141M     0 100% /snap/gnome-3-26-1604/100
/dev/loop10                  240M  240M     0 100% /snap/zoom-client/132
/dev/loop12                   65M   65M     0 100% /snap/gtk-common-themes/1513
/dev/loop11                  130M  130M     0 100% /snap/skype/162
/dev/loop13                  338M  338M     0 100% /snap/wine-platform-runtime/216
/dev/loop15                  5.5M  5.5M     0 100% /snap/notepad-plus-plus/258
/dev/loop14                  135M  135M     0 100% /snap/skype/164
/dev/loop16                  618M  618M     0 100% /snap/libreoffice/204
/dev/loop17                  304M  304M     0 100% /snap/wine-platform-5-stable/16
/dev/loop18                   52M   52M     0 100% /snap/snap-store/518
/dev/loop19                  218M  218M     0 100% /snap/gnome-3-34-1804/60
/dev/loop20                  240M  240M     0 100% /snap/zoom-client/134
/dev/loop21                  5.7M  5.7M     0 100% /snap/notepad-plus-plus/253
/dev/loop22                  338M  338M     0 100% /snap/wine-platform-runtime/206
/dev/loop23                   65M   65M     0 100% /snap/gtk-common-themes/1514
/dev/loop24                  219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop25                  2.3M  2.3M     0 100% /snap/gnome-system-monitor/148
/dev/loop26                   52M   52M     0 100% /snap/snap-store/498
/dev/loop28                  163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop29                  2.3M  2.3M     0 100% /snap/gnome-system-monitor/157
/dev/loop27                  216M  216M     0 100% /snap/wine-platform-5-stable/13
/dev/loop30                  607M  607M     0 100% /snap/libreoffice/203
/dev/loop31                  162M  162M     0 100% /snap/gnome-3-28-1804/128
/dev/sda2                    705M  210M  445M  33% /boot
/dev/sda1                    511M  7.9M  504M   2% /boot/efi
tmpfs                        784M   32K  784M   1% /run/user/1000
david@david-N7x0WU:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
udev                          992387    594   991793    1% /dev
tmpfs                        1003457   1282  1002175    1% /run
/dev/mapper/ubuntu--vg-root 30384128 389049 29995079    2% /
tmpfs                        1003457      5  1003452    1% /dev/shm
tmpfs                        1003457      6  1003451    1% /run/lock
tmpfs                        1003457     18  1003439    1% /sys/fs/cgroup
/dev/loop0                        34     34        0  100% /snap/canonical-livepatch/94
/dev/loop3                     12921  12921        0  100% /snap/core/10823
/dev/loop2                      1355   1355        0  100% /snap/chromium/1479
/dev/loop4                     10809  10809        0  100% /snap/core18/1944
/dev/loop5                     12867  12867        0  100% /snap/core/10583
/dev/loop6                     10817  10817        0  100% /snap/core18/1988
/dev/loop7                      1355   1355        0  100% /snap/chromium/1497
/dev/loop1                        34     34        0  100% /snap/canonical-livepatch/95
/dev/loop8                     27631  27631        0  100% /snap/gnome-3-26-1604/98
/dev/loop9                     27624  27624        0  100% /snap/gnome-3-26-1604/100
/dev/loop10                    13534  13534        0  100% /snap/zoom-client/132
/dev/loop12                    63811  63811        0  100% /snap/gtk-common-themes/1513
/dev/loop11                    15167  15167        0  100% /snap/skype/162
/dev/loop13                    27781  27781        0  100% /snap/wine-platform-runtime/216
/dev/loop15                      243    243        0  100% /snap/notepad-plus-plus/258
/dev/loop14                    15168  15168        0  100% /snap/skype/164
/dev/loop16                    14632  14632        0  100% /snap/libreoffice/204
/dev/loop17                     2515   2515        0  100% /snap/wine-platform-5-stable/16
/dev/loop18                    15847  15847        0  100% /snap/snap-store/518
/dev/loop19                    18513  18513        0  100% /snap/gnome-3-34-1804/60
/dev/loop20                    13534  13534        0  100% /snap/zoom-client/134
/dev/loop21                      242    242        0  100% /snap/notepad-plus-plus/253
/dev/loop22                    27781  27781        0  100% /snap/wine-platform-runtime/206
/dev/loop23                    63978  63978        0  100% /snap/gtk-common-themes/1514
/dev/loop24                    18508  18508        0  100% /snap/gnome-3-34-1804/66
/dev/loop25                      784    784        0  100% /snap/gnome-system-monitor/148
/dev/loop26                    15847  15847        0  100% /snap/snap-store/498
/dev/loop28                    27807  27807        0  100% /snap/gnome-3-28-1804/145
/dev/loop29                      872    872        0  100% /snap/gnome-system-monitor/157
/dev/loop27                     2515   2515        0  100% /snap/wine-platform-5-stable/13
/dev/loop30                    14484  14484        0  100% /snap/libreoffice/203
/dev/loop31                    27798  27798        0  100% /snap/gnome-3-28-1804/128
/dev/sda2                      46848    321    46527    1% /boot
/dev/sda1                          0      0        0     - /boot/efi
tmpfs                        1003457     96  1003361    1% /run/user/1000
```

---

### Post by daithi_dearg on 2021-03-03
Came across this:
[https://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html](https://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html)

Note sure should I have done this but failed anyway:
```
rm: cannot remove '/snap/gtk-common-themes/1514/share/themes/elementary/gtk-3.0/gtk.css': Read-only file system
rm: cannot remove '/snap/gtk-common-themes/1514/share/themes/elementary/gtk-3.0/palette.css': Read-only file system
rm: cannot remove '/snap/gtk-common-themes/1514/snap/manifest.yaml': Read-only file system
rm: cannot remove '/snap/gtk-common-themes/1514/snap/snapcraft.yaml': Read-only file system
```

Not too sure where to go from here.

---

### Post by deadflowr on 2021-03-03
Snaps are loop mounted into the snap directory, the actual snaps are in the /var/lib/snapd/snaps directory, 
but don't rm them as that'll cause more issues than you want.

Use snap tools to remove old snaps.
here's a simple script to do it, which will leave you with one revision of each installed snap:
```
#!/bin/sh
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done
```
save it as any file name you want and make it executable and then run
```
sudo ./filename-here
```
replace filename-here with whatever the file name make is.

FWIW, you can cut the snaps from the df output by excluding squashfs filesystem type snaps use like
```
df -Th -x squashfs
```

But based on the output you have lots of space and plenty of inodes.
Both / and /boot are not nearly close to full.

---

### Post by daithi_dearg on 2021-03-04
Ran the script but as expected similar issues:
```
david@david-N7x0WU:~/scripts$ sudo apt install --reinstall  linux-modules-extra-5.4.0-66-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-66-generic
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
Need to get 0 B/38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
(Reading database ... 319452 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-66-generic (5.4.0-66.74) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-66-generic/kernel/drivers/media/pci/ttpci/dvb-ttpci.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This is the output from dmesg and perhaps there are other logs I should be looking at:
```
david@david-N7x0WU:~/scripts$ dmesg|tail
[  310.933238] apt[23117]: segfault at 0 ip 00007fb8c410d7d7 sp 00007ffc7699d9d0 error 4 in libc-2.31.so[7fb8c40ad000+178000]
[  310.933244] Code: 00 00 00 f3 0f 1e fa 85 f6 0f 8e 14 01 00 00 41 55 41 54 49 89 fc 55 89 f5 53 48 83 ec 08 83 fe 01 0f 84 0c 01 00 00 48 89 d3 <8b> 12 89 d1 81 e1 00 80 00 00 75 3f 48 8b bb 88 00 00 00 64 4c 8b

```

Do I need to accept defeat?

---

### Post by deadflowr on 2021-03-04
Try purging the package instead of reinstalling.
Also do you have any AV software running like this user did: [https://forums.linuxmint.com/viewtopic.php?t=295201]("https://forums.linuxmint.com/viewtopic.php?t=295201")
or something similar.

---

### Post by Impavidus on 2021-03-04
> **deadflowr said:**
> Also do you have any AV software running like this user did: [https://forums.linuxmint.com/viewtopic.php?t=295201](https://forums.linuxmint.com/viewtopic.php?t=295201)
or something similar.
Already looked at that:
> **Impavidus said:**
> It's a bit weird that you get an "operation  not permitted" error (which is different from the "permission denied"  error). I may have found one lead: [https://askubuntu.com/questions/898606/operation-not-permitted-while-installing-linux-headers-4-8-0-45](https://askubuntu.com/questions/898606/operation-not-permitted-while-installing-linux-headers-4-8-0-45)
Bug report: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1685984](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1685984)
That bug was reported 4 years ago. I guess the dpkg people consider this a bug in the AV software and the AV people think dpkg should be able to work around that... Or something like it.

Still, maybe check again that all AV software is disabled.

---

### Post by daithi_dearg on 2021-03-04
I had ClamAV disabled when I got the error.

Just to go an extra step I ended up removing the AV altogether to be sure.

In the grub menu I have a 65 and 66 kernel but Wifi card works on neither.

Still getting similar issues and I hope I did the purge correctly:
```
david@david-N7x0WU:~$ sudo apt remove --purge linux-modules-extra-5.4.0-66-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-modules-extra-5.4.0-66-generic' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
david@david-N7x0WU:~$ sudo apt install --reinstall  linux-modules-extra-5.4.0-66-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-66-generic
0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
Need to get 0 B/38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
(Reading database ... 289475 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-66-generic (5.4.0-66.74) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-66-generic/kernel/drivers/media/usb/tm6000/tm6000-alsa.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by deadflowr on 2021-03-05
Run all the commands in the the first post in the link I provided in post #25.
Switch out the first command to remove linux-image-generic with the linux-modules-extra-5.4.0-66-generic package
like
```
sudo dpkg --remove --force-remove-reinstreq linux-modules-extra-5.4.0-66-generic
```

That should completely clear the system of the package.

---

### Post by daithi_dearg on 2021-03-05
Already removed AV.

Purged 66 and was able to reinstall it with:
```
sudo apt install linux-modules-extra-5.4.0-66-generic
```

In the grub menu can boot into .66 but don't see the Wifi card but in .42 I do see it.

I did a cleanup of the other kernels and I am left with these:
```
david@david-N7x0WU:~$ dpkg --list 'linux-*' | grep -v '^rc\|^un'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture Description
+++-=============================================-===========================-============-===============================================================
ii  linux-base                                    4.5ubuntu3.1                all          Linux image base package
ii  linux-firmware                                1.187.9                     all          Firmware for Linux kernel drivers
in  linux-headers-5.11.3-051103-generic           <none>                      amd64        (no description available)
ii  linux-headers-5.4.0-42                        5.4.0-42.46                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-66-generic                  5.4.0-66.74                 amd64        Signed kernel image generic
ii  linux-libc-dev:amd64                          5.4.0-65.73                 amd64        Linux Kernel Headers for development
in  linux-modules-5.10.12-051012-generic          <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
ii  linux-modules-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-66-generic                5.4.0-66.74                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-5.6.14-050614-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-43-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-45-generic         <none>                      amd64        (no description available)
ii  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-65-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-66-generic          <none>                      amd64        (no description available)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5        all          base package for ALSA and OSS sound systems
```

---

