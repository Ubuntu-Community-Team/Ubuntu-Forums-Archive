---
title: "Problems Booting Into Ubuntu Install [After Other Issues]"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by jay767 on 2007-10-15
Hi, I had a problem installing 7.04 32-bit and was hoping someone could offer an opinion. BTW, I also had a problem with the 7.10 64-bit RC. I'll try to keep this message as short as possible.

Computer: Asus K8N, Sempron 1.8 GHz 64-bit, 1 GB ram, sda is 250 GB sata and the drive I boot from, hda is 80 GB IDE

At the start, I had an ntfs partition, about 20 gigs of unused space that used to be a Fedora installation, and a fat32 partition that was used as a shared drive between os's.

I tried to fill the gap in the middle with the 7.10 64bit RC but I got a message in the middle of installing about not being able to mount something starting with an 'm,' I believe. I regret not writing it down but I was asked to try again and did. The message didn't come back but at restart I was greeted with "failed to load os."

I tried a few things, like writing a new mbr in the other os. Nothing worked. Fortunately I had already moved anything I wanted to keep to the other drive before this point, because after trying to run chkdsk sda1 was so messed up not even Knoppix could mount it.

After this , I did a few things.
1: Installed the other os, on the entire 250 GB drive. I then resized it but the other os was having fits in explorer about applications using files and other apps crashing or not running. I figured the resizing was bad and removed all the partitions.

2: I went through the installation process for Ubuntu 7.04 32 bit (feisty fawn?) but, at restart, was greeted by "failed to load os." Rebooting with the live cd proved that all of the file structure was apparently there (I used the entire sata drive).

3: Scratching my head, I tried installing Fedora Core 7. It actually booted into linux. But I'm still not 100% happy, because I'm tired of all the extra stuff in Fedora that I don't use as well as all of the default-on services that don't apply to me.

So I think I'll try the Ubuntu install once again before settling in with Fedora. I've had it installed in the past on a second computer (currently has no hdd; it went into the gf's after hers malfunctioned). I do have a few questions that I'm hoping someone can answer (I'm grasping at straws for what's going on):

Q: The used boot sector is which by default? The drive that is being used to install Ubuntu on (sda in my case) or would it go to the other drive?

Q: I assume Ubuntu and indeed most distros can boot from a sata drive while there is an ide in place as well, even if the sata drive is reported by the partitioner as as being a scsi drive. Am I right on this one?

Thanks,
Jay

---

### Post by Pumalite on 2007-10-15
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

---

### Post by jay767 on 2007-10-15
Quite the read, thanks. I don't think I got out of it what I should have though,because I'm still puttering around with settings.

What I've done since my first post is removed Fedora and installed Ubuntu 7.04 as the only OS on the computer. It made it further this time - the screen says GRUB with a cursor but that's it. Ctrl+Alt+Del won't work, I have to use the oh-crap button to restart into the live cd.

After reading the thread above, I checked my device.map and menu.lst.

In device.map, I have:
hd0    /dev/hda
hd1    /dev/sda
hd2    /dev/sdb

In menu.lst, I have:

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=11e9cf6e-96cd-417b-9249-27c8a277d540 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=11e9cf6e-96cd-417b-9249-27c8a277d540 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

from fdisk -l, I found out the following:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1      155058    78149200+   7  HPFS/NTFS
ubuntu@ubuntu:~$

SO, if I got this right, sda1 (flagged as boot) has my Ubuntu installation and is called in grub by hd1,0.

If grub is pointing to the right drive/partition but still not loading Ubuntu then... ok, I'm still lost.

It shouldn't be this difficult to install Ubuntu to the entire drive should it?

Maybe I'll download the alternate disc and try it.

Thanks,
Jay

---

### Post by Pumalite on 2007-10-16
Try changing the order of boot.

---

