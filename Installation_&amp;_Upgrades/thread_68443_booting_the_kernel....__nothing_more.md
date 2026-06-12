---
title: "booting the kernel....  nothing more"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by Svargon on 2005-09-23
I updated my system by running apt-get upgrade and apt-get dist-update.  Hours later when I rebooted the system I notice 

Uncompressing Linux...OK booting the kernel             thats it nothing more.

I tried rebooting into recovery mode and I get the same thing.
I booted off a Knoppix CD and I examined my grub configuration: 

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

memtest86+ seems to work.

I am wondering what is the best way to recover from this?  

I would like to try to save the system without re-installing.
I have an Athlon XP 1350 MHz

Any help would be appreciated.   Thanks in advance..

 ](*,)

---

