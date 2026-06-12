---
title: "Need help installing GRUB, mainly finding HDD partition."
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by SlaughterDog on 2007-10-10
Well good ol' Windows overwrote my bootloader and now I'd like to get GRUB back. I have tried to use the LiveCD and go into the grub console and use setup (a la [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)) but if I use (hd0,0) it says device does not exist, and if I use (sd0,0) it says error parsing number. I can't even get it to change root to that. My old menu.lst had (hd0,2) for the linux to load though. I had no luck using the find test like they suggest.

How can I find out what to tell it?

---

### Post by ted65 on 2007-10-10
Try this out. It has helped me out several times:

[http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

---

### Post by SlaughterDog on 2007-10-14
I don't think that's what I need. I need help finding out what to tell it to install grub to.

---

### Post by Pumalite on 2007-10-14
Grub is installed to sda1 by default. You can installed in the partition you install the system in. Live CD has the option in step 7 'Advanced Tab'. Now, to know where to point it, do this at the Terminal: sudo fdisk -lu. It will tell you your partitions/drives and you will know what to do.

---

### Post by SlaughterDog on 2007-10-16
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   228556754   114278346    7  HPFS/NTFS
/dev/sda2       228556755   245762369     8602807+   b  W95 FAT32
/dev/sda3       245762370   309733199    31985415   83  Linux
/dev/sda4       309733200   312576704     1421752+   5  Extended
/dev/sda5       309733263   312576704     1421721   82  Linux swap / Solaris

```

I in the grub terminal, I can't type in anything sda without getting 'error parsing number'.

---

### Post by logos34 on 2007-10-16
> **SlaughterDog said:**
> I in the grub terminal, I can't type in anything sda without getting 'error parsing number'.

That's because grub uses the 'hd_' notation for all drives (does not differentiate between ide and scsi)

try this [howto]("http://ubuntuforums.org/showthread.php?t=224351").  You want to overwrite the windows bootloader on the mbr, so use 'setup (hd0)'

---

### Post by SlaughterDog on 2007-10-19
Thanks a lot! I see my problem was not going into the grub console using sudo. Now I've got it installed.

---

