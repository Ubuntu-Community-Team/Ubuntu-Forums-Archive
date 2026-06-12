---
title: "Partial upgrade running Ubuntu 22.04.2 LTS"
date: 2023-03-24
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2023-03-24
I would liketo know how I can best get my system cleaned up.
First I got this message:
 	 		 			 			 				**Not all updates can be installed**
> Run a partial upgradeto install as many as updates as possible
This can be caused by ... 			 		

 	
 
I tried clicked on Partial Upgrade.  Below are the errors which  came up  during the process, then following are some commands I tried  all of  which returned errors:
installed linux-image-5.4.0-124-generic package post-removal script subprocess returned error exit status 1

installed grub-pc package post-installation script subprocess returned error exit status 127

installed linux-image-5.15.0-67-generic package post-installation script subprocess returned error exit status 1

The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

It is impossible to install or remove any software. Please use the   package manager "Synaptic" or run "sudo apt-get install -f" in a   terminal to fix this issue at first.


reuven@reuven-OptiPlex-9020:~$ sudo apt-get install -f
[sudo] password for reuven: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflashrom1 libftdi1-2 libllvm13 libllvm13:i386
  linux-image-5.4.0-125-generic linux-modules-5.4.0-125-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-5.4.0-124-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 13.7 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 260683 files and directories currently installed.)
Removing linux-image-5.4.0-124-generic (5.4.0-124.140) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-124-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
Found background image: /home/reuven/CityOnTheEdgeOfForever.jpeg
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries:   libcrypto.so.1.1: cannot open shared object file: No such file or   directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.4.0-124-generic (--remove):
 installed linux-image-5.4.0-124-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.4.0-124-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
reuven@reuven-OptiPlex-9020:~$ 

reuven@reuven-OptiPlex-9020:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflashrom1 libftdi1-2 libllvm13 libllvm13:i386
  linux-image-5.4.0-125-generic linux-modules-5.4.0-125-generic
Use 'euven@reuven-OptiPlex-9020:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflashrom1 libftdi1-2 libllvm13 libllvm13:i386
  linux-image-5.4.0-125-generic linux-modules-5.4.0-125-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-5.4.0-124-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 13.7 MB disk space will be freed.
Do you want to continue? [Y/n] y
' to remove them.
The following packages will be REMOVED:
  linux-image-5.4.0-124-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 13.7 MB disk space will be freed.
Do you want to continue? [Y/n] y

reuven@reuven-OptiPlex-9020:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  libflashrom1 libftdi1-2 libllvm13 libllvm13:i386
  linux-image-5.4.0-124-generic linux-image-5.4.0-125-generic
  linux-modules-5.4.0-125-generic
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 301 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 260683 files and directories currently installed.)
Removing linux-image-5.4.0-124-generic (5.4.0-124.140) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-124-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
Found background image: /home/reuven/CityOnTheEdgeOfForever.jpeg
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.s
o.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.4.0-124-generic (--remove):
 installed linux-image-5.4.0-124-generic package post-removal script subprocess 
returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.4.0-124-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ActionParsnip on 2023-03-24
Look online for the error:
```

/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory

```

---

### Post by MAFoElffen on 2023-03-24
I did (googled), and found that that problem can be corrected by manually downloading the package from Debian and installing it with dpkg
```

wget -N -t 5 -T 10 http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.1_1.1.0l-1~deb9u6_amd64.deb
sudo dpkg -i ./libssl1.1_1.1.0l-1~deb9u6_amd64.deb

```
Which will reinstalls symlink libcrypto.so.1.1...

RE: [https://askubuntu.com/questions/1403778/upgrading-to-ubuntu-22-04-causes-libcrypto-errors-apt-dpkg-broken](https://askubuntu.com/questions/1403778/upgrading-to-ubuntu-22-04-causes-libcrypto-errors-apt-dpkg-broken)

Which I think that is the upstream package for 'libssl3'...

---

