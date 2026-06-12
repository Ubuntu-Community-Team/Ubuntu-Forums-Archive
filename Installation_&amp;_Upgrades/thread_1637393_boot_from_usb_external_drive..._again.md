---
title: "boot from usb external drive... again"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by nthali on 2010-12-04
hello,
this is really a continuation of my previous failed tries to install ubuntu on an external hard drive. first i tried installing it in a partition of my 500G external drive (first partition was a ntfs), and it wouldn't boot from it - think i got the grub rescue prompt
then following this link: [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
i had ubuntu "erase and use entire disk" for my external drive.
again, after the install and reboot, i hit "Esc"during the boot and chose the "boot from usb" option, and now i get the "grub>" prompt.
weird thing is when i do an "ls"at the grub prompt i see:
(hd0) (hd0, msdos1) (hd1) (hd1,msdos2) (hd1, msdos1)
which doesn't make sense, since i asked ubuntu to erase my entire hd1. setting root to any of these throws an "unknown filesystem" error.
do i need to manually muck around with the grub config to be able to boot ubuntu?

Thanks,
Nilesh

---

### Post by cosine352 on 2010-12-04
probably your grub is in the internal hdd. so try to boot from the internal hdd and I guess it will give you the option to boot the external hdd in the menu list.

---

### Post by efflandt on 2010-12-04
The drive you boot from will show in grub as (hd0), even if it ends up as sdb or sdf once Linux is running.

Do you end up in grub or grub rescue prompt?  Do you get any strange output or errors from there when doing:

ls (hd0, msdos1)/
ls (hd0, msdos1)/boot
ls (hd0, msdos1)/boot/grub

Use gparted from live CD or USB iso to delete that partition and create a 100 GB partition at the beginning of the USB drive, manually install there (and make sure grub is there at bottom of install partition screen) and see if that works.

Some computers, including my new desktop, just cannot boot way out on a larger USB drive, even though they have no problem booting well beyond 500 GB on their internal drive.

---

### Post by wilee-nilee on 2010-12-04
This is basically the same problem of your 2 other threads do this, with the external plugged in.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

