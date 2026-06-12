---
title: "Issue after upgrading to 17.10 and Kernel -- Output included"
date: 2017-12-09
forum: Installation &amp; Upgrades
---

### Post by shikhirarora on 2017-12-09
I am having some issues after upgrading to 17.10 -- something is wrong and I've tried everything to fix it, but to no avail. When rebooting, it does not boot all the disk paritions properly and only after doing the mount all command do they all show up. But, the real issues are with apt. I cannot use it to any functional value..which is a problem.

And I cannot get the kernel to update, even though I installed 4.15. It does not work as it should, still showing 4.14 after reboot on output of uname -a.

If someone has any insight, I've tried the following:
```

vlexar@node1:~$ sudo dpkg --configure -a
Setting up keyboard-configuration (1.166ubuntu7) ...
/usr/local/bin/setupcon: line 899: /usr/local/bin/ckbcomp: No such file or directory
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up systemd (234-2ubuntu12.1) ...
systemd-machine-id-setup: error while loading shared libraries: libsystemd-shared-232.so: cannot open shared object file: No such file or directory
dpkg: error processing package systemd (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of console-setup-linux:
 console-setup-linux depends on keyboard-configuration (= 1.166ubuntu7); however:
  Package keyboard-configuration is not configured yet.


dpkg: error processing package console-setup-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on console-setup-linux | console-setup-freebsd | hurd; however:
  Package console-setup-linux is not configured yet.
  Package console-setup-freebsd is not installed.
  Package hurd is not installed.
 console-setup depends on keyboard-configuration (= 1.166ubuntu7); however:
  Package keyboard-configuration is not configured yet.


dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd (= 234-2ubuntu12.1); however:
  Package systemd is not configured yet.


dpkg: error processing package libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 keyboard-configuration
 systemd
 console-setup-linux
 console-setup
 libpam-systemd:amd64

```




[B]The issue with apt lies here:
[/B]```

vlexar@node1:~$ sudo apt-get clean && sudo apt-get autoremove && cd /varlib/apt && sudo mv list list.old && sudo mkdir -p list/partial && sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.10.0-40-generic linux-image-extra-4.10.0-40-generic
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
7 not fully installed or removed.
After this operation, 226 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 293952 files and directories currently installed.)
Removing linux-image-extra-4.10.0-40-generic (4.10.0-40.44) ...
depmod: FATAL: could not load /boot/System.map-4.10.0-40-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-40-generic /boot/vmlinuz-4.10.0-40-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-40-generic /boot/vmlinuz-4.10.0-40-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-40-generic
WARNING: missing /lib/modules/4.10.0-40-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.10.0-40-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_tbfZzV/lib/modules/4.10.0-40-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_tbfZzV/lib/modules/4.10.0-40-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-40-generic /boot/vmlinuz-4.10.0-40-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.10.0-40-generic /boot/vmlinuz-4.10.0-40-generic
Generating grub configuration file ...
grub-probe: error: disk `md2' not found.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-extra-4.10.0-40-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.10.0-40-generic (4.10.0-40.44) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.10.0-40-generic /boot/vmlinuz-4.10.0-40-generic
update-initramfs: Deleting /boot/initrd.img-4.10.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.10.0-40-generic /boot/vmlinuz-4.10.0-40-generic
Generating grub configuration file ...
grub-probe: error: disk `md2' not found.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.10.0-40-generic.postrm line 330.
dpkg: error processing package linux-image-4.10.0-40-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.10.0-40-generic
 linux-image-4.10.0-40-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**Similarly**: 

```

vlexar@node1:~$ sudo aptitude update && sudo aptitude upgrade
Hit http://us.archive.ubuntu.com/ubuntu artful InRelease
Get: 1 http://us.archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]                               
Get: 2 http://us.archive.ubuntu.com/ubuntu artful-backports InRelease [72.2 kB]                                                                                        
Get: 3 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]                             
Hit http://archive.canonical.com/ubuntu artful InRelease                              
Fetched 229 kB in 0s (565 kB/s)                                 
                                         
Resolving dependencies...                
The following partially installed packages will be configured:
  console-setup console-setup-linux keyboard-configuration libpam-systemd systemd 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
E: Can't find a source to download version '4.10.0-40.44' of 'linux-image-4.10.0-40-generic:amd64'
After unpacking 0 B will be used.
E: Can't find a source to download version '4.10.0-40.44' of 'linux-image-4.10.0-40-generic:amd64'
E: Internal error: couldn't generate list of packages to download
E: Perhaps the package lists are out of date, please try 'aptitude update' (or equivalent) first

```

```

vlexar@node1:~$ dpkg -l | grep linux-image
rc  linux-image-4.10.0-20-generic                      4.10.0-20.22                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-21-generic                      4.10.0-21.23                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-22-generic                      4.10.0-22.24                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-24-generic                      4.10.0-24.28                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-26-generic                      4.10.0-26.30                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-28-generic                      4.10.0-28.32                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-32-generic                      4.10.0-32.36                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-33-generic                      4.10.0-33.37                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-35-generic                      4.10.0-35.39                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-37-generic                      4.10.0-37.41                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-38-generic                      4.10.0-38.42                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
iH  linux-image-4.10.0-40-generic                      4.10.0-40.44                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.12.0-041200-generic                  4.12.0-041200.201707022031               amd64        Linux kernel image for version 4.12.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-19-generic                      4.13.0-19.22                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.14.0-999-generic                     4.14.0-999.201711012202                  amd64        Linux kernel image for version 4.14.0 on 64 bit x86 SMP
ii  linux-image-4.14.4-041404-generic                  4.14.4-041404.201712050630               amd64        Linux kernel image for version 4.14.4 on 64 bit x86 SMP
ii  linux-image-4.15.0-041500rc2-generic               4.15.0-041500rc2.201712031230            amd64        Linux kernel image for version 4.15.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-20-generic                4.10.0-20.22                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-21-generic                4.10.0-21.23                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-22-generic                4.10.0-22.24                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-24-generic                4.10.0-24.28                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-26-generic                4.10.0-26.30                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-28-generic                4.10.0-28.32                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ic  linux-image-extra-4.10.0-32-generic                4.10.0-32.36                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-33-generic                4.10.0-33.37                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-35-generic                4.10.0-35.39                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-37-generic                4.10.0-37.41                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-38-generic                4.10.0-38.42                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
pH  linux-image-extra-4.10.0-40-generic                4.10.0-40.44                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-19-generic                4.13.0-19.22                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                4.13.0.19.20                             amd64        Generic Linux kernel image

```
```

vlexar@node1:~$ strace -v -e uname uname -v
uname({sysname="Linux", nodename="node1.execsrvr.xyz", release="4.14.0-999-generic", version="#201711012202 SMP Thu Nov 2 02:04:36 UTC 2017", machine="x86_64", domainname="(none)"}) = 0
#201711012202 SMP Thu Nov 2 02:04:36 UTC 2017
+++ exited with 0 +++
vlexar@node1:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
Generating grub configuration file ...
grub-probe: error: disk `md2' not found.


```

```

vlexar@node1:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
tmpfs           3.2G   14M  3.1G   1% /run
/dev/md3        393G  120G  253G  33% /
tmpfs            16G  8.0K   16G   1% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
/dev/md2         20G  159M   18G   1% /boot
/dev/nvme0n1p1  510M  156K  510M   1% /boot/efi

```

---

