---
title: "ubuntu &amp; XP &amp; gentoo?"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by noodles_x on 2007-02-09
Hi
i want to try gentoo, but keep ubuntu and xp. I installed gentoo, but didn't install his grub. I decided  
ti keep ubuntu's grub and edit menu.lst so i can boot gentoo. 
My menu.lst is

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=b1ac7f68-d184-4080-9c20-e56008e9eba4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=b1ac7f68-d184-4080-9c20-e56008e9eba4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot



title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I added this section for gentoo
title=GeNtOo LiNuX
root (hd0,5) 
kernel /boot/kernel-genkernel-x86-2.6.17-gentoo-r7 root=/dev/sda6 

But when i try to boot gentoo I get
VFS cannot open root device sda6 or unknown - block(0,0)
please append a correct "root="boot option
KERNEL PANIC - NOT SYNCING VFS - unable to mount root fs on unknown block (0,0)

I know that "root=/dev/sda6" iis correct.  My friend says that ubuntu has a silly menu.lst cause 
"root=UUID=b1ac7f68-d184-4080-9c20-e56008e9eba4 ro quiet splash" isn't the "official" way.
I tried to put that in gentoo's root= but it didn't work, it breaks even quicker.
Help please?:confused:

---

### Post by confused57 on 2007-02-09
Here's the recommended Gentoo genkernel grub entry:

> title=Gentoo Linux 2.6.17-r5
root (hd0,5)
kernel /boot/kernel-genkernel-x86-2.6.17-gentoo-r7 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda6 udev
initrd /boot/initramfs-genkernel-x86-2.6.17-gentoo-r7

If the above doesn't work, you "might" be able to use the Ubuntu live cd & install Gentoo's grub to the root partition(sda6), then add an entry to Ubuntu's grub to boot Gentoo using chainloading, e.g.

title   Gentoo
rootnoverify  (hd0,5)
chainloader +1

How to install grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

I don't believe you have to use the root=UUID#, even to boot Edgy, you could also use just root=/dev/sda1, instead of the UUID in the kernel line.

---

### Post by grazie on 2007-02-09
I'd suggest intially (note the = has gone in the title)

title GeNtOo LiNuX
kernel (hd0,5)/boot/kernel-genkernel-x86-2.6.17-gentoo-r7
append="root=/dev/sda6 ro"

Tweak this as you wish.

Have you enabled SCSI or more likely SATA support in the gentoo kernel?

If you're still having problems, post your /etc/fstab and the output from 'sudo fdisk -l /dev/sda', Of course, if you're booting gentoo you'll not need the sudo.

---

### Post by noodles_x on 2007-02-09
@confused57
 title=Gentoo Linux 2.6.17-r5
root (hd0,5)
kernel /boot/kernel-genkernel-x86-2.6.17-gentoo-r7 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda6 udev
initrd /boot/initramfs-genkernel-x86-2.6.17-gentoo-r7
it works!

@grazie it doesn't work

thanks for help!

---

