---
title: "Grub2 &quot;loopback&quot; and Parted Magic"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-08-18
Someone posted that they tried to get Grub2 and loopback working with partmagic ISO Image. I got it working using this method:

```
menuentry "loop-back-pmagic from harddisk (ISO = pmagic-4.4.iso)" {
  loopback loop ([COLOR="Red"]**hd0,5**[/COLOR])/pmagic-4.4.iso
  linux (loop)/pmagic/bzImage isofrom=/dev/sda5/pmagic-4.4.iso root=/dev/ram0 livecd quiet vga=773 noeject noprompt sleep=0 load_ramdisk=1 prompt_ramdisk=0 loglevel=0 keymap=us
  initrd (loop)/pmagic/initramfs
boot
}
```

Make sure you DO NOT change the name of the pmagic ISO file. If your using pmagic-4.4.iso then use that name only. Otherwise you will be dropped to a busybox. It's recommended to use the current version 4.4. I uses far less memory.

Note: Use your own location where you stored the iso that I have in "red"

---

### Post by ayates on 2009-08-18
Just tried this out and it works like a charm.

Thanks VMC.

---

### Post by ranch hand on 2009-08-18
OK, I am game and this sounds like fun.

What do you do with the iso?  Is this the only think on the partition?  Is the iso just on your Desktop on some existing OS?

---

### Post by ayates on 2009-08-18
Just download the iso from here: [http://wiki.partedmagic.com/index.php/Downloads](http://wiki.partedmagic.com/index.php/Downloads)
to the / directory of any partition. It boots like a livecd.

---

### Post by VMC on 2009-08-18
> **ranch hand said:**
> OK, I am game and this sounds like fun.

What do you do with the iso?  Is this the only think on the partition?  Is the iso just on your Desktop on some existing OS?

Mine os on the root of my fifth partition, you can put the iso anywhere you like, you just have to tell grub where to find it.

If its on your desktop then use:
**isofrom=/dev/sdxX/home/Desktop/pmagic-4.4.iso**

---

### Post by ranch hand on 2009-08-19
VMC & ayates
Thank you both very much.

I am an infatuated lover of grub-legacy.

Grub2 still has a lot of awfully rough spots.  Inspite of that, I am very excited about it.  I think it is going to be just great.

I am not going to use the pmagic-4.4.iso.  I thought I would just use some iso that I have of some live CD.  They should all work the same.

What a great way to check the buggers.  I got one the other day and the md5sum was perfect.  The /boot/grub/menu.lst (Juanty variation) was not all there.  Down loaded it again and it was fine but I had to burn it twice (I really like RW disks) to find out.  The first I would not have caught until trying to install.  But the second I could have checked this way.

Is this neat or what?

Thanks again.  I will try this tomorrow.

---

### Post by ranch hand on 2009-08-20
OK that didn't work and now I am too groggy to continue.  There has to be something simple that I am not getting but I don't know what I have done even.

If this doesn't make sense it is too little sleep.

I'll be back.

---

