---
title: "Installation options on Ubuntu 6.10 desktop CD"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by deehzee on 2007-02-19
Hi,

I am just wondering  about the following situation.

If I try to install ubuntu on an external (USB) hard drive, and do NOT change the default option for the GRUB (which is (hd0)), is the grub going to be installed on the external drive, or in the internal drive?

I am asking this because, when I installed it on the USB drive with /dev/sda for the location of the GRUB, my computer didn't book from the external hard drive.  I edited the line to (hd0,0) and it started to boot (though it did not boot, because it could not access the tty).

Thanks for your replies in advance,
Deb.

---

### Post by deehzee on 2007-02-20
I have an IDE and an SCSI drive (external USB).  If the grub is installed in the SCSI usb hard drive.  What will be the grub name for that drive (hd0) or (hd1)?

---

### Post by deehzee on 2007-02-22
Hi :

After reading the GRUB manual I was able to solve my problem.  So I thought I will share it for the benefit of the others.  Here are the main points:

(Remember: I had two hard drives -- an internal IDE hard drive, and an external USB (SCSI) hard drive).

1.  If the USB drive (with Grub installed on its MBR) is the device you are booting from, then the GRUB will always see this drive as (hd0).   So in my case, after GRUB loads from the USB drive,  (hd0) refers to the USB drive, and (hd1) refers to the internal hard drive.

2.  So I went to command line in GRUB, by pressing "c".  and edited the root line to (hd0,0), this is where I have /boot  necessary to boot the ubuntu distribution (feisty herd4).

3.  After booting into the ubuntu, I changed /boot/grub/menu.lst  and edited the root line to (hd0,0) for the ubuntu distributions.  

4.  I also wanted to boot the Windows XP on my internal hard drive from the USB GRUB screen.
So I added the lines for windows in the menu.lst as follows

```

# on /dev/hdc2
title		Microsoft Windows XP Professional
## Need to swap the drives (see p.13 of GNU Grub manual)
map		(hd0)	(hd1)
map		(hd1)	(hd0)
root		(hd1,1)
savedefault
makeactive
chainloader	+1

```

Please note, that I have the windows on the second partition of my internal hard drive, which is why ubuntu sees it in /dev/hdc2.  For the Grub it is (hd1,1).  Also note the  "map" commands.  Yo need to swap (hd0) and (hd1) if windows is not in the same hard drive as the GRUB.

5.  Finally if you make mistake anywhere, there is an useful CD called "Super GRUB disk." 

I hope it helps.  Comments and corrections are most welcome!

---

