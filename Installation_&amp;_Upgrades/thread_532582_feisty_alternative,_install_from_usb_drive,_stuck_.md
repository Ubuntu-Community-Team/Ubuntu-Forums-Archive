---
title: "feisty alternative, install from usb drive, stuck at &quot;detect and mount cdrom&quot;"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by threefcata on 2007-08-22
I 'm trying to install feisty on my thinkpad x31 laptop(256M ram) without a cdrom drive or media dock or whatever. I managed to write grub to the MBR of my SanDisk cruzer micro and boot from it, and I tried using both liveCd and alternative(ISOs). For the liveCD it's just unacceptably slow, I thought I may due to the fact the laptop having only 256M RAM so I tried alternative CD later, but it just got stuck at "detect and mount cdrom" where it always fails.

The MD5 sums of the iso image is right.

I have read about this in other threads, one of them mentioned buying a "pre0loaded" usb stick to solve the problem but I'm geologically impossible to do that. I also read about the issue with some Intel chipsets but X31 is a fairly old model and there shouldn't be problem with the chipset it's using..

Any idea?

thank you

---

### Post by CValentine on 2007-08-23
Well, the problem is, that the alternative CD doesn't work well with removable media. For instance i wasn't able to install from my external USB CD-Rom, but sadly my internal one is broken so i had to come up with a workaround to install to my external hdd from a Live-CD, which will work fine in USB CD-Rom drives.
If you can, borrow an external CD-Rom and follow my guide here: [http://ubuntuforums.org/showthread.php?t=523861]("http://ubuntuforums.org/showthread.php?t=523861")

or maybe this one is an alternative for you (it's experimental, but quite cool :-) ):
[http://wubi-installer.org/]("http://wubi-installer.org/")
Just read the Faq to make sure you know it's pros and cons...

Regards,

CV

---

### Post by pxwpxw on 2007-08-23
> **threefcata said:**
> I 'm trying to install feisty on my thinkpad x31 laptop(256M ram) without a cdrom drive 
...
Any idea?
thank you

Use an installer that does not look for a CD. The installer on your CD looks for a cdrom, cant find it because it is not there. 

See the Installation Guide, Section 4, for the method using a USB stick, or other drive, or a partiton on your internal drive.

[https://help.ubuntu.com/7.04/installation-guide/i386/install-methods.html](https://help.ubuntu.com/7.04/installation-guide/i386/install-methods.html)

The trick is to use grub to boot hd-media installer images (vmlinuz and initrd.gz or equivalent) that look for an iso image of the Alternate install CD, as downloaded but not burned, which you have got. This iso image goes with the installerr images on the external drive or internal partition.

You can also do a very simple network install by just putting netboot install images (described for the USB Stick booting), where you just download and write a boot.img to a usb stick (8MB or so ) and boot that from grub.

The section 4 shows where to get these installer images.
The i386 variety are at

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/)

or your local mirror.

---

