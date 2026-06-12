---
title: "Installation from Windows"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by cornsnap on 2007-05-25
Hi,

I am doing an installation from within Windows 2000 (I do not have floppies or cdrom on my laptop) following the Ubuntu documentation and it says to "Download linux and initrd.gz from....".  The link does allow me to download the initrd.gz but I don't understand what they mean by "Download Linux"?  Does this mean download the iso of Ubuntu?

Thanks.

---

### Post by rillip on 2007-05-25
Would you mind posting the link you are reading this from?  Personally I am not aware of a way to do what  is being proposed, and I don't see any way that would work.  If you were going to try and do a dual boot, it couldn't because the partitions would be active and you wouldn't be able to create new ones with gparted.  I suppose if you already had them set up it MIGHT be possible, but the idea of installing one OS from inside another OS seems... error prone.  If you were trying to do a full install, I don't see how you could do that, since there are Windows system files active and the disk will not be formatable.

I'm not saying it can't be done, but it doesn't make sense to me how it can be acomplished.  If you can provide the link, maybe it'll become more clear.

---

### Post by cornsnap on 2007-05-25
Here is the link.


[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by rillip on 2007-05-25
Lemme review, will edit this post with any advice

Okay, I understand how this is going to work. If you follow the link,

[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)

One of the files there is named linux and another is named initrd.gz.  Those are the two files it is telling you to download.  The proceede with the instructions.

Basically, it's adding a line to your boot.ini to let you install completely over the net.  This'll take a while, but it doesn't actually install it from within Windows, it's done before Windows boots.  

Good luck!

---

### Post by cornsnap on 2007-05-25
I've done that now I have a directory called c:\boot which contains the linux and initrd.gz files.  I've configured my boot.ini and grub.  However I get this message after choosing the Ubuntu install in grub.

kernel (hd0,0)/boot/linux vga=normal ramdisk_size-14972 root=/dev/rd/0 rw -- [Linux-bzImage, setup=0x1c00, size=0x1a82cc]

initrd (hd0,0)/boot/initrd.gz

Error 17: File not found

Any ideas?

Thanks.

---

### Post by rillip on 2007-05-27
Sorry, never used this method before.  Hopefully someone with more knowledge comes along and will know.

---

