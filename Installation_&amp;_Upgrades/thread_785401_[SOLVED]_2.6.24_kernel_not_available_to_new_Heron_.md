---
title: "[SOLVED] 2.6.24 kernel not available to new Heron install"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by jsimerly on 2008-05-07
Just upgraded from 7.10 to 8.04.  /boot/grub/menu.lst boot entries:

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.24-17-generic root=/dev/mapper/rootvg-root_lv ro quiet splash
initrd          /initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.24-17-generic root=/dev/mapper/rootvg-root_lv ro single
initrd          /initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.24-16-generic root=/dev/mapper/rootvg-root_lv ro quiet splash
initrd          /initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.24-16-generic root=/dev/mapper/rootvg-root_lv ro single
initrd          /initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/rootvg-root_lv ro quiet splash
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/rootvg-root_lv ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 8.04, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/rootvg-root_lv ro quiet splash
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/rootvg-root_lv ro single
initrd          /initrd.img-2.6.20-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

Running kernel:

uname -r
2.6.22-14-generic

When I reboot, the only boot options are:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernel 2.6.20-16-generic
Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
memtest

Given that my grub menu.lst file references Ubuntu 8.04, where in the world is the bootloader reading Ubuntu 7.10?  Is there a "shadow" menu.lst file that gets read instead of the "real" /boot/grub/menu.lst?

Here is /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/rootvg-root_lv /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1 -- converted during upgrade to edgy
UUID=89fde834-d7dd-4b97-9ebb-88f4f503ab11 /boot ext3 defaults 0 2
/dev/mapper/home_data_vg-home_lv /home           ext3    defaults        0       2
/dev/mapper/home_data_vg-opt_lv /opt            ext3    defaults        0       2
/dev/mapper/home_data_vg-src_lv /source         ext3    defaults        0       2
/dev/mapper/home_data_vg-srv_lv /srv            ext3    defaults        0       2
/dev/mapper/home_data_vg-tmp_lv /tmp            ext3    defaults        0       2
/dev/mapper/rootvg-usr_lv /usr            ext3    defaults        0       2
/dev/mapper/home_data_vg-usr_local_lv /usr/local      ext3    defaults        0       2
/dev/mapper/home_data_vg-var_lv /var            ext3    defaults        0       2
/dev/mapper/home_data_vg-var_log_lv /var/log        ext3    defaults        0       2
/dev/mapper/home_data_vg-backup /backup        ext3    defaults         0       2
/dev/mapper/rootvg-swap_lv none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by fixitdude on 2008-05-07
It's got to be getting info from somewhere else, the list you show doesn't have memtest in it, but the boot menu does!

Maybe hardy doesn't like that you have this device:

/dev/mapper/rootvg-root_lv /

And also this one:

UUID=89fde834-d7dd-4b97-9ebb-88f4f503ab11 /boot

The first one probably has a /boot directory too, kernel doesn't know what to do and probably uses the first one at boot.

Some older install messed up your fstab I think. I hate these UUID things, it just makes things harder to figure out.

I don't want to make your system unbootable, so try this at your own risk and remember that you can use terminal by booting from the live CD and then you can edit your fstab if the thing doesn't boot.

WARNING: Make sure you know how to boot the live CD and access your HD via terminal, and how to edit a simple file.

Make a copy of the good newer menu list file, copy it to /home since that shouldn't change when we do this.

That said, I would first try commenting out the one line like this

# UUID=89fde834-d7dd-4b97-9ebb-88f4f503ab11 /boot

If that works you may have to put the newer entries into the menu list etc. and the kernels may not be there now so that's another problem you have to figure out how to copy them over. Maybe the live CD can help mount the /boot from the UUID.

I don't like the look of your fstab anyway, you should look into fixing it.

---

### Post by jsimerly on 2008-05-07
Fixitdude, thanks for the step-by-step suggestion.  While checking out the live CD for system functionality, I mounted /dev/sda1 to /mnt/boot.  I went into /mnt/boot and found the /boot/grub/menu.lst that corresponds to the only boot options my system has (Ubuntu 7.10).


# fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000024f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+  83  Linux
/dev/sda2              19        9039    72461182+   5  Extended
/dev/sda5              19        9039    72461151   8e  Linux LVM

So, problem found.  Fixing it, that's another story.

Even if I commented out the UUID entry in /etc/fstab, I don't see how it would work.  Obviously, I set up a separate disk partition for /boot when I built the system a few years ago.  By the time the system boots to a user level, the /boot partition on /dev/sda1 has been over-mounted by the /boot directory contained in the root file system of the Linux LVM extended partition /dev/sda5.  So the /etc/fstab file is not even read because the /dev/sda1 Linux partition is the first bootable partition found.

---

### Post by fixitdude on 2008-05-07
If you comment that then it boots from the new stuff /boot, the one that's NOT sda1, right? Grub should be looking in /boot, which would then be the new one.

Oh, maybe you have to set / to boot too, might take a bit more research.

EDIT: OK, maybe a quick fix, copy *all* the new stuff /boot over to the old "sda1" /boot and it should boot OK. Save the old /boot stuff somewhere just in case.

---

### Post by jsimerly on 2008-05-18
Reinstalled 8.04 from Alternate CD. Kept existing partitions intact and let install format only non-user data partitions, /, /usr, /boot, and /var.

---

