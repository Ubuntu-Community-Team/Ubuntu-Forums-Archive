---
title: "the cache has no package named 'linux-modules-extra-5.4.0-139-generic:amd64"
date: 2023-02-15
forum: Installation &amp; Upgrades
---

### Post by embcen on 2023-02-15
Hello,

I am on a Ubuntu 18.04 LTS machine.
I have never had any system issue so far, but yesterday I received the following warning:

'Unknown error: '<class 'KeyError'>' (the cache has no package named 'linux-modules-extra-5.4.0-139-generic:amd64')'

I suppose Ubuntu tried to launch software updater and failed somewhere.
i launched it myself and it warned me that some software couldn't be checked for updates.
In the list of unused kernel updates to be removed there are the following entries:

Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
Signed kernel image generic

How can I solve this problem? Is it worrying?

---

### Post by MAFoElffen on 2023-02-18
Strange. Is in Focal (20.04): [https://packages.ubuntu.com/focal/linux-image-generic](https://packages.ubuntu.com/focal/linux-image-generic)

What is the output of 
```

apt-cache show linux-modules-extra-5.4.0-139-generic

```

---

### Post by embcen on 2023-02-19
Hi MAFoElffen, thanks for your reply.
Below is the output of the code you suggested:

```
$ apt-cache show linux-modules-extra-5.4.0-139-generic
Package: linux-modules-extra-5.4.0-139-generic
Architecture: amd64
Version: 5.4.0-139.156~18.04.1
Priority: optional
Section: kernel
Source: linux-hwe-5.4
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 190524
Depends: linux-image-5.4.0-139-generic | linux-image-unsigned-5.4.0-139-generic, crda | wireless-crda
Filename: pool/main/l/linux-hwe-5.4/linux-modules-extra-5.4.0-139-generic_5.4.0-139.156~18.04.1_amd64.deb
Size: 38645640
MD5sum: 5fbfb66bab2d4c5e1c686e6d7afa9561
SHA1: 686126ce25c0ce4b9834964e660def4ee3a5cde9
SHA256: abc933ad898b1e1723eb4ea64eab0abd2616b50fa8884e054995c60e865f9959
SHA512: 4e12f2389622abb1ca8443f359a132789fc8ecc34309a73303905ca979f6018aa94fa417029d28d2ec3dea2344839f9aa6c759b7bda18e3068d2805d997c5962
Description-en: Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
 This package contains the Linux kernel extra modules for version 5.4.0 on
 64 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.
Description-md5: bad067be2bd404cd3e219540aa5e7fbf
Supported: 5y


```

---

### Post by MAFoElffen on 2023-02-19
It says it's there... can you
```
 
sudo apt update
sudo apt upgrade

```
...without error?

---

### Post by embcen on 2023-02-19
I did not see any error:

```
$ sudo apt update
[sudo] password for marco: 
Hit:1 http://it.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 https://deb.opera.com/opera-stable stable InRelease                                                                                            
Get:3 http://it.archive.ubuntu.com/ubuntu bionic-updates InRelease [88,7 kB]                                                                         
Hit:5 http://ppa.launchpad.net/rael-gc/rvm/ubuntu bionic InRelease                                                                                   
Hit:6 https://packages.microsoft.com/repos/vscode stable InRelease                                                                            
Get:7 http://it.archive.ubuntu.com/ubuntu bionic-backports InRelease [83,3 kB]                                                                       
Get:8 http://security.ubuntu.com/ubuntu bionic-security InRelease [88,7 kB]                                                                          
Get:4 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic InRelease [15,4 kB]                                                             
Get:9 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [2.901 kB]                                                           
Get:10 http://it.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [1.608 kB]                      
Get:11 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [297 kB]               
Get:12 http://it.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [302 kB]                  
Get:13 http://it.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2.464 B]               
Get:15 http://it.archive.ubuntu.com/ubuntu bionic-backports/main amd64 DEP-11 Metadata [8.120 B]
Get:16 http://it.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [10,0 kB]                                         
E: Repository 'http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic InRelease' changed its 'Label' value from 'gimp' to 'gimp stable'      
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
Do you want to accept these changes and continue updating from this repository? [y/N] y
Hit:14 https://packagecloud.io/AtomEditor/atom/any any InRelease                                                                                     
Get:17 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic/main amd64 Packages [10,2 kB]                                                  
Get:18 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic/main i386 Packages [10,2 kB]                                                   
Get:19 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [76,9 kB]                                                        
Get:20 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic/main Translation-en [5.944 B]                                                  
Get:21 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [61,1 kB]                                                    
Get:22 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2.464 B]                                                  
Fetched 5.572 kB in 15s (370 kB/s)                                                                                                                   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
11 packages can be upgraded. Run 'apt list --upgradable' to see them.

$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gconf-service gconf-service-backend gconf2 gconf2-common gyp libde265-0 libgconf-2-4 libgegl-0.3-0 libheif1 libjs-async libjs-inherits
  libjs-node-uuid libllvm7 libllvm8 libllvm9 libuv1-dev linux-hwe-5.4-headers-5.4.0-100 linux-hwe-5.4-headers-5.4.0-104
  linux-hwe-5.4-headers-5.4.0-105 linux-hwe-5.4-headers-5.4.0-107 linux-hwe-5.4-headers-5.4.0-109 linux-hwe-5.4-headers-5.4.0-110
  linux-hwe-5.4-headers-5.4.0-113 linux-hwe-5.4-headers-5.4.0-117 linux-hwe-5.4-headers-5.4.0-120 linux-hwe-5.4-headers-5.4.0-121
  linux-hwe-5.4-headers-5.4.0-122 linux-hwe-5.4-headers-5.4.0-124 linux-hwe-5.4-headers-5.4.0-125 linux-hwe-5.4-headers-5.4.0-126
  linux-hwe-5.4-headers-5.4.0-128 linux-hwe-5.4-headers-5.4.0-131 linux-hwe-5.4-headers-5.4.0-132 linux-hwe-5.4-headers-5.4.0-135
  linux-hwe-5.4-headers-5.4.0-136 linux-hwe-5.4-headers-5.4.0-42 linux-hwe-5.4-headers-5.4.0-45 linux-hwe-5.4-headers-5.4.0-47
  linux-hwe-5.4-headers-5.4.0-48 linux-hwe-5.4-headers-5.4.0-51 linux-hwe-5.4-headers-5.4.0-52 linux-hwe-5.4-headers-5.4.0-53
  linux-hwe-5.4-headers-5.4.0-54 linux-hwe-5.4-headers-5.4.0-56 linux-hwe-5.4-headers-5.4.0-58 linux-hwe-5.4-headers-5.4.0-59
  linux-hwe-5.4-headers-5.4.0-60 linux-hwe-5.4-headers-5.4.0-62 linux-hwe-5.4-headers-5.4.0-64 linux-hwe-5.4-headers-5.4.0-65
  linux-hwe-5.4-headers-5.4.0-66 linux-hwe-5.4-headers-5.4.0-67 linux-hwe-5.4-headers-5.4.0-70 linux-hwe-5.4-headers-5.4.0-71
  linux-hwe-5.4-headers-5.4.0-72 linux-hwe-5.4-headers-5.4.0-73 linux-hwe-5.4-headers-5.4.0-74 linux-hwe-5.4-headers-5.4.0-77
  linux-hwe-5.4-headers-5.4.0-80 linux-hwe-5.4-headers-5.4.0-81 linux-hwe-5.4-headers-5.4.0-84 linux-hwe-5.4-headers-5.4.0-86
  linux-hwe-5.4-headers-5.4.0-87 linux-hwe-5.4-headers-5.4.0-89 linux-hwe-5.4-headers-5.4.0-90 linux-hwe-5.4-headers-5.4.0-91
  linux-hwe-5.4-headers-5.4.0-92 linux-hwe-5.4-headers-5.4.0-94 linux-hwe-5.4-headers-5.4.0-96 linux-hwe-5.4-headers-5.4.0-97
  linux-hwe-5.4-headers-5.4.0-99 node-abbrev node-ansi node-ansi-color-table node-archy node-async node-balanced-match node-block-stream
  node-brace-expansion node-combined-stream node-concat-map node-cookie-jar node-delayed-stream node-forever-agent node-form-data node-fs.realpath
  node-fstream node-fstream-ignore node-github-url-from-git node-glob node-graceful-fs node-hosted-git-info node-inflight node-inherits node-ini
  node-isexe node-json-stringify-safe node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp node-mute-stream node-node-uuid node-nopt
  node-npmlog node-once node-osenv node-path-is-absolute node-pseudomap node-qs node-read node-request node-retry node-rimraf node-semver node-sha
  node-slide node-spdx-correct node-spdx-expression-parse node-spdx-license-ids node-tar node-tunnel-agent node-underscore
  node-validate-npm-package-license node-which node-wrappy node-yallist python-cairo python-gobject-2 python-gtk2 python3-msgpack shim
Use 'sudo apt autoremove' to remove them.
The following security updates require Ubuntu Pro with 'esm-apps' enabled:
  libopenjp2-7 node-hosted-git-info libgegl-0.3-0 libzmq5 libopenmpt0 nodejs
  redis-tools libsdl2-2.0-0 libmysofa0 nodejs-doc redis-server
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages will be upgraded:
  code gimp gimp-data grub-efi-amd64-bin grub-efi-amd64-signed libbabl-0.1-0 libgegl-0.4-0 libgegl-common libgimp2.0 ubuntu-advantage-tools
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 122 MB of archives.
After this operation, 6.741 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic/main amd64 libbabl-0.1-0 amd64 0.1.72+om-0ubu18.04.7.11~ppa [328 kB]
Get:2 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 ubuntu-advantage-tools amd64 27.13.5~18.04.1 [172 kB]
Get:3 https://packages.microsoft.com/repos/vscode stable/main amd64 code amd64 1.75.1-1675893397 [98,2 MB]                               
Get:4 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 grub-efi-amd64-signed amd64 1.187.3~18.04.1+2.06-2ubuntu14.1 [1.343 kB]
Get:5 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic/main amd64 libgegl-common all 1:0.4.18+om-0ubu18.04.18~ppa [612 kB]
Get:6 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 grub-efi-amd64-bin amd64 2.06-2ubuntu14.1 [1.591 kB]       
Get:7 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic/main amd64 libgegl-0.4-0 amd64 1:0.4.18+om-0ubu18.04.18~ppa [928 kB]
Get:8 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic/main amd64 gimp amd64 2.10.14+om-1ubu18.04.7~ppa [4.222 kB]
Get:9 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic/main amd64 libgimp2.0 amd64 2.10.14+om-1ubu18.04.7~ppa [808 kB]
Get:10 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic/main amd64 gimp-data all 2.10.14+om-1ubu18.04.7~ppa [13,9 MB]
Fetched 122 MB in 8s (15,1 MB/s)                                                                                                                     
Preconfiguring packages ...
(Reading database ... 1221899 files and directories currently installed.)
Preparing to unpack .../0-ubuntu-advantage-tools_27.13.5~18.04.1_amd64.deb ...
Unpacking ubuntu-advantage-tools (27.13.5~18.04.1) over (27.13.3~18.04.1) ...
Preparing to unpack .../1-code_1.75.1-1675893397_amd64.deb ...
Unpacking code (1.75.1-1675893397) over (1.75.0-1675266613) ...
Preparing to unpack .../2-libbabl-0.1-0_0.1.72+om-0ubu18.04.7.11~ppa_amd64.deb ...
Unpacking libbabl-0.1-0:amd64 (0.1.72+om-0ubu18.04.7.11~ppa) over (0.1.66+om-0ubu18.04.1~ppa) ...
Preparing to unpack .../3-libgegl-common_1%3a0.4.18+om-0ubu18.04.18~ppa_all.deb ...
Unpacking libgegl-common (1:0.4.18+om-0ubu18.04.18~ppa) over (1:0.4.16+om-0ubu18.04.9~ppa) ...
Preparing to unpack .../4-libgegl-0.4-0_1%3a0.4.18+om-0ubu18.04.18~ppa_amd64.deb ...
Unpacking libgegl-0.4-0:amd64 (1:0.4.18+om-0ubu18.04.18~ppa) over (1:0.4.16+om-0ubu18.04.9~ppa) ...
Preparing to unpack .../5-gimp_2.10.14+om-1ubu18.04.7~ppa_amd64.deb ...
Unpacking gimp (2.10.14+om-1ubu18.04.7~ppa) over (2.10.12+om-1ubu18.04.1~ppa) ...
Preparing to unpack .../6-libgimp2.0_2.10.14+om-1ubu18.04.7~ppa_amd64.deb ...
Unpacking libgimp2.0 (2.10.14+om-1ubu18.04.7~ppa) over (2.10.12+om-1ubu18.04.1~ppa) ...
Preparing to unpack .../7-gimp-data_2.10.14+om-1ubu18.04.7~ppa_all.deb ...
Unpacking gimp-data (2.10.14+om-1ubu18.04.7~ppa) over (2.10.12+om-1ubu18.04.1~ppa) ...
Preparing to unpack .../8-grub-efi-amd64-signed_1.187.3~18.04.1+2.06-2ubuntu14.1_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.187.3~18.04.1+2.06-2ubuntu14.1) over (1.173.2~18.04.1+2.04-1ubuntu47.4) ...
Preparing to unpack .../9-grub-efi-amd64-bin_2.06-2ubuntu14.1_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.06-2ubuntu14.1) over (2.04-1ubuntu47.4) ...
Setting up ubuntu-advantage-tools (27.13.5~18.04.1) ...
Setting up grub-efi-amd64-bin (2.06-2ubuntu14.1) ...
Setting up libbabl-0.1-0:amd64 (0.1.72+om-0ubu18.04.7.11~ppa) ...
Setting up gimp-data (2.10.14+om-1ubu18.04.7~ppa) ...
Installing new version of config file /etc/gimp/2.0/gimprc ...
Setting up grub-efi-amd64-signed (1.187.3~18.04.1+2.06-2ubuntu14.1) ...
Installing for x86_64-efi platform.
Installation finished. No error reported.
Setting up libgegl-common (1:0.4.18+om-0ubu18.04.18~ppa) ...
Setting up libgegl-0.4-0:amd64 (1:0.4.18+om-0ubu18.04.18~ppa) ...
Setting up code (1.75.1-1675893397) ...
Setting up libgimp2.0 (2.10.14+om-1ubu18.04.7~ppa) ...
Setting up gimp (2.10.14+om-1ubu18.04.7~ppa) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for shared-mime-info (1.9-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1.6) ...

```

---

### Post by MAFoElffen on 2023-02-19
Yes. You seem to be fine.

Somethings, when the repo's are 'in the midst' of getting updated, things get confused. It all seems to sort itself out over time.

---

### Post by ActionParsnip on 2023-02-20
Bionic has a matter of weeks support left. You may want to use this as the catalyst to wipe the install off and do a clean install of Jammy. You can restore your user data from your backups

---

