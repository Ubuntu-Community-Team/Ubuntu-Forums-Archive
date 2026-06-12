---
title: "Just updated the kernel and cannot boot using 3.5.0-26"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by jonathanfv on 2013-03-19
Hi again! Here I have another problem to fix... (Sorry for not being   very helpful with others' threads, I'm just not experienced enough to be   much help.) I just updated the kernel (normal update), and my   computer can't boot properly with the kernel 3.5.0-26, and I have to   boot from 3.5.0-25 for it to work. Am I the only one with this problem? I   tried to reinstall all my kernels and kernel headers, but it didn't   solve it and I had to change Grub so it boots from the -25 version   instead. Thanks for anyone who can help.

---

### Post by dino99 on 2013-03-20
explain clearly the issue: what do you mean exactly by "cant boot properly" ?
which errors do you get ?
which errors are logged into /var/log/dmesg ?

---

### Post by tux-gamer on 2013-03-20
I got the same error, i'am using Ubuntu 12.10
i cannot upgrade kernel from 3.5.0-25 to 3.5.0-26, i have been reboot , and run **apt-get upgrade** again, then reboot again, but i still got the same error and grub still using 3.5.0-25

here the error log when i do **apt-get upgrade**:
```

Setting up linux-image-3.5.0-26-generic (3.5.0-26.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.5.0-26-generic...
P: Writing config for /boot/vmlinuz-3.5.0-25-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-wheezy/extlinux/memtest.bin': No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-26-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-26-generic:
 linux-image-extra-3.5.0-26-generic depends on linux-image-3.5.0-26-generic; however:
  Package linux-image-3.5.0-26-generic is not configured yet.

dpkg: error processing linux-image-extra-3.5.0-26-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-26-generic; however:
  Package linux-image-3.5.0-26-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.5.0-26-generic; however:
  Package linux-image-extra-3.5.0-26-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.

dpkg: error processing lNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                    No apport report written because the error message indicates its a followup error from a previous failure.
                                                                      No apport report written because the error message indicates its a followup error from a previous failure.
                                        inux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-generic; however:
  Package linux-generic is not configured yet.

dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Setting up handbrake-gtk (0.9.8+ppa1~quantal1) ...
Errors were encountered while processing:
 linux-image-3.5.0-26-generic
 linux-image-extra-3.5.0-26-generic
 linux-image-generic
 linux-generic
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

List info regarding memtest error:
```

tux-gamer@Asus-X201EP:~$ ll /usr/share/syslinux/themes/debian-wheezy/extlinux/memtest.bin
lrwxrwxrwx 1 root root 20 Jul  1  2012 /usr/share/syslinux/themes/debian-wheezy/extlinux/memtest.bin -> /boot/memtest86+.bin
tux-gamer@Asus-X201EP:~$ ll /boot/
total 59608
drwxr-xr-x   4 root root     4096 Mar 20 15:21 ./
drwxr-xr-x. 25 root root     4096 Mar 20 15:21 ../
-rw-r--r--   1 root root   858289 Feb 26 02:32 abi-3.5.0-25-generic
-rw-r--r--   1 root root   858541 Mar  9 06:49 abi-3.5.0-26-generic
-rw-r--r--   1 root root   154500 Feb 26 02:32 config-3.5.0-25-generic
-rw-r--r--   1 root root   154500 Mar  9 06:49 config-3.5.0-26-generic
drwxr-xr-x   3 root root     4096 Mar 20 15:21 extlinux/
drwxr-xr-x   5 root root     4096 Mar 15 00:03 grub/
-rw-r--r--   1 root root 21979240 Feb 28 21:09 initrd.img-3.5.0-25-generic
-rw-r--r--   1 root root 22004913 Mar 20 15:21 initrd.img-3.5.0-26-generic
-rw-------   1 root root  2323653 Feb 26 02:32 System.map-3.5.0-25-generic
-rw-------   1 root root  2318941 Mar  9 06:49 System.map-3.5.0-26-generic
-rw-------   1 root root  5180432 Feb 26 02:32 vmlinuz-3.5.0-25-generic
-rw-------   1 root root  5167568 Mar  9 06:49 vmlinuz-3.5.0-26-generic
tux-gamer@Asus-X201EP:~$ dpkg -l memtest86+
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                         Version             Architecture        Description
+++-============================-===================-===================-=============================================================
ii  memtest86+                   4.20-1.1ubuntu2.1   i386                thorough real-mode memory tester
tux-gamer@Asus-X201EP:~$ dpkg -L memtest86+
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/memtest86+
/usr/share/doc/memtest86+/README.gz
/usr/share/doc/memtest86+/README.Debian
/usr/share/doc/memtest86+/examples
/usr/share/doc/memtest86+/examples/grub-menu.lst
/usr/share/doc/memtest86+/examples/lilo.conf
/usr/share/doc/memtest86+/changelog.Debian.gz
/usr/share/doc/memtest86+/copyright
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/memtest86+
/usr/bin
/usr/lib
/usr/lib/memtest86+
/usr/lib/memtest86+/memtest86+.elf
/usr/lib/memtest86+/memtest86+.iso
/boot
/boot/memtest86+_multiboot.bin
/boot/memtest86+.bin
/etc
/etc/grub.d
/etc/grub.d/20_memtest86+
tux-gamer@Asus-X201EP:~$ 

```

please , i need some help...




Edit:
Solved after delete **memtest86+**, why i must un install memtest to solve it... sad... :(

```

tux-gamer@Asus-X201EP:~$ sudo apt-get remove memtest86+
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcdio-paranoia1 libmkv0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  memtest86+ syslinux-themes-debian syslinux-themes-debian-wheezy ubuntu-standard
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 2,632 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 321158 files and directories currently installed.)
Removing syslinux-themes-debian ...
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.5.0-26-generic...
P: Writing config for /boot/vmlinuz-3.5.0-25-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
P: Updating /boot/extlinux/extlinux.conf...
Removing syslinux-themes-debian-wheezy ...
Removing ubuntu-standard ...
Removing memtest86+ ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found Windows 8 (loader) on /dev/sda1
Found openSUSE 12.3 (x86_64) on /dev/sda6
done
Setting up linux-image-3.5.0-26-generic (3.5.0-26.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.5.0-26-generic...
P: Writing config for /boot/vmlinuz-3.5.0-25-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found Windows 8 (loader) on /dev/sda1
Found openSUSE 12.3 (x86_64) on /dev/sda6
done
Setting up linux-image-extra-3.5.0-26-generic (3.5.0-26.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.5.0-26-generic...
P: Writing config for /boot/vmlinuz-3.5.0-25-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found Windows 8 (loader) on /dev/sda1
Found openSUSE 12.3 (x86_64) on /dev/sda6
done
Setting up linux-image-generic (3.5.0.26.32) ...
Setting up linux-generic (3.5.0.26.32) ...
Setting up linux-generic-pae (3.5.0.26.32) ...
tux-gamer@Asus-X201EP:~$  

```

---

### Post by jonathanfv on 2013-03-31
Hi there. I'm really sorry I didn't give more details in my initial post, my mother recently passed away (the day before I wrote that) and I was pretty busy with my family. Here's an update on the problem, which is still not fixed. At first, I just went around it by booting using kernel version 3.5.0-25 instead of 3.5.0-26. But today, I rebooted using the same settings as usual, and guess what? Same thing happened. I'm now running on 3.5.0-24, and I really have to figure it out before it does the same on all my versions of the kernel! I took a picture of my screen, and here's what it was showing when it stopped booting:

[[IMG]http://img580.imageshack.us/img580/3834/errorud.jpg[/IMG]]("http://img580.imageshack.us/img580/3834/errorud.jpg")

Sorry I have to ask for help again, but I have no idea what the problem can be, and I'd hate to reinstall everything, especially since this might occur again. And sorry one more time for not being present, my family needed me more.

---

### Post by jonathanfv on 2013-03-31
Just fixed the problem by reinstalling Bumblebee and the Nvidia driver, which bbswitch is part of (Bumblebee). Just noticed how bbswitch appeared often on the error message. Bumblebee/Nvidia messing everything up again... Hum... Anyway. Now everything works fine with all versions of the kernel, that I also reinstalled.

Even if it's fixed, I'd like if someone could point me out some resources to understand these messages better.

---

