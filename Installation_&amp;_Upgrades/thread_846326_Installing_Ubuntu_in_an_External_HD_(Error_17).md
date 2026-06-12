---
title: "Installing Ubuntu in an External HD (Error 17)"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by Hoffmann on 2008-07-01
Hi All,

First of all, I need to say that I was able to install Fedora 9 in my external USB hard drive; I was able to boot on that device; etc.
However, since I AM A BIG UBUNTU FAN, I would like to install it, instead.
ok.
The problem is that when I install Ubuntu in my external USB HD, I get the error:

ERROR 17: Cannot mount selected partition.

So, I did the following:

(1) I checked it out the /boot/grub/menu.lst, and I got:
...
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0fbc8e14-6ef6-4667-9ad2-03753e7131bc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0fbc8e14-6ef6-4667-9ad2-03753e7131bc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet


(2) So, by using the Live CD, and using the terminal:
sudo fdisk -l
I got:
...
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1300    10442218+  83  Linux
/dev/sdb2            8667        9039     2996122+   5  Extended
 

(3)sudo grub
grub> find /boot/grub/stage1
grub> (hd1,0)

(4) grub> root (hd1,0)

(5) grub> setup (hd1)

(6) grub> quit

 --> And I reboot the system, I got ERROR 17 again!


(7) I decided to reinstall grub, like this:
sudo grub-install --root-directory=/mnt/root /dev/sdb

---> After rebooting the system, I got ERROR 17 once again!

Could anyone, please, let me know what I am missing?

Thanks a lot!

---

### Post by dstew on 2008-07-01
Do you get this error after selecting a grub menu item, or before the menu appears?

---

### Post by Hoffmann on 2008-07-01
I got that error after selecting a grub menu item.

---

### Post by Willberg on 2008-07-01
I get this error too, trying to install on my external IDE USB-Enclosed hard drive. Error 17.

I, too, have the same boot commands in grub. I tried messing with them, but to no avail. I know significantly less about Linux than the OP though.

Any help, much appreciated!

---

### Post by Pumalite on 2008-07-01
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
I think you have to install Grub to the external and then edit /etc/menu.lst and make 'groot' and 'root' (hd0,0)
Check this link too:
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)

---

### Post by mvdberg112 on 2008-07-01
> **Hoffmann said:**
> (3)sudo grub
grub> find /boot/grub/stage1
grub> (hd1,0)
(4) grub> root (hd1,0)
(5) grub> setup (hd1)
(6) grub> quit
 --> And I reboot the system, I got ERROR 17 again!

(7) I decided to reinstall grub, like this:
sudo grub-install --root-directory=/mnt/root /dev/sdb
---> After rebooting the system, I got ERROR 17 once again!

You are booting with something else, I understand, because you are using Grub. Looks to me that booting from the USB and booting from the (live) CD (or whatever), give different numbers to the disk.
Assume that the disk, the format and the installation is all OK. Then Error 17 would mean that a disk is defined that is broken, corrupt, not existing.

Your command:
```
setup (hd1)
```
apparently worked, because Grub came up, but just did not want to boot the right Linux installation! So we need to look in the menu.lst.

So, try to boot from USB again. Do not choose any Grub option, but select 'c' (command)
Does "find /boot/grub/stage1" work here? What is the output? 
Does for example root (hd0,0) work? or root (hd1,1)? Because the BIOS is reading the USB over the normal hdd, maybe the USB is seen as the first HDD (=hd0), instead of the second (=hd1).
Also, give us a copy of the menu.lst item that you are choosing. For example, mine looks like this: 
```
title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=4cb72186-2c06-4fab-957e-e8772f34bf9c ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

```
Is your UUID right? I had that once wrong. There is an article telling how to find it and get it right.

---

### Post by Willberg on 2008-07-01
mvdberg112 fixed it! Thanks!

Running 

find /boot/grub/stage

Gave me (hd0,0), rather than (hd1,0), which is what was in the boot commands. So I just changed it, and it booted fine. I'm talking to you from my Ubuntu now!

---

### Post by Hoffmann on 2008-07-03
Hi,

Thanks a lot everybody!
Well, my working around to that problem was to re-install Ubuntu (ALTERNATE desktop CD), and installing Lilo boot manager on /dev/sdb1, instead of Grub. All work this time.

Hoffmann

---

