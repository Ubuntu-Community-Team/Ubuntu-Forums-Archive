---
title: "Re-installing Grub2 after XP"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by cr0bar on 2009-12-14
Beforehand, I had Ubuntu 9.10 installed first onto my drive, then I installed Windows 7 afterwards.

I followed this guide to re-installing grub2 and it worked without any problems whatsoever:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

But, now I removed 7 and installed XP in its stead in the same partition (after formatting). Following the same guide works up to the point of chrooting.

Enclosed is the relevant part of the terminal output:

```
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5727    46002096    5  Extended
/dev/sda2   *        5728       11952    50002312+   7  HPFS/NTFS
/dev/sda3           11953       24321    99353992+   7  HPFS/NTFS
/dev/sda5               1         747     6000214+  82  Linux swap / Solaris
/dev/sda6             748        5727    40001818+  83  Linux
ubuntu@ubuntu:/$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:/$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:/$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:/$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error

```

---

### Post by phillw on 2009-12-14
Hi,

you'll be wanting this one -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Should get you back up and running :D

If you have problems, then you can re-install Grub2 - that is over here --> [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Regards,

Phill.

---

### Post by cr0bar on 2009-12-14
Thanks for the reply. I got grub2 reinstalled and Ubuntu boots fine now, but for some reason it's still thinking 7 is in the menu. Looks like I need to get it to detect XP, but that's easily fixed later on.

---

### Post by darkod on 2009-12-14
> **cr0bar said:**
> Thanks for the reply. I got grub2 reinstalled and Ubuntu boots fine now, but for some reason it's still thinking 7 is in the menu. Looks like I need to get it to detect XP, but that's easily fixed later on.

Did you run:
sudo update-grub

The config files might still be "old" and using win7 entry. Grub2 is just restored using same config files.

---

### Post by stlsaint on 2009-12-14
you can simply edit the grub.cfg entry for it to say Windows XP (if thats what you are referring to)

---

