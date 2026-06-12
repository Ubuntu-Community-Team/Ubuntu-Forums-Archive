---
title: "GRUB2 ISO boot from ext4 AMD64"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by mitcoes on 2010-11-28
I've asked a solution and read a good one for ext2, but it does not work in my ext4 AMD64.
It is in spanish, you can translate with google translate or any other or even read only the commands.

[http://usemoslinux.blogspot.com/2010/11/como-arrancar-una-imagen-iso-desde.html#more](http://usemoslinux.blogspot.com/2010/11/como-arrancar-una-imagen-iso-desde.html#more)

In ext2, more or less the entry must be

menuentry "Lubuntu Live" { 
set root=(hd0,5) 
loopback loop /vbox/lubuntu-10.10.iso 
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/vbox/lubuntu-10.10.iso -- 
initrd (loop)/casper/initrd.lz 
}

but in ext4, it gives me an error of 

file not found
you must load kernel first
even i changed, after an ls in GRUB the hd0.5 by hd0.msdos5, in my case hd0.msdos1, but with upper simple commas as in the main kernel entry.

I think there would be an easy way of adding ISO rescue - or prove - images to GRUB menu from the program in system/administration/boot manager, but in the meantime, a section in GRUB ubuntu main page explaining how to do this in ext2 - as I post - and in ext4 - as I ask someone to explain me how to do -


My 40_custom, where only works Ubuntu entry is: 



#!/bin/sh 

exec tail -n +3 $0 

# This file provides an easy way to add custom menu entries. Simply type the 

# menu entries you want to add after this comment. Be careful not to change 

# the 'exec tail' line above. 



menuentry "Ubuntu, with Linux 2.6.35-23-generic" --class ubuntu --class gnu-linux --class gnu --class os { 

recordfail 

insmod part_msdos 

insmod ext2 

set root='(hd0,msdos1)' 

search --no-floppy --fs-uuid --set c617a74c-d199-49fc-997e-77ebbe33a8bb 

linux /boot/vmlinuz-2.6.35-23-generic root=UUID=c617a74c-d199-49fc-997e-77ebbe33a8bb ro quiet splash nomodeset # video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap 

initrd /boot/initrd.img-2.6.35-23-generic 

} 

menuentry "Rescatux" { 

recordfail 

insmod part_msdos 

insmod ext2 

set root='(hd0,msdos1)' 

loopback loop /isos/rescatux.iso 

linux (loop)/casper/vmlinuz boot=casper locale=es_ES bootkbd=es console-setup/layoutcode=es quiet splash iso-scan/filename=/isos/rescatux.iso -- 

initrd (loop)/casper/initrd.lz 

} 



menuentry "rescatux2" { 

set root='(hd0,msdos1)' 

loopback loop /isos/rescatux.iso 

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/isos/rescatux.iso -- 

initrd (loop)/casper/initrd.lz 

}

---

### Post by dino99 on 2010-11-28
The bible is there:

  [http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

---

### Post by oldfred on 2010-11-28
Do not know if lubuntu is set up for loop mouting.


Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

This worked for Maverick ISO on harddrive in hd0,5, but hd0,5 was really sdc5 as I boot sdc. I prefer the set isofile style as it seems a little cleaner.
```
menuentry "Ubuntu 10.10 Maverick ISO 64bit" {
    set isofile="/boot/ISO/maverick-desktop-amd64.iso"
 
    loopback loop (hd0,5)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by mitcoes on 2010-12-03
Thanks, I tried with burg that has a similar sintaxis than normal grub , because my grub put msdos1 as the partition number hd(0,msdos1) and it did not work, I'll keep trying. But I think the problem resides in that my boot partition is **ext4 istead of ext2** and I must do anything different.

I will try to put 
insmod ext2
but it did not work for the other methods I tried


this is my normal entry, but is not the case:


menuentry 'Ubuntu GNU/Linux, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c617a74c-d199-49fc-997e-77ebbe33a8bb
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=c617a74c-d199-49fc-997e-77ebbe33a8bb ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}

---

### Post by oldfred on 2010-12-03
I got those kind of error messages whenever I had the path incorrect. Are you referring to the correct drive, partition, then you have to from / have exact path.

---

### Post by drs305 on 2010-12-03
I just put an entry for Lubuntu in my ISO submenu and it worked properly. As with *oldfred* think it is an address problem. I don't have a Maverick version to test.

The ISO is stored on sdb6 in /iso
> 
menuentry 'Lubuntu ISO          sdb6'                        {
loopback loop (hd1,6)/iso/lubuntu-10.04.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/lubuntu-10.04.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


---

