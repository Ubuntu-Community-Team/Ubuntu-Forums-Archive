---
title: "Boot disk full during upgrade and not able to run apt-get autoremove to free up space"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by Peter_Sotos on 2016-07-29
Hello All!

I've tried upgrading to the latest version of Ubuntu but I am having issues. First off I have a full boot partition:

Filesystem                    1K-blocks    Used Available Use% Mounted on
udev                            1899728       0   1899728   0% /dev
tmpfs                            383540    5768    377772   2% /run
/dev/mapper/<myserver>--vg-root 236067592 3456340 220596660   2% /
tmpfs                           1917688       4   1917684   1% /dev/shm
tmpfs                              5120       0      5120   0% /run/lock
tmpfs                           1917688       0   1917688   0% /sys/fs/cgroup
/dev/sda1                        240972  229907         0 100% /boot
/dev/sdb1                     961302560   73496 951461452   1% /media/hdd
tmpfs                            383540       0    383540   0% /run/user/1000

Secondly, when I try and run apt-get autoremove it fails:


sudo apt-get autoremove
[sudo] password for xxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-31-generic : Depends: linux-image-4.4.0-31-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-31-generic but it is not installed
                       Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.

Any help is appreciated! :/

---

### Post by kyrithis on 2016-07-29
You're missing dependencies. Run "sudo apt-get -f install" in terminal, and it'll automatically get what you need and finish the autoremove.

---

### Post by Peter_Sotos on 2016-07-30
I've tried that but it fails:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic linux-headers-4.4.0-22 linux-headers-4.4.0-22-generic
  linux-image-4.2.0-35-generic linux-image-4.4.0-21-generic linux-image-4.4.0-22-generic linux-image-extra-4.2.0-35-generic
  linux-image-extra-4.4.0-21-generic linux-image-extra-4.4.0-22-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-31-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-31-generic
0 upgraded, 1 newly installed, 0 to remove and 69 not upgraded.
7 not fully installed or removed.
Need to get 0 B/18.7 MB of archives.
After this operation, 55.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 200413 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-31-generic_4.4.0-31.50_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-31-generic (4.4.0-31.50) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-31-generic_4.4.0-31.50_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-31-generic' to '/boot/vmlinuz-4.4.0-31-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-31-generic_4.4.0-31.50_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've also tried running apt-get autoremove but it fails as well:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-31-generic : Depends: linux-image-4.4.0-31-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-31-generic but it is not installed
                       Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.
```

---

### Post by grahammechanical on 2016-07-30
You are in the situation where the system is trying to install a new kernel but cannot because the boot partition is full and so the operation is not completed. Every time you run apt-get it tries to complete the operation. It is a kind of loop.

At the Grub boot menu we can select Advanced options for Ubuntu and then select a kernel with recovery mode. At the recovery menu select Clean - try to make free space that will run both the clean and autoremove commands.

Running autoremove from recovery mode might be more effective than running it after Linux and Ubuntu are fully loaded. With versions of Ubuntu before 16.04 the autoremove command will only remove one kernel each time it is run. But from 16.04 onwards the autoremove command will remove all kernels but the latest two kernels.

Anyone with a separate boot partition should run autoremove from time to time to avoid this situation which may happen when the OS gets an updated kernel as it does sometimes quiet often. To upgrade from one version of Ubuntu to another we need first to update the existing version and that may mean newer kernels.

Regards.

---

### Post by Peter_Sotos on 2016-08-10
When I try and run the grub menu, anytime I hit any arrow keys to select advanced options, it just starts booting.

---

### Post by Peter_Sotos on 2016-08-11
I solved this! What I needed to do was to go in and delete the oldest kernels from /boot by using the rm command. I cleared up just enough space so that I wasnt at 100% and then used the normal dpkg --purge command for the rest. I resolved this on all my linux servers. :) They are all now at 50% or less of the /boot drive space. Thanks for the help all!

---

