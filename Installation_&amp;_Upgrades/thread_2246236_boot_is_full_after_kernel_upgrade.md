---
title: "/boot is full after kernel upgrade"
date: 2014-09-29
forum: Installation &amp; Upgrades
---

### Post by Derlis_Fernando_Ga on 2014-09-29
After kernel upgrades messages appear indicating that /boot is full.

apt-get clean was issue with no results...
:~# apt-get clean
:~# df -m
Filesystem                  1M-blocks   Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root    456958 230666    203058  54% /
none                                1      0         1   0% /sys/fs/cgroup
udev                             5988      1      5988   1% /dev
tmpfs                            1200      2      1199   1% /run
none                                5      0         5   0% /run/lock
none                             5999      1      5999   1% /run/shm
none                              100      1       100   1% /run/user
/dev/sda1                         236    222         2 100% /boot

/boot contains...
:~# ls -a1 /boot
.
..
abi-3.11.0-20-generic
abi-3.13.0-27-generic
abi-3.13.0-29-generic
abi-3.13.0-30-generic
abi-3.13.0-32-generic
abi-3.13.0-34-generic
abi-3.13.0-35-generic
abi-3.13.0-36-generic
config-3.11.0-20-generic
config-3.13.0-27-generic
config-3.13.0-29-generic
config-3.13.0-30-generic
config-3.13.0-32-generic
config-3.13.0-34-generic
config-3.13.0-35-generic
config-3.13.0-36-generic
grub
initrd.img-3.11.0-20-generic
initrd.img-3.13.0-27-generic
initrd.img-3.13.0-29-generic
initrd.img-3.13.0-30-generic
initrd.img-3.13.0-32-generic
initrd.img-3.13.0-34-generic
initrd.img-3.13.0-35-generic
lost+found
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
System.map-3.11.0-20-generic
System.map-3.13.0-27-generic
System.map-3.13.0-29-generic
System.map-3.13.0-30-generic
System.map-3.13.0-32-generic
System.map-3.13.0-34-generic
System.map-3.13.0-35-generic
System.map-3.13.0-36-generic
vmlinuz-3.11.0-20-generic
vmlinuz-3.13.0-27-generic
vmlinuz-3.13.0-29-generic
vmlinuz-3.13.0-30-generic
vmlinuz-3.13.0-32-generic
vmlinuz-3.13.0-34-generic
vmlinuz-3.13.0-35-generic
vmlinuz-3.13.0-36-generic

Issued.... "apt-get autoremove" with the following errors

:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.13.0-36-generic (3.13.0-36.63) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.13.0-36-generic
vmlinuz(/boot/vmlinuz-3.13.0-36-generic
) points to /boot/vmlinuz-3.13.0-36-generic
 (/boot/vmlinuz-3.13.0-36-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-36-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-36-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-36-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-36-generic.postinst line 1025.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    No apport report written because MaxReports is reached already
                                                                                                                                                                                                                                                                                  dpkg: error processing package linux-image-3.13.0-36-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-36-generic:
 linux-image-extra-3.13.0-36-generic depends on linux-image-3.13.0-36-generic; however:
  Package linux-image-3.13.0-36-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-36-generic; however:
  Package linux-image-3.13.0-36-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-36-generic; however:
  Package linux-image-extra-3.13.0-36-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.36.43); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any helps?

Thanks in advance!!

---

### Post by JMB74 on 2014-09-29
Need to remove at least one kernel to create some space.

So perhaps....

```
sudo dpkg --purge linux-image-3.13.0-27-generic linux-image-extra-3.13.0-27-generic
```

---

### Post by slickymaster on 2014-09-29
Hi Derlis_Fernando_Ga, welcome to the forums.

Please follow this link to see the various options you have for removing old kernels: [How do I remove or hide old kernel versions to clean up the boot menu]("http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu")

---

### Post by Derlis_Fernando_Ga on 2014-09-30
It works.

Thanks for your help!!

---

### Post by slickymaster on 2014-09-30
You're welcome. Glad you got it fixed.

Please mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution for this problem.

---

