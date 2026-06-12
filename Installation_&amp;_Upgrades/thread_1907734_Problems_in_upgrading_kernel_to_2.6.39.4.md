---
title: "Problems in upgrading kernel to 2.6.39.4"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by Vipul03 on 2012-01-12
Hi,

I am a newbee in kernel compilation and I am trying to upgrade my Lucid from kernel "2.6.32-33-generic" to "2.6.39.4".

I compiled the kernel with default configuration for i386 architecture, installed it, created initramfs for the same. My grub.cfg looks as below

[INDENT]menuentry 'Ubuntu, with Linux 2.6.39.4-TEST' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39abd5ae-5bae-4981-92c1-4e861748a0b3
	linux	/boot/vmlinuz-2.6.39.4-TEST root=UUID=39abd5ae-5bae-4981-92c1-4e861748a0b3 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.39.4-TEST
}
menuentry 'Ubuntu, with Linux 2.6.39.4-TEST (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39abd5ae-5bae-4981-92c1-4e861748a0b3
	echo	'Loading Linux 2.6.39.4-TEST ...'
	linux	/boot/vmlinuz-2.6.39.4-TEST root=UUID=39abd5ae-5bae-4981-92c1-4e861748a0b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39.4-TEST
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39abd5ae-5bae-4981-92c1-4e861748a0b3
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=39abd5ae-5bae-4981-92c1-4e861748a0b3 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39abd5ae-5bae-4981-92c1-4e861748a0b3
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=39abd5ae-5bae-4981-92c1-4e861748a0b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}

[/INDENT]


But when I am trying to boot with the new kernel I am getting the screen saying 

[INDENT]mount: mounting none on /dev failed: No such device
mount: mounting /dev/disk/by-uuid/39abd5ae-5bae-4981-92c1-4e861748a0b3 on /root failed: No such device
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target system doesn't have /sbin/init
No init found. Try passing init= bootarg

BusyBox v1.13.3 built-in shell(ash)
Enter 'help' for a list of built-in commands.
(initramfs)[/INDENT]


I don't understand what went wrong. I searched on google but could not solve the issue.

Thanks for help.
Vipul

---

### Post by lemming465 on 2012-01-21
A bit more context would help.  How were the options set when you built the kernel?  Could we see the output of **ls -l /boot**?  What was the exact command used to build the initrd (e.g. history | grep initrd)?

---

### Post by Vipul03 on 2012-01-24
Hi,

I used the option "make defconfig" for generating the options/configuration file, which generated the configuration for i386.

The result of  ls -l /boot is below

[INDENT]-rw-r--r-- 1 root root   652139 2011-07-08 08:09 abi-2.6.32-33-generic
-rw-r--r-- 1 root root   116025 2011-07-08 08:09 config-2.6.32-33-generic
-rw-r--r-- 1 root root   130925 2012-01-11 17:40 config-2.6.39.4-TEST
drwxr-xr-x 3 root root     4096 2012-01-12 15:29 grub
-rw-r--r-- 1 root root  8360530 2012-01-03 13:06 initrd.img-2.6.32-33-generic
-rw-r--r-- 1 root root 65202410 2012-01-12 15:28 initrd.img-2.6.39.4-TEST
-rw-r--r-- 1 root root   160280 2010-03-23 15:07 memtest86+.bin
-rw-r--r-- 1 root root  1690625 2011-07-08 08:09 System.map-2.6.32-33-generic
-rw-r--r-- 1 root root  1797971 2012-01-11 17:40 System.map-2.6.39.4-TEST
-rw-r--r-- 1 root root     1196 2011-07-08 08:12 vmcoreinfo-2.6.32-33-generic
-rw-r--r-- 1 root root  4036896 2011-07-08 08:09 vmlinuz-2.6.32-33-generic
-rw-r--r-- 1 root root  4271632 2012-01-11 17:40 vmlinuz-2.6.39.4-TEST[/INDENT]


The command used to generate the initrd is as follow
[INDENT]sudo update-initramfs -c -k 2.6.39.4-TEST[/INDENT]

I am using VM (Virtual Box V4.1.2r73507) for the same.

If any other information is required, please let me know.
Thanks for replying.
Vipul

---

### Post by aikikode on 2012-01-24
I have the same very problem after compiling and installing 3.3-rc1 kernel on Ubuntu 10.04.

I used [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) for instructions. The only difference is that I used 'make defconfig' instead of 'make oldconfig'.

---

### Post by raja.genupula on 2012-01-24
> **Vipul03 said:**
> Hi,

I am a newbee in kernel compilation and I am trying to upgrade my Lucid from kernel "2.6.32-33-generic" to "2.6.39.4".

I compiled the kernel with default configuration for i386 architecture, installed it, created initramfs for the same. My grub.cfg looks as below

[INDENT]menuentry 'Ubuntu, with Linux 2.6.39.4-TEST' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39abd5ae-5bae-4981-92c1-4e861748a0b3
	linux	/boot/vmlinuz-2.6.39.4-TEST root=UUID=39abd5ae-5bae-4981-92c1-4e861748a0b3 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.39.4-TEST
}
menuentry 'Ubuntu, with Linux 2.6.39.4-TEST (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39abd5ae-5bae-4981-92c1-4e861748a0b3
	echo	'Loading Linux 2.6.39.4-TEST ...'
	linux	/boot/vmlinuz-2.6.39.4-TEST root=UUID=39abd5ae-5bae-4981-92c1-4e861748a0b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39.4-TEST
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39abd5ae-5bae-4981-92c1-4e861748a0b3
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=39abd5ae-5bae-4981-92c1-4e861748a0b3 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39abd5ae-5bae-4981-92c1-4e861748a0b3
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=39abd5ae-5bae-4981-92c1-4e861748a0b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}

[/INDENT]


But when I am trying to boot with the new kernel I am getting the screen saying 

[INDENT]mount: mounting none on /dev failed: No such device
mount: mounting /dev/disk/by-uuid/39abd5ae-5bae-4981-92c1-4e861748a0b3 on /root failed: No such device
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target system doesn't have /sbin/init
No init found. Try passing init= bootarg

BusyBox v1.13.3 built-in shell(ash)
Enter 'help' for a list of built-in commands.
(initramfs)[/INDENT]


I don't understand what went wrong. I searched on google but could not solve the issue.

Thanks for help.
Vipul

I think you have given enough information . please insert a live cd or USB then move to live system from there check your harddisk using **fsck** command and try again . 

let us know what you got .

---

