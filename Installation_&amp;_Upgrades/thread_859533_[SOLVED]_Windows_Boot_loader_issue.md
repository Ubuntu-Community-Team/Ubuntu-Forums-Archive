---
title: "[SOLVED] Windows Boot loader issue"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by vijaychandilya on 2008-07-14
I have Windows XP Pro and Ubuntu 8.04 installed on my single hard disk. I want to use the Windows XP boot loader to dual boot. So I followed the instructions and copied the boot sector of the parition that ubuntu was installed in using dd. I copied this over to C:\ and modified the XP boot loader to include this as an option. 

However, when I boot and choose Ubuntu, GRUB just hangs - it shows a blank screen and does not do anything. What am I doing wrong?

Here is my boot.ini:
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\boot.bin="Ubuntu 8.04"
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

P.S. Even the installed Windows Recovery console does not work - it ends in the dreaded Blue Screen. 

Regards,
Vijay

---

### Post by logos34 on 2008-07-15
Boot the live cd and write grub to the boot/first sector of the ubuntu root partition, then run dd again and copy to windows C:\.

Ex: linux is sda2:

> **sudo grub**

grub> **find /boot/grub/stage1**
(it should output 'root hd0,1')
grub> **root (hd0,1)**
grub> **setup (hd0,1)** -->writes grub to root partition
grub> **quit**

Now mount windows partition with write access:

[B]sudo mkdir /media/windows

sudo mount -t ntfs-3g /dev/sda1 /media/windows[/B]

**dd if=/dev/sda2 of=/media/windows/boot.bin bs=512 count=1**

---

### Post by vijaychandilya on 2008-07-15
> **logos34 said:**
> Boot the live cd and write grub to the boot/first sector of the ubuntu root partition, then run dd again and copy to windows C:\.

Ex: linux is sda2:



Now mount windows partition with write access:

[B]sudo mkdir /media/windows

sudo mount -t ntfs-3g /dev/sda1 /media/windows[/B]

**dd if=/dev/sda2 of=/media/windows/boot.bin bs=512 count=1**

That worked, thanks very much! Just for my understanding, what was I doing wrong before? Why did I have to write to linux boot record again using GRUB before copying it over? Or was the issue with the way I had copied it over before?

---

### Post by logos34 on 2008-07-15
I think probably you just needed to write grub to the root partition. (Grub does not write the IPL to the root partition bootsector by default--frankly I don't know why not).  If you don't, and then run the dd command, it just copies an empty sector.  (If you still have the old one you could open it up in hex editor and it would be blank).  That's my guess.

Anyway, glad it works now.  Mark thread as 'solved' (thread tools). Enjoy

---

