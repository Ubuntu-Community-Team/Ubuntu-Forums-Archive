---
title: "Dual Booting XP Ubuntu Grub Error Two HDDs"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by yellolegalpad on 2007-12-06
I've read through many other threads and continually run into a parameter that I think doesn't affect my situation and finally decided to post my own.  I'm very new to ubuntu linux, so detail would be very welcomed.  I recently installed a dual boot system on the same HDD on my Dell laptop with Ubuntu 7.1  following these instructions: [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

It worked amazingly well considering all of the dual boot problem threads I've read.  No problems.  The instructions required me to use this code to mount the share and copy the ubuntu.bin to boot from into the ntfs windows partition:

mkdir /mnt/osshare
mount -t msdos /dev/hda6 /mnt/osshare
dd if=/dev/hda2 of=/mnt/osshare/ubuntu.bin bs=512 count=1

I then directed the windows boot.ini to this file that I copied from the share into my windows C:\ drive.

No problems.  I then decided that I liked ubuntu so much that I wanted the same on my desktop on dual HDDs.  Windows is installed on a 60GB (hda0) and I installed ubuntu onto an extra 20GB  (sdb).  I partitioned everything before hand - sdb1 is ext3, sdb2 is linux-swap, sdb3 is fat32 for share.  And then once again followed the instructions from the before mentioned page to mount the share and copy the ubuntu.bin to my C:\ drive and then open windows boot.ini to add Linux to the windows boot page.  

Problem:  When I select Ubuntu Linux from the boot page I get a screen like this:

"Grub" *flashing cursur*

I then set sdb as primar HDD to boot from in BIOS and get

"Error 22"

I can load my installed ubuntu OS from the system rescue CD mentioned on the instruction page I used, but that seems to be the only way.  

Where's my problem??

thanks!

---

### Post by yellolegalpad on 2007-12-06
It may also be worth mentioning the code I used on my desktop:

mkdir /mnt/osshare
mount -t vfat /dev/sdb3 /mnt/osshare
dd if=/dev/sdb1 of=/mnt/osshare/ubuntu.bin bs=512 count=1

(where sdb3 is my fat32 share partition and sdb1 is my linux installed partition)

the ubuntu.bin shows up in windows and I copy it to C:\ (hda) and tell the windows boot.ini to add it to the boot menu: C:\ubuntu.bin="Ubuntu Linux"

Also - my desktop uses the amd64 version of ubuntu - this is different from my laptop which is not 64bit.

---

### Post by yellolegalpad on 2007-12-07
any thoughts?

---

### Post by confused57 on 2007-12-07
I've never used boot.ini to boot linux, so I'm not sure what the problem may be, but you might want to boot into Ubuntu(using the Rescue cd) and post the output of:
```
gedit /boot/grub/menu.lst
```
and
```
gedit /boot/grub/device.map
```

For your menu.lst, you probably just need to post the OS boot entries.

---

### Post by yellolegalpad on 2007-12-07
menu.lst:

```
## ## End Default Options ## 

title		Ubuntu 7.10, kernel 2.6.22-14-generic 
root		(hd2,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a6f458c1-2eef-4348-b5af-2b1b478b5722 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
quiet 

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root		(hd2,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a6f458c1-2eef-4348-b5af-2b1b478b5722 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 

title		Ubuntu 7.10, memtest86+ 
root		(hd2,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 


```

device.map

```

(hd0)    /dev/hda
(hd1)    /dev/sda
(hd2)    /dev/sdb
(hd3)    /dev/sdc

```

---

### Post by confused57 on 2007-12-07
Here's a description of grub error 22:
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

You might also want to post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

I was under the impression that you only had 2 hard drives, fdisk -l will show info on your other 2 drives that may or may not be relevant to your problem.

You can use the Ubuntu live cd to reinstall grub to the root partition:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Read the instructions in the thread, but you won't install to (hd0), but to the partition that "find /boot/grub/stage1" finds, e.g.
root (hd2,0)
setup (hd2,0)

Also, when you boot first to your Ubuntu drive you could try "trial & error" to see if your Ubuntu will boot with a different root drive...you can do this by highlighting your Ubuntu entry in the grub boot menu, press "e" to edit, then highlight the line with root, press "e" again, change root from (hd2,x) to (hd1,x), press "enter", then "b" to boot...x means leave this as it is...if this doesn't work, try changing root to (hd3,x), using this method....or even try (hd0,x).  On second thought, you'd need to try (hd0,x) first.

***Added***:  I would recommend that you use grub to boot your Ubuntu drive and you can also add an entry to boot your Windows drive to your menu.lst.  This will require that your Ubuntu root be (hd0,x), which if the temporary method above works, you can make it permanent in you /boot/grub/menu.lst.

---

