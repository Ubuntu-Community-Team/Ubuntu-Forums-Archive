---
title: "[SOLVED] Grub stage 2 read error, no menu...right after fresh install"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by Margus81 on 2008-10-04
I have 2 hard disks - one 320Gb with new cable (dont know the names)
3 partitions c,d,e.... c with Vista

Second HDD I added specially for linux... 40GB

With Ubuntu or OpenSuse - both fail just after fresh install...

I though the problem to be one of those dual boot/Vista problems...

But after reading and making all those grub /boot/grub/menu.1st stuff I read...nothing helped...

I took away the Vista disk...

leaving only one HDD purely for linux...


Again - failed!

The problem might be, that since the smaller HDD is still with the old cable (the wide one) and the motherboard has only one slot for this cable, I had to connect it together with the DVD rom.

Now, again, as with or without 320GB hdd, I can complete the installation, it recognises all the discs...and with live CD I can surf all partitions...

But Grub somehow fails to read it...

I tried with jumpers - made DVD master HDD slave and opposite...


same thing always :( Grub Loading----stage 2Read Error...


The Grub Menu never appears...


I am really out of options here...

should I format the 40GB to Fat32 and Install Linux so that it puts himself after that? Maybe first GB would be Fat and then linux partition begins? Should it help...

?

---

### Post by Pumalite on 2008-10-04
Can you boot a Live CD or did you install with an Alternate CD. If the first, then: post:
sudo fdik -lu

---

### Post by Margus81 on 2008-10-04
Thank you for the quick responce! I did live CD...

however now I am in the middle of reinstalling (with fat in the beginning)

If it fails, I can run the LiveCD and give you the results!


Thank You!

---

### Post by Margus81 on 2008-10-04
In the meanwhile I did opensuse install...failed...

Then I turned back to Ubuntu - made livecd install with "use whole disk" partitioning

After install and restart - same thing...

Now the fdisk thing You asked for:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x085c085c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74862899    37431418+  83  Linux
/dev/sda2        74862900    78156224     1646662+   5  Extended
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris

---

### Post by Margus81 on 2008-10-04
Meanwhile, as I am waiting for the help...I will post some stuff...

grub> find /boot/grub/stage2
find /boot/grub/stage2
 (hd0,0)

grub> root (hd0,0)
root (hd0,0)

grub> setup (hd0) 
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> find /boot/grub/menu.lst
find /boot/grub/menu.lst
 (hd0,0)

The menu.lst file>

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d5728151-a1c2-46a1-9afd-a421819eed1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d5728151-a1c2-46a1-9afd-a421819eed1f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


And one other thing I noticed:
I have like two drives to go to on my LiveCD now:
File System (Size 1.4 GB)
38.8 GB Media

The Grub Folder is NOT on File System, but 38.8 Media...
so /boot/grub.. does not exist.

It is /media/disk/boot/grub

Maybe it gives a picture....

---

### Post by Margus81 on 2008-10-04
Ok!

I KIND OF found the solution. After removing the DVD it started working.


Conclusion:

GRUB DOES NOT WORK IF THE HDD SHARES ITS CABLE WITH DVD. NO MATTER WHICH ONE IS THE MASTER.
I THINK IT IS A PROBLEM.

Now I have to think, whether I use Ubuntu without the DVD rom (which I actually do not use that often) or stick with Vista

---

### Post by Margus81 on 2008-10-23
I have to apologize!!!

Even Windows could not restart with my setup. 
So it is not the fault of the Grub.

I did Windows install, I read and formatted the disc, copied the files..

The made a restart and could not do it!

Only after I removed the DVD, it could restart. Sadly it required the CD to go on...

I have one USB DVD also, but I don't know how to use so early...

Bios???

---

