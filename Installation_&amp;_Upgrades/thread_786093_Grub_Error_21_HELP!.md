---
title: "Grub Error 21 HELP!"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by rpage on 2008-05-07
Hi all... 
Had a good install of 7.10 that I upgraded to 8.04. All was well. Then I decided to try to make an install on a usb drive. Booted to live CD and installed to usb jumpdrive. All seemed well... but usb stick got wacked. So, when I went to boot my normal, good install of 8.04 I get a Grub error 21.

I found info via google how to fix it. However, it will not work. Here is what I am doing....

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e3e7af1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42006d26

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4982    40017883+   7  HPFS/NTFS
root@ubuntu:/home/ubuntu# grub-install /dev/hda1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.




Ideas? Suggestions? I am trying to avoid a fresh install. Thanks in advance for your time!!

Rick

---

### Post by Rallg on 2008-05-07
Get to GParted (from live CD) and ensure that the partition you want to boot has the boot flag marked.

Also ensure that the Grub menu.lst does not think that your USB pendrive is the hard drive. I multi-boot from USB without problem (when the USB is not inserted at boot, my computer goes directly to Vista). But I had to modify the Grub menu.lst to refer to the hard drive as hd1 rather than hd0, since Grub on the USB thinks it is hd0 there.

More than that, I know not.

---

### Post by Pumalite on 2008-05-07
This will help further to give you an idea of the nature of the problem:
[http://users.bigpond.net.au/hermanzone/p15.htm#11](http://users.bigpond.net.au/hermanzone/p15.htm#11)

---

