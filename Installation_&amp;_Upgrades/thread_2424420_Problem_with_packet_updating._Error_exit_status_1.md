---
title: "Problem with packet updating. Error exit status 1"
date: 2019-08-08
forum: Installation &amp; Upgrades
---

### Post by blurred82 on 2019-08-08
Hi All,
I've got 18.04.3 on VMware EXI 6.0
Some time ago I had a disk problem which ended by fixing with fdisk tool.
After that I had some communicate that few *.list files are broken so I have deleted them from /var/lib/dpkg/info

This ends up with this communicate:
```
nawrocki@ubuntu:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode intel-microcode iucode-tool
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-4.15.0-55-generic
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
2 not fully installed or removed.
After this operation, 8,324 kB disk space will be freed.
Do you want to continue? [Y/n] Y
**dpkg: warning: files list file for package 'libpolkit-agent-1-0:amd64' missing; assuming package has no files currently installed**
**dpkg: warning: files list file for package 'policykit-1' missing; assuming package has no files currently installed**
**dpkg: warning: files list file for package 'java-common' missing; assuming package has no files currently installed**
**dpkg: warning: files list file for package 'gettext-base' missing; assuming package has no files currently installed**
**dpkg: warning: files list file for package 'libpolkit-backend-1-0:amd64' missing; assuming package has no files currently installed**
**dpkg: warning: files list file for package 'libdns-export1100' missing; assuming package has no files currently installed**
**dpkg: warning: files list file for package 'libpolkit-gobject-1-0:amd64' missing; assuming package has no files currently installed**
(Reading database ... 171570 files and directories currently installed.)
Removing linux-image-4.15.0-55-generic (4.15.0-55.60) ...

```

But finally I cant do anything with apt, because I get this communicate while trying to update my system:
```
nawrocki@ubuntu:/var/lib/apt/lists$ sudo apt upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode intel-microcode iucode-tool
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  libnss-systemd libpam-systemd libsystemd0 libudev1 systemd systemd-sysv udev
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/12.4 MB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
dpkg: warning: files list file for package 'libpolkit-agent-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'policykit-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'java-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gettext-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-backend-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdns-export1100' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-gobject-1-0:amd64' missing; assuming package has no files currently installed
(Reading database ... 171571 files and directories currently installed.)
Preparing to unpack .../libsystemd0_237-3ubuntu10.25_amd64.deb ...
Unpacking libsystemd0:amd64 (237-3ubuntu10.25) over (237-3ubuntu10.24) ...
Setting up libsystemd0:amd64 (237-3ubuntu10.25) ...
dpkg: warning: files list file for package 'libpolkit-agent-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'policykit-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'java-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gettext-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-backend-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdns-export1100' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-gobject-1-0:amd64' missing; assuming package has no files currently installed
(Reading database ... 171571 files and directories currently installed.)
Preparing to unpack .../libnss-systemd_237-3ubuntu10.25_amd64.deb ...
Unpacking libnss-systemd:amd64 (237-3ubuntu10.25) over (237-3ubuntu10.24) ...
Preparing to unpack .../libpam-systemd_237-3ubuntu10.25_amd64.deb ...
Unpacking libpam-systemd:amd64 (237-3ubuntu10.25) over (237-3ubuntu10.24) ...
Preparing to unpack .../systemd_237-3ubuntu10.25_amd64.deb ...
Unpacking systemd (237-3ubuntu10.25) over (237-3ubuntu10.24) ...
Preparing to unpack .../udev_237-3ubuntu10.25_amd64.deb ...
Unpacking udev (237-3ubuntu10.25) over (237-3ubuntu10.24) ...
Preparing to unpack .../libudev1_237-3ubuntu10.25_amd64.deb ...
Unpacking libudev1:amd64 (237-3ubuntu10.25) over (237-3ubuntu10.24) ...
Setting up libudev1:amd64 (237-3ubuntu10.25) ...
Setting up systemd (237-3ubuntu10.25) ...
dpkg: warning: files list file for package 'libpolkit-agent-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'policykit-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'java-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gettext-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-backend-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdns-export1100' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-gobject-1-0:amd64' missing; assuming package has no files currently installed
(Reading database ... 171571 files and directories currently installed.)
Preparing to unpack .../systemd-sysv_237-3ubuntu10.25_amd64.deb ...
Unpacking systemd-sysv (237-3ubuntu10.25) over (237-3ubuntu10.24) ...
Setting up libnss-systemd:amd64 (237-3ubuntu10.25) ...
Processing triggers for ureadahead (0.100.0-21) ...
Setting up systemd-sysv (237-3ubuntu10.25) ...
Setting up linux-image-4.15.0-52-generic (4.15.0-52.56) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up udev (237-3ubuntu10.25) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for dbus (1.12.2-1ubuntu1.1) ...
Setting up libpam-systemd:amd64 (237-3ubuntu10.25) ...
Processing triggers for linux-image-4.15.0-52-generic (4.15.0-52.56) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-52-generic
/etc/kernel/postinst.d/x-grub-legacy-ec2:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-4.15.0-54-generic
Found kernel: /vmlinuz-4.15.0-52-generic
Found kernel: /vmlinuz-4.15.0-54-generic
Found kernel: /vmlinuz-4.15.0-52-generic
Updating /boot/grub/menu.lst ... done


/etc/kernel/postinst.d/zz-update-grub:
/usr/sbin/update-grub: 3: exec: grub-mkconfig: Exec format error
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
dpkg: error processing package linux-image-4.15.0-52-generic (--configure):
 installed linux-image-4.15.0-52-generic package post-installation script subprocess returned error exit status 1
Processing triggers for initramfs-tools (0.130ubuntu3.8) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-54-generic
Errors were encountered while processing:
 linux-image-4.15.0-52-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
nawrocki@ubuntu:/var/lib/apt/lists$
```

Could you help mi please with repairing my server?

Thanks in advance,
Pawel

---

### Post by cruzer001 on 2019-08-08
Removing /var/cache/apt/archives could remove those warnings.

But you show a kernel error with an older kernel.
The "autoremove" command can at times clean up kernels.

Mine is a home unit (noVMware), not a production machine and on it I would remove 4.15.0-52 manually.  Is the 55.xx version still installed?

May help, may do nothing.

---

### Post by blurred82 on 2019-08-09
I have deleted all files from /var/cache/apt
Looks like  vmlinuz-4.15.0-55-generic is missing

```
nawrocki@ubuntu:~$ ls -lsh /boot/
total 109M
214K -rw-r--r-- 1 root root 213K Jun  4 22:33 config-4.15.0-52-generic
214K -rw-r--r-- 1 root root 213K Jun 24 11:39 config-4.15.0-54-generic
214K -rw-r--r-- 1 root root 213K Jul  2 18:41 config-4.15.0-55-generic
1.0K drwxr-xr-x 5 root root 1.0K Aug  9 14:14 grub
 26M -rw-r--r-- 1 root root  26M Aug  8 14:25 initrd.img-4.15.0-52-generic
 56M -rw-r--r-- 1 root root  55M Aug  8 14:26 initrd.img-4.15.0-54-generic
 12K drwx------ 2 root root  12K Nov 14  2016 lost+found
3.9M -rw------- 1 root root 3.9M Jun  4 22:33 System.map-4.15.0-52-generic
3.9M -rw------- 1 root root 3.9M Jun 24 11:39 System.map-4.15.0-54-generic
3.9M -rw------- 1 root root 3.9M Jul  2 18:41 System.map-4.15.0-55-generic
8.0M -rw------- 1 root root 8.0M Jun  4 22:39 vmlinuz-4.15.0-52-generic
8.0M -rw------- 1 root root 8.0M Jun 24 12:21 vmlinuz-4.15.0-54-generic
nawrocki@ubuntu:~$
```

```
nawrocki@ubuntu:~$ uname -r
4.15.0-54-generic

```

---

