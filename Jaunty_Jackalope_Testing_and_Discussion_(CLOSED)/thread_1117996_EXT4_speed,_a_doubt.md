---
title: "EXT4 speed, a doubt"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-04-06
As in the post title, I have a doubt about the speed of ext4 fs; I switched completely (/) on ext4 and I forced an fsck to the next reboot
```
cd /
sudo touch /forcefsck
```
Well when the fsck took place on the next reboot the speed of the action is quite slow, let's say similar (or a little be slower) than ext3, and in my view nothing is changed from before.

I ask this because I've read around that the speed of fsck on ext4 is noticeable quicker.

Any thought?

---

### Post by amano on 2009-04-06
Just updating to ext4 will only keep everything in ext3 format and just newly written files will use extents (which is the main advantage of ext4).

---

### Post by screaminj3sus on 2009-04-06
I used a fresh install to switch to ext4 and it is notceably faster than ect especially with boot times.

---

### Post by nu2this on 2009-04-06
> **screaminj3sus said:**
> I used a fresh install to switch to ext4 and it is notceably faster than ect especially with boot times.

Does that mean that I would do this:
1. have all of my vital documents backed up (done anyway)
2.Prior to installing Jaunty wipe my HDD completely
3.Then install Jaunty then replace My backed documents into the new /home
Is this how I'd get the speed & other benefits of ext4 from the get go?

---

### Post by graysky on 2009-04-06
This might be a stupid question, but where is the defrag tool that works on ext4?  I can't find it in the jaunty repo...

---

### Post by TrueTom on 2009-04-06
> **graysky said:**
> This might be a stupid question, but where is the defrag tool that works on ext4?  I can't find it in the jaunty repo...

There is no such thing (yet).

---

### Post by dentaku65 on 2009-04-06
> **amano said:**
> Just updating to ext4 will only keep everything in ext3 format and just newly written files will use extents (which is the main advantage of ext4).

Thanks for the info amano.
In meanwhile I've istalled the kernel 2.6.29.1 downloaded from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
But when I choose it from Grub I get this error message:
> Grub Error 13: "Invalid or unsupported executable format"
No problem if I boot with 2.6.28-11 Ubuntu kernel.
So, my question is: is grub recognizing properly a file written on ext4 fs?
My system has only Ubuntu installed; I've tried with a different kernel (2.6.29rc8 ), but same result.

Here my last part of /boot/grub/menu.lst
```
title		Ubuntu jaunty (development branch), kernel 2.6.29-020629rc8-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.29-020629rc8-generic root=UUID=a1487447-90fe-458d-a594-bc70d233ed59 ro splash vga=791 quiet 
initrd		/boot/initrd.img-2.6.29-020629rc8-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.29-020629rc8-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.29-020629rc8-generic root=UUID=a1487447-90fe-458d-a594-bc70d233ed59 ro  single
initrd		/boot/initrd.img-2.6.29-020629rc8-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a1487447-90fe-458d-a594-bc70d233ed59 ro splash vga=791 quiet 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a1487447-90fe-458d-a594-bc70d233ed59 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-10-generic root=UUID=a1487447-90fe-458d-a594-bc70d233ed59 ro splash vga=791 quiet 
initrd		/boot/initrd.img-2.6.28-10-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-10-generic root=UUID=a1487447-90fe-458d-a594-bc70d233ed59 ro  single
initrd		/boot/initrd.img-2.6.28-10-generic

title		Ubuntu jaunty (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```
Here my /boot/grub/device.map
```
(hd0)	/dev/sda
```

---

### Post by dabl on 2009-04-06
On a clean installation of Kubuntu 9.04 Beta, 64-bit, on an ext4 partition, I can assure you the fsck is WAYYYYYYYYYY faster than on ext3.  I haven't measured it, but there's no question about it -- the first time I saw it, I thought it had aborted the fsck, it was so much faster.   :guitar:

But the basic boot time seems about the same.  Actually, there is a noticeable delay in starting the boot, after the grub menu disappears and before the boot process begins.  Then it goes about the same as on ext3.

---

### Post by FuturePilot on 2009-04-06
> **dentaku65 said:**
> As in the post title, I have a doubt about the speed of ext4 fs; I switched completely (/) on ext4 and I forced an fsck to the next reboot
```
cd /
sudo touch /forcefsck
```
Well when the fsck took place on the next reboot the speed of the action is quite slow, let's say similar (or a little be slower) than ext3, and in my view nothing is changed from before.

I ask this because I've read around that the speed of fsck on ext4 is noticeable quicker.

Any thought?
The speed of fsck on Ext4 mainly comes from the fact that it doesn't need to check empty blocks. So if your drive is rather full, you might not see the speed difference as much.

> **amano said:**
> Just updating to ext4 will only keep everything in ext3 format and just newly written files will use extents (which is the main advantage of ext4).

This shouldn't have anything to do with fsck speed.

---

### Post by BGFG on 2009-04-06
> **TrueTom said:**
> There is no such thing (yet).
 :)

[http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/](http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/)

[http://lwn.net/Articles/284529/](http://lwn.net/Articles/284529/)

@graysky. I would not suggest you use it yet though.

---

### Post by dentaku65 on 2009-04-07
> **FuturePilot said:**
> The speed of fsck on Ext4 mainly comes from the fact that it doesn't need to check empty blocks. So if your drive is rather full, you might not see the speed difference as much.



This shouldn't have anything to do with fsck speed.

So in this case I confirm the same performance of ext3 with ext4 on fsck; my hd have 85% of free space.

---

