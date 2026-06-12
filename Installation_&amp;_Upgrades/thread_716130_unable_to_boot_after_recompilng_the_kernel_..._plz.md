---
title: "unable to boot after recompilng the kernel ... plz help"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by harry_12345 on 2008-03-05
I recompile the kernel (my first homework assignment in linux kernel programming) and now I am unable to boot in the newly compiled kernel.

I followed all the steps mentioned at [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) and the compilation was successful.

I am running ubuntu on parallels

Following is what I get when boot into the newly compiled kernel

check_root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/module/ ls /dev
ALERT /dev/disk/by-uuid/ed1fc968-dd83-412c-a55a-73ec03cd15e8 does not exist Dropping to shell.

Also, removed the uuid while booting and replaced it by root=/dev/sda1 and still unable to boot.

Any inputs in this regard will be help.

Also booting in the old and getting the output of the following commands

harshad@OhBoy:~$ blkid
/dev/sda1: UUID="ed1fc968-dd83-412c-a55a-73ec03cd15e8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="8d2fb78f-cb16-48b0-8813-cd39b13a519a" TYPE="swap" 
harshad@OhBoy:~$ 

Some portion of menu.lst

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=ed1fc968-dd83-412c-a55a-73ec03cd15e8 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=ed1fc968-dd83-412c-a55a-73ec03cd15e8 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, kernel 2.6.18.1-firsthw
root (hd0,0)
kernel /boot/vmlinuz-2.6.18.1-firsthw root=UUID=ed1fc968-dd83-412c-a55a-73ec03cd15e8 ro quiet splash
initrd /boot/initrd.img-2.6.18.1-firsthw
quiet

title Ubuntu 7.10, kernel 2.6.18.1-firsthw (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.18.1-firsthw root=UUID=ed1fc968-dd83-412c-a55a-73ec03cd15e8 ro single
initrd /boot/initrd.img-2.6.18.1-firsthw

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

Please Reply ASAP

---

### Post by prshah on 2008-03-06
Did you use the "--initrd" switch when compiling your Ubuntu kernel?

Cheers,
PRShah

---

