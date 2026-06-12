---
title: "New Kernel does not boot"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by killedbydeath on 2008-03-03
For OS course we should build a new kernel to write a custom system call.
My new kernel does not boot and gives the following errors while booting:

WARNING: Could not open directory /lib/modules/2.6.22.21 no such file or directory

FATAL: Could not open /lib/modules/2.6.22.21/modules.dep.temp for writing no such file or directory

Check root=bootarg cat /proc/cmdline or missing modules,devices : cat(proc/modules ls /dev

Alert /dev/disk/by-uuid/<my current kernel root> does not exists

Dropping to shell

and the busybox built-in shell appears.

For the new kernel build : 

I downloaded the my current kernel version's source files( 2.6.22-14)  and extract them to my /home directory. Then i used commands
make mrproper
make defconfig
make oldconfig

After that i changed the EXTRAVERSION macro to .21 in Makefile in my kernel source folder.
then i used "make" command to compile the new kernel.
I used "make modules" and "make modules_install" commands to install the modules 
For the last step i copied the "bzImage" file in in kernel source directory's /arch/i386/boot to the /boot directory and i changed my menu.lst file in /boot/grub and append 

title		Ubuntu 7.10, kernel 2.6.22-14-21 
root	       (hd0,6)
kernel	      /boot/bzImage root=UUID=6f08fbed-2423-4b54-83ad-68e48a6eef87 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

for those lines above i only copied my current kernel settings for grub and  changed the "/boot/bzImage" part. 
I have my / and /home (which includes the kernel source directory) directories in different partitions can it be the reason for the errors in my new kernel boot ? Because i checked the /lib/modules/2.6.22.21 folder and indeed it exists.

---

