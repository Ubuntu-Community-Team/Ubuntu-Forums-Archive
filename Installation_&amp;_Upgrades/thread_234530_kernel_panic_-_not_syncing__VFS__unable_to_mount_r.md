---
title: "kernel panic - not syncing : VFS : unable to mount root fs on unknown-block(0,0)"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by GeekyGibbon on 2006-08-11
Hi, Im a windows user who's very new to linux, but trying to set up my computer to dual boot to ubuntu.

I installed ubuntu 6.06.1 from the live cd asking it to automatically handle the partitioning of the 30Gb of free space I created using GPartEd. It all seemed to go ok and the grub thing loaded up fine when I rebooted. I checked my windows install and it was still good, but then when I tried to boot to ubuntu I got this error message:
kernel panic - not syncing : VFS : unable to mount root fs on unknown-block(0,0)

Could somebody possibly suggest what may be going wrong and/or how I might go about fixing it? In answering bare in mind that Im new to linux and arnt familiar with using the command line and and the ins and outs of 'mounting drives'.

Any help or suggestions are appreciated. Thanks.

---

### Post by NeoCream on 2006-08-14
Do you use or is the root-partition on a sataII Disk?

---

### Post by mgazb on 2008-04-04
I have just upgraded from Feisty to Gutsy on my HP 6715b laptop. It's dual boot with Vista.

The new kernel 2.6.22-14-generic doesn't boot and I get this error.
I can boot the old 2.6.20-15-generic kernel.

I suspect that it's something to do with the line in /boot/grub/menu.lst

> 
/boot/vmlinuz-2.6.22-14-generic root=UUID=82d9a33a-0c80-4d6b-90b5-13aaff946f6d ro quiet splash


as it seems not to be finding the root partition.

If I run mount the top line reads
> 
/dev/sda5 on / type ext3 (rw,errors=remount-ro)


should I use root=/dev/sda5 instead of using the UUID mechanism?

thanks

dan

---

