---
title: "I have a problem with update"
date: 2022-06-08
forum: Installation &amp; Upgrades
---

### Post by elforescanvia on 2022-06-08
Hello community!!! i have server with ubuntu 20.04 but be try install the update and it's show errors the what attach

```

root@cenazosaesaweb:~# apt install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfwupdplugin1 linux-azure-5.13-cloud-tools-5.13.0-1023 linux-azure-5.13-cloud-tools-5.13.0-1025 linux-azure-5.13-headers-5.13.0-1023 linux-azure-5.13-headers-5.13.0-1025 linux-azure-5.13-tools-5.13.0-1023
  linux-azure-5.13-tools-5.13.0-1025 linux-cloud-tools-5.13.0-1023-azure linux-cloud-tools-5.13.0-1025-azure linux-headers-5.13.0-1023-azure linux-headers-5.13.0-1025-azure linux-image-5.13.0-1023-azure linux-image-5.13.0-1025-azure
  linux-modules-5.13.0-1023-azure linux-modules-5.13.0-1025-azure linux-tools-5.13.0-1023-azure linux-tools-5.13.0-1025-azure
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-5.13.0-1023-azure linux-image-5.13.0-1025-azure linux-image-5.13.0-1028-azure
Suggested packages:
  fdutils linux-azure-5.13-doc-5.13.0 | linux-azure-5.13-source-5.13.0 linux-azure-5.13-tools
The following NEW packages will be installed:
  linux-image-5.13.0-1023-azure linux-image-5.13.0-1025-azure linux-image-5.13.0-1028-azure
0 upgraded, 3 newly installed, 0 to remove and 58 not upgraded.
14 not fully installed or removed.
Need to get 28.4 MB of archives.
After this operation, 28.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://azure.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.13.0-1028-azure amd64 5.13.0-1028.33~20.04.1 [9485 kB]
Get:2 http://azure.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.13.0-1023-azure amd64 5.13.0-1023.27~20.04.1 [9473 kB]
Get:3 http://azure.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.13.0-1025-azure amd64 5.13.0-1025.29~20.04.1 [9485 kB]
Fetched 28.4 MB in 4s (8105 kB/s)
dpkg: warning: files list file for package 'linux-modules-5.13.0-1014-azure' missing; assuming package has no files currently installed
(Reading database ... 278034 files and directories currently installed.)
Preparing to unpack .../linux-image-5.13.0-1028-azure_5.13.0-1028.33~20.04.1_amd64.deb ...
Unpacking linux-image-5.13.0-1028-azure (5.13.0-1028.33~20.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-5.13.0-1028-azure_5.13.0-1028.33~20.04.1_amd64.deb (--unpack):
 unable to open '/boot/vmlinuz-5.13.0-1028-azure.dpkg-new': Operation not permitted
Preparing to unpack .../linux-image-5.13.0-1023-azure_5.13.0-1023.27~20.04.1_amd64.deb ...
Unpacking linux-image-5.13.0-1023-azure (5.13.0-1023.27~20.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-5.13.0-1023-azure_5.13.0-1023.27~20.04.1_amd64.deb (--unpack):
 unable to open '/boot/vmlinuz-5.13.0-1023-azure.dpkg-new': Operation not permitted
Preparing to unpack .../linux-image-5.13.0-1025-azure_5.13.0-1025.29~20.04.1_amd64.deb ...
Unpacking linux-image-5.13.0-1025-azure (5.13.0-1025.29~20.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-5.13.0-1025-azure_5.13.0-1025.29~20.04.1_amd64.deb (--unpack):
 unable to open '/boot/vmlinuz-5.13.0-1025-azure.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-5.13.0-1028-azure_5.13.0-1028.33~20.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-5.13.0-1023-azure_5.13.0-1023.27~20.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-5.13.0-1025-azure_5.13.0-1025.29~20.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I dont know about the kernel, what do you do recommend in this case, i probed any command, by example: apt install -f , apt autoremove, etc.. and all show the same error

Thanks

---

### Post by GhX6GZMB on 2022-06-08
Seems the "azure" repository has a problem. Try switching to a different server.

---

### Post by gale85 on 2022-06-08
sudo dpkg --configure -a

---

### Post by elforescanvia on 2022-06-08
thanks by repply, I to change the repository in source.list and it the same error in the screen getting the same error

```

root@cenazosaesaweb:~# cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ focal main restricted
deb http://archive.ubuntu.com/ubuntu/ focal-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ focal universe
deb http://archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://archive.ubuntu.com/ubuntu/ focal multiverse
deb http://archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

```

```

root@localhost:/etc/apt# apt install --fix-broken
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfwupdplugin1 linux-azure-5.13-cloud-tools-5.13.0-1023 linux-azure-5.13-cloud-tools-5.13.0-1025 linux-azure-5.13-headers-5.13.0-1023 linux-azure-5.13-headers-5.13.0-1025 linux-azure-5.13-tools-5.13.0-1023
  linux-azure-5.13-tools-5.13.0-1025 linux-cloud-tools-5.13.0-1023-azure linux-cloud-tools-5.13.0-1025-azure linux-headers-5.13.0-1023-azure linux-headers-5.13.0-1025-azure linux-image-5.13.0-1023-azure linux-image-5.13.0-1025-azure
  linux-modules-5.13.0-1023-azure linux-modules-5.13.0-1025-azure linux-tools-5.13.0-1023-azure linux-tools-5.13.0-1025-azure
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-5.13.0-1023-azure linux-image-5.13.0-1025-azure linux-image-5.13.0-1028-azure
Suggested packages:
  fdutils linux-azure-5.13-doc-5.13.0 | linux-azure-5.13-source-5.13.0 linux-azure-5.13-tools
The following NEW packages will be installed:
  linux-image-5.13.0-1023-azure linux-image-5.13.0-1025-azure linux-image-5.13.0-1028-azure
0 upgraded, 3 newly installed, 0 to remove and 58 not upgraded.
14 not fully installed or removed.
Need to get 28.4 MB of archives.
After this operation, 28.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.13.0-1028-azure amd64 5.13.0-1028.33~20.04.1 [9485 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.13.0-1023-azure amd64 5.13.0-1023.27~20.04.1 [9473 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.13.0-1025-azure amd64 5.13.0-1025.29~20.04.1 [9485 kB]
Fetched 28.4 MB in 1s (38.1 MB/s)
dpkg: warning: files list file for package 'linux-modules-5.13.0-1014-azure' missing; assuming package has no files currently installed
(Reading database ... 278034 files and directories currently installed.)
Preparing to unpack .../linux-image-5.13.0-1028-azure_5.13.0-1028.33~20.04.1_amd64.deb ...
Unpacking linux-image-5.13.0-1028-azure (5.13.0-1028.33~20.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-5.13.0-1028-azure_5.13.0-1028.33~20.04.1_amd64.deb (--unpack):
 unable to open '/boot/vmlinuz-5.13.0-1028-azure.dpkg-new': Operation not permitted
Preparing to unpack .../linux-image-5.13.0-1023-azure_5.13.0-1023.27~20.04.1_amd64.deb ...
Unpacking linux-image-5.13.0-1023-azure (5.13.0-1023.27~20.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-5.13.0-1023-azure_5.13.0-1023.27~20.04.1_amd64.deb (--unpack):
 unable to open '/boot/vmlinuz-5.13.0-1023-azure.dpkg-new': Operation not permitted
Preparing to unpack .../linux-image-5.13.0-1025-azure_5.13.0-1025.29~20.04.1_amd64.deb ...
Unpacking linux-image-5.13.0-1025-azure (5.13.0-1025.29~20.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-5.13.0-1025-azure_5.13.0-1025.29~20.04.1_amd64.deb (--unpack):
 unable to open '/boot/vmlinuz-5.13.0-1025-azure.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-5.13.0-1028-azure_5.13.0-1028.33~20.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-5.13.0-1023-azure_5.13.0-1023.27~20.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-5.13.0-1025-azure_5.13.0-1025.29~20.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

what other solution could i try

---

### Post by elforescanvia on 2022-06-08
I execute dpkg-configure -a and show it error in the makelog file, any idea?

```
DKMS make.log for microsoft-dependency-agent-9.10.14 for kernel 5.13.0-1028-azure (x86_64)Wed Jun  8 17:15:31 -05 2022
make: Entering directory '/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux'
make -C /lib/modules/5.13.0-1028-azure/build M=/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux modules
make[1]: Entering directory '/usr/src/linux-headers-5.13.0-1028-azure'
  CC [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bs_trampolines.o
  CC [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bs_hooks.o
  CC [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bs_driver.o
  CC [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/sock_context.o
/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bs_driver.c:158:6: error: ‘struct file_operations’ has no member named ‘ioctl’
  158 |     .ioctl = bs_old_ioctl,
      |      ^~~~~
/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bs_driver.c:158:14: error: positional initialization of field in ‘struct’ declared with ‘designated_init’ attribute [-Werror=designated-init]
  158 |     .ioctl = bs_old_ioctl,
      |              ^~~~~~~~~~~~
/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bs_driver.c:158:14: note: (near initialization for ‘bs_fops’)
/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bs_driver.c:158:14: error: initialization of ‘long unsigned int’ from ‘int (*)(struct inode *, struct file *, unsigned int,  long unsigned int)’ makes integer from pointer without a cast [-Werror=int-conversion]
/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bs_driver.c:158:14: note: (near initialization for ‘bs_fops.mmap_supported_flags’)
cc1: all warnings being treated as errors
make[2]: *** [scripts/Makefile.build:281: /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bs_driver.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [Makefile:1879: /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.13.0-1028-azure'
make: *** [Makefile:40: default] Error 2
make: Leaving directory '/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux'
make: Entering directory '/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel'
make -C /lib/modules/5.13.0-1028-azure/build M=/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel modules
make[1]: Entering directory '/usr/src/linux-headers-5.13.0-1028-azure'
  CC [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/bs_eventchannel.o
  CC [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/../linux_oscompat.o
  CC [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/../../common/bluechannel.o
  CC [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/../../common/hash.o
  LD [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/bluechannel.o
  MODPOST /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/Module.symvers
  CC [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/bluechannel.mod.o
  LD [M]  /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/bluechannel.ko
  BTF [M] /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/bluechannel.ko
Skipping BTF generation for /var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel/bluechannel.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-5.13.0-1028-azure'
sync


*** Microsoft Dependency Agent bluechannel driver build successful. ***


make: Leaving directory '/var/lib/dkms/microsoft-dependency-agent/9.10.14/build/src/linux/bluechannel'

```

---

### Post by ActionParsnip on 2022-06-09
Have you logged a support ticket with Microsoft for this as well.

---

### Post by gale85 on 2022-06-09
Try this [https://www.tecmint.com/sub-process-usr-bin-dpkg-returned-an-error-in-ubuntu/](https://www.tecmint.com/sub-process-usr-bin-dpkg-returned-an-error-in-ubuntu/)

---

