---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-03-14
forum: Installation &amp; Upgrades
---

### Post by aboodyman on 2017-03-14
Help me I'm not able to use from the command apt at all, look at the output whenever I try to use the command:
```
sudo: unable to resolve host Samsung
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  thermald
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-66-generic* linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-66-generic* linux-image-generic*
0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
14 not fully installed or removed.
After this operation, 1,091 MB disk space will be freed.
Do you want to continue? [Y/n] Y'
(Reading database ... 318356 files and directories currently installed.)
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_8SSrER/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_8SSrER/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_1VZVzu/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_1VZVzu/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_QXJkog/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_QXJkog/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_fAOAFi/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_fAOAFi/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ian-weisser on 2017-03-14
Read the error message line by line. It's pretty straightforward.

Example: Here's the first error.

> depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: **No such file or directory**

The package manager is looking for a file that it previously placed so it can work with it, but the file isn't there anymore.
Did you delete it? If so, why?
If possible, reinstall the entire package so the package manager can remove it properly. There are other ways, but this is the best way for a beginner.

Lesson: Never manually remove a file placed by the package manager. It might solve some immediate problem, but there is a price to pay later.

---

### Post by aboodyman on 2017-03-14
> **ian-weisser said:**
> Read the error message line by line. It's pretty straightforward.

Example: Here's the first error.



The package manager is looking for a file that it previously placed so it can work with it, but the file isn't there anymore.
Did you delete it? If so, why?
If possible, reinstall the entire package so the package manager can remove it properly. There are other ways, but this is the best way for a beginner.

Lesson: Never manually remove a file placed by the package manager. It might solve some immediate problem, but there is a price to pay later.
How do I reinstall it if I can't use the APT command? and I didn't delete that file at all

---

### Post by aboodyman on 2017-03-14
Nevermind, I solved it by a simple dist-upgrade, Thanks ian weisser for the reply

---

### Post by ian-weisser on 2017-03-14
Happy to see you found a solution.

---

### Post by aboodyman on 2017-03-14
> **aboodyman said:**
> Nevermind, I solved it by a simple dist-upgrade, Thanks ian weisser for the reply
Oops, it didn't work, here's the output:
[https://paste.ubuntu.com/24176962/](https://paste.ubuntu.com/24176962/)
welp, the same output

---

### Post by #&amp;thj^% on 2017-03-14
What is returned from the terminal with:
```
df
```
Also would not hurt to see what kernels are indeed installed via:
```
sudo dpkg --get-selections | grep linux  
```
Paste back using code tags... both results please>

---

### Post by aboodyman on 2017-03-14
Output of df
```

Filesystem     1K-blocks     Used Available Use% Mounted on
udev             2987400        0   2987400   0% /dev
tmpfs             602160     8988    593172   2% /run
/dev/sda6       58086620 35968904  19143972  66% /
tmpfs            3010788    54416   2956372   2% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            3010788        0   3010788   0% /sys/fs/cgroup
tmpfs             602160       60    602100   1% /run/user/1002

```
Output of the other one:
```

console-setup-linux                install
libselinux1:amd64                install
libselinux1:i386                install
linux-base                    install
linux-firmware                    install
linux-headers-4.4.0-47                install
linux-headers-4.4.0-47-generic            install
linux-headers-4.4.0-64                install
linux-headers-4.4.0-64-generic            install
linux-headers-4.4.0-66                install
linux-headers-4.4.0-66-generic            install
linux-headers-4.4.0-67                install
linux-headers-4.4.0-67-generic            install
linux-headers-generic                install
linux-image-4.4.0-21-generic            deinstall
linux-image-4.4.0-36-generic            deinstall
linux-image-4.4.0-38-generic            deinstall
linux-image-4.4.0-42-generic            deinstall
linux-image-4.4.0-45-generic            deinstall
linux-image-4.4.0-47-generic            install
linux-image-4.4.0-64-generic            install
linux-image-4.4.0-66-generic            install
linux-image-4.4.0-67-generic            install
linux-image-extra-4.4.0-21-generic        deinstall
linux-image-extra-4.4.0-36-generic        deinstall
linux-image-extra-4.4.0-38-generic        deinstall
linux-image-extra-4.4.0-42-generic        deinstall
linux-image-extra-4.4.0-45-generic        deinstall
linux-image-extra-4.4.0-47-generic        install
linux-image-extra-4.4.0-64-generic        install
linux-image-extra-4.4.0-66-generic        install
linux-image-extra-4.4.0-67-generic        install
linux-image-generic                install
linux-libc-dev:amd64                install
linux-sound-base                install
pptp-linux                    install
syslinux                    install
syslinux-common                    install
syslinux-legacy                    install
util-linux                    install

```

---

### Post by #&amp;thj^% on 2017-03-14
Do you have Proposed Repos enabled? <<<Nevermind I see that you do.
Just run this and return the output from the terminal again please:
```
sudo apt autoremove
```
Just enter the code do not run it yet.(Or Accept)

---

### Post by aboodyman on 2017-03-14
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic linux-image-4.4.0-45-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-45-generic snap-confine
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
16 not fully installed or removed.
After this operation, 872 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 350668 files and directories currently installed.)
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_RAqsvb/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_RAqsvb/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_FsUXPQ/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_FsUXPQ/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ITfPh9/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ITfPh9/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_qJM8J9/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_qJM8J9/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing snap-confine (2.23.1) ...
Errors were encountered while processing:
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by #&amp;thj^% on 2017-03-14
Well I did not want it to run, just list the output first..:D
Lets see if we can get this right now.
```
sudo apt install linux-headers-4.4.0-36-generic
```
Followed by this:
```
sudo apt autoremove -s
```
Again posting back the return of both.

---

### Post by #&amp;thj^% on 2017-03-14
Did I lose you?

---

### Post by aboodyman on 2017-03-15
I'm so sorry about not replying, but it was so late so I had to sleep :(
anyway here is the output of the first one:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  linux-headers-4.4.0-36
The following packages will be REMOVED:
  linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic
  linux-image-4.4.0-42-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-64-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-64-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-36 linux-headers-4.4.0-36-generic
0 upgraded, 2 newly installed, 10 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 10.7 MB of archives.
After this operation, 1,013 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-4.4.0-36 all 4.4.0-36.55 [9,935 kB]
Get:2 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-4.4.0-36-generic amd64 4.4.0-36.55 [779 kB]
Fetched 10.7 MB in 2min 25s (73.7 kB/s)                                        
(Reading database ... 318361 files and directories currently installed.)
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_hBaEz5/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_hBaEz5/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Jy8xjT/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Jy8xjT/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ckBc0E/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ckBc0E/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_cElfuD/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_cElfuD/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
WARNING: missing /lib/modules/4.4.0-64-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-64-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_lnb4JU/lib/modules/4.4.0-64-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_lnb4JU/lib/modules/4.4.0-64-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

and to the second one:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic
  linux-image-4.4.0-42-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-64-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-64-generic
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
16 not fully installed or removed.
Remv linux-image-extra-4.4.0-36-generic [4.4.0-36.55]
Remv linux-image-4.4.0-36-generic [4.4.0-36.55]
Remv linux-image-extra-4.4.0-38-generic [4.4.0-38.57]
Remv linux-image-4.4.0-38-generic [4.4.0-38.57]
Remv linux-image-extra-4.4.0-42-generic [4.4.0-42.62]
Remv linux-image-4.4.0-42-generic [4.4.0-42.62]
Remv linux-image-extra-4.4.0-45-generic [4.4.0-45.66]
Remv linux-image-4.4.0-45-generic [4.4.0-45.66]
Remv linux-image-extra-4.4.0-64-generic [4.4.0-64.85]
Remv linux-image-4.4.0-64-generic [4.4.0-64.85]
Conf grub-pc (2.02~beta2-36ubuntu3.8 Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-66-generic (4.4.0-66.87 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-67-generic (4.4.0-67.88 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-66-generic (4.4.0-66.87 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-67-generic (4.4.0-67.88 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-generic (4.4.0.67.72 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
```
It seems like these corrupt packages are unremovable for some reason :confused:

---

### Post by #&amp;thj^% on 2017-03-15
Is there a real reason you need to have the **proposed repos** enabled?
> The testing area for updates. This repository is recommended only  to those interested in helping to test updates and provide feedback.   According to [the community documentation on backports]("https://help.ubuntu.com/community/UbuntuBackports") the proposed repository is:
  [INDENT]   the testing area for -updates. A   number of people must give positive   feedback on these packages before they   are allowed into -updates. This   repository is recommended ONLY to   people interested in helping to test   updates and provide feedback. Since   they are in effect testing updates,   [COLOR=#ff0000]there is a higher chance of defective   updates in this repository.[/COLOR]

 [/INDENT]  Also see [this thread and its links]("http://ubuntuforums.org/showthread.php?t=404968").


Plus I have never seen a system in such a state....Not rubbing salt in a wound here, but this did not happen on it's own.
I am willing to try some very harsh methods to see if we can fix this to a reliable system again.
_**NOTE: These methods require a Nuclear Approach...and run a high risk of further leaving your system in a UN-usable state. (So Now do you have good back-ups in place) **_
Next thing to consider here, is the time spent on fixing this...Verse's  just A New Clean Install worth it. (IE: Nice and Tidy and Proper, vs no telling what?) 
But to be sure... If we can not GET "Apt" happy nobody will be happy

---

### Post by aboodyman on 2017-03-15
How exactly do I enable proposed repos?

---

### Post by coffeecat on 2017-03-15
> **aboodyman said:**
> How exactly do I enable proposed repos?

Please re-read 1fallen's post #14. You already have the proposed repo enabled. I wouldn't be surprised if having the proposed repo has either caused or contributed to your problems. 

Did I say please re-read 1fallen's post? Particularly the quote about what the proposed repository is for.

---

### Post by deadflowr on 2017-03-15
> **aboodyman said:**
> How exactly do I enable proposed repos?

In your case it would be how to disable.
But is this an Ubuntu server or an Ubuntu desktop?

For server you need to edit the sources.list file at /etc/apt/sources.list, and comment (meaning add a # to the beginning) every line listed as -proposed in it.

For desktops, it's much easier as all you need to do is open Software and Updates and go to Updates and uncheck the proposed option.
(The setting may also be in a separate tab marked as Developers Options, or something to that affect. But it's still in the same Software and Updates program)

---

### Post by howefield on 2017-03-15
> **aboodyman said:**
> How exactly do I enable proposed repos?

As 1fallen said earlier it appears that you already do have the proposed repositories enabled. Probably not a good idea unless there is a very specific reason for it.

Software& Applications > Developer Options tab > check box

[ATTACH=CONFIG]274156[/ATTACH]

Edit : well ninja'ed :)

---

### Post by #&amp;thj^% on 2017-03-15
You already have it enabled.
One method would be like this : [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)
But that's not the point we don't want it enabled...just the known to be Stable packages that are in the Factory Repos.
Here is what shows from your Paste Bin:
```

Get:10 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-image-extra-4.4.0-67-generic amd64 4.4.0-67.88 [35.9 MB]
Get:11 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-image-generic amd64 4.4.0.67.71 [2,436 B]                
Get:12 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 coreutils amd64 8.25-2ubuntu3~16.04 [1,174 kB]                
Get:13 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 zlib1g-dev amd64 1:1.2.8.dfsg-2ubuntu4.1 [168 kB]              
Get:14 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 zlib1g i386 1:1.2.8.dfsg-2ubuntu4.1 [52.1 kB]                  
Get:15 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 zlib1g amd64 1:1.2.8.dfsg-2ubuntu4.1 [51.2 kB]                
Get:16 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libapt-pkg5.0 amd64 1.2.20 [707 kB]                            
Get:17 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libapt-inst2.0 amd64 1.2.20 [55.6 kB]                          
Get:18 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 apt amd64 1.2.20 [1,042 kB]                                    
Get:19 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 apt-utils amd64 1.2.20 [196 kB]                                
Get:20 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libpam-systemd amd64 229-4ubuntu17 [115 kB]                    
Get:21 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libudev1 amd64 229-4ubuntu17 [55.3 kB]                        
Get:22 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 libudev1 i386 229-4ubuntu17 [58.5 kB]                          
Get:23 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 udev amd64 229-4ubuntu17 [992 kB]                              
Get:24 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 libsystemd0 i386 229-4ubuntu17 [223 kB]                        
Get:25 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libsystemd0 amd64 229-4ubuntu17 [205 kB]                      
Get:26 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 systemd amd64 229-4ubuntu17 [3,623 kB]                        
Get:27 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 systemd-sysv amd64 229-4ubuntu17 [12.8 kB]                    
Get:28 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupsppdc1 amd64 2.1.3-4ubuntu0.2 [44.9 kB]                  
Get:29 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupsmime1 amd64 2.1.3-4ubuntu0.2 [13.1 kB]                  
Get:30 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupsimage2 amd64 2.1.3-4ubuntu0.2 [16.1 kB]                
Get:31 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupscgi1 amd64 2.1.3-4ubuntu0.2 [27.3 kB]                  
Get:32 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-browsed amd64 1.8.3-2ubuntu3.3 [94.1 kB]                  
Get:33 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-daemon amd64 2.1.3-4ubuntu0.2 [301 kB]                    
Get:34 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-core-drivers amd64 2.1.3-4ubuntu0.2 [27.3 kB]            
Get:35 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-filters-core-drivers amd64 1.8.3-2ubuntu3.3 [127 kB]      
Get:36 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-filters amd64 1.8.3-2ubuntu3.3 [448 kB]                  
Get:37 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-server-common all 2.1.3-4ubuntu0.2 [493 kB]              
Get:38 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups amd64 2.1.3-4ubuntu0.2 [192 kB]                          
Get:39 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-bsd amd64 2.1.3-4ubuntu0.2 [34.8 kB]                      
Get:40 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-client amd64 2.1.3-4ubuntu0.2 [133 kB]                    
Get:41 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 libcups2 i386 2.1.3-4ubuntu0.2 [212 kB]                        
Get:42 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcups2 amd64 2.1.3-4ubuntu0.2 [196 kB]                      
Get:43 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupsfilters1 amd64 1.8.3-2ubuntu3.3 [80.8 kB]              
Get:44 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libfontembed1 amd64 1.8.3-2ubuntu3.3 [47.5 kB]                
Get:45 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-common all 2.1.3-4ubuntu0.2 [134 kB]                      
Get:46 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-ppdc amd64 2.1.3-4ubuntu0.2 [26.6 kB]                    
Get:47 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 language-pack-ar all 1:16.04+20161009 [66.1 kB]                
Get:48 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 language-pack-gnome-ar all 1:16.04+20161009 [260 kB]          
Get:49 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgtk2.0-common all 2.24.30-1ubuntu1.16.04.1 [123 kB]        
Get:50 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgtk2.0-bin amd64 2.24.30-1ubuntu1.16.04.1 [9,826 B]        
Get:51 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgail-common amd64 2.24.30-1ubuntu1.16.04.1 [111 kB]        
Get:52 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgail18 amd64 2.24.30-1ubuntu1.16.04.1 [14.2 kB]            
Get:53 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgtk2.0-0 amd64 2.24.30-1ubuntu1.16.04.1 [1,776 kB]          
Get:54 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libunity-gtk2-parser0 amd64 0.0.0+15.04.20150118-0ubuntu3 [25.0 kB]
Get:55 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libunity-gtk3-parser0 amd64 0.0.0+15.04.20150118-0ubuntu3 [24.6 kB]
Get:56 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-client-core-5.7 amd64 5.7.17-0ubuntu0.16.04.2 [6,516 kB]
Get:57 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-common all 5.7.17-0ubuntu0.16.04.2 [15.7 kB]            
Get:58 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-client-5.7 amd64 5.7.17-0ubuntu0.16.04.2 [1,666 kB]      
Get:59 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-server-5.7 amd64 5.7.17-0ubuntu0.16.04.2 [2,466 kB]      
Get:60 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-server-core-5.7 amd64 5.7.17-0ubuntu0.16.04.2 [7,564 kB]
Get:61 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-gtk-module-common all 0.0.0+15.04.20150118-0ubuntu3 [3,716 B]
Get:62 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-gtk2-module amd64 0.0.0+15.04.20150118-0ubuntu3 [8,752 B]
Get:63 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-gtk3-module amd64 0.0.0+15.04.20150118-0ubuntu3 [9,246 B]
Get:64 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 apt-transport-https amd64 1.2.20 [26.1 kB]                    
Get:65 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 pciutils amd64 1:3.3.1-1.1ubuntu1.1 [234 kB]                  
Get:66 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libpci3 amd64 1:3.3.1-1.1ubuntu1.1 [24.5 kB]                  
Get:67 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 wget amd64 1.17.1-1ubuntu1.2 [298 kB]                          
Get:68 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 binutils amd64 2.26.1-1ubuntu1~16.04.4 [2,311 kB]              
Get:69 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 ubuntu-software amd64 3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1 [11.7 kB]
Get:70 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 gnome-software amd64 3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1 [228 kB]
Get:71 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 gnome-software-common all 3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1 [2,257 kB]
Get:72 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 libmysqlclient20 i386 5.7.17-0ubuntu0.16.04.2 [795 kB]          
Get:73 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libmysqlclient20 amd64 5.7.17-0ubuntu0.16.04.2 [811 kB]        
Get:74 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libnautilus-extension1a amd64 1:3.18.4.is.3.14.3-0ubuntu6 [53.7 kB]
Get:75 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libunity-control-center1 amd64 15.04.0+16.04.20170214-0ubuntu1 [81.1 kB]
Get:76 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-headers-4.4.0-67 all 4.4.0-67.88 [9,899 kB]              
Get:77 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-headers-4.4.0-67-generic amd64 4.4.0-67.88 [779 kB]      
Get:78 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-headers-generic amd64 4.4.0.67.71 [2,414 B]              
Get:79 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-libc-dev amd64 4.4.0-67.88 [839 kB]                      
Get:80 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-client all 5.7.17-0ubuntu0.16.04.2 [10.0 kB]            
Get:81 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-server all 5.7.17-0ubuntu0.16.04.2 [10.8 kB]            
Get:82 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 nautilus-data all 1:3.18.4.is.3.14.3-0ubuntu6 [48.1 kB]        
Get:83 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 nautilus amd64 1:3.18.4.is.3.14.3-0ubuntu6 [505 kB]            
Get:84 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 network-manager-openvpn-gnome amd64 1.1.93-1ubuntu1.1 [180 kB]
Get:85 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 network-manager-openvpn amd64 1.1.93-1ubuntu1.1 [26.5 kB]  
Get:86 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 software-properties-common all 0.96.20.6 [9,432 B]            
Get:87 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 software-properties-gtk all 0.96.20.6 [47.1 kB]                
Get:88 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 python3-software-properties all 0.96.20.6 [20.1 kB]            
Get:89 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 snap-confine amd64 2.23.1 [1,532 B]                            
Get:90 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 snapd amd64 2.23.1 [9,242 kB]                                  
Get:91 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unattended-upgrades all 0.90ubuntu0.4 [31.8 kB]                
Get:92 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-control-center amd64 15.04.0+16.04.20170214-0ubuntu1 [834 kB]
Get:93 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-control-center-faces all 15.04.0+16.04.20170214-0ubuntu1 [180 kB]
Get:94 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 vino amd64 3.8.1-0ubuntu9.2 [140 kB]                         
```
All those Packages are coming from the Proposed Repos...you should be understanding or getting an Idea now.
Very sorry if this sounds harsh...not trying to come across as such...but the facts are just the facts.

---

### Post by aboodyman on 2017-03-15
Alrighty, Now Proposed Repos are disabled, now what do I do?

---

### Post by aboodyman on 2017-03-15
> **1fallen said:**
> You already have it enabled.
One method would be like this : [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)
But that's not the point we don't want it enabled...just the known to be Stable packages that are in the Factory Repos.
Her is what shows from your Paste Bin:
```

Get:10 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-image-extra-4.4.0-67-generic amd64 4.4.0-67.88 [35.9 MB]
Get:11 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-image-generic amd64 4.4.0.67.71 [2,436 B]                
Get:12 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 coreutils amd64 8.25-2ubuntu3~16.04 [1,174 kB]                
Get:13 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 zlib1g-dev amd64 1:1.2.8.dfsg-2ubuntu4.1 [168 kB]              
Get:14 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 zlib1g i386 1:1.2.8.dfsg-2ubuntu4.1 [52.1 kB]                  
Get:15 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 zlib1g amd64 1:1.2.8.dfsg-2ubuntu4.1 [51.2 kB]                
Get:16 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libapt-pkg5.0 amd64 1.2.20 [707 kB]                            
Get:17 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libapt-inst2.0 amd64 1.2.20 [55.6 kB]                          
Get:18 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 apt amd64 1.2.20 [1,042 kB]                                    
Get:19 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 apt-utils amd64 1.2.20 [196 kB]                                
Get:20 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libpam-systemd amd64 229-4ubuntu17 [115 kB]                    
Get:21 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libudev1 amd64 229-4ubuntu17 [55.3 kB]                        
Get:22 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 libudev1 i386 229-4ubuntu17 [58.5 kB]                          
Get:23 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 udev amd64 229-4ubuntu17 [992 kB]                              
Get:24 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 libsystemd0 i386 229-4ubuntu17 [223 kB]                        
Get:25 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libsystemd0 amd64 229-4ubuntu17 [205 kB]                      
Get:26 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 systemd amd64 229-4ubuntu17 [3,623 kB]                        
Get:27 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 systemd-sysv amd64 229-4ubuntu17 [12.8 kB]                    
Get:28 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupsppdc1 amd64 2.1.3-4ubuntu0.2 [44.9 kB]                  
Get:29 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupsmime1 amd64 2.1.3-4ubuntu0.2 [13.1 kB]                  
Get:30 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupsimage2 amd64 2.1.3-4ubuntu0.2 [16.1 kB]                
Get:31 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupscgi1 amd64 2.1.3-4ubuntu0.2 [27.3 kB]                  
Get:32 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-browsed amd64 1.8.3-2ubuntu3.3 [94.1 kB]                  
Get:33 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-daemon amd64 2.1.3-4ubuntu0.2 [301 kB]                    
Get:34 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-core-drivers amd64 2.1.3-4ubuntu0.2 [27.3 kB]            
Get:35 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-filters-core-drivers amd64 1.8.3-2ubuntu3.3 [127 kB]      
Get:36 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-filters amd64 1.8.3-2ubuntu3.3 [448 kB]                  
Get:37 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-server-common all 2.1.3-4ubuntu0.2 [493 kB]              
Get:38 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups amd64 2.1.3-4ubuntu0.2 [192 kB]                          
Get:39 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-bsd amd64 2.1.3-4ubuntu0.2 [34.8 kB]                      
Get:40 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-client amd64 2.1.3-4ubuntu0.2 [133 kB]                    
Get:41 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 libcups2 i386 2.1.3-4ubuntu0.2 [212 kB]                        
Get:42 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcups2 amd64 2.1.3-4ubuntu0.2 [196 kB]                      
Get:43 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libcupsfilters1 amd64 1.8.3-2ubuntu3.3 [80.8 kB]              
Get:44 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libfontembed1 amd64 1.8.3-2ubuntu3.3 [47.5 kB]                
Get:45 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-common all 2.1.3-4ubuntu0.2 [134 kB]                      
Get:46 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 cups-ppdc amd64 2.1.3-4ubuntu0.2 [26.6 kB]                    
Get:47 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 language-pack-ar all 1:16.04+20161009 [66.1 kB]                
Get:48 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 language-pack-gnome-ar all 1:16.04+20161009 [260 kB]          
Get:49 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgtk2.0-common all 2.24.30-1ubuntu1.16.04.1 [123 kB]        
Get:50 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgtk2.0-bin amd64 2.24.30-1ubuntu1.16.04.1 [9,826 B]        
Get:51 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgail-common amd64 2.24.30-1ubuntu1.16.04.1 [111 kB]        
Get:52 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgail18 amd64 2.24.30-1ubuntu1.16.04.1 [14.2 kB]            
Get:53 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgtk2.0-0 amd64 2.24.30-1ubuntu1.16.04.1 [1,776 kB]          
Get:54 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libunity-gtk2-parser0 amd64 0.0.0+15.04.20150118-0ubuntu3 [25.0 kB]
Get:55 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libunity-gtk3-parser0 amd64 0.0.0+15.04.20150118-0ubuntu3 [24.6 kB]
Get:56 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-client-core-5.7 amd64 5.7.17-0ubuntu0.16.04.2 [6,516 kB]
Get:57 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-common all 5.7.17-0ubuntu0.16.04.2 [15.7 kB]            
Get:58 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-client-5.7 amd64 5.7.17-0ubuntu0.16.04.2 [1,666 kB]      
Get:59 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-server-5.7 amd64 5.7.17-0ubuntu0.16.04.2 [2,466 kB]      
Get:60 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-server-core-5.7 amd64 5.7.17-0ubuntu0.16.04.2 [7,564 kB]
Get:61 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-gtk-module-common all 0.0.0+15.04.20150118-0ubuntu3 [3,716 B]
Get:62 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-gtk2-module amd64 0.0.0+15.04.20150118-0ubuntu3 [8,752 B]
Get:63 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-gtk3-module amd64 0.0.0+15.04.20150118-0ubuntu3 [9,246 B]
Get:64 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 apt-transport-https amd64 1.2.20 [26.1 kB]                    
Get:65 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 pciutils amd64 1:3.3.1-1.1ubuntu1.1 [234 kB]                  
Get:66 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libpci3 amd64 1:3.3.1-1.1ubuntu1.1 [24.5 kB]                  
Get:67 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 wget amd64 1.17.1-1ubuntu1.2 [298 kB]                          
Get:68 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 binutils amd64 2.26.1-1ubuntu1~16.04.4 [2,311 kB]              
Get:69 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 ubuntu-software amd64 3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1 [11.7 kB]
Get:70 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 gnome-software amd64 3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1 [228 kB]
Get:71 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 gnome-software-common all 3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1 [2,257 kB]
Get:72 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main i386 libmysqlclient20 i386 5.7.17-0ubuntu0.16.04.2 [795 kB]          
Get:73 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libmysqlclient20 amd64 5.7.17-0ubuntu0.16.04.2 [811 kB]        
Get:74 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libnautilus-extension1a amd64 1:3.18.4.is.3.14.3-0ubuntu6 [53.7 kB]
Get:75 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libunity-control-center1 amd64 15.04.0+16.04.20170214-0ubuntu1 [81.1 kB]
Get:76 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-headers-4.4.0-67 all 4.4.0-67.88 [9,899 kB]              
Get:77 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-headers-4.4.0-67-generic amd64 4.4.0-67.88 [779 kB]      
Get:78 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-headers-generic amd64 4.4.0.67.71 [2,414 B]              
Get:79 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-libc-dev amd64 4.4.0-67.88 [839 kB]                      
Get:80 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-client all 5.7.17-0ubuntu0.16.04.2 [10.0 kB]            
Get:81 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 mysql-server all 5.7.17-0ubuntu0.16.04.2 [10.8 kB]            
Get:82 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 nautilus-data all 1:3.18.4.is.3.14.3-0ubuntu6 [48.1 kB]        
Get:83 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 nautilus amd64 1:3.18.4.is.3.14.3-0ubuntu6 [505 kB]            
Get:84 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 network-manager-openvpn-gnome amd64 1.1.93-1ubuntu1.1 [180 kB]
Get:85 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 network-manager-openvpn amd64 1.1.93-1ubuntu1.1 [26.5 kB]  
Get:86 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 software-properties-common all 0.96.20.6 [9,432 B]            
Get:87 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 software-properties-gtk all 0.96.20.6 [47.1 kB]                
Get:88 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 python3-software-properties all 0.96.20.6 [20.1 kB]            
Get:89 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 snap-confine amd64 2.23.1 [1,532 B]                            
Get:90 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 snapd amd64 2.23.1 [9,242 kB]                                  
Get:91 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unattended-upgrades all 0.90ubuntu0.4 [31.8 kB]                
Get:92 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-control-center amd64 15.04.0+16.04.20170214-0ubuntu1 [834 kB]
Get:93 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 unity-control-center-faces all 15.04.0+16.04.20170214-0ubuntu1 [180 kB]
Get:94 http://eg.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 vino amd64 3.8.1-0ubuntu9.2 [140 kB]                         
```
All those Packages are coming from the Proposed Repos...you should be understanding or getting an Idea now.
Very sorry if this sounds harsh...not trying to come across as such...but the facts are just the facts.
No no it's okay you don't have to be sorry, I can be pretty dumb sometimes :D

---

### Post by deadflowr on 2017-03-15
Personally, I'd run a clean then reload the updates, then try running the upgrade commands
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```
The clean command will flush out the package archives.
This should make sure any residual packages related to the problem proposed packages are gone.
Just for double measure.

---

### Post by #&amp;thj^% on 2017-03-15
> **deadflowr said:**
> Personally, I'd run a clean then reload the updates, then try running the upgrade commands
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```
The clean command will flush out the package archives.
This should make sure any residual packages related to the problem proposed packages are gone.
Just for double measure.

+1  And let us know how this goes.
We "might" still be able to clean up from Proposed.
Post back anything from the terminal so we know.

---

### Post by aboodyman on 2017-03-15
The **clean **and **update** went well, now I'm downloading the **dist-upgrade**. Personally I think the **dist-upgrade** will fail, if it does I'm going to give you guys the output. Anyway here's the **update **output:
```
Hit:1 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu xenial InRelease
Hit:2 http://eg.archive.ubuntu.com/ubuntu xenial InRelease          
Get:3 http://eg.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease          
Hit:5 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease
Ign:6 http://dl.google.com/linux/chrome/deb stable InRelease        
Ign:7 http://dl.google.com/linux/earth/deb stable InRelease         
Hit:8 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial InRelease
Ign:9 http://dl.google.com/linux/talkplugin/deb stable InRelease               
Hit:10 http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu xenial InRelease
Hit:11 http://ppa.launchpad.net/nickguletskii200/glxosd/ubuntu xenial InRelease
Hit:12 http://dl.google.com/linux/chrome/deb stable Release                    
Hit:13 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial InRelease  
Hit:14 http://dl.google.com/linux/earth/deb stable Release                     
Hit:15 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial InRelease
Hit:16 http://dl.google.com/linux/talkplugin/deb stable Release                
Get:17 http://eg.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Hit:18 http://ppa.launchpad.net/webupd8team/haguichi/ubuntu xenial InRelease   
Hit:19 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease       
Get:22 http://eg.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:24 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.1 kB]
Get:25 http://eg.archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [42.4 kB]
Get:26 http://eg.archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.1 kB]
Get:27 http://eg.archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:28 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [288 kB]
Hit:29 https://repo.skype.com/deb stable InRelease                             
Hit:30 http://repo.steampowered.com/steam precise InRelease                    
Get:31 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [186 kB]
Get:32 http://eg.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [159 kB]
Get:33 http://eg.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [180 kB]
Get:34 http://eg.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:35 http://eg.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Fetched 1,291 kB in 17s (75.4 kB/s)                                            
Reading package lists... Done
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:14 and /etc/apt/sources.list.d/xenial-partner.list:4

```There is still about 30mins left to go

---

### Post by aboodyman on 2017-03-15
Here's the output for **dist-upgrade:**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 251 MB/289 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-4.4.0-42-generic amd64 4.4.0-42.62 [18.8 MB]
Get:2 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-4.4.0-45-generic amd64 4.4.0-45.66 [18.8 MB]
Get:3 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-4.4.0-64-generic amd64 4.4.0-64.85 [21.8 MB]
Get:4 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-36-generic amd64 4.4.0-36.55 [39.0 MB]
Get:5 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-38-generic amd64 4.4.0-38.57 [39.0 MB]  
Get:6 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-42-generic amd64 4.4.0-42.62 [39.0 MB]  
Get:7 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-45-generic amd64 4.4.0-45.66 [39.0 MB]  
Get:8 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-64-generic amd64 4.4.0-64.85 [36.0 MB]  
Fetched 251 MB in 24min 18s (172 kB/s)  
Setting up grub-pc (2.02~beta2-36ubuntu3.8) ...
/var/lib/dpkg/info/grub-pc.config: 6: /etc/default/grub: 10: not found
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: error processing package linux-image-4.4.0-36-generic (--configure):
 package linux-image-4.4.0-36-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-38-generic (--configure):
 package linux-image-4.4.0-38-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-42-generic (--configure):
 package linux-image-4.4.0-42-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-45-generic (--configure):
 package linux-image-4.4.0-45-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-64-generic (--configure):
 package linux-image-4.4.0-64-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Setting up linux-image-4.4.0-No apport report written because MaxReports is reached already
                                                                                           No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
                                                                                 66-generic (4.4.0-66.87) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-66-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-66-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-4.4.0-67-generic (4.4.0-67.88) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-67-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-67-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-4.4.0-36-generic (--configure):
 package linux-image-extra-4.4.0-36-generic is not ready for configuration
 cannot configure (current status 'half-installed')
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-4.4.0-38-generic (--configure):
 package linux-image-extra-4.4.0-38-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--configure):
 package linux-image-extra-4.4.0-42-generic is not ready for configuration
 cannot configure (current status 'half-installed')
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing package linux-image-extra-4.4.0-45-generic (--configure):
 package linux-image-extra-4.4.0-45-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--configure):
 package linux-image-extra-4.4.0-64-generic is not ready for configuration
 cannot configure (current status 'half-installed')
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-66-generic:
 linux-image-extra-4.4.0-66-generic depends on linux-image-4.4.0-66-generic; however:
  Package linux-image-4.4.0-66-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-66-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-67-generic:
 linux-image-extra-4.4.0-67-generic depends on linux-image-4.4.0-67-generic; however:
  Package linux-image-4.4.0-67-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-67-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-67-generic; however:
  Package linux-image-4.4.0-67-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-67-generic; however:
  Package linux-image-extra-4.4.0-67-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 grub-pc
 linux-image-4.4.0-36-generic
 linux-image-4.4.0-38-generic
 linux-image-4.4.0-42-generic
 linux-image-4.4.0-45-generic
 linux-image-4.4.0-64-generic
 linux-image-4.4.0-66-generic
 linux-image-4.4.0-67-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-extra-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-extra-4.4.0-66-generic
 linux-image-extra-4.4.0-67-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by #&amp;thj^% on 2017-03-15
> **aboodyman said:**
> Here's the output for **dist-upgrade:**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 251 MB/289 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-4.4.0-42-generic amd64 4.4.0-42.62 [18.8 MB]
Get:2 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-4.4.0-45-generic amd64 4.4.0-45.66 [18.8 MB]
Get:3 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-4.4.0-64-generic amd64 4.4.0-64.85 [21.8 MB]
Get:4 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-36-generic amd64 4.4.0-36.55 [39.0 MB]
Get:5 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-38-generic amd64 4.4.0-38.57 [39.0 MB]  
Get:6 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-42-generic amd64 4.4.0-42.62 [39.0 MB]  
Get:7 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-45-generic amd64 4.4.0-45.66 [39.0 MB]  
Get:8 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-64-generic amd64 4.4.0-64.85 [36.0 MB]  
Fetched 251 MB in 24min 18s (172 kB/s)  
Setting up grub-pc (2.02~beta2-36ubuntu3.8) ...
/var/lib/dpkg/info/grub-pc.config: 6: /etc/default/grub: 10: not found
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: error processing package linux-image-4.4.0-36-generic (--configure):
 package linux-image-4.4.0-36-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-38-generic (--configure):
 package linux-image-4.4.0-38-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-42-generic (--configure):
 package linux-image-4.4.0-42-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-45-generic (--configure):
 package linux-image-4.4.0-45-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-64-generic (--configure):
 package linux-image-4.4.0-64-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Setting up linux-image-4.4.0-No apport report written because MaxReports is reached already
                                                                                           No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
                                                                                 66-generic (4.4.0-66.87) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-66-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-66-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-4.4.0-67-generic (4.4.0-67.88) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-67-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-67-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-4.4.0-36-generic (--configure):
 package linux-image-extra-4.4.0-36-generic is not ready for configuration
 cannot configure (current status 'half-installed')
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-4.4.0-38-generic (--configure):
 package linux-image-extra-4.4.0-38-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--configure):
 package linux-image-extra-4.4.0-42-generic is not ready for configuration
 cannot configure (current status 'half-installed')
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing package linux-image-extra-4.4.0-45-generic (--configure):
 package linux-image-extra-4.4.0-45-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--configure):
 package linux-image-extra-4.4.0-64-generic is not ready for configuration
 cannot configure (current status 'half-installed')
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-66-generic:
 linux-image-extra-4.4.0-66-generic depends on linux-image-4.4.0-66-generic; however:
  Package linux-image-4.4.0-66-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-66-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-67-generic:
 linux-image-extra-4.4.0-67-generic depends on linux-image-4.4.0-67-generic; however:
  Package linux-image-4.4.0-67-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-67-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-67-generic; however:
  Package linux-image-4.4.0-67-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-67-generic; however:
  Package linux-image-extra-4.4.0-67-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 grub-pc
 linux-image-4.4.0-36-generic
 linux-image-4.4.0-38-generic
 linux-image-4.4.0-42-generic
 linux-image-4.4.0-45-generic
 linux-image-4.4.0-64-generic
 linux-image-4.4.0-66-generic
 linux-image-4.4.0-67-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-extra-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-extra-4.4.0-66-generic
 linux-image-extra-4.4.0-67-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Well we thought there was a good chance of this...
Now to see if we can revert back we'll have to pin the packages from the Ubuntu repositories: for stable, updates, security and backports we'll use a priority greater than 1000 which will cause the packages from these repositories to be installed even if this constitutes a downgrade and for the proposed repository, we'll set a pin priority of less than 0 which prevents the packages from being installed.

To do this, create a file called "**99-downgrade-proposed**" under /etc/apt/preferences.d/ - I'll use Gedit below:

```
sudo -H gedit /etc/apt/preferences.d/99-downgrade-proposed
```


And in this file, paste the following:

```
Package: *
Pin: release a=xenial
Pin-Priority: 1001

Package: *
Pin: release a=xenial-updates
Pin-Priority: 1001

Package: *
Pin: release a=xenial-security
Pin-Priority: 1001

Package: *
Pin: release a=xenial-backports
Pin-Priority: 1001

Package: *
Pin: release a=xenial-proposed
Pin-Priority: -1

```

Then save the file.


3. Now you can start the downgrade by using the commands below:
```

sudo apt-get update
sudo apt-get dist-upgrade -s
```
         ^^^^ _**I added this "-s"**_ which will only run a simulation or dry run nothing will happen or be changed...but I would like to see the output from the terminal first before proceeding to the next steps. Pretty Please..

Make sure "dist-upgrade" doesn't remove any important packages. If everything looks ok, proceed with the downgrade. 

You'll have to keep in mind that it's possible to encounter "error processing packageX ... trying to overwrite fileX which is also in package Y" dpkg errors - see how to fix them HERE. :[http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html](http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html)

4. After downgrading, you can remove the file created under step 2:

```
sudo rm /etc/apt/preferences.d/99-downgrade-proposed
```

---

### Post by ian-weisser on 2017-03-15
> **aboodyman said:**
> 
Setting up grub-pc (2.02~beta2-36ubuntu3.8) ...
/var/lib/dpkg/info/grub-pc.config: 6: /etc/default/grub: 10: not found
dpkg: error processing package grub-pc (--configure):

Interesting. Again, the very first error seems to be a deleted file.

---

### Post by aboodyman on 2017-03-15
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libappstream3
Use 'sudo apt autoremove' to remove it.
The following NEW packages will be installed:
  autoconf automake autopoint dh-autoreconf libappstream4 libltdl-dev
  libstemmer0d libtool
The following packages will be upgraded:
  appstream debhelper libarchive13
The following packages will be DOWNGRADED:
  apt apt-transport-https apt-utils binutils coreutils cups cups-browsed
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ppdc cups-server-common language-pack-ar
  language-pack-gnome-ar libapt-inst2.0 libapt-pkg5.0 libcups2 libcups2:i386
  libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1
  libfontembed1 libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libmysqlclient20 libmysqlclient20:i386
  libnautilus-extension1a libpam-systemd libpci3 libsystemd0 libsystemd0:i386
  libudev1 libudev1:i386 libunity-control-center1 libunity-gtk2-parser0
  libunity-gtk3-parser0 mysql-client mysql-client-5.7 mysql-client-core-5.7
  mysql-common mysql-server mysql-server-5.7 mysql-server-core-5.7 nautilus
  nautilus-data pciutils python3-software-properties
  software-properties-common software-properties-gtk systemd systemd-sysv udev
  unattended-upgrades unity-control-center unity-control-center-faces
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module vino wget zlib1g
  zlib1g:i386 zlib1g-dev
3 upgraded, 8 newly installed, 72 downgraded, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Inst coreutils [8.25-2ubuntu3~16.04] (8.25-2ubuntu2 Ubuntu:16.04/xenial [amd64])
Conf coreutils (8.25-2ubuntu2 Ubuntu:16.04/xenial [amd64])
Inst zlib1g-dev [1:1.2.8.dfsg-2ubuntu4.1] (1:1.2.8.dfsg-2ubuntu4 Ubuntu:16.04/xenial [amd64]) []
Inst zlib1g [1:1.2.8.dfsg-2ubuntu4.1] (1:1.2.8.dfsg-2ubuntu4 Ubuntu:16.04/xenial [amd64]) [zlib1g:amd64 on zlib1g:i386] [zlib1g:i386 on zlib1g:amd64] [zlib1g:i386 ]
Inst zlib1g:i386 [1:1.2.8.dfsg-2ubuntu4.1] (1:1.2.8.dfsg-2ubuntu4 Ubuntu:16.04/xenial [i386])
Inst apt-utils [1.2.20] (1.2.19 Ubuntu:16.04/xenial-updates [amd64]) []
Inst apt [1.2.20] (1.2.19 Ubuntu:16.04/xenial-updates [amd64])
Conf apt (1.2.19 Ubuntu:16.04/xenial-updates [amd64])
Inst libapt-pkg5.0 [1.2.20] (1.2.19 Ubuntu:16.04/xenial-updates [amd64])
Conf zlib1g (1:1.2.8.dfsg-2ubuntu4 Ubuntu:16.04/xenial [amd64])
Conf zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4 Ubuntu:16.04/xenial [i386])
Conf libapt-pkg5.0 (1.2.19 Ubuntu:16.04/xenial-updates [amd64])
Inst libapt-inst2.0 [1.2.20] (1.2.19 Ubuntu:16.04/xenial-updates [amd64])
Inst libpam-systemd [229-4ubuntu17] (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64]) []
Inst libudev1:i386 [229-4ubuntu17] (229-4ubuntu16 Ubuntu:16.04/xenial-updates [i386]) [libudev1:amd64 on libudev1:i386] [libudev1:i386 on libudev1:amd64] [libudev1:amd64 ]
Inst libudev1 [229-4ubuntu17] (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64]) [udev:amd64 ]
Conf libudev1 (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64]) [udev:amd64 ]
Conf libudev1:i386 (229-4ubuntu16 Ubuntu:16.04/xenial-updates [i386]) [udev:amd64 ]
Inst udev [229-4ubuntu17] (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64]) []
Inst libsystemd0 [229-4ubuntu17] (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64]) [libsystemd0:amd64 on libsystemd0:i386] [libsystemd0:i386 on libsystemd0:amd64] [libsystemd0:i386 systemd:amd64 ]
Inst libsystemd0:i386 [229-4ubuntu17] (229-4ubuntu16 Ubuntu:16.04/xenial-updates [i386]) [systemd:amd64 ]
Inst systemd [229-4ubuntu17] (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64])
Conf libsystemd0 (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64])
Conf libsystemd0:i386 (229-4ubuntu16 Ubuntu:16.04/xenial-updates [i386])
Conf systemd (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64])
Inst systemd-sysv [229-4ubuntu17] (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64])
Conf systemd-sysv (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64])
Inst libcupscgi1 [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64]) []
Inst libcupsfilters1 [1.8.3-2ubuntu3.3] (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64]) []
Inst libcupsimage2 [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64]) []
Inst cups-browsed [1.8.3-2ubuntu3.3] (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64]) []
Inst cups-bsd [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64]) []
Inst cups-client [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64]) [cups:amd64 ]
Inst libcupsppdc1 [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64]) [cups:amd64 ]
Inst cups-core-drivers [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64]) [cups:amd64 ]
Inst cups-daemon [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64]) [cups:amd64 ]
Inst libcupsmime1 [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64]) [cups:amd64 ]
Inst libcups2 [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64]) [libcups2:amd64 on libcups2:i386] [libcups2:i386 on libcups2:amd64] [libcups2:i386 cups:amd64 ]
Inst libcups2:i386 [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [i386]) [cups:amd64 ]
Inst cups-server-common [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [all]) [cups:amd64 ]
Inst cups [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Inst cups-filters [1.8.3-2ubuntu3.3] (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64])
Inst cups-filters-core-drivers [1.8.3-2ubuntu3.3] (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64])
Inst libfontembed1 [1.8.3-2ubuntu3.3] (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64])
Inst cups-ppdc [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Inst cups-common [2.1.3-4ubuntu0.2] (2.1.3-4 Ubuntu:16.04/xenial [all])
Inst language-pack-ar [1:16.04+20161009] (1:16.04+20160627 Ubuntu:16.04/xenial-updates [all])
Inst language-pack-gnome-ar [1:16.04+20161009] (1:16.04+20160627 Ubuntu:16.04/xenial-updates [all])
Inst libstemmer0d (0+svn585-1 Ubuntu:16.04/xenial [amd64])
Inst libgtk2.0-common [2.24.30-1ubuntu1.16.04.1] (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [all])
Inst libgtk2.0-bin [2.24.30-1ubuntu1.16.04.1] (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64]) []
Inst libgail-common [2.24.30-1ubuntu1.16.04.1] (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64]) []
Inst libgail18 [2.24.30-1ubuntu1.16.04.1] (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64]) []
Inst libgtk2.0-0 [2.24.30-1ubuntu1.16.04.1] (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Inst unity-gtk3-module [0.0.0+15.04.20150118-0ubuntu3] (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [amd64])
Inst libunity-gtk3-parser0 [0.0.0+15.04.20150118-0ubuntu3] (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [amd64])
Inst unity-gtk2-module [0.0.0+15.04.20150118-0ubuntu3] (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [amd64])
Inst unity-gtk-module-common [0.0.0+15.04.20150118-0ubuntu3] (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [all])
Inst libunity-gtk2-parser0 [0.0.0+15.04.20150118-0ubuntu3] (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [amd64])
Inst mysql-client-core-5.7 [5.7.17-0ubuntu0.16.04.2] (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Inst mysql-common [5.7.17-0ubuntu0.16.04.2] (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [all])
Conf mysql-common (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [all])
Inst mysql-server-5.7 [5.7.17-0ubuntu0.16.04.2] (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64]) []
Inst mysql-client-5.7 [5.7.17-0ubuntu0.16.04.2] (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64]) []
Inst mysql-server-core-5.7 [5.7.17-0ubuntu0.16.04.2] (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Inst apt-transport-https [1.2.20] (1.2.19 Ubuntu:16.04/xenial-updates [amd64])
Inst pciutils [1:3.3.1-1.1ubuntu1.1] (1:3.3.1-1.1ubuntu1 Ubuntu:16.04/xenial [amd64]) []
Inst libpci3 [1:3.3.1-1.1ubuntu1.1] (1:3.3.1-1.1ubuntu1 Ubuntu:16.04/xenial [amd64])
Inst wget [1.17.1-1ubuntu1.2] (1.17.1-1ubuntu1.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Inst libappstream4 (0.10.6-1~ubuntu16.04.2 Ubuntu:16.04/xenial-backports [amd64])
Inst appstream [0.9.4-1ubuntu2] (0.10.6-1~ubuntu16.04.2 Ubuntu:16.04/xenial-backports [amd64])
Inst autoconf (2.69-9 Ubuntu:16.04/xenial [all])
Inst automake (1:1.15-4ubuntu1 Ubuntu:16.04/xenial [all])
Inst autopoint (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [all])
Inst binutils [2.26.1-1ubuntu1~16.04.4] (2.26.1-1ubuntu1~16.04.3 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Inst libtool (2.4.6-0.1 Ubuntu:16.04/xenial [all])
Inst dh-autoreconf (12~ubuntu16.04.1 Ubuntu:16.04/xenial-backports [all])
Inst debhelper [9.20160115ubuntu3] (10.2.2ubuntu1~ubuntu16.04.1 Ubuntu:16.04/xenial-backports [all])
Inst libarchive13 [3.1.2-11ubuntu0.16.04.3] (3.2.1-2~ubuntu16.04.1 Ubuntu:16.04/xenial-backports [amd64])
Inst libltdl-dev (2.4.6-0.1 Ubuntu:16.04/xenial [amd64])
Inst libmysqlclient20 [5.7.17-0ubuntu0.16.04.2] (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64]) [libmysqlclient20:amd64 on libmysqlclient20:i386] [libmysqlclient20:i386 on libmysqlclient20:amd64] [libmysqlclient20:i386 ]
Inst libmysqlclient20:i386 [5.7.17-0ubuntu0.16.04.2] (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [i386])
Inst libnautilus-extension1a [1:3.18.4.is.3.14.3-0ubuntu6] (1:3.18.4.is.3.14.3-0ubuntu5 Ubuntu:16.04/xenial-updates [amd64])
Inst libunity-control-center1 [15.04.0+16.04.20170214-0ubuntu1] (15.04.0+16.04.20160705-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Inst mysql-client [5.7.17-0ubuntu0.16.04.2] (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [all])
Inst mysql-server [5.7.17-0ubuntu0.16.04.2] (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [all])
Inst nautilus-data [1:3.18.4.is.3.14.3-0ubuntu6] (1:3.18.4.is.3.14.3-0ubuntu5 Ubuntu:16.04/xenial-updates [all])
Inst nautilus [1:3.18.4.is.3.14.3-0ubuntu6] (1:3.18.4.is.3.14.3-0ubuntu5 Ubuntu:16.04/xenial-updates [amd64])
Inst software-properties-common [0.96.20.6] (0.96.20.5 Ubuntu:16.04/xenial-updates [all]) []
Inst software-properties-gtk [0.96.20.6] (0.96.20.5 Ubuntu:16.04/xenial-updates [all]) []
Inst python3-software-properties [0.96.20.6] (0.96.20.5 Ubuntu:16.04/xenial-updates [all])
Inst unattended-upgrades [0.90ubuntu0.4] (0.90ubuntu0.3 Ubuntu:16.04/xenial-updates [all])
Inst unity-control-center [15.04.0+16.04.20170214-0ubuntu1] (15.04.0+16.04.20160705-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Inst unity-control-center-faces [15.04.0+16.04.20170214-0ubuntu1] (15.04.0+16.04.20160705-0ubuntu1 Ubuntu:16.04/xenial-updates [all])
Inst vino [3.8.1-0ubuntu9.2] (3.8.1-0ubuntu9.1 Ubuntu:16.04/xenial-updates [amd64])
Conf grub-pc (2.02~beta2-36ubuntu3.8 Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-36-generic (4.4.0-36.55 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-38-generic (4.4.0-38.57 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-42-generic (4.4.0-42.62 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-45-generic (4.4.0-45.66 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-64-generic (4.4.0-64.85 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-66-generic (4.4.0-66.87 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-67-generic (4.4.0-67.88 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-36-generic (4.4.0-36.55 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-38-generic (4.4.0-38.57 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-42-generic (4.4.0-42.62 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-45-generic (4.4.0-45.66 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-64-generic (4.4.0-64.85 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-66-generic (4.4.0-66.87 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-67-generic (4.4.0-67.88 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-generic (4.4.0.67.72 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf zlib1g-dev (1:1.2.8.dfsg-2ubuntu4 Ubuntu:16.04/xenial [amd64])
Conf libapt-inst2.0 (1.2.19 Ubuntu:16.04/xenial-updates [amd64])
Conf apt-utils (1.2.19 Ubuntu:16.04/xenial-updates [amd64])
Conf libpam-systemd (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64])
Conf udev (229-4ubuntu16 Ubuntu:16.04/xenial-updates [amd64])
Conf libcups2 (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf libcups2:i386 (2.1.3-4 Ubuntu:16.04/xenial [i386])
Conf libcupscgi1 (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf libcupsfilters1 (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64])
Conf libcupsimage2 (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf cups-browsed (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64])
Conf cups-common (2.1.3-4 Ubuntu:16.04/xenial [all])
Conf cups-client (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf cups-bsd (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf libcupsppdc1 (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf libcupsmime1 (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf cups-daemon (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf cups-filters-core-drivers (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64])
Conf cups-core-drivers (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf cups-server-common (2.1.3-4 Ubuntu:16.04/xenial [all])
Conf cups-ppdc (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf libfontembed1 (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64])
Conf cups-filters (1.8.3-2ubuntu3.1 Ubuntu:16.04/xenial-updates [amd64])
Conf cups (2.1.3-4 Ubuntu:16.04/xenial [amd64])
Conf language-pack-ar (1:16.04+20160627 Ubuntu:16.04/xenial-updates [all])
Conf language-pack-gnome-ar (1:16.04+20160627 Ubuntu:16.04/xenial-updates [all])
Conf libstemmer0d (0+svn585-1 Ubuntu:16.04/xenial [amd64])
Conf libgtk2.0-common (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [all])
Conf libgtk2.0-0 (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf libgtk2.0-bin (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf libgail18 (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf libgail-common (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf libunity-gtk3-parser0 (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [amd64])
Conf unity-gtk-module-common (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [all])
Conf unity-gtk3-module (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [amd64])
Conf libunity-gtk2-parser0 (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [amd64])
Conf unity-gtk2-module (0.0.0+15.04.20150118-0ubuntu2 Ubuntu:16.04/xenial [amd64])
Conf mysql-client-core-5.7 (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf mysql-client-5.7 (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf mysql-server-core-5.7 (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf mysql-server-5.7 (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf apt-transport-https (1.2.19 Ubuntu:16.04/xenial-updates [amd64])
Conf libpci3 (1:3.3.1-1.1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf pciutils (1:3.3.1-1.1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf wget (1.17.1-1ubuntu1.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf libappstream4 (0.10.6-1~ubuntu16.04.2 Ubuntu:16.04/xenial-backports [amd64])
Conf appstream (0.10.6-1~ubuntu16.04.2 Ubuntu:16.04/xenial-backports [amd64])
Conf autoconf (2.69-9 Ubuntu:16.04/xenial [all])
Conf automake (1:1.15-4ubuntu1 Ubuntu:16.04/xenial [all])
Conf autopoint (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [all])
Conf binutils (2.26.1-1ubuntu1~16.04.3 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf libtool (2.4.6-0.1 Ubuntu:16.04/xenial [all])
Conf dh-autoreconf (12~ubuntu16.04.1 Ubuntu:16.04/xenial-backports [all])
Conf debhelper (10.2.2ubuntu1~ubuntu16.04.1 Ubuntu:16.04/xenial-backports [all])
Conf libarchive13 (3.2.1-2~ubuntu16.04.1 Ubuntu:16.04/xenial-backports [amd64])
Conf libltdl-dev (2.4.6-0.1 Ubuntu:16.04/xenial [amd64])
Conf libmysqlclient20:i386 (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [i386])
Conf libmysqlclient20 (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf libnautilus-extension1a (1:3.18.4.is.3.14.3-0ubuntu5 Ubuntu:16.04/xenial-updates [amd64])
Conf libunity-control-center1 (15.04.0+16.04.20160705-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Conf mysql-client (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [all])
Conf mysql-server (5.7.17-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [all])
Conf nautilus-data (1:3.18.4.is.3.14.3-0ubuntu5 Ubuntu:16.04/xenial-updates [all])
Conf nautilus (1:3.18.4.is.3.14.3-0ubuntu5 Ubuntu:16.04/xenial-updates [amd64])
Conf python3-software-properties (0.96.20.5 Ubuntu:16.04/xenial-updates [all])
Conf software-properties-common (0.96.20.5 Ubuntu:16.04/xenial-updates [all])
Conf software-properties-gtk (0.96.20.5 Ubuntu:16.04/xenial-updates [all])
Conf unattended-upgrades (0.90ubuntu0.3 Ubuntu:16.04/xenial-updates [all])
Conf unity-control-center (15.04.0+16.04.20160705-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Conf unity-control-center-faces (15.04.0+16.04.20160705-0ubuntu1 Ubuntu:16.04/xenial-updates [all])
Conf vino (3.8.1-0ubuntu9.1 Ubuntu:16.04/xenial-updates [amd64])
```

---

### Post by #&amp;thj^% on 2017-03-15
Well it still looks like a crap shoot (Roll of Dice) to me!!!
But at this point...Let's go for it:
```
sudo apt-get dist-upgrade
```
Then we will see if we had any good luck due us.
**BTW: I am Assuming here, Now and forward..that you have back-ups in place, For a Possible diaster or mishap.**

---

### Post by aboodyman on 2017-03-15
Alrighty Let's do this, Wish me luck :P

---

### Post by aboodyman on 2017-03-15
I think I have the same problem with the same corrupt packages
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libappstream3
Use 'sudo apt autoremove' to remove it.
The following NEW packages will be installed:
  autoconf automake autopoint dh-autoreconf libappstream4 libltdl-dev
  libstemmer0d libtool
The following packages will be upgraded:
  appstream debhelper libarchive13
The following packages will be DOWNGRADED:
  apt apt-transport-https apt-utils binutils coreutils cups cups-browsed
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ppdc cups-server-common language-pack-ar
  language-pack-gnome-ar libapt-inst2.0 libapt-pkg5.0 libcups2 libcups2:i386
  libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1
  libfontembed1 libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libmysqlclient20 libmysqlclient20:i386
  libnautilus-extension1a libpam-systemd libpci3 libsystemd0 libsystemd0:i386
  libudev1 libudev1:i386 libunity-control-center1 libunity-gtk2-parser0
  libunity-gtk3-parser0 mysql-client mysql-client-5.7 mysql-client-core-5.7
  mysql-common mysql-server mysql-server-5.7 mysql-server-core-5.7 nautilus
  nautilus-data pciutils python3-software-properties
  software-properties-common software-properties-gtk systemd systemd-sysv udev
  unattended-upgrades unity-control-center unity-control-center-faces
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module vino wget zlib1g
  zlib1g:i386 zlib1g-dev
3 upgraded, 8 newly installed, 72 downgraded, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 41.7 MB/330 MB of archives.
After this operation, 5,800 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 coreutils amd64 8.25-2ubuntu2 [1,175 kB]
Get:2 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 zlib1g-dev amd64 1:1.2.8.dfsg-2ubuntu4 [168 kB]
Get:3 http://eg.archive.ubuntu.com/ubuntu xenial/main i386 zlib1g i386 1:1.2.8.dfsg-2ubuntu4 [52.2 kB]
Get:4 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 zlib1g amd64 1:1.2.8.dfsg-2ubuntu4 [51.3 kB]
Get:5 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt-utils amd64 1.2.19 [196 kB]
Get:6 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt amd64 1.2.19 [1,042 kB]
Get:7 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libapt-pkg5.0 amd64 1.2.19 [707 kB]
Get:8 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libapt-inst2.0 amd64 1.2.19 [55.8 kB]
Get:9 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libudev1 amd64 229-4ubuntu16 [55.2 kB]
Get:10 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main i386 libudev1 i386 229-4ubuntu16 [58.4 kB]
Get:11 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 udev amd64 229-4ubuntu16 [992 kB]
Get:12 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpam-systemd amd64 229-4ubuntu16 [115 kB]
Get:13 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main i386 libsystemd0 i386 229-4ubuntu16 [223 kB]
Get:14 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libsystemd0 amd64 229-4ubuntu16 [205 kB]
Get:15 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 systemd amd64 229-4ubuntu16 [3,756 kB]
Get:16 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 systemd-sysv amd64 229-4ubuntu16 [12.7 kB]
Get:17 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libcupscgi1 amd64 2.1.3-4 [27.2 kB]
Get:18 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 cups-core-drivers amd64 2.1.3-4 [27.2 kB]
Get:19 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cups-browsed amd64 1.8.3-2ubuntu3.1 [92.7 kB]
Get:20 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cups-filters amd64 1.8.3-2ubuntu3.1 [448 kB]
Get:21 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cups-filters-core-drivers amd64 1.8.3-2ubuntu3.1 [127 kB]
Get:22 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 cups-daemon amd64 2.1.3-4 [301 kB]
Get:23 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libcupsmime1 amd64 2.1.3-4 [13.1 kB]
Get:24 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 cups-server-common all 2.1.3-4 [493 kB]
Get:25 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 cups amd64 2.1.3-4 [192 kB]
Get:26 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 cups-bsd amd64 2.1.3-4 [34.8 kB]
Get:27 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 cups-client amd64 2.1.3-4 [133 kB]
Get:28 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libcupsimage2 amd64 2.1.3-4 [16.1 kB]
Get:29 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libcupsppdc1 amd64 2.1.3-4 [44.9 kB]
Get:30 http://eg.archive.ubuntu.com/ubuntu xenial/main i386 libcups2 i386 2.1.3-4 [213 kB]
Get:31 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libcups2 amd64 2.1.3-4 [197 kB]
Get:32 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcupsfilters1 amd64 1.8.3-2ubuntu3.1 [80.4 kB]
Get:33 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libfontembed1 amd64 1.8.3-2ubuntu3.1 [47.1 kB]
Get:34 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 cups-ppdc amd64 2.1.3-4 [26.6 kB]
Get:35 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 cups-common all 2.1.3-4 [134 kB]
Get:36 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 language-pack-ar all 1:16.04+20160627 [1,818 B]
Get:37 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 language-pack-gnome-ar all 1:16.04+20160627 [1,846 B]
Get:38 http://eg.archive.ubuntu.com/ubuntu xenial/universe amd64 libstemmer0d amd64 0+svn585-1 [62.1 kB]
Get:39 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libgail-common amd64 2.24.30-1ubuntu1 [111 kB]
Get:40 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libgail18 amd64 2.24.30-1ubuntu1 [14.2 kB]
Get:41 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libgtk2.0-common all 2.24.30-1ubuntu1 [123 kB]
Get:42 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libgtk2.0-bin amd64 2.24.30-1ubuntu1 [9,820 B]
Get:43 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libgtk2.0-0 amd64 2.24.30-1ubuntu1 [1,777 kB]
Get:44 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 unity-gtk3-module amd64 0.0.0+15.04.20150118-0ubuntu2 [9,244 B]
Get:45 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libunity-gtk3-parser0 amd64 0.0.0+15.04.20150118-0ubuntu2 [25.1 kB]
Get:46 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 unity-gtk2-module amd64 0.0.0+15.04.20150118-0ubuntu2 [8,754 B]
Get:47 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 unity-gtk-module-common all 0.0.0+15.04.20150118-0ubuntu2 [4,170 B]
Get:48 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libunity-gtk2-parser0 amd64 0.0.0+15.04.20150118-0ubuntu2 [25.6 kB]
Get:49 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 mysql-client-core-5.7 amd64 5.7.17-0ubuntu0.16.04.1 [6,325 kB]
Get:50 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 mysql-common all 5.7.17-0ubuntu0.16.04.1 [15.1 kB]
Get:51 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 mysql-server-5.7 amd64 5.7.17-0ubuntu0.16.04.1 [2,856 kB]
Get:52 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 mysql-client-5.7 amd64 5.7.17-0ubuntu0.16.04.1 [1,762 kB]
Get:53 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 mysql-server-core-5.7 amd64 5.7.17-0ubuntu0.16.04.1 [7,728 kB]
Get:54 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt-transport-https amd64 1.2.19 [26.0 kB]
Get:55 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 pciutils amd64 1:3.3.1-1.1ubuntu1 [234 kB]
Get:56 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libpci3 amd64 1:3.3.1-1.1ubuntu1 [24.3 kB]
Get:57 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 wget amd64 1.17.1-1ubuntu1.1 [298 kB]
Get:58 http://eg.archive.ubuntu.com/ubuntu xenial-backports/main amd64 libappstream4 amd64 0.10.6-1~ubuntu16.04.2 [87.2 kB]
Get:59 http://eg.archive.ubuntu.com/ubuntu xenial-backports/main amd64 appstream amd64 0.10.6-1~ubuntu16.04.2 [97.0 kB]
Get:60 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 autoconf all 2.69-9 [321 kB]
Get:61 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 automake all 1:1.15-4ubuntu1 [510 kB]
Get:62 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 autopoint all 0.19.7-2ubuntu3 [406 kB]
Get:63 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 binutils amd64 2.26.1-1ubuntu1~16.04.3 [2,310 kB]
Get:64 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libtool all 2.4.6-0.1 [193 kB]
Get:65 http://eg.archive.ubuntu.com/ubuntu xenial-backports/main amd64 dh-autoreconf all 12~ubuntu16.04.1 [15.7 kB]
Get:66 http://eg.archive.ubuntu.com/ubuntu xenial-backports/main amd64 debhelper all 10.2.2ubuntu1~ubuntu16.04.1 [743 kB]
Get:67 http://eg.archive.ubuntu.com/ubuntu xenial-backports/main amd64 libarchive13 amd64 3.2.1-2~ubuntu16.04.1 [283 kB]
Get:68 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 libltdl-dev amd64 2.4.6-0.1 [162 kB]
Get:69 http://eg.archive.ubuntu.com/ubuntu xenial-security/main i386 libmysqlclient20 i386 5.7.17-0ubuntu0.16.04.1 [794 kB]
Get:70 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 libmysqlclient20 amd64 5.7.17-0ubuntu0.16.04.1 [809 kB]
Get:71 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnautilus-extension1a amd64 1:3.18.4.is.3.14.3-0ubuntu5 [53.8 kB]
Get:72 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libunity-control-center1 amd64 15.04.0+16.04.20160705-0ubuntu1 [81.0 kB]
Get:73 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 mysql-client all 5.7.17-0ubuntu0.16.04.1 [10.0 kB]
Get:74 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 mysql-server all 5.7.17-0ubuntu0.16.04.1 [10.1 kB]
Get:75 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 nautilus-data all 1:3.18.4.is.3.14.3-0ubuntu5 [48.1 kB]
Get:76 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 nautilus amd64 1:3.18.4.is.3.14.3-0ubuntu5 [504 kB]
Get:77 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 software-properties-common all 0.96.20.5 [9,432 B]
Get:78 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 software-properties-gtk all 0.96.20.5 [47.2 kB]
Get:79 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3-software-properties all 0.96.20.5 [19.9 kB]
Get:80 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unattended-upgrades all 0.90ubuntu0.3 [31.7 kB]
Get:81 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unity-control-center amd64 15.04.0+16.04.20160705-0ubuntu1 [835 kB]
Get:82 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unity-control-center-faces all 15.04.0+16.04.20160705-0ubuntu1 [180 kB]
Get:83 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 vino amd64 3.8.1-0ubuntu9.1 [141 kB]
Fetched 41.7 MB in 4min 9s (167 kB/s)                                          
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: downgrading coreutils from 8.25-2ubuntu3~16.04 to 8.25-2ubuntu2
(Reading database ... 318362 files and directories currently installed.)
Preparing to unpack .../coreutils_8.25-2ubuntu2_amd64.deb ...
Unpacking coreutils (8.25-2ubuntu2) over (8.25-2ubuntu3~16.04) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up coreutils (8.25-2ubuntu2) ...
dpkg: warning: downgrading zlib1g-dev:amd64 from 1:1.2.8.dfsg-2ubuntu4.1 to 1:1.2.8.dfsg-2ubuntu4
(Reading database ... 318362 files and directories currently installed.)
Preparing to unpack .../zlib1g-dev_1%3a1.2.8.dfsg-2ubuntu4_amd64.deb ...
Unpacking zlib1g-dev:amd64 (1:1.2.8.dfsg-2ubuntu4) over (1:1.2.8.dfsg-2ubuntu4.1) ...
dpkg: warning: downgrading zlib1g:amd64 from 1:1.2.8.dfsg-2ubuntu4.1 to 1:1.2.8.dfsg-2ubuntu4
Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4_amd64.deb ...
De-configuring zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4.1) ...
Unpacking zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4) over (1:1.2.8.dfsg-2ubuntu4.1) ...
dpkg: warning: downgrading zlib1g:i386 from 1:1.2.8.dfsg-2ubuntu4.1 to 1:1.2.8.dfsg-2ubuntu4
Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4_i386.deb ...
Unpacking zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4) over (1:1.2.8.dfsg-2ubuntu4.1) ...
dpkg: warning: downgrading apt-utils from 1.2.20 to 1.2.19
Preparing to unpack .../apt-utils_1.2.19_amd64.deb ...
Unpacking apt-utils (1.2.19) over (1.2.20) ...
dpkg: warning: downgrading apt from 1.2.20 to 1.2.19
Preparing to unpack .../archives/apt_1.2.19_amd64.deb ...
Unpacking apt (1.2.19) over (1.2.20) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up apt (1.2.19) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
dpkg: warning: downgrading libapt-pkg5.0:amd64 from 1.2.20 to 1.2.19
(Reading database ... 318362 files and directories currently installed.)
Preparing to unpack .../libapt-pkg5.0_1.2.19_amd64.deb ...
Unpacking libapt-pkg5.0:amd64 (1.2.19) over (1.2.20) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4) ...
Setting up zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4) ...
Setting up libapt-pkg5.0:amd64 (1.2.19) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
dpkg: warning: downgrading libapt-inst2.0:amd64 from 1.2.20 to 1.2.19
(Reading database ... 318362 files and directories currently installed.)
Preparing to unpack .../libapt-inst2.0_1.2.19_amd64.deb ...
Unpacking libapt-inst2.0:amd64 (1.2.19) over (1.2.20) ...
dpkg: warning: downgrading libudev1:i386 from 229-4ubuntu17 to 229-4ubuntu16
Preparing to unpack .../libudev1_229-4ubuntu16_i386.deb ...
De-configuring libudev1:amd64 (229-4ubuntu17) ...
Unpacking libudev1:i386 (229-4ubuntu16) over (229-4ubuntu17) ...
dpkg: warning: downgrading libudev1:amd64 from 229-4ubuntu17 to 229-4ubuntu16
Preparing to unpack .../libudev1_229-4ubuntu16_amd64.deb ...
Unpacking libudev1:amd64 (229-4ubuntu16) over (229-4ubuntu17) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up libudev1:amd64 (229-4ubuntu16) ...
Setting up libudev1:i386 (229-4ubuntu16) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
dpkg: warning: downgrading udev from 229-4ubuntu17 to 229-4ubuntu16
(Reading database ... 318362 files and directories currently installed.)
Preparing to unpack .../udev_229-4ubuntu16_amd64.deb ...
Unpacking udev (229-4ubuntu16) over (229-4ubuntu17) ...
dpkg: warning: downgrading libpam-systemd:amd64 from 229-4ubuntu17 to 229-4ubuntu16
Preparing to unpack .../libpam-systemd_229-4ubuntu16_amd64.deb ...
Unpacking libpam-systemd:amd64 (229-4ubuntu16) over (229-4ubuntu17) ...
dpkg: warning: downgrading libsystemd0:amd64 from 229-4ubuntu17 to 229-4ubuntu16
Preparing to unpack .../libsystemd0_229-4ubuntu16_amd64.deb ...
De-configuring libsystemd0:i386 (229-4ubuntu17) ...
Unpacking libsystemd0:amd64 (229-4ubuntu16) over (229-4ubuntu17) ...
dpkg: warning: downgrading libsystemd0:i386 from 229-4ubuntu17 to 229-4ubuntu16
Preparing to unpack .../libsystemd0_229-4ubuntu16_i386.deb ...
Unpacking libsystemd0:i386 (229-4ubuntu16) over (229-4ubuntu17) ...
dpkg: warning: downgrading systemd from 229-4ubuntu17 to 229-4ubuntu16
Preparing to unpack .../systemd_229-4ubuntu16_amd64.deb ...
Unpacking systemd (229-4ubuntu16) over (229-4ubuntu17) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up libsystemd0:amd64 (229-4ubuntu16) ...
Setting up libsystemd0:i386 (229-4ubuntu16) ...
Setting up systemd (229-4ubuntu16) ...
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
dpkg: warning: downgrading systemd-sysv from 229-4ubuntu17 to 229-4ubuntu16
(Reading database ... 318362 files and directories currently installed.)
Preparing to unpack .../systemd-sysv_229-4ubuntu16_amd64.deb ...
Unpacking systemd-sysv (229-4ubuntu16) over (229-4ubuntu17) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up systemd-sysv (229-4ubuntu16) ...
dpkg: warning: downgrading libcupscgi1:amd64 from 2.1.3-4ubuntu0.2 to 2.1.3-4
(Reading database ... 318362 files and directories currently installed.)
Preparing to unpack .../libcupscgi1_2.1.3-4_amd64.deb ...
Unpacking libcupscgi1:amd64 (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading cups-core-drivers from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../cups-core-drivers_2.1.3-4_amd64.deb ...
Unpacking cups-core-drivers (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading cups-browsed from 1.8.3-2ubuntu3.3 to 1.8.3-2ubuntu3.1
Preparing to unpack .../cups-browsed_1.8.3-2ubuntu3.1_amd64.deb ...
Unpacking cups-browsed (1.8.3-2ubuntu3.1) over (1.8.3-2ubuntu3.3) ...
dpkg: warning: downgrading cups-filters from 1.8.3-2ubuntu3.3 to 1.8.3-2ubuntu3.1
Preparing to unpack .../cups-filters_1.8.3-2ubuntu3.1_amd64.deb ...
Unpacking cups-filters (1.8.3-2ubuntu3.1) over (1.8.3-2ubuntu3.3) ...
dpkg: warning: downgrading cups-filters-core-drivers from 1.8.3-2ubuntu3.3 to 1.8.3-2ubuntu3.1
Preparing to unpack .../cups-filters-core-drivers_1.8.3-2ubuntu3.1_amd64.deb ...
Unpacking cups-filters-core-drivers (1.8.3-2ubuntu3.1) over (1.8.3-2ubuntu3.3) ...
dpkg: warning: downgrading cups-daemon from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../cups-daemon_2.1.3-4_amd64.deb ...
Warning: Stopping cups.service, but it can still be activated by:
  cups.socket
Unpacking cups-daemon (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading libcupsmime1:amd64 from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../libcupsmime1_2.1.3-4_amd64.deb ...
Unpacking libcupsmime1:amd64 (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading cups-server-common from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../cups-server-common_2.1.3-4_all.deb ...
Unpacking cups-server-common (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading cups from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../cups_2.1.3-4_amd64.deb ...
Unpacking cups (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading cups-bsd from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../cups-bsd_2.1.3-4_amd64.deb ...
Unpacking cups-bsd (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading cups-client from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../cups-client_2.1.3-4_amd64.deb ...
Unpacking cups-client (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading libcupsimage2:amd64 from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../libcupsimage2_2.1.3-4_amd64.deb ...
Unpacking libcupsimage2:amd64 (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading libcupsppdc1:amd64 from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../libcupsppdc1_2.1.3-4_amd64.deb ...
Unpacking libcupsppdc1:amd64 (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading libcups2:amd64 from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../libcups2_2.1.3-4_amd64.deb ...
De-configuring libcups2:i386 (2.1.3-4ubuntu0.2) ...
Unpacking libcups2:amd64 (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading libcups2:i386 from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../libcups2_2.1.3-4_i386.deb ...
Unpacking libcups2:i386 (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading libcupsfilters1:amd64 from 1.8.3-2ubuntu3.3 to 1.8.3-2ubuntu3.1
Preparing to unpack .../libcupsfilters1_1.8.3-2ubuntu3.1_amd64.deb ...
Unpacking libcupsfilters1:amd64 (1.8.3-2ubuntu3.1) over (1.8.3-2ubuntu3.3) ...
dpkg: warning: downgrading libfontembed1:amd64 from 1.8.3-2ubuntu3.3 to 1.8.3-2ubuntu3.1
Preparing to unpack .../libfontembed1_1.8.3-2ubuntu3.1_amd64.deb ...
Unpacking libfontembed1:amd64 (1.8.3-2ubuntu3.1) over (1.8.3-2ubuntu3.3) ...
dpkg: warning: downgrading cups-ppdc from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../cups-ppdc_2.1.3-4_amd64.deb ...
Unpacking cups-ppdc (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading cups-common from 2.1.3-4ubuntu0.2 to 2.1.3-4
Preparing to unpack .../cups-common_2.1.3-4_all.deb ...
Unpacking cups-common (2.1.3-4) over (2.1.3-4ubuntu0.2) ...
dpkg: warning: downgrading language-pack-ar from 1:16.04+20161009 to 1:16.04+20160627
Preparing to unpack .../language-pack-ar_1%3a16.04+20160627_all.deb ...
Unpacking language-pack-ar (1:16.04+20160627) over (1:16.04+20161009) ...
dpkg: warning: downgrading language-pack-gnome-ar from 1:16.04+20161009 to 1:16.04+20160627
Preparing to unpack .../language-pack-gnome-ar_1%3a16.04+20160627_all.deb ...
Unpacking language-pack-gnome-ar (1:16.04+20160627) over (1:16.04+20161009) ...
Selecting previously unselected package libstemmer0d:amd64.
Preparing to unpack .../libstemmer0d_0+svn585-1_amd64.deb ...
Unpacking libstemmer0d:amd64 (0+svn585-1) ...
dpkg: warning: downgrading libgail-common:amd64 from 2.24.30-1ubuntu1.16.04.1 to 2.24.30-1ubuntu1
Preparing to unpack .../libgail-common_2.24.30-1ubuntu1_amd64.deb ...
Unpacking libgail-common:amd64 (2.24.30-1ubuntu1) over (2.24.30-1ubuntu1.16.04.1) ...
dpkg: warning: downgrading libgail18:amd64 from 2.24.30-1ubuntu1.16.04.1 to 2.24.30-1ubuntu1
Preparing to unpack .../libgail18_2.24.30-1ubuntu1_amd64.deb ...
Unpacking libgail18:amd64 (2.24.30-1ubuntu1) over (2.24.30-1ubuntu1.16.04.1) ...
dpkg: warning: downgrading libgtk2.0-common from 2.24.30-1ubuntu1.16.04.1 to 2.24.30-1ubuntu1
Preparing to unpack .../libgtk2.0-common_2.24.30-1ubuntu1_all.deb ...
Unpacking libgtk2.0-common (2.24.30-1ubuntu1) over (2.24.30-1ubuntu1.16.04.1) ...
dpkg: warning: downgrading libgtk2.0-bin from 2.24.30-1ubuntu1.16.04.1 to 2.24.30-1ubuntu1
Preparing to unpack .../libgtk2.0-bin_2.24.30-1ubuntu1_amd64.deb ...
Unpacking libgtk2.0-bin (2.24.30-1ubuntu1) over (2.24.30-1ubuntu1.16.04.1) ...
dpkg: warning: downgrading libgtk2.0-0:amd64 from 2.24.30-1ubuntu1.16.04.1 to 2.24.30-1ubuntu1
Preparing to unpack .../libgtk2.0-0_2.24.30-1ubuntu1_amd64.deb ...
Unpacking libgtk2.0-0:amd64 (2.24.30-1ubuntu1) over (2.24.30-1ubuntu1.16.04.1) ...
dpkg: warning: downgrading unity-gtk3-module:amd64 from 0.0.0+15.04.20150118-0ubuntu3 to 0.0.0+15.04.20150118-0ubuntu2
Preparing to unpack .../unity-gtk3-module_0.0.0+15.04.20150118-0ubuntu2_amd64.deb ...
Unpacking unity-gtk3-module:amd64 (0.0.0+15.04.20150118-0ubuntu2) over (0.0.0+15.04.20150118-0ubuntu3) ...
dpkg: warning: downgrading libunity-gtk3-parser0:amd64 from 0.0.0+15.04.20150118-0ubuntu3 to 0.0.0+15.04.20150118-0ubuntu2
Preparing to unpack .../libunity-gtk3-parser0_0.0.0+15.04.20150118-0ubuntu2_amd64.deb ...
Unpacking libunity-gtk3-parser0:amd64 (0.0.0+15.04.20150118-0ubuntu2) over (0.0.0+15.04.20150118-0ubuntu3) ...
dpkg: warning: downgrading unity-gtk2-module:amd64 from 0.0.0+15.04.20150118-0ubuntu3 to 0.0.0+15.04.20150118-0ubuntu2
Preparing to unpack .../unity-gtk2-module_0.0.0+15.04.20150118-0ubuntu2_amd64.deb ...
Unpacking unity-gtk2-module:amd64 (0.0.0+15.04.20150118-0ubuntu2) over (0.0.0+15.04.20150118-0ubuntu3) ...
dpkg: warning: downgrading unity-gtk-module-common from 0.0.0+15.04.20150118-0ubuntu3 to 0.0.0+15.04.20150118-0ubuntu2
Preparing to unpack .../unity-gtk-module-common_0.0.0+15.04.20150118-0ubuntu2_all.deb ...
Unpacking unity-gtk-module-common (0.0.0+15.04.20150118-0ubuntu2) over (0.0.0+15.04.20150118-0ubuntu3) ...
dpkg: warning: downgrading libunity-gtk2-parser0:amd64 from 0.0.0+15.04.20150118-0ubuntu3 to 0.0.0+15.04.20150118-0ubuntu2
Preparing to unpack .../libunity-gtk2-parser0_0.0.0+15.04.20150118-0ubuntu2_amd64.deb ...
Unpacking libunity-gtk2-parser0:amd64 (0.0.0+15.04.20150118-0ubuntu2) over (0.0.0+15.04.20150118-0ubuntu3) ...
dpkg: warning: downgrading mysql-client-core-5.7 from 5.7.17-0ubuntu0.16.04.2 to 5.7.17-0ubuntu0.16.04.1
Preparing to unpack .../mysql-client-core-5.7_5.7.17-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-client-core-5.7 (5.7.17-0ubuntu0.16.04.1) over (5.7.17-0ubuntu0.16.04.2) ...
dpkg: warning: downgrading mysql-common from 5.7.17-0ubuntu0.16.04.2 to 5.7.17-0ubuntu0.16.04.1
Preparing to unpack .../mysql-common_5.7.17-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-common (5.7.17-0ubuntu0.16.04.1) over (5.7.17-0ubuntu0.16.04.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for systemd (229-4ubuntu16) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Processing triggers for doc-base (0.10.7) ...
Processing 1 changed doc-base file...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Setting up mysql-common (5.7.17-0ubuntu0.16.04.1) ...
dpkg: warning: downgrading mysql-server-5.7 from 5.7.17-0ubuntu0.16.04.2 to 5.7.17-0ubuntu0.16.04.1
(Reading database ... 318324 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.17-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-server-5.7 (5.7.17-0ubuntu0.16.04.1) over (5.7.17-0ubuntu0.16.04.2) ...
dpkg: warning: downgrading mysql-client-5.7 from 5.7.17-0ubuntu0.16.04.2 to 5.7.17-0ubuntu0.16.04.1
Preparing to unpack .../mysql-client-5.7_5.7.17-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-client-5.7 (5.7.17-0ubuntu0.16.04.1) over (5.7.17-0ubuntu0.16.04.2) ...
dpkg: warning: downgrading mysql-server-core-5.7 from 5.7.17-0ubuntu0.16.04.2 to 5.7.17-0ubuntu0.16.04.1
Preparing to unpack .../mysql-server-core-5.7_5.7.17-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-server-core-5.7 (5.7.17-0ubuntu0.16.04.1) over (5.7.17-0ubuntu0.16.04.2) ...
dpkg: warning: downgrading apt-transport-https from 1.2.20 to 1.2.19
Preparing to unpack .../apt-transport-https_1.2.19_amd64.deb ...
Unpacking apt-transport-https (1.2.19) over (1.2.20) ...
dpkg: warning: downgrading pciutils from 1:3.3.1-1.1ubuntu1.1 to 1:3.3.1-1.1ubuntu1
Preparing to unpack .../pciutils_1%3a3.3.1-1.1ubuntu1_amd64.deb ...
Unpacking pciutils (1:3.3.1-1.1ubuntu1) over (1:3.3.1-1.1ubuntu1.1) ...
dpkg: warning: downgrading libpci3:amd64 from 1:3.3.1-1.1ubuntu1.1 to 1:3.3.1-1.1ubuntu1
Preparing to unpack .../libpci3_1%3a3.3.1-1.1ubuntu1_amd64.deb ...
Unpacking libpci3:amd64 (1:3.3.1-1.1ubuntu1) over (1:3.3.1-1.1ubuntu1.1) ...
dpkg: warning: downgrading wget from 1.17.1-1ubuntu1.2 to 1.17.1-1ubuntu1.1
Preparing to unpack .../wget_1.17.1-1ubuntu1.1_amd64.deb ...
Unpacking wget (1.17.1-1ubuntu1.1) over (1.17.1-1ubuntu1.2) ...
Selecting previously unselected package libappstream4:amd64.
Preparing to unpack .../libappstream4_0.10.6-1~ubuntu16.04.2_amd64.deb ...
Unpacking libappstream4:amd64 (0.10.6-1~ubuntu16.04.2) ...
Preparing to unpack .../appstream_0.10.6-1~ubuntu16.04.2_amd64.deb ...
Unpacking appstream (0.10.6-1~ubuntu16.04.2) over (0.9.4-1ubuntu2) ...
Selecting previously unselected package autoconf.
Preparing to unpack .../autoconf_2.69-9_all.deb ...
Unpacking autoconf (2.69-9) ...
Selecting previously unselected package automake.
Preparing to unpack .../automake_1%3a1.15-4ubuntu1_all.deb ...
Unpacking automake (1:1.15-4ubuntu1) ...
Selecting previously unselected package autopoint.
Preparing to unpack .../autopoint_0.19.7-2ubuntu3_all.deb ...
Unpacking autopoint (0.19.7-2ubuntu3) ...
dpkg: warning: downgrading binutils from 2.26.1-1ubuntu1~16.04.4 to 2.26.1-1ubuntu1~16.04.3
Preparing to unpack .../binutils_2.26.1-1ubuntu1~16.04.3_amd64.deb ...
Unpacking binutils (2.26.1-1ubuntu1~16.04.3) over (2.26.1-1ubuntu1~16.04.4) ...
Selecting previously unselected package libtool.
Preparing to unpack .../libtool_2.4.6-0.1_all.deb ...
Unpacking libtool (2.4.6-0.1) ...
Selecting previously unselected package dh-autoreconf.
Preparing to unpack .../dh-autoreconf_12~ubuntu16.04.1_all.deb ...
Unpacking dh-autoreconf (12~ubuntu16.04.1) ...
Preparing to unpack .../debhelper_10.2.2ubuntu1~ubuntu16.04.1_all.deb ...
Unpacking debhelper (10.2.2ubuntu1~ubuntu16.04.1) over (9.20160115ubuntu3) ...
Preparing to unpack .../libarchive13_3.2.1-2~ubuntu16.04.1_amd64.deb ...
Unpacking libarchive13:amd64 (3.2.1-2~ubuntu16.04.1) over (3.1.2-11ubuntu0.16.04.3) ...
Selecting previously unselected package libltdl-dev:amd64.
Preparing to unpack .../libltdl-dev_2.4.6-0.1_amd64.deb ...
Unpacking libltdl-dev:amd64 (2.4.6-0.1) ...
dpkg: warning: downgrading libmysqlclient20:amd64 from 5.7.17-0ubuntu0.16.04.2 to 5.7.17-0ubuntu0.16.04.1
Preparing to unpack .../libmysqlclient20_5.7.17-0ubuntu0.16.04.1_amd64.deb ...
De-configuring libmysqlclient20:i386 (5.7.17-0ubuntu0.16.04.2) ...
Unpacking libmysqlclient20:amd64 (5.7.17-0ubuntu0.16.04.1) over (5.7.17-0ubuntu0.16.04.2) ...
dpkg: warning: downgrading libmysqlclient20:i386 from 5.7.17-0ubuntu0.16.04.2 to 5.7.17-0ubuntu0.16.04.1
Preparing to unpack .../libmysqlclient20_5.7.17-0ubuntu0.16.04.1_i386.deb ...
Unpacking libmysqlclient20:i386 (5.7.17-0ubuntu0.16.04.1) over (5.7.17-0ubuntu0.16.04.2) ...
dpkg: warning: downgrading libnautilus-extension1a:amd64 from 1:3.18.4.is.3.14.3-0ubuntu6 to 1:3.18.4.is.3.14.3-0ubuntu5
Preparing to unpack .../libnautilus-extension1a_1%3a3.18.4.is.3.14.3-0ubuntu5_amd64.deb ...
Unpacking libnautilus-extension1a:amd64 (1:3.18.4.is.3.14.3-0ubuntu5) over (1:3.18.4.is.3.14.3-0ubuntu6) ...
dpkg: warning: downgrading libunity-control-center1 from 15.04.0+16.04.20170214-0ubuntu1 to 15.04.0+16.04.20160705-0ubuntu1
Preparing to unpack .../libunity-control-center1_15.04.0+16.04.20160705-0ubuntu1_amd64.deb ...
Unpacking libunity-control-center1 (15.04.0+16.04.20160705-0ubuntu1) over (15.04.0+16.04.20170214-0ubuntu1) ...
dpkg: warning: downgrading mysql-client from 5.7.17-0ubuntu0.16.04.2 to 5.7.17-0ubuntu0.16.04.1
Preparing to unpack .../mysql-client_5.7.17-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-client (5.7.17-0ubuntu0.16.04.1) over (5.7.17-0ubuntu0.16.04.2) ...
dpkg: warning: downgrading mysql-server from 5.7.17-0ubuntu0.16.04.2 to 5.7.17-0ubuntu0.16.04.1
Preparing to unpack .../mysql-server_5.7.17-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-server (5.7.17-0ubuntu0.16.04.1) over (5.7.17-0ubuntu0.16.04.2) ...
dpkg: warning: downgrading nautilus-data from 1:3.18.4.is.3.14.3-0ubuntu6 to 1:3.18.4.is.3.14.3-0ubuntu5
Preparing to unpack .../nautilus-data_1%3a3.18.4.is.3.14.3-0ubuntu5_all.deb ...
Unpacking nautilus-data (1:3.18.4.is.3.14.3-0ubuntu5) over (1:3.18.4.is.3.14.3-0ubuntu6) ...
dpkg: warning: downgrading nautilus from 1:3.18.4.is.3.14.3-0ubuntu6 to 1:3.18.4.is.3.14.3-0ubuntu5
Preparing to unpack .../nautilus_1%3a3.18.4.is.3.14.3-0ubuntu5_amd64.deb ...
Unpacking nautilus (1:3.18.4.is.3.14.3-0ubuntu5) over (1:3.18.4.is.3.14.3-0ubuntu6) ...
dpkg: warning: downgrading software-properties-common from 0.96.20.6 to 0.96.20.5
Preparing to unpack .../software-properties-common_0.96.20.5_all.deb ...
Unpacking software-properties-common (0.96.20.5) over (0.96.20.6) ...
dpkg: warning: downgrading software-properties-gtk from 0.96.20.6 to 0.96.20.5
Preparing to unpack .../software-properties-gtk_0.96.20.5_all.deb ...
Unpacking software-properties-gtk (0.96.20.5) over (0.96.20.6) ...
dpkg: warning: downgrading python3-software-properties from 0.96.20.6 to 0.96.20.5
Preparing to unpack .../python3-software-properties_0.96.20.5_all.deb ...
Unpacking python3-software-properties (0.96.20.5) over (0.96.20.6) ...
dpkg: warning: downgrading unattended-upgrades from 0.90ubuntu0.4 to 0.90ubuntu0.3
Preparing to unpack .../unattended-upgrades_0.90ubuntu0.3_all.deb ...
Unpacking unattended-upgrades (0.90ubuntu0.3) over (0.90ubuntu0.4) ...
dpkg: warning: downgrading unity-control-center from 15.04.0+16.04.20170214-0ubuntu1 to 15.04.0+16.04.20160705-0ubuntu1
Preparing to unpack .../unity-control-center_15.04.0+16.04.20160705-0ubuntu1_amd64.deb ...
Unpacking unity-control-center (15.04.0+16.04.20160705-0ubuntu1) over (15.04.0+16.04.20170214-0ubuntu1) ...
dpkg: warning: downgrading unity-control-center-faces from 15.04.0+16.04.20170214-0ubuntu1 to 15.04.0+16.04.20160705-0ubuntu1
Preparing to unpack .../unity-control-center-faces_15.04.0+16.04.20160705-0ubuntu1_all.deb ...
Unpacking unity-control-center-faces (15.04.0+16.04.20160705-0ubuntu1) over (15.04.0+16.04.20170214-0ubuntu1) ...
dpkg: warning: downgrading vino from 3.8.1-0ubuntu9.2 to 3.8.1-0ubuntu9.1
Preparing to unpack .../vino_3.8.1-0ubuntu9.1_amd64.deb ...
Unpacking vino (3.8.1-0ubuntu9.1) over (3.8.1-0ubuntu9.2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for systemd (229-4ubuntu16) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for doc-base (0.10.7) ...
Processing 1 added doc-base file...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Setting up grub-pc (2.02~beta2-36ubuntu3.8) ...
/var/lib/dpkg/info/grub-pc.config: 6: /etc/default/grub: 10: not found
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: error processing package linux-image-4.4.0-36-generic (--configure):
 package linux-image-4.4.0-36-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-38-generic (--configure):
 package linux-image-4.4.0-38-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-42-generic (--configure):
 package linux-image-4.4.0-42-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-45-generic (--configure):
 package linux-image-4.4.0-45-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-4.4.0-64-generic (--configure):
 package linux-image-4.4.0-64-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Setting up linux-image-4.4.0-No apport report written because MaxReports is reached already
                                                                                           No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
                                                                                   66-generic (4.4.0-66.87) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-66-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-66-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-4.4.0-67-generic (4.4.0-67.88) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-67-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-67-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-4.4.0-36-generic (--configure):
 package linux-image-extra-4.4.0-36-generic is not ready for configuration
 cannot configure (current status 'half-installed')
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-4.4.0-38-generic (--configure):
 package linux-image-extra-4.4.0-38-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--configure):
 package linux-image-extra-4.4.0-42-generic is not ready for configuration
 cannot configure (current status 'half-installed')No apport report written because MaxReports is reached already
                                                                                                                 No apport report written because MaxReports is reached already

dpkg: error processing package linux-image-extra-4.4.0-45-generic (--configure):
 package linux-image-extra-4.4.0-45-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--configure):
 package linux-image-extra-4.4.0-64-generic is not ready for configuration
 cannot configure (current status 'half-installed')
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-66-generic:
 linux-image-extra-4.4.0-66-generic depends on linux-image-4.4.0-66-generic; however:
  Package linux-image-4.4.0-66-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-66-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-67-generic:
 linux-image-extra-4.4.0-67-generic depends on linux-image-4.4.0-67-generic; however:
  Package linux-image-4.4.0-67-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-67-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-67-generic; however:
  Package linux-image-4.4.0-67-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-67-generic; however:
  PaNo apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                                                                                                No apport report written because MaxReports is reached already
                                                        ckage linux-image-extra-4.4.0-67-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up zlib1g-dev:amd64 (1:1.2.8.dfsg-2ubuntu4) ...
Setting up libapt-inst2.0:amd64 (1.2.19) ...
Setting up apt-utils (1.2.19) ...
Setting up udev (229-4ubuntu16) ...
addgroup: The group `input' already exists as a system group. Exiting.
update-initramfs: deferring update (trigger activated)
Setting up libpam-systemd:amd64 (229-4ubuntu16) ...
Setting up libcups2:amd64 (2.1.3-4) ...
Setting up libcups2:i386 (2.1.3-4) ...
Setting up libcupscgi1:amd64 (2.1.3-4) ...
Setting up libcupsmime1:amd64 (2.1.3-4) ...
Setting up cups-daemon (2.1.3-4) ...
Setting up libcupsfilters1:amd64 (1.8.3-2ubuntu3.1) ...
Setting up libcupsimage2:amd64 (2.1.3-4) ...
Setting up cups-filters-core-drivers (1.8.3-2ubuntu3.1) ...
Setting up cups-core-drivers (2.1.3-4) ...
Setting up cups-browsed (1.8.3-2ubuntu3.1) ...
Setting up libfontembed1:amd64 (1.8.3-2ubuntu3.1) ...
Setting up cups-filters (1.8.3-2ubuntu3.1) ...

Setting up cups-server-common (2.1.3-4) ...
Setting up libcupsppdc1:amd64 (2.1.3-4) ...
Setting up cups-common (2.1.3-4) ...
Setting up cups-client (2.1.3-4) ...
Setting up cups-ppdc (2.1.3-4) ...
Setting up cups (2.1.3-4) ...
Updating PPD files for cups ...
Setting up cups-bsd (2.1.3-4) ...
Setting up language-pack-ar (1:16.04+20160627) ...
Setting up language-pack-gnome-ar (1:16.04+20160627) ...
Setting up libstemmer0d:amd64 (0+svn585-1) ...
Setting up libgtk2.0-common (2.24.30-1ubuntu1) ...
Setting up libgtk2.0-0:amd64 (2.24.30-1ubuntu1) ...
Setting up libgail18:amd64 (2.24.30-1ubuntu1) ...
Setting up libgail-common:amd64 (2.24.30-1ubuntu1) ...
Setting up libgtk2.0-bin (2.24.30-1ubuntu1) ...
Setting up libunity-gtk3-parser0:amd64 (0.0.0+15.04.20150118-0ubuntu2) ...
Setting up unity-gtk-module-common (0.0.0+15.04.20150118-0ubuntu2) ...
Setting up unity-gtk3-module:amd64 (0.0.0+15.04.20150118-0ubuntu2) ...
Setting up libunity-gtk2-parser0:amd64 (0.0.0+15.04.20150118-0ubuntu2) ...
Setting up unity-gtk2-module:amd64 (0.0.0+15.04.20150118-0ubuntu2) ...
Setting up mysql-client-core-5.7 (5.7.17-0ubuntu0.16.04.1) ...
Setting up mysql-client-5.7 (5.7.17-0ubuntu0.16.04.1) ...
Setting up mysql-server-core-5.7 (5.7.17-0ubuntu0.16.04.1) ...
Setting up mysql-server-5.7 (5.7.17-0ubuntu0.16.04.1) ...
Checking if update is needed.
This installation of MySQL is already upgraded to 5.7.17, use --force if you still need to run mysql_upgrade
Setting up apt-transport-https (1.2.19) ...
Setting up libpci3:amd64 (1:3.3.1-1.1ubuntu1) ...
Setting up pciutils (1:3.3.1-1.1ubuntu1) ...
Setting up wget (1.17.1-1ubuntu1.1) ...
Setting up libappstream4:amd64 (0.10.6-1~ubuntu16.04.2) ...
Setting up appstream (0.10.6-1~ubuntu16.04.2) ...
Installing new version of config file /etc/appstream.conf ...
Installing new version of config file /etc/apt/apt.conf.d/50appstream ...
AppStream cache update completed successfully.
Setting up autoconf (2.69-9) ...
Setting up automake (1:1.15-4ubuntu1) ...
update-alternatives: using /usr/bin/automake-1.15 to provide /usr/bin/automake (automake) in auto mode
Setting up autopoint (0.19.7-2ubuntu3) ...
Setting up binutils (2.26.1-1ubuntu1~16.04.3) ...
Setting up libtool (2.4.6-0.1) ...
Setting up libarchive13:amd64 (3.2.1-2~ubuntu16.04.1) ...
Setting up libltdl-dev:amd64 (2.4.6-0.1) ...
Setting up libmysqlclient20:i386 (5.7.17-0ubuntu0.16.04.1) ...
Setting up libmysqlclient20:amd64 (5.7.17-0ubuntu0.16.04.1) ...
Setting up libnautilus-extension1a:amd64 (1:3.18.4.is.3.14.3-0ubuntu5) ...
Setting up libunity-control-center1 (15.04.0+16.04.20160705-0ubuntu1) ...
Setting up mysql-client (5.7.17-0ubuntu0.16.04.1) ...
Setting up mysql-server (5.7.17-0ubuntu0.16.04.1) ...
Setting up nautilus-data (1:3.18.4.is.3.14.3-0ubuntu5) ...
Setting up nautilus (1:3.18.4.is.3.14.3-0ubuntu5) ...
Setting up python3-software-properties (0.96.20.5) ...
Setting up software-properties-common (0.96.20.5) ...
Setting up software-properties-gtk (0.96.20.5) ...
Setting up unattended-upgrades (0.90ubuntu0.3) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up unity-control-center (15.04.0+16.04.20160705-0ubuntu1) ...
Setting up unity-control-center-faces (15.04.0+16.04.20160705-0ubuntu1) ...
Setting up vino (3.8.1-0ubuntu9.1) ...
Setting up dh-autoreconf (12~ubuntu16.04.1) ...
Setting up debhelper (10.2.2ubuntu1~ubuntu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-67-generic
Errors were encountered while processing:
 grub-pc
 linux-image-4.4.0-36-generic
 linux-image-4.4.0-38-generic
 linux-image-4.4.0-42-generic
 linux-image-4.4.0-45-generic
 linux-image-4.4.0-64-generic
 linux-image-4.4.0-66-generic
 linux-image-4.4.0-67-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-extra-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-extra-4.4.0-66-generic
 linux-image-extra-4.4.0-67-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I think if I find a way to remove those corrupt packages and reinstalling them, It could work

---

### Post by aboodyman on 2017-03-15
Will it work if I download the corrupt packages from this website:
[https://www.ubuntuupdates.org](https://www.ubuntuupdates.org)

---

### Post by #&amp;thj^% on 2017-03-15
:confused: What dose this show:
```
cd /boot && ls
```

---

### Post by aboodyman on 2017-03-15
```
abi-4.4.0-47-generic     config-4.4.0-67-generic      memtest86+.bin               System.map-4.4.0-67-generic
abi-4.4.0-66-generic     grub                         memtest86+.elf               vmlinuz-4.4.0-47-generic
abi-4.4.0-67-generic     initrd.img-4.4.0-47-generic  memtest86+_multiboot.bin     vmlinuz-4.4.0-66-generic
config-4.4.0-47-generic  initrd.img-4.4.0-66-generic  System.map-4.4.0-47-generic  vmlinuz-4.4.0-67-generic
config-4.4.0-66-generic  initrd.img-4.4.0-67-generic  System.map-4.4.0-66-generic
```

---

### Post by aboodyman on 2017-03-15
I'm going to try downloading all the .deb files of the corrupt packages and installing them

---

### Post by #&amp;thj^% on 2017-03-15
Huumm? Need to wrap my head around this for a bit.
What is the output of this:
```
 apt policy byobu
```

---

### Post by aboodyman on 2017-03-15
```
byobu:
  Installed: (none)
  Candidate: 5.106-0ubuntu1
  Version table:
     5.106-0ubuntu1 500
        500 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://eg.archive.ubuntu.com/ubuntu xenial/main i386 Package
```

---

### Post by #&amp;thj^% on 2017-03-15
> **aboodyman said:**
> I'm going to try downloading all the .deb files of the corrupt packages and install them

Were not having Download problems we are having APT problems.
Stay patient and on course...or proceed on your own. (Hope that makes sense):D

---

### Post by aboodyman on 2017-03-15
> **1fallen said:**
> Were not having Download problems we are having APT problems.
Stay patient and on course...or proceed on your own. (Hope that makes sense):D
ok then

---

### Post by #&amp;thj^% on 2017-03-15
> **aboodyman said:**
> ```
byobu:
  Installed: (none)
  Candidate: 5.106-0ubuntu1
  Version table:
     5.106-0ubuntu1 500
        500 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://eg.archive.ubuntu.com/ubuntu xenial/main i386 Package
```
Well let see if we can install it then:
```
sudo apt install byobu
```
Fingers Crossed...

---

### Post by aboodyman on 2017-03-15
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libappstream3
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  gawk pastebinit python3-newt run-one screen tmux
Suggested packages:
  ccze gawk-doc
The following packages will be REMOVED:
  linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-64-generic linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-64-generic
The following NEW packages will be installed:
  byobu gawk pastebinit python3-newt run-one screen tmux
0 upgraded, 7 newly installed, 10 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 1,325 kB of archives.
After this operation, 1,087 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 gawk amd64 1:4.1.3+dfsg-0.1 [398 kB]
Get:2 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 python3-newt amd64 0.52.18-1ubuntu2 [18.9 kB]
Get:3 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 tmux amd64 2.1-3build1 [223 kB]
Get:4 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 screen amd64 4.3.1-2build1 [560 kB]
Get:5 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 byobu all 5.106-0ubuntu1 [105 kB]                                        
Get:6 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 pastebinit all 1.5-1 [14.6 kB]                                           
Get:7 http://eg.archive.ubuntu.com/ubuntu xenial/main amd64 run-one all 1.17-0ubuntu1 [5,760 B]                                      
Fetched 1,325 kB in 13s (95.2 kB/s)                                                                                                  
Preconfiguring packages ...
(Reading database ... 318650 files and directories currently installed.)
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_RA4gIj/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_RA4gIj/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_tBkm4t/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_tBkm4t/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_x42aj5/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_x42aj5/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_FGoyVT/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_FGoyVT/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
WARNING: missing /lib/modules/4.4.0-64-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-64-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_EXv3c6/lib/modules/4.4.0-64-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_EXv3c6/lib/modules/4.4.0-64-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by aboodyman on 2017-03-15
By the way I have got to go :(
Sorry about that, talk to you tommorow

---

### Post by #&amp;thj^% on 2017-03-15
No worries!;)
About the same time I was today...
EDIT: if you will,  try to boot to the oldest or lowest kernel version you have in Grub:
And then give me output of this:
```
uname -r
```
Also this:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"`
```

---

### Post by aboodyman on 2017-03-16
First one:
```
4.4.0-47-generic
```
Second one:
```
linux-base
linux-firmware
linux-headers-4.4.0-66
linux-headers-4.4.0-66-generic
linux-headers-4.4.0-67
linux-headers-4.4.0-67-generic
linux-headers-generic
linux-libc-dev:amd64
linux-sound-base
```

---

### Post by #&amp;thj^% on 2017-03-16
> **aboodyman said:**
> First one:
```
4.4.0-47-generic
```
Second one:
```
linux-base
linux-firmware
linux-headers-4.4.0-66
linux-headers-4.4.0-66-generic
linux-headers-4.4.0-67
linux-headers-4.4.0-67-generic
linux-headers-generic
linux-libc-dev:amd64
linux-sound-base
```
Cool...:)
That is not the normal kernel you boot to right? (4.4.0-47-generic)

---

### Post by aboodyman on 2017-03-16
I don't really know :P
How exactly do I know what kernel I boot to?
I'm sorry I'm kind of a beginner here, so bare with me :D

---

### Post by #&amp;thj^% on 2017-03-16
So this is just a normal boot-up yes?

---

### Post by aboodyman on 2017-03-16
I guess so

---

### Post by #&amp;thj^% on 2017-03-16
My Friend we have big problems here::(
Well lets double check with this to be sure.
```
apt policy linux-image-extra-4.4.0-47-generic && apt policy linux-image-4.4.0-47-generic
```
Paste back the output please.

---

### Post by aboodyman on 2017-03-16
```
linux-image-extra-4.4.0-47-generic:
  Installed: 4.4.0-47.68
  Candidate: 4.4.0-47.68
  Version table:
 *** 4.4.0-47.68 500
        500 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
linux-image-4.4.0-47-generic:
  Installed: 4.4.0-47.68
  Candidate: 4.4.0-47.68
  Version table:
 *** 4.4.0-47.68 500
        500 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://eg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by #&amp;thj^% on 2017-03-16
Very odd??? They do not show here:
```
 	

 	linux-base
linux-firmware
linux-headers-4.4.0-66
linux-headers-4.4.0-66-generic
linux-headers-4.4.0-67
linux-headers-4.4.0-67-generic
linux-headers-generic
linux-libc-dev:amd64
linux-sound-base 

```
Just to try to show you some important difference's...here is what mine shows.
```
linux-base
linux-firmware
linux-generic-hwe-16.04
linux-headers-4.8.0-42
linux-headers-4.8.0-42-generic
linux-headers-4.9.11-040911
linux-headers-4.9.11-040911-lowlatency
linux-headers-generic-hwe-16.04
linux-image-4.8.0-42-generic
linux-image-4.9.11-040911-lowlatency
linux-image-extra-4.8.0-42-generic
linux-image-generic-hwe-16.04
linux-libc-dev:amd64
linux-sound-base


```
So I will point out you have no "Entry's" for any "linux-image"
This is very puzzling to me, as to how such a thing happened...in other words this is not a normal flaw/bug in software code.

---

### Post by aboodyman on 2017-03-16
I really don't know what to do, Thank you so much for your help tho, I really appreciate your effort trying to help me :D

---

### Post by #&amp;thj^% on 2017-03-16
We can try a nuclear approach next,,,but no guaranties it will fix it.
Up to you now....let me know.
Your very welcome though.:D You have been a good sport through all of this.

---

### Post by aboodyman on 2017-03-16
I think we have no other option I guess...

---

### Post by #&amp;thj^% on 2017-03-16
First I'm going to show it using the --dry-run switch with apt-get. That way you can give it a try without actually changing your system.

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get --dry-run remove
```
Yep we need to see the return from this, so paste back.

---

### Post by aboodyman on 2017-03-16
There ya go:
```
dpkg-query: no packages found matching linux-image-4.4.0-36-generic_4.4.0-36.55_amd64.deb
dpkg-query: no packages found matching linux-image-4.4.0-38-generic_4.4.0-38.57_amd64.deb
dpkg-query: no packages found matching linux-image-4.4.0-42-generic_4.4.0-42.62_amd64.deb
dpkg-query: no packages found matching linux-image-4.4.0-45-generic_4.4.0-45.66_amd64.deb
dpkg-query: no packages found matching linux-image-4.4.0-64-generic_4.4.0-64.85_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-36-generic_4.4.0-36.55_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-38-generic_4.4.0-38.57_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-42-generic_4.4.0-42.62_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-45-generic_4.4.0-45.66_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-64-generic_4.4.0-64.85_amd64.deb
[sudo] password for abzo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic linux-image-4.4.0-45-generic linux-image-4.4.0-64-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-64-generic
0 upgraded, 0 newly installed, 9 to remove and 4 not upgraded.
16 not fully installed or removed.
Remv linux-image-extra-4.4.0-38-generic [4.4.0-38.57]
Remv linux-image-4.4.0-38-generic [4.4.0-38.57]
Remv linux-image-extra-4.4.0-42-generic [4.4.0-42.62]
Remv linux-image-4.4.0-42-generic [4.4.0-42.62]
Remv linux-image-extra-4.4.0-45-generic [4.4.0-45.66]
Remv linux-image-4.4.0-45-generic [4.4.0-45.66]
Remv linux-image-extra-4.4.0-64-generic [4.4.0-64.85]
Remv linux-image-4.4.0-64-generic [4.4.0-64.85]
Remv linux-image-extra-4.4.0-36-generic [4.4.0-36.55]
Conf grub-pc (2.02~beta2-36ubuntu3.8 Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-36-generic (4.4.0-36.55 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-66-generic (4.4.0-66.87 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-4.4.0-67-generic (4.4.0-67.88 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-66-generic (4.4.0-66.87 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-extra-4.4.0-67-generic (4.4.0-67.88 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf linux-image-generic (4.4.0.67.72  [amd64])
```

---

### Post by #&amp;thj^% on 2017-03-16
This is very troublesome to me:
```

dpkg-query: no packages found matching linux-image-4.4.0-36-generic_4.4.0-36.55_amd64.deb 
dpkg-query: no packages found matching linux-image-4.4.0-38-generic_4.4.0-38.57_amd64.deb
dpkg-query: no packages found matching linux-image-4.4.0-42-generic_4.4.0-42.62_amd64.deb
dpkg-query: no packages found matching linux-image-4.4.0-45-generic_4.4.0-45.66_amd64.deb
dpkg-query: no packages found matching linux-image-4.4.0-64-generic_4.4.0-64.85_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-36-generic_4.4.0-36.55_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-38-generic_4.4.0-38.57_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-42-generic_4.4.0-42.62_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-45-generic_4.4.0-45.66_amd64.deb
dpkg-query: no packages found matching linux-image-extra-4.4.0-64-generic_4.4.0-64.85_amd64.deb
```
Let us leave this for tonite...and attack it again tomorrow.
Maybe a light-bulb will spark something over nite in me...

---

### Post by aboodyman on 2017-03-16
Alright man talk to you tomorrow :D

---

### Post by Bashing-om on 2017-03-17
@1fallen;

subscribed . will monitor .

[INDENT][INDENT]'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jenelle on 2017-03-17
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


is this same sort of thing or do i need to make a new post ?? 
i have my system up grades there to install but that error happens not sure how or where i need to report the problem or how to fix it ??

---

### Post by wildmanne39 on 2017-03-17
@jenelle, please start a new thread so you and the person that started this one can both get the help you need.

---

### Post by vasa1 on 2017-03-17
In the very first part of the very first post of this thread, we have```
sudo: unable to resolve host Samsung
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  thermald
Use 'sudo apt autoremove' to remove it.
```
What was the command that was issued to provoke```
sudo: unable to resolve host Samsung
```and why is thermald no longer required?

I wonder what command was issued to make thermald "no longer required".

---

### Post by aboodyman on 2017-03-17
I already solved the: **sudo: unable to resolve host Samsung  **problem, It was something in the hosts file.
but this isn't the real problem, I solved it and it didn't have any effect on the real problem

---

### Post by Bashing-om on 2017-03-17
aboodyman; Hello;

While we await your 1st responder, 1fallen, to return.
It will be instructive to see what returns:
```

df -h
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux

```
get an idea of what is broke where - and maybe break the package manager even more on the path to resolution .

same same - making an omelette ->
[INDENT][INDENT]gotta break eggs
[/INDENT][/INDENT]

---

### Post by jenelle on 2017-03-17
> **wildmanne39 said:**
> @jenelle, please start a new thread so you and the person that started this one can both get the help you need.

Cheers thanks will do later today when I get home

---

### Post by #&amp;thj^% on 2017-03-18
> **vasa1 said:**
> In the very first part of the very first post of this thread, we have```
sudo: unable to resolve host Samsung
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  thermald
Use 'sudo apt autoremove' to remove it.
```
I wonder what command was issued to make thermald "no longer required".
vasa1 I think that came in with Proposed being enabled...I had seen it also when I first ran my test run removing all changes from Proposed. (Just My guess though)

> **Bashing-om said:**
> aboodyman; Hello;

While we await your 1st responder, 1fallen, to return.
_**It will be instructive to see what returns:**_
```

df -h
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux

```
get an idea of what is broke where - and maybe break the package manager even more on the path to resolution .

same same - making an omelette ->[INDENT][INDENT]gotta break eggs
[/INDENT]
[/INDENT]

+1 Thanks Ole Friend.;)
Sorry for the long delay...it just could not have been avoided.

---

### Post by aboodyman on 2017-03-21
df -h:
```
Filesystem      Size  Used Avail Use% Mounted onudev            2.9G     0  2.9G   0% /dev
tmpfs           589M  8.8M  580M   2% /run
/dev/sda6        56G   42G   12G  79% /
tmpfs           2.9G  170M  2.8G   6% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.9G     0  2.9G   0% /sys/fs/cgroup
tmpfs           589M  112K  588M   1% /run/user/1002

```
ls -al /usr/src/:
```
total 44
drwxr-xr-x 11 root root 4096 &#1605;&#1575;&#1585; 15 17:08 .
drwxr-xr-x 12 root root 4096 &#1587;&#1576;&#1578;  3  2016 ..
drwxr-xr-x  2 root root 4096 &#1587;&#1576;&#1578;  3  2016 bbswitch-0.8
drwxr-xr-x 27 root root 4096 &#1606;&#1608;&#1601; 10 11:23 linux-headers-4.4.0-47
drwxr-xr-x  7 root root 4096 &#1606;&#1608;&#1601; 10 11:23 linux-headers-4.4.0-47-generic
drwxr-xr-x 27 root root 4096 &#1605;&#1575;&#1585;  9 14:58 linux-headers-4.4.0-66
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585;  9 14:58 linux-headers-4.4.0-66-generic
drwxr-xr-x 27 root root 4096 &#1605;&#1575;&#1585; 14 16:43 linux-headers-4.4.0-67
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585; 14 16:43 linux-headers-4.4.0-67-generic
drwxr-xr-x  8 root root 4096 &#1601;&#1576;&#1585; 25 06:30 nvidia-378-378.13
lrwxrwxrwx  1 root root   32 &#1610;&#1606;&#1575; 16 20:20 vboxhost-5.1.14 -> ../share/virtualbox/src/vboxhost
drwxr-xr-x 12 root root 4096 &#1605;&#1575;&#1585;  9 15:04 virtualbox-5.0.32

```
ls -al /lib/modules/
```
total 24
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 02:47 .
drwxr-xr-x 24 root root 4096 &#1605;&#1575;&#1585;  9 14:56 ..
drwxr-xr-x  5 root root 4096 &#1605;&#1575;&#1585; 17 17:01 4.4.0-36-generic
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585; 14 14:23 4.4.0-47-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 17:02 4.4.0-66-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 17:03 4.4.0-67-generic

```

ls -al /boot/
```
total 191488drwxr-xr-x  3 root root     4096 &#1605;&#1575;&#1585; 17 17:03 .
drwxr-xr-x 25 root root     4096 &#1605;&#1575;&#1585; 17 17:03 ..
-rw-r--r--  1 root root  1241960 &#1571;&#1594;&#1587; 11  2016 abi-4.4.0-36-generic
-rw-r--r--  1 root root  1243086 &#1571;&#1603;&#1578; 27 00:27 abi-4.4.0-47-generic
-rw-r--r--  1 root root  1245512 &#1605;&#1575;&#1585;  3 20:25 abi-4.4.0-66-generic
-rw-r--r--  1 root root  1245659 &#1605;&#1575;&#1585;  8 20:52 abi-4.4.0-67-generic
-rw-r--r--  1 root root   189696 &#1571;&#1594;&#1587; 11  2016 config-4.4.0-36-generic
-rw-r--r--  1 root root   189809 &#1571;&#1603;&#1578; 27 00:27 config-4.4.0-47-generic
-rw-r--r--  1 root root   190247 &#1605;&#1575;&#1585;  3 20:25 config-4.4.0-66-generic
-rw-r--r--  1 root root   190236 &#1605;&#1575;&#1585;  8 20:52 config-4.4.0-67-generic
drwxr-xr-x  5 root root     4096 &#1601;&#1576;&#1585; 25 06:29 grub
-rw-r--r--  1 root root 12755965 &#1605;&#1575;&#1585; 17 17:01 initrd.img-4.4.0-36-generic
-rw-r--r--  1 root root 44390630 &#1601;&#1576;&#1585; 27 16:49 initrd.img-4.4.0-47-generic
-rw-r--r--  1 root root 44388948 &#1605;&#1575;&#1585; 17 17:02 initrd.img-4.4.0-66-generic
-rw-r--r--  1 root root 44402123 &#1605;&#1575;&#1585; 17 17:03 initrd.img-4.4.0-67-generic
-rw-r--r--  1 root root   182704 &#1610;&#1606;&#1575; 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 &#1610;&#1606;&#1575; 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 &#1610;&#1606;&#1575; 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3867829 &#1571;&#1594;&#1587; 11  2016 System.map-4.4.0-36-generic
-rw-------  1 root root  3873447 &#1571;&#1603;&#1578; 27 00:27 System.map-4.4.0-47-generic
-rw-------  1 root root  3883990 &#1605;&#1575;&#1585;  3 20:25 System.map-4.4.0-66-generic
-rw-------  1 root root  3882318 &#1605;&#1575;&#1585;  8 20:52 System.map-4.4.0-67-generic
-rw-------  1 root root  7045472 &#1571;&#1594;&#1587; 11  2016 vmlinuz-4.4.0-36-generic
-rw-------  1 root root  7060896 &#1571;&#1603;&#1578; 27 00:27 vmlinuz-4.4.0-47-generic
-rw-------  1 root root  7087024 &#1605;&#1575;&#1585;  3 20:25 vmlinuz-4.4.0-66-generic
-rw-------  1 root root  7083312 &#1605;&#1575;&#1585;  8 20:52 vmlinuz-4.4.0-67-generic

```
dpkg -l | grep linux
```
ii  console-setup-linux                                         1.108ubuntu15.3                               all          Linux specific part of console-setupii  libselinux1:amd64                                           2.4-3build2                                   amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                            2.4-3build2                                   i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                              1.10.0-1                                      amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                               1.10.0-1                                      i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                        1.10.0-1                                      amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                                         1.10.0-1                                      i386         Video4linux frame format conversion library
ii  linux-base                                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                              1.157.8                                       all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-47                                      4.4.0-47.68                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic                              4.4.0-47.68                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66                                      4.4.0-66.87                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic                              4.4.0-66.87                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-67                                      4.4.0-67.88                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-67-generic                              4.4.0-67.88                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.67.72                                   amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-21-generic                                4.4.0-21.37                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-36-generic                                4.4.0-36.55                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-38-generic                                4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-42-generic                                4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-45-generic                                4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                                4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-67-generic                                4.4.0-67.88                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-36-generic                          4.4.0-36.55                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-38-generic                          4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-42-generic                          4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-45-generic                          4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic                          4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-67-generic                          4.4.0-67.88                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                         4.4.0.67.72                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-67.88                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  pptp-linux                                                  1.8.0-1                                       amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                                    3:6.03+dfsg-11ubuntu1                         amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                                  2.27.1-6ubuntu3.2                             amd64        miscellaneous system utilities

```

---

### Post by aboodyman on 2017-03-21
Sorry for the inactivity btw :/

---

### Post by ian-weisser on 2017-03-21
Seems fairly straightforward: These seem the packages you must fix...
> **aboodyman said:**
> ```

iF  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-67-generic                                4.4.0-67.88                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-67-generic                          4.4.0-67.88                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                         4.4.0.67.72                                   amd64        Generic Linux kernel image

```


...and these seem the packages you must uninstall.
> **aboodyman said:**
> ```

iF  linux-image-4.4.0-36-generic                                4.4.0-36.55                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-38-generic                                4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-42-generic                                4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-45-generic                                4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-36-generic                          4.4.0-36.55                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-38-generic                          4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-42-generic                          4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-45-generic                          4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

```

---

### Post by aboodyman on 2017-03-23
whenever I try to uninstall these packages it gives me an error.
and whenever I try to fix these packages it gives me the same error.
So how do I "force" fix/uninstall these packages?

---

### Post by westie457 on 2017-03-23
Hello,
        to uninstall broken packages you must first reinstall them. Starting with those listed by ian-weisser to be uninstalled ```
sudo apt install --reinstall [COLOR=#000000][FONT=&quot]linux-image-4.4.0-36-generic linux-image-extra-4.4.0.36-generic
```
Repeat for each pair of packages. Then 'sudo apt install --reinstall' the packages that need fixing including any that cause error messages in the terminal.
Last command should be ```
sudo update-grub
```
Reboot the system, open the terminal ```
sudo apt update
sudo apt dist-upgrade # Reboot again if a new kernel is installed
sudo apt autoremove
sudo update-grub # for safety
sudo apt autoclean
```


**If this does not work then it will be the nuclear approach.**
[/FONT][/COLOR]

---

### Post by aboodyman on 2017-03-23
> **westie457 said:**
> Hello,
        to uninstall broken packages you must first reinstall them. Starting with those listed by ian-weisser to be uninstalled ```
sudo apt install --reinstall [COLOR=#000000][FONT=&amp]linux-image-4.4.0-36-generic linux-image-extra-4.4.0.36-generic[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]
Repeat for each pair of packages. Then 'sudo apt install --reinstall' the packages that need fixing including any that cause error messages in the terminal.
Last command should be ```
sudo update-grub
```
Reboot the system, open the terminal ```
sudo apt update
sudo apt dist-upgrade # Reboot again if a new kernel is installed
sudo apt autoremove
sudo update-grub # for safety
sudo apt autoclean
```


**If this does not work then it will be the nuclear approach.**
[/FONT][/COLOR]
Okay working on it...
Oh and can you please tell me what you mean by "nuclear approach"?

---

### Post by aboodyman on 2017-03-23
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Note, selecting 'linux-image-extra-4.4.0-36-generic' for regex 'linux-image-extra-4.4.0.36-generic'
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-64-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-64-generic
0 upgraded, 0 newly installed, 2 reinstalled, 8 to remove and 28 not upgraded.
16 not fully installed or removed.
Need to get 39.0 MB of archives.
After this operation, 873 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-36-generic amd64 4.4.0-36.55 [39.0 MB]
Fetched 39.0 MB in 9min 36s (67.6 kB/s)                                        
E: Internal Error, No file name for linux-image-4.4.0-36-generic:amd64

```

---

### Post by westie457 on 2017-03-23
The 'nuclear approach' or 'nuclear option'  is by-passing 'apt' and 'dpkg' package-management. This very risky to the system and is the last option before recommending a new install of the system.
Things can go horribly wrong with this 'nuclear option' so be prepared for the worse case scenario.

---

### Post by aboodyman on 2017-03-23
I think there is no other way other than that.
and I take full responsibility if things went horribly wrong...

---

### Post by aboodyman on 2017-03-23
> **westie457 said:**
> Hello,
        to uninstall broken packages you must first reinstall them. Starting with those listed by ian-weisser to be uninstalled ```
sudo apt install --reinstall [COLOR=#000000][FONT=&amp]linux-image-4.4.0-36-generic linux-image-extra-4.4.0.36-generic[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]
Repeat for each pair of packages. Then 'sudo apt install --reinstall' the packages that need fixing including any that cause error messages in the terminal.
Last command should be ```
sudo update-grub
```
Reboot the system, open the terminal ```
sudo apt update
sudo apt dist-upgrade # Reboot again if a new kernel is installed
sudo apt autoremove
sudo update-grub # for safety
sudo apt autoclean
```


**If this does not work then it will be the nuclear approach.**
[/FONT][/COLOR]
It is not working :(

---

### Post by aboodyman on 2017-03-23
Hold on hold on, it might be working...
Na, It's not working :(

---

### Post by westie457 on 2017-03-23
> **aboodyman said:**
> Hold on hold on, it might be working...
Na, It's not working :(

Which part was nearly working?

Has anyone suggested you run ```
sudo apt install -fy
``` to try and fix this? 
Still safe and not yet the other option.

---

### Post by aboodyman on 2017-03-23
```
                                                              Errors were encountered while processing: linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
it didn't say that some packages had errors so I thought this was progress, but it turned out that it didn't work
Here's the output of [COLOR=#000000][FONT=&quot]sudo apt install -fy[/FONT][/COLOR] I guess it didn't work :/
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-64-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-64-generic
0 upgraded, 0 newly installed, 9 to remove and 28 not upgraded.
16 not fully installed or removed.
After this operation, 1,035 MB disk space will be freed.
(Reading database ... 319737 files and directories currently installed.)
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_JL3hCy/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_JL3hCy/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_R8K28C/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_R8K28C/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_v14UUl/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_v14UUl/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
WARNING: missing /lib/modules/4.4.0-64-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-64-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_bxEQdA/lib/modules/4.4.0-64-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_bxEQdA/lib/modules/4.4.0-64-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ian-weisser on 2017-03-23
> **aboodyman said:**
> ```
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
```

Has somebody been manually deleting files? If so, don't do that anymore.
Regardless, fix these as suggested by the system and reinstall these header packages. That's what is blocking the kernel image installs, which is in turn blocking old kernel (and header) removals.

---

### Post by aboodyman on 2017-03-24
I swear I haven't deleted any of those files.
I am not able to reinstall these packages, It just doesn't allow me to

---

### Post by Bashing-om on 2017-03-24
aboodyman; Hey --

Still trying to hang with you .,
Look, if you do not provide the exact command AND the outputs, we can not guess at what is going on . Nor, provide a possible exact solution .

For instance: the Package manager advise for ONE instance:
> 
Please install the linux-headers-4.4.0-38-generic package

So, show us .
```

sudo apt install -- reinstall linux-headers-4.4.0-38-generic

```
Depending on what the package manager does and advises is what we do next.
We do want to remain in the package management system to effect any restoration IF at all possible. We try not to intervene manually here and break the package manager even more . Though as a means of last resort - well we can, But, only as a means of last resort . Bad Bad things will happen going behind the package manager's back . Can be a real chore to make the package manager happy once more . 

see if
[INDENT][INDENT]we can fix this properly
[/INDENT][/INDENT]

---

### Post by aboodyman on 2017-03-27
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  linux-headers-4.4.0-38
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-64-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-64-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic
0 upgraded, 2 newly installed, 9 to remove and 34 not upgraded.
16 not fully installed or removed.
Need to get 10.7 MB of archives.
After this operation, 958 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-4.4.0-38 all 4.4.0-38.57 [9,948 kB]
Get:2 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-4.4.0-38-generic amd64 4.4.0-38.57 [785 kB]
Fetched 10.7 MB in 3min 59s (44.8 kB/s)                                        
(Reading database ... 319737 files and directories currently installed.)
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_xVoxeB/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_xVoxeB/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ihUIQt/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ihUIQt/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_6FlX1l/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_6FlX1l/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
WARNING: missing /lib/modules/4.4.0-64-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-64-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_cQlmVI/lib/modules/4.4.0-64-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_cQlmVI/lib/modules/4.4.0-64-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
this is the exact output I get

---

### Post by Bashing-om on 2017-03-27
aboodyman; Well !! Not ....

We have the advisory:
> 
Ensure all necessary drivers are built into the linux image!

and we look and find that:
> 
iU  linux-image-generic


So let's try:
```

sudo apt install --reinstall linux-image-generic

```

See if we can push this along a bit closer to a resolution .

[INDENT][INDENT]puzzle - putting the pieces together
[/INDENT][/INDENT]

---

### Post by aboodyman on 2017-03-27
here ya go:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Reinstallation of linux-image-generic is not possible, it cannot be downloaded.
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-64-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-64-generic
0 upgraded, 0 newly installed, 9 to remove and 34 not upgraded.
16 not fully installed or removed.
After this operation, 1,035 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 319737 files and directories currently installed.)
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_6D0MuS/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_6D0MuS/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_atcAI1/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_atcAI1/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_KpQX61/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_KpQX61/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
WARNING: missing /lib/modules/4.4.0-64-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-64-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_zN9qod/lib/modules/4.4.0-64-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_zN9qod/lib/modules/4.4.0-64-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2017-03-27
aboodyman; Yuk !

OK, I am getting frustrated and impatient, consider getting dirty to fix this .
show:
```

uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```

[INDENT][INDENT]sledge hammer approach
[/INDENT][/INDENT]

---

### Post by aboodyman on 2017-03-27
uname -r:
```
4.4.0-47-generic
```
ls -al /usr/src/:
```
total 44
drwxr-xr-x 11 root root 4096 &#1605;&#1575;&#1585; 15 17:08 .
drwxr-xr-x 12 root root 4096 &#1587;&#1576;&#1578;  3  2016 ..
drwxr-xr-x  2 root root 4096 &#1587;&#1576;&#1578;  3  2016 bbswitch-0.8
drwxr-xr-x 27 root root 4096 &#1606;&#1608;&#1601; 10 11:23 linux-headers-4.4.0-47
drwxr-xr-x  7 root root 4096 &#1606;&#1608;&#1601; 10 11:23 linux-headers-4.4.0-47-generic
drwxr-xr-x 27 root root 4096 &#1605;&#1575;&#1585;  9 14:58 linux-headers-4.4.0-66
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585;  9 14:58 linux-headers-4.4.0-66-generic
drwxr-xr-x 27 root root 4096 &#1605;&#1575;&#1585; 14 16:43 linux-headers-4.4.0-67
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585; 14 16:43 linux-headers-4.4.0-67-generic
drwxr-xr-x  8 root root 4096 &#1601;&#1576;&#1585; 25 06:30 nvidia-378-378.13
lrwxrwxrwx  1 root root   32 &#1610;&#1606;&#1575; 16 20:20 vboxhost-5.1.14 -> ../share/virtualbox/src/vboxhost
drwxr-xr-x 12 root root 4096 &#1605;&#1575;&#1585;  9 15:04 virtualbox-5.0.32
```
ls -al /boot/:
```
total 191488
drwxr-xr-x  3 root root     4096 &#1571;&#1576;&#1585;  1 19:01 .
drwxr-xr-x 25 root root     4096 &#1605;&#1575;&#1585; 17 17:03 ..
-rw-r--r--  1 root root  1241960 &#1571;&#1594;&#1587; 11  2016 abi-4.4.0-36-generic
-rw-r--r--  1 root root  1243086 &#1571;&#1603;&#1578; 27 00:27 abi-4.4.0-47-generic
-rw-r--r--  1 root root  1245512 &#1605;&#1575;&#1585;  3 20:25 abi-4.4.0-66-generic
-rw-r--r--  1 root root  1245659 &#1605;&#1575;&#1585;  8 20:52 abi-4.4.0-67-generic
-rw-r--r--  1 root root   189696 &#1571;&#1594;&#1587; 11  2016 config-4.4.0-36-generic
-rw-r--r--  1 root root   189809 &#1571;&#1603;&#1578; 27 00:27 config-4.4.0-47-generic
-rw-r--r--  1 root root   190247 &#1605;&#1575;&#1585;  3 20:25 config-4.4.0-66-generic
-rw-r--r--  1 root root   190236 &#1605;&#1575;&#1585;  8 20:52 config-4.4.0-67-generic
drwxr-xr-x  5 root root     4096 &#1601;&#1576;&#1585; 25 06:29 grub
-rw-r--r--  1 root root 12755471 &#1571;&#1576;&#1585;  1 19:01 initrd.img-4.4.0-36-generic
-rw-r--r--  1 root root 44390630 &#1601;&#1576;&#1585; 27 16:49 initrd.img-4.4.0-47-generic
-rw-r--r--  1 root root 44388948 &#1605;&#1575;&#1585; 17 17:02 initrd.img-4.4.0-66-generic
-rw-r--r--  1 root root 44402123 &#1605;&#1575;&#1585; 17 17:03 initrd.img-4.4.0-67-generic
-rw-r--r--  1 root root   182704 &#1610;&#1606;&#1575; 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 &#1610;&#1606;&#1575; 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 &#1610;&#1606;&#1575; 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3867829 &#1571;&#1594;&#1587; 11  2016 System.map-4.4.0-36-generic
-rw-------  1 root root  3873447 &#1571;&#1603;&#1578; 27 00:27 System.map-4.4.0-47-generic
-rw-------  1 root root  3883990 &#1605;&#1575;&#1585;  3 20:25 System.map-4.4.0-66-generic
-rw-------  1 root root  3882318 &#1605;&#1575;&#1585;  8 20:52 System.map-4.4.0-67-generic
-rw-------  1 root root  7045472 &#1571;&#1594;&#1587; 11  2016 vmlinuz-4.4.0-36-generic
-rw-------  1 root root  7060896 &#1571;&#1603;&#1578; 27 00:27 vmlinuz-4.4.0-47-generic
-rw-------  1 root root  7087024 &#1605;&#1575;&#1585;  3 20:25 vmlinuz-4.4.0-66-generic
-rw-------  1 root root  7083312 &#1605;&#1575;&#1585;  8 20:52 vmlinuz-4.4.0-67-generic

```
dpkg -l | grep linux-:
```
ii  linux-base                                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                              1.157.8                                       all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-47                                      4.4.0-47.68                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic                              4.4.0-47.68                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66                                      4.4.0-66.87                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic                              4.4.0-66.87                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-67                                      4.4.0-67.88                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-67-generic                              4.4.0-67.88                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.67.72                                   amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-21-generic                                4.4.0-21.37                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-36-generic                                4.4.0-36.55                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-38-generic                                4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-42-generic                                4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-45-generic                                4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                                4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-67-generic                                4.4.0-67.88                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-36-generic                          4.4.0-36.55                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-38-generic                          4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-42-generic                          4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-45-generic                          4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic                          4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-67-generic                          4.4.0-67.88                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                         4.4.0.67.72                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-67.88                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
```
I'm sorry some stuff are arabic, don't worry about that, it's just because I'm actually from an arabic country

---

### Post by Bashing-om on 2017-03-27
aboodyman; Hey;

Need also :
```

ls -al /lib/modules/

```

Looks like dirty - so far - is the better way to go .

as to
> 
I'm sorry some stuff are arabic, 

Thus far not a hindrance - I get the gist of what I need .

[INDENT][INDENT]break it .. and have the system heal it's self .
[INDENT][INDENT][INDENT]what a way to go
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aboodyman on 2017-03-27
there ya go:
```
total 24drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 02:47 .
drwxr-xr-x 24 root root 4096 &#1605;&#1575;&#1585;  9 14:56 ..
drwxr-xr-x  5 root root 4096 &#1571;&#1576;&#1585;  1 19:01 4.4.0-36-generic
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585; 14 14:23 4.4.0-47-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 17:02 4.4.0-66-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 17:03 4.4.0-67-generic
```

---

### Post by Bashing-om on 2017-03-27
aboodyman; Errrkkk ..

> **aboodyman said:**
> there ya go:
```
total 24drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 02:47 .
drwxr-xr-x 24 root root 4096 &#1605;&#1575;&#1585;  9 14:56 ..
drwxr-xr-x  5 root root 4096 &#1571;&#1576;&#1585;  1 19:01 4.4.0-36-generic
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585; 14 14:23 4.4.0-47-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 17:02 4.4.0-66-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 17:03 4.4.0-67-generic
```

That one I will need translating ( I am not able to in google) as I am tracking but 3 versions installed that I do not want to touch.

[INDENT][INDENT]can not do it all
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-03-27
aboodyman; Hey !

1fallen was able to translate for us.
Let's run:
```

sudo rm -rf /lib/modules/4.4.0-36-generic*
sudo rm /boot/*-4.4.0-36-generic
sudo apt -f install

```
Now, depending what results here we do some final cleanup.


[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aboodyman on 2017-04-07
Sorry for the inactivity, I had internet connection problems
here's the output for[B] sudo apt -f install:
[/B]```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-64-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-64-generic
0 upgraded, 0 newly installed, 9 to remove and 85 not upgraded.
16 not fully installed or removed.
After this operation, 1,035 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 319741 files and directories currently installed.)
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_FXMoQI/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_FXMoQI/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_leovht/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_leovht/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_vxzq0z/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_vxzq0z/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
WARNING: missing /lib/modules/4.4.0-64-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-64-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_syZ6Dc/lib/modules/4.4.0-64-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_syZ6Dc/lib/modules/4.4.0-64-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_8L1dal/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_8L1dal/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2017-04-07
aboodyman; Welp -

That ain't good ! Let's get a fresh look at what is.
See then what we can do to address:
> 
Errors were encountered while processing:
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Show us a new:
```

df -h
df -i
lsb_release -a
uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```
The output in English, please as that is the only human language I can deal with .
And we get prepared to get dirty as the quickest way to resolve all this . For others reading this thread; NOT a good thing to do, getting dirty is the last resort.

We match up the libraries and files .. and have the system heal it's self when we get all straightened out .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by aboodyman on 2017-04-07
df -h
```

Filesystem      Size  Used Avail Use% Mounted onudev            2.9G     0  2.9G   0% /dev
tmpfs           589M  8.8M  580M   2% /run
/dev/sda6        56G   40G   14G  76% /
tmpfs           2.9G   42M  2.9G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.9G     0  2.9G   0% /sys/fs/cgroup
tmpfs           589M   96K  588M   1% /run/user/1002

```
df -i
```

Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            746850    580  746270    1% /dev
tmpfs           752697    836  751861    1% /run
/dev/sda6      3702784 455614 3247170   13% /
tmpfs           752697     66  752631    1% /dev/shm
tmpfs           752697      6  752691    1% /run/lock
tmpfs           752697     16  752681    1% /sys/fs/cgroup
tmpfs           752697     39  752658    1% /run/user/1002

```
lsb_release -a
```

LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

```
uname -r
```

4.4.0-47-generic

```
ls -al /usr/src/
```
total 44
drwxr-xr-x 11 root root 4096 &#1605;&#1575;&#1585; 15 17:08 .
drwxr-xr-x 12 root root 4096 &#1587;&#1576;&#1578;  3  2016 ..
drwxr-xr-x  2 root root 4096 &#1587;&#1576;&#1578;  3  2016 bbswitch-0.8
drwxr-xr-x 27 root root 4096 &#1606;&#1608;&#1601; 10 11:23 linux-headers-4.4.0-47
drwxr-xr-x  7 root root 4096 &#1606;&#1608;&#1601; 10 11:23 linux-headers-4.4.0-47-generic
drwxr-xr-x 27 root root 4096 &#1605;&#1575;&#1585;  9 14:58 linux-headers-4.4.0-66
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585;  9 14:58 linux-headers-4.4.0-66-generic
drwxr-xr-x 27 root root 4096 &#1605;&#1575;&#1585; 14 16:43 linux-headers-4.4.0-67
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585; 14 16:43 linux-headers-4.4.0-67-generic
drwxr-xr-x  8 root root 4096 &#1601;&#1576;&#1585; 25 06:30 nvidia-378-378.13
lrwxrwxrwx  1 root root   32 &#1610;&#1606;&#1575; 16 20:20 vboxhost-5.1.14 -> ../share/virtualbox/src/vboxhost
drwxr-xr-x 12 root root 4096 &#1605;&#1575;&#1585;  9 15:04 virtualbox-5.0.32



```
ls -al /lib/modules/
```
total 20
drwxr-xr-x  5 root root 4096 &#1571;&#1576;&#1585;  7 19:44 .
drwxr-xr-x 24 root root 4096 &#1605;&#1575;&#1585;  9 14:56 ..
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#1585; 14 14:23 4.4.0-47-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 17:02 4.4.0-66-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#1585; 17 17:03 4.4.0-67-generic



```
ls -al /boot/
```
total 176076drwxr-xr-x  3 root root     4096 &#1571;&#1576;&#1585;  7 19:45 .
drwxr-xr-x 25 root root     4096 &#1605;&#1575;&#1585; 17 17:03 ..
-rw-r--r--  1 root root  1243086 &#1571;&#1603;&#1578; 27 00:27 abi-4.4.0-47-generic
-rw-r--r--  1 root root  1245512 &#1605;&#1575;&#1585;  3 20:25 abi-4.4.0-66-generic
-rw-r--r--  1 root root  1245659 &#1605;&#1575;&#1585;  8 20:52 abi-4.4.0-67-generic
-rw-r--r--  1 root root   189809 &#1571;&#1603;&#1578; 27 00:27 config-4.4.0-47-generic
-rw-r--r--  1 root root   190247 &#1605;&#1575;&#1585;  3 20:25 config-4.4.0-66-generic
-rw-r--r--  1 root root   190236 &#1605;&#1575;&#1585;  8 20:52 config-4.4.0-67-generic
drwxr-xr-x  5 root root     4096 &#1601;&#1576;&#1585; 25 06:29 grub
-rw-r--r--  1 root root  9333680 &#1571;&#1576;&#1585;  7 19:45 initrd.img-4.4.0-36-generic
-rw-r--r--  1 root root 44390630 &#1601;&#1576;&#1585; 27 16:49 initrd.img-4.4.0-47-generic
-rw-r--r--  1 root root 44388948 &#1605;&#1575;&#1585; 17 17:02 initrd.img-4.4.0-66-generic
-rw-r--r--  1 root root 44402123 &#1605;&#1575;&#1585; 17 17:03 initrd.img-4.4.0-67-generic
-rw-r--r--  1 root root   182704 &#1610;&#1606;&#1575; 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 &#1610;&#1606;&#1575; 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 &#1610;&#1606;&#1575; 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3873447 &#1571;&#1603;&#1578; 27 00:27 System.map-4.4.0-47-generic
-rw-------  1 root root  3883990 &#1605;&#1575;&#1585;  3 20:25 System.map-4.4.0-66-generic
-rw-------  1 root root  3882318 &#1605;&#1575;&#1585;  8 20:52 System.map-4.4.0-67-generic
-rw-------  1 root root  7060896 &#1571;&#1603;&#1578; 27 00:27 vmlinuz-4.4.0-47-generic
-rw-------  1 root root  7087024 &#1605;&#1575;&#1585;  3 20:25 vmlinuz-4.4.0-66-generic
-rw-------  1 root root  7083312 &#1605;&#1575;&#1585;  8 20:52 vmlinuz-4.4.0-67-generic



```
dpkg -l | grep linux-
```
ii  linux-base                                                  4.0ubuntu1                                    all          Linux image base packageii  linux-firmware                                              1.157.8                                       all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-47                                      4.4.0-47.68                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic                              4.4.0-47.68                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66                                      4.4.0-66.87                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic                              4.4.0-66.87                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-67                                      4.4.0-67.88                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-67-generic                              4.4.0-67.88                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.67.72                                   amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-21-generic                                4.4.0-21.37                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-36-generic                                4.4.0-36.55                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-38-generic                                4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-42-generic                                4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-45-generic                                4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                                4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-67-generic                                4.4.0-67.88                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-36-generic                          4.4.0-36.55                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-38-generic                          4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-42-generic                          4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-45-generic                          4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic                          4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-67-generic                          4.4.0-67.88                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                         4.4.0.67.72                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-67.88                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2017-04-07
aboodyman; Hey;

Again, English is all I can deal with .
I think I can make out all but the  /lib/modules/ output .

Try as :
```

LANG=C;ls -al  /lib/modules/

```

[INDENT][INDENT]maybe yes.
[/INDENT][/INDENT]

---

### Post by aboodyman on 2017-04-07
The arabic text is just the names of the months so don't worry about it.
```

total 20
drwxr-xr-x  5 root root 4096 &#1571;&#1576;&#65533;  7 19:44 .
drwxr-xr-x 24 root root 4096 &#1605;&#1575;&#65533;  9 14:56 ..
drwxr-xr-x  7 root root 4096 &#1605;&#1575;&#65533; 14 14:23 4.4.0-47-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#65533; 17 17:02 4.4.0-66-generic
drwxr-xr-x  6 root root 4096 &#1605;&#1575;&#65533; 17 17:03 4.4.0-67-generic

```

---

### Post by Bashing-om on 2017-04-07
aboodyman; Hummm ..

Let's try this, and see if the package manager will allow:
```

sudo apt install linux-generic
sudo apt install --reinstall linux-image-generic

```
where we are trying real hard not to go the dirty route .

( I can accept that we will have to purge the 36,38,42,45,64,66 and 67 kernels)

[INDENT][INDENT]we find a way
[/INDENT][/INDENT]

---

### Post by aboodyman on 2017-04-10
sudo apt install linux-generic:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-headers-generic
  linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
  linux-image-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-64-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-64-generic
The following NEW packages will be installed:
  linux-generic linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic
  linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
The following packages will be upgraded:
  linux-headers-generic linux-image-generic
2 upgraded, 5 newly installed, 9 to remove and 83 not upgraded.
16 not fully installed or removed.
Need to get 68.4 MB of archives.
After this operation, 739 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-4.4.0-72-generic amd64 4.4.0-72.93 [21.8 MB]
Get:2 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-extra-4.4.0-72-generic amd64 4.4.0-72.93 [35.9 MB]
Get:3 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-generic amd64 4.4.0.72.78 [2,334 B]
Get:4 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-4.4.0-72 all 4.4.0-72.93 [9,888 kB]
Get:5 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-4.4.0-72-generic amd64 4.4.0-72.93 [784 kB]
Get:6 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-generic amd64 4.4.0.72.78 [2,302 B]
Get:7 http://eg.archive.ubuntu.com/ubuntu xenial-security/main amd64 linux-generic amd64 4.4.0.72.78 [1,790 B]
Fetched 68.4 MB in 29min 27s (38.7 kB/s)                                       
(Reading database ... 319741 files and directories currently installed.)
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_tMJgRK/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_tMJgRK/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_A2FkVk/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_A2FkVk/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_98cPlB/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_98cPlB/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
WARNING: missing /lib/modules/4.4.0-64-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-64-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_fPHq7l/lib/modules/4.4.0-64-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_fPHq7l/lib/modules/4.4.0-64-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_t661XK/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_t661XK/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
sudo apt install --reinstall linux-image-generic:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
  linux-headers-4.4.0-72-generic
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-64-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-64-generic
The following NEW packages will be installed:
  linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
The following packages will be upgraded:
  linux-image-generic
1 upgraded, 2 newly installed, 9 to remove and 84 not upgraded.
16 not fully installed or removed.
Need to get 0 B/57.8 MB of archives.
After this operation, 816 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 319741 files and directories currently installed.)
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-38-generic cannot be found.
Please install the linux-headers-4.4.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_t30Y9x/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_t30Y9x/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-42-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-42-generic cannot be found.
Please install the linux-headers-4.4.0-42-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
WARNING: missing /lib/modules/4.4.0-42-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-42-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_4bf9Ro/lib/modules/4.4.0-42-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_4bf9Ro/lib/modules/4.4.0-42-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-45-generic cannot be found.
Please install the linux-headers-4.4.0-45-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
WARNING: missing /lib/modules/4.4.0-45-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_FGUBcZ/lib/modules/4.4.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_FGUBcZ/lib/modules/4.4.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-64-generic cannot be found.
Please install the linux-headers-4.4.0-64-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
WARNING: missing /lib/modules/4.4.0-64-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-64-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_HvsUzH/lib/modules/4.4.0-64-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_HvsUzH/lib/modules/4.4.0-64-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_uudEwx/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_uudEwx/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: 10: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-38-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2017-04-10
aboodyman : WelP !

> 
2 upgraded, 5 newly installed, 9 to remove and 83 not upgraded.

try :
```

sudo apt update
sudo apt full-upgrade

```

As we try and stay clean .
Hope
[INDENT][INDENT]the package manager will do it's job
[/INDENT][/INDENT]

---

