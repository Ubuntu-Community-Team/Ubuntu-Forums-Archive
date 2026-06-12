---
title: "[PROBLEM] error when I try to upgrede kubuntu 15.10 to 16.04"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by andry93miticohotm on 2016-04-24
Hi to all, I tried to upgrade my system with gui but when I reboot my pc I seen an error about kdeinit5 so I boot a live usb of kubuntu 16.04, i mounted my partition and I made chroot.Now when I try  to upgred from apt-get dist-upgrade I have an error: ```
The following packages were automatically installed and are no longer required:
  libc-ares-dev libcglib-java libcommons-httpclient-java libept1.4.16 libpgm-5.1-0
  libsodium13 libv8-3.14-dev libv8-3.14.5 libvte-2.90-9 libvte-2.90-common libx264-146
  libzmq3 openjdk-7-doc
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-image-4.4.0-21-generic
The following packages will be upgraded:
  acpid
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
906 not fully installed or removed.
Need to get 0 B/18.7 MB of archives.
After this operation, 55.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
E: Can not write log (Is /dev/pts mounted?) - posix_openpt (2: No such file or directory)
(Reading database ... 285817 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-21-generic_4.4.0-21.37_amd64.deb ...
grep: /proc/cpuinfo: No such file or directory
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-21-generic_4.4.0-21.37_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Preparing to unpack .../acpid_1%3a2.0.26-1ubuntu2_amd64.deb ...
 * Stopping ACPI services...                                                            start-stop-daemon: nothing in /proc - not mounted?
invoke-rc.d: initscript acpid, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg: trying script from the new package instead ...
 * Stopping ACPI services...                                                            start-stop-daemon: nothing in /proc - not mounted?
invoke-rc.d: initscript acpid, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/acpid_1%3a2.0.26-1ubuntu2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-21-generic_4.4.0-21.37_amd64.deb
 /var/cache/apt/archives/acpid_1%3a2.0.26-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@kubuntu:/var/cache/debconf# apt-get install -f linux-image-4.4.0-21-generic_4.4.0-21.37_amd6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-4.4.0-21-generic_4.4.0-21.37_amd6
E: Couldn't find any package by glob 'linux-image-4.4.0-21-generic_4.4.0-21.37_amd6'
E: Couldn't find any package by regex 'linux-image-4.4.0-21-generic_4.4.0-21.37_amd6'
```

---

### Post by Impavidus on 2016-04-24
Have you mounted /proc, /dev and /sys inside the chroot? apt-get complains that it cannot find things in /dev and /proc that should normally be there. Read [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) and pay attention to the three **sudo mount --bind ...** commands.

---

### Post by andry93miticohotm on 2016-04-24
yeah! thank yo so much, I solve my problem. I have followed the instruction of the above link and I run the command again.

---

