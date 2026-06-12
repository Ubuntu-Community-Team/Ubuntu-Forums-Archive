---
title: "Unable to upgrade , E: Unmet dependencies. Try using -f"
date: 2017-06-21
forum: Installation &amp; Upgrades
---

### Post by seerapu2 on 2017-06-21
Ubuntu@Ubuntu:~$ sudo apt-get -y dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-71-generic : Depends: linux-image-4.4.0-71-generic but it is not installed
 linux-image-extra-4.4.0-81-generic : Depends: linux-image-4.4.0-81-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-81-generic but it is not installed
                       Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.


Please help me to resolve this issue

---

### Post by Impavidus on 2017-06-21
Try this command (as suggested):```
sudo apt-get -f install
```
If that doesn't work, run these commands for some more diagnostics and post results:```
df -h
df -i
dpkg -l | grep 'linux-*'
```

---

### Post by seerapu2 on 2017-06-21
Hi
Thank you for reply,

sudo apt-get -f install

also returning the same error
refer below
----------------
```
ubuntu@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-headers-4.4.0-63 linux-headers-4.4.0-63-generic
  linux-headers-4.4.0-64 linux-headers-4.4.0-64-generic linux-headers-4.4.0-65 linux-headers-4.4.0-65-generic linux-headers-4.4.0-71 linux-headers-4.4.0-71-generic
  linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic linux-image-4.4.0-64-generic linux-image-4.4.0-65-generic
  linux-image-4.4.0-71-generic linux-image-extra-4.4.0-59-generic linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic
  linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-65-generic linux-image-extra-4.4.0-71-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-71-generic linux-image-4.4.0-81-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-71-generic linux-image-4.4.0-81-generic
0 upgraded, 2 newly installed, 0 to remove and 139 not upgraded.
10 not fully installed or removed.
Need to get 0 B/43.7 MB of archives.
After this operation, 133 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 404617 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-81-generic_4.4.0-81.104_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-81-generic (4.4.0-81.104) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-81-generic_4.4.0-81.104_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-81-generic' to '/boot/vmlinuz-4.4.0-81-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
Preparing to unpack .../linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-71-generic (4.4.0-71.92) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-71-generic' to '/boot/vmlinuz-4.4.0-71-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-81-generic_4.4.0-81.104_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
--------------------
```

please refer the below results

```
----------------------------
df -h
Filesystem                     Size  Used Avail Use% Mounted on
udev                           2.0G     0  2.0G   0% /dev
tmpfs                          396M  5.8M  390M   2% /run
/dev/mapper/template--vg-root   36G   12G   24G  33% /
tmpfs                          2.0G  4.0K  2.0G   1% /dev/shm
tmpfs                          5.0M     0  5.0M   0% /run/lock
tmpfs                          2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/sda1                      472M  463M     0 100% /boot
tmpfs                          396M     0  396M   0% /run/user/7185
ubuntu@ubuntu:~$ df -i
Filesystem                     Inodes  IUsed   IFree IUse% Mounted on
udev                           500783    433  500350    1% /dev
tmpfs                          505784    612  505172    1% /run
/dev/mapper/template--vg-root 2362752 434046 1928706   19% /
tmpfs                          505784      2  505782    1% /dev/shm
tmpfs                          505784      3  505781    1% /run/lock
tmpfs                          505784     16  505768    1% /sys/fs/cgroup
/dev/sda1                      124928    348  124580    1% /boot
tmpfs                          505784      4  505780    1% /run/user/7185
ubuntu@ubuntu:~$ dpkg -l | grep 'linux-*'
ii  console-setup-linux                1.108ubuntu15.2                            all          Linux specific part of console-setup
ii  libselinux1:amd64                  2.4-3build2                                amd64        SELinux runtime shared libraries
ii  libselinux1:i386                   2.4-3build2                                i386         SELinux runtime shared libraries
ii  linux-base                         4.0ubuntu1                                 all          Linux image base package
ii  linux-firmware                     1.157.8                                    all          Firmware for Linux kernel drivers
iU  linux-generic                      4.4.0.81.87                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-51             4.4.0-51.72                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic     4.4.0-51.72                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57             4.4.0-57.78                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic     4.4.0-57.78                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-59             4.4.0-59.80                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic     4.4.0-59.80                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-62             4.4.0-62.83                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-62-generic     4.4.0-62.83                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-63             4.4.0-63.84                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-63-generic     4.4.0-63.84                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-64             4.4.0-64.85                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic     4.4.0-64.85                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-65             4.4.0-65.86                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-65-generic     4.4.0-65.86                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66             4.4.0-66.87                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic     4.4.0-66.87                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-70             4.4.0-70.91                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-70-generic     4.4.0-70.91                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-71             4.4.0-71.92                                all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-71-generic     4.4.0-71.92                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-81             4.4.0-81.104                               all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-81-generic     4.4.0-81.104                               amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-generic              4.4.0.81.87                                amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-21-generic       4.4.0-21.37                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic       4.4.0-45.66                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic       4.4.0-51.72                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic       4.4.0-57.78                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic       4.4.0-59.80                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic       4.4.0-62.83                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-63-generic       4.4.0-63.84                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-generic       4.4.0-64.85                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-65-generic       4.4.0-65.86                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-66-generic       4.4.0-66.87                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-70-generic       4.4.0-70.91                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic 4.4.0-21.37                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-generic 4.4.0-51.72                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic 4.4.0-57.78                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic 4.4.0-59.80                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic 4.4.0-62.83                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-63-generic 4.4.0-63.84                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic 4.4.0-64.85                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-65-generic 4.4.0-65.86                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-66-generic 4.4.0-66.87                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-70-generic 4.4.0-70.91                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-71-generic 4.4.0-71.92                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-81-generic 4.4.0-81.104                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                4.4.0.81.87                                amd64        Generic Linux kernel image
ii  util-linux                         2.27.1-6ubuntu3.1                          amd64        miscellaneous system utilities
```

---

### Post by Impavidus on 2017-06-21
Your /boot partition is full with old kernels. It's best to regularly uninstall old kernels once you have verified the new kernel works. apt-get offers to autoremove them, but that will most likely not work right now.

Try to get some headroom by manually uninstalling some old kernels. With a bit of luck, this will help:
```

sudo dpkg -P  linux-image{,-extra}-4.4.0-{51,57,59}-generic

```
That should remove 3 old kernels. Please post output in [noparse]```
code tags
```[/noparse], like I did above. It's more readable.

If it doesn't work, post the output of this:```
ls -l /boot
```

---

### Post by seerapu2 on 2017-06-22
Same issue still , please refer the below log.
Thank you for suggesting ```


[code]sudo dpkg -P  linux-image{,-extra}-4.4.0-{51,57,59}-generic
```

here is the log for below command
```
sudo dpkg -P  linux-image{,-extra}-4.4.0-{51,57,59}-generic
```
```
Ubuntu@Ubuntu:~$ sudo dpkg -P  linux-image{,-extra}-4.4.0-{51,57,59}-generic
(Reading database ... 404617 files and directories currently installed.)
Removing linux-image-extra-4.4.0-51-generic (4.4.0-51.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-51-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-51-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-57-generic (4.4.0-57.78) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-57-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-57-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-59-generic (4.4.0-59.80) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-59-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-59-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-51-generic (4.4.0-51.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-4.4.0-51-generic (4.4.0-51.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Removing linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Removing linux-image-4.4.0-59-generic (4.4.0-59.80) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-4.4.0-59-generic (4.4.0-59.80) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
Errors were encountered while processing:
 linux-image-extra-4.4.0-51-generic
 linux-image-extra-4.4.0-57-generic
 linux-image-extra-4.4.0-59-generic
```


also find the log for 
```
ls -l /boot
``````
Ubuntu@Ubuntu:~$ ls -l /boot
total 317907
-rw-r--r-- 1 root root  1242701 Oct 19  2016 abi-4.4.0-45-generic
-rw-r--r-- 1 root root  1244118 Jan 18 07:59 abi-4.4.0-62-generic
-rw-r--r-- 1 root root  1245512 Feb  1 11:39 abi-4.4.0-63-generic
-rw-r--r-- 1 root root  1245512 Feb 20 05:40 abi-4.4.0-64-generic
-rw-r--r-- 1 root root  1245659 Feb 23 12:00 abi-4.4.0-65-generic
-rw-r--r-- 1 root root  1245512 Mar  3 10:25 abi-4.4.0-66-generic
-rw-r--r-- 1 root root  1245659 Mar 22 09:11 abi-4.4.0-70-generic
-rw-r--r-- 1 root root   189760 Oct 19  2016 config-4.4.0-45-generic
-rw-r--r-- 1 root root   190047 Jan 18 07:59 config-4.4.0-62-generic
-rw-r--r-- 1 root root   190247 Feb  1 11:39 config-4.4.0-63-generic
-rw-r--r-- 1 root root   190247 Feb 20 05:40 config-4.4.0-64-generic
-rw-r--r-- 1 root root   190236 Feb 23 12:00 config-4.4.0-65-generic
-rw-r--r-- 1 root root   190247 Mar  3 10:25 config-4.4.0-66-generic
-rw-r--r-- 1 root root   190236 Mar 22 09:11 config-4.4.0-70-generic
drwxr-xr-x 5 root root     1024 Jun 22 02:00 grub
-rw-r--r-- 1 root root 12423894 Feb 10 00:02 initrd.img-4.4.0-45-generic
-rw-r--r-- 1 root root 37508600 Feb 10 00:01 initrd.img-4.4.0-62-generic
-rw-r--r-- 1 root root 37496724 Feb 20 07:45 initrd.img-4.4.0-63-generic
-rw-r--r-- 1 root root 37499958 Feb 22 03:52 initrd.img-4.4.0-64-generic
-rw-r--r-- 1 root root 37507962 Mar  2 05:39 initrd.img-4.4.0-65-generic
-rw-r--r-- 1 root root 37499693 Mar  8 10:57 initrd.img-4.4.0-66-generic
-rw-r--r-- 1 root root 37506582 Mar 27 13:53 initrd.img-4.4.0-70-generic
drwx------ 2 root root    12288 May 12  2016 lost+found
-rw------- 1 root root  3869895 Oct 19  2016 System.map-4.4.0-45-generic
-rw------- 1 root root  3875553 Jan 18 07:59 System.map-4.4.0-62-generic
-rw------- 1 root root  3883990 Feb  1 11:39 System.map-4.4.0-63-generic
-rw------- 1 root root  3883990 Feb 20 05:40 System.map-4.4.0-64-generic
-rw------- 1 root root  3882407 Feb 23 12:00 System.map-4.4.0-65-generic
-rw------- 1 root root  3883990 Mar  3 10:25 System.map-4.4.0-66-generic
-rw------- 1 root root  3882277 Mar 22 09:11 System.map-4.4.0-70-generic
-rw------- 1 root root  7054208 Oct 19  2016 vmlinuz-4.4.0-45-generic
-rw------- 1 root root  7070992 Jan 18 07:59 vmlinuz-4.4.0-62-generic
-rw------- 1 root root  7087088 Feb  1 11:39 vmlinuz-4.4.0-63-generic
-rw------- 1 root root  7087152 Feb 20 05:40 vmlinuz-4.4.0-64-generic
-rw------- 1 root root  7082608 Feb 23 12:00 vmlinuz-4.4.0-65-generic
-rw------- 1 root root  7087024 Mar  3 10:25 vmlinuz-4.4.0-66-generic
-rw------- 1 root root  7083344 Mar 22 09:11 vmlinuz-4.4.0-70-generic


```

Even when I tried to remove individual kernels also facing the same issue, please refer below console output

```
Ubuntu@Ubuntu:~$ sudo apt-get -y remove linux-image-4.4.0-66-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-66-generic : Depends: linux-image-4.4.0-66-generic but it is not going to be installed
 linux-image-extra-4.4.0-71-generic : Depends: linux-image-4.4.0-71-generic but it is not going to be installed
 linux-image-extra-4.4.0-81-generic : Depends: linux-image-4.4.0-81-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.4.0-81-generic but it is not going to be installed
                       Recommends: thermald but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Impavidus on 2017-06-22
Interesting. It failed to remove the linux-image-extra-4.4.0-... packages, but it did remove the linux-image-4.4.0-... packages. That should have cleared up some space. Try to remove them again:```
sudo dpkg -P linux-image-extra-4.4.0-{51,57,59}-generic
```
Make sure which kernel you run right now:```
uname -r
```Does it give you version 4.4.0-65 or higher? Then try to remove some more:```
sudo dpkg -P linux-image{,-extra}-4.4.0-{62,63,64}-generic
```Then let's see the current status:```
dpkg -l | grep 'linux-*'
df -h /boot
```

---

### Post by seerapu2 on 2017-06-22
console output of
```
sudo dpkg -P linux-image-extra-4.4.0-{51,57,59}-generic
```
```
:~$ sudo dpkg -P linux-image-extra-4.4.0-{51,57,59}-generic
(Reading database ... 387802 files and directories currently installed.)
Removing linux-image-extra-4.4.0-51-generic (4.4.0-51.72) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-51-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
depmod: WARNING: could not open /lib/modules/4.4.0-51-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/4.4.0-51-generic/modules.builtin: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_IlSqSS/lib/modules/4.4.0-51-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_IlSqSS/lib/modules/4.4.0-51-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-extra-4.4.0-51-generic (4.4.0-51.72) ...
Removing linux-image-extra-4.4.0-57-generic (4.4.0-57.78) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-57-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
depmod: WARNING: could not open /lib/modules/4.4.0-57-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/4.4.0-57-generic/modules.builtin: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_IVVSm1/lib/modules/4.4.0-57-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_IVVSm1/lib/modules/4.4.0-57-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-extra-4.4.0-57-generic (4.4.0-57.78) ...
Removing linux-image-extra-4.4.0-59-generic (4.4.0-59.80) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-59-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
depmod: WARNING: could not open /lib/modules/4.4.0-59-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/4.4.0-59-generic/modules.builtin: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_HhGXD6/lib/modules/4.4.0-59-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_HhGXD6/lib/modules/4.4.0-59-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-extra-4.4.0-59-generic (4.4.0-59.80) ...

```
console output of 
```
sudo dpkg -P linux-image{,-extra}-4.4.0-{62,63,64}-generic
```
```
:~$ sudo dpkg -P linux-image{,-extra}-4.4.0-{62,63,64}-generic
(Reading database ... 387802 files and directories currently installed.)
Removing linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
Removing linux-image-extra-4.4.0-63-generic (4.4.0-63.84) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-extra-4.4.0-63-generic (4.4.0-63.84) ...
Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
Removing linux-image-4.4.0-62-generic (4.4.0-62.83) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-62-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-4.4.0-62-generic (4.4.0-62.83) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Removing linux-image-4.4.0-63-generic (4.4.0-63.84) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-63-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-4.4.0-63-generic (4.4.0-63.84) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
Removing linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
done
Purging configuration files for linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic

```
current using kernel verion
```
4.4.0-70-generic
```
console output of below command
```
dpkg -l | grep 'linux-*'
```
```
:~$ dpkg -l | grep 'linux-*'
ii  console-setup-linux                1.108ubuntu15.2                            all          Linux specific part of console-setup
ii  libselinux1:amd64                  2.4-3build2                                amd64        SELinux runtime shared libraries
ii  libselinux1:i386                   2.4-3build2                                i386         SELinux runtime shared libraries
ii  linux-base                         4.0ubuntu1                                 all          Linux image base package
ii  linux-firmware                     1.157.8                                    all          Firmware for Linux kernel drivers
iU  linux-generic                      4.4.0.81.87                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-51             4.4.0-51.72                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic     4.4.0-51.72                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57             4.4.0-57.78                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic     4.4.0-57.78                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-59             4.4.0-59.80                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic     4.4.0-59.80                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-62             4.4.0-62.83                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-62-generic     4.4.0-62.83                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-63             4.4.0-63.84                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-63-generic     4.4.0-63.84                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-64             4.4.0-64.85                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic     4.4.0-64.85                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-65             4.4.0-65.86                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-65-generic     4.4.0-65.86                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66             4.4.0-66.87                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic     4.4.0-66.87                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-70             4.4.0-70.91                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-70-generic     4.4.0-70.91                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-71             4.4.0-71.92                                all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-71-generic     4.4.0-71.92                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-81             4.4.0-81.104                               all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-81-generic     4.4.0-81.104                               amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-generic              4.4.0.81.87                                amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-21-generic       4.4.0-21.37                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic       4.4.0-45.66                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-65-generic       4.4.0-65.86                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-66-generic       4.4.0-66.87                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-70-generic       4.4.0-70.91                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic 4.4.0-21.37                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-65-generic 4.4.0-65.86                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-66-generic 4.4.0-66.87                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-70-generic 4.4.0-70.91                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-71-generic 4.4.0-71.92                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-81-generic 4.4.0-81.104                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                4.4.0.81.87                                amd64        Generic Linux kernel image
ii  util-linux                         2.27.1-6ubuntu3.1                          amd64        miscellaneous system utilities

```
console output of below command
```
df -h /boot
```
```
:~$ ll /boot/
total 194663
drwxr-xr-x  4 root root     4096 Jun 22 04:54 ./
drwxr-xr-x 24 root root     4096 Mar 27 13:53 ../
-rw-r--r--  1 root root  1242701 Oct 19  2016 abi-4.4.0-45-generic
-rw-r--r--  1 root root  1245659 Feb 23 12:00 abi-4.4.0-65-generic
-rw-r--r--  1 root root  1245512 Mar  3 10:25 abi-4.4.0-66-generic
-rw-r--r--  1 root root  1245659 Mar 22 09:11 abi-4.4.0-70-generic
-rw-r--r--  1 root root   189760 Oct 19  2016 config-4.4.0-45-generic
-rw-r--r--  1 root root   190236 Feb 23 12:00 config-4.4.0-65-generic
-rw-r--r--  1 root root   190247 Mar  3 10:25 config-4.4.0-66-generic
-rw-r--r--  1 root root   190236 Mar 22 09:11 config-4.4.0-70-generic
drwxr-xr-x  5 root root     1024 Jun 22 04:54 grub/
-rw-r--r--  1 root root 12423894 Feb 10 00:02 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root  7999242 Jun 22 04:53 initrd.img-4.4.0-51-generic
-rw-r--r--  1 root root  7999322 Jun 22 04:53 initrd.img-4.4.0-57-generic
-rw-r--r--  1 root root  7999333 Jun 22 04:53 initrd.img-4.4.0-59-generic
-rw-r--r--  1 root root 37507962 Mar  2 05:39 initrd.img-4.4.0-65-generic
-rw-r--r--  1 root root 37499693 Mar  8 10:57 initrd.img-4.4.0-66-generic
-rw-r--r--  1 root root 37506582 Mar 27 13:53 initrd.img-4.4.0-70-generic
drwx------  2 root root    12288 May 12  2016 lost+found/
-rw-------  1 root root  3869895 Oct 19  2016 System.map-4.4.0-45-generic
-rw-------  1 root root  3882407 Feb 23 12:00 System.map-4.4.0-65-generic
-rw-------  1 root root  3883990 Mar  3 10:25 System.map-4.4.0-66-generic
-rw-------  1 root root  3882277 Mar 22 09:11 System.map-4.4.0-70-generic
-rw-------  1 root root  7054208 Oct 19  2016 vmlinuz-4.4.0-45-generic
-rw-------  1 root root  7082608 Feb 23 12:00 vmlinuz-4.4.0-65-generic
-rw-------  1 root root  7087024 Mar  3 10:25 vmlinuz-4.4.0-66-generic
-rw-------  1 root root  7083344 Mar 22 09:11 vmlinuz-4.4.0-70-generic
```

---

### Post by Impavidus on 2017-06-22
Did df -h /boot give no output or did you forget to post? According to post #3 it should have given output. If it shows something significantly less than 100% you're good to proceed.

There were a few warnings in the dpkg output, but it seems to have worked. Six old kernels removed, I think you can try to get the new kernels installed:```
sudo apt -f install
```
Then reboot and make sure you're running kernel 4.4.0-81:```
uname -r
```
If all looks fine, try to autoremove some old stuff:```
sudo apt autoremove --purge
```
Then again```
dpkg -l | grep 'linux-*'
```to see if any more cleanup is necessary.

---

### Post by seerapu2 on 2017-06-23
yeah, sorry I forgot to post the data for df -h /bbot

please refer below

```
:~$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       472M  200M  249M  45% /boot
```

here is the output of ```

dpkg -l | grep 'linux-*'
```

```
:~$ dpkg -l | grep 'linux-*'
ii  console-setup-linux                1.108ubuntu15.2                            all          Linux specific part of console-setup
ii  libselinux1:amd64                  2.4-3build2                                amd64        SELinux runtime shared libraries
ii  libselinux1:i386                   2.4-3build2                                i386         SELinux runtime shared libraries
ii  linux-base                         4.0ubuntu1                                 all          Linux image base package
ii  linux-firmware                     1.157.8                                    all          Firmware for Linux kernel drivers
ii  linux-generic                      4.4.0.81.87                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-51             4.4.0-51.72                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic     4.4.0-51.72                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-70             4.4.0-70.91                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-70-generic     4.4.0-70.91                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-71             4.4.0-71.92                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-71-generic     4.4.0-71.92                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-81             4.4.0-81.104                               all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-81-generic     4.4.0-81.104                               amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic              4.4.0.81.87                                amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-21-generic       4.4.0-21.37                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic       4.4.0-45.66                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-70-generic       4.4.0-70.91                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-71-generic       4.4.0-71.92                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-81-generic       4.4.0-81.104                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic 4.4.0-21.37                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-70-generic 4.4.0-70.91                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-71-generic 4.4.0-71.92                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-81-generic 4.4.0-81.104                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                4.4.0.81.87                                amd64        Generic Linux kernel image
ii  util-linux                         2.27.1-6ubuntu3.1                          amd64        miscellaneous system utilities

```

now it's taking 81 kernel

```
:~$ uname -r
4.4.0-81-generic

```

Here is the latest out put of the command
```
dpkg -l | grep 'linux-*'
```

```
:~# dpkg -l | grep 'linux-*'
ii  console-setup-linux                1.108ubuntu15.3                            all          Linux specific part of console-setup
ii  libselinux1:amd64                  2.4-3build2                                amd64        SELinux runtime shared libraries
ii  libselinux1:i386                   2.4-3build2                                i386         SELinux runtime shared libraries
ii  linux-base                         4.0ubuntu1                                 all          Linux image base package
ii  linux-firmware                     1.157.11                                   all          Firmware for Linux kernel drivers
ii  linux-generic                      4.4.0.81.87                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-81             4.4.0-81.104                               all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-81-generic     4.4.0-81.104                               amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic              4.4.0.81.87                                amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-21-generic       4.4.0-21.37                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-81-generic       4.4.0-81.104                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic 4.4.0-21.37                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-81-generic 4.4.0-81.104                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                4.4.0.81.87                                amd64        Generic Linux kernel image
ii  util-linux                         2.27.1-6ubuntu3.2                          amd64        miscellaneous system utilities


```

Please confirm, I think now everything is fine in my machine right?

---

### Post by Impavidus on 2017-06-23
Everything is fine now. Just don't forget to occasionally autoremove old packages. Ubuntu can be configured to do so automatically (search the forum for "unattended upgrades"), but it's good to check sometimes to make sure everything works. That way you can prevent these problems.

Edit: Actually, one would usually keep one old kernel, just in case there's some undetected problem with the latest kernel.

Can you mark this thread as solved? Thread tools -> mark as solved.

---

