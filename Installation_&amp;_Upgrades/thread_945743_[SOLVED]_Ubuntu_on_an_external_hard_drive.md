---
title: "[SOLVED] Ubuntu on an external hard drive"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by dharmabum4732 on 2008-10-12
Hello,

I'd really like to install Ubuntu on an external hard drive to try it out; but after various attempts, I can't seem to get it to boot.  After doing some research I found that this may be a problem with my BIOS settings, but I'm not really sure.  At this point, I'd like to start from scratch and ask for some advice before I try again.

Here is an outline of my hardware:

-Motherboard: Asus P5E3 Premium
-Hard drives: 2x298GB in (soft) raid 0
-USB external hard drive (from which I'd like to boot Ubuntu)

I hope that the above information is sufficient: please let me know if any additional information would be helpful.

Best,
-Max

---

### Post by dharmabum4732 on 2008-10-12
I tried again, but still no luck.

I installed ubuntu 8.04 from a live CD onto my external hard drive
-The drive was labeled "sdc"
-To avoid affecting my MBR on my internal drives, I clicked on the advanced button at the end of the setup and installed the boot loader on the sdc1 partition.

When I tried to boot up, I configured my BIOS settings to boot from a usb device.  Then I get an error.  The error is "error 21: selected disk does not exist."

Any suggestions?
-Max

---

### Post by dharmabum4732 on 2008-10-12
Hello,

Sorry if it seems like I'm talking to myself, here; but I wanted to include some potentially useful information.

When I booted from the live CD, I did "sudo fdisk -l" in the terminal (I've seen this done in a variety of similar posts).

Here is the outcome:
```
ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xbe58e3c5 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       77826   625135616    7  HPFS/NTFS 
 
Disk /dev/sdb: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x00000000 
 
Disk /dev/sdb doesn't contain a valid partition table 
 
Disk /dev/sdc: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x28f12a69 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *           1       13995   112414806   83  Linux 
/dev/sdc2           13996       14593     4803435    5  Extended 
/dev/sdc5           13996       14593     4803403+  82  Linux swap / Solaris
```

Then I also looked to see what was in the /boot/grub/menu.list file.

Here it is:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fb459d9d-1116-448d-aef3-4bdd422fc5a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fb459d9d-1116-448d-aef3-4bdd422fc5a4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet
```

Any thoughts?
-Max

---

### Post by caljohnsmith on 2008-10-12
If you told Grub to install to /dev/sdc1, that's the boot sector of the sdc1 partition; the problem with that is you need a boot loader in the MBR (Master Boot Record) in order to boot the HDD. Therefore, you should have used /dev/sdc to install Grub to the MBR. 

But the good news is you don't have to reinstall just to put Grub in the MBR of sdc. Just follow these easy steps:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
And that should make your sdc drive bootable. The next problem is with your menu.lst, so if you can open that up again (as root user), then change all your Ubuntu entries to use "root (hd0,0)" instead of "root (hd2,0)". Let me know how it goes or if you run into problems. :)

---

### Post by dharmabum4732 on 2008-10-12
Hi caljohnsmith,

Thanks for the advice!  I will try it now and post the results.

---

### Post by dharmabum4732 on 2008-10-12
Hi caljohnsmith,

You've solved the problem.  Thank you!

---

### Post by caljohnsmith on 2008-10-13
That's great news it's working, and glad I could help out. Cheers and have fun. :)

---

