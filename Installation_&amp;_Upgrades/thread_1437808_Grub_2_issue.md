---
title: "Grub 2 issue"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by lorenzippo on 2010-03-24
I just deleted my Windows 7 partition and installed Mint 8 in it's place. I now boot Windows Vista, Ubuntu 9.10 and Mint 8. The grub menu is from Mint 8 and has the Mint 8 distro on top and that green mint background. (yuck)  I have fixed the boot order with Mint 8 start manager but I want the old Ubuntu grub menu with Ubuntu on top and I want to edit out some of the other entries. In addition I can't mount the Mint 8 partition in Ubuntu. I get an NTFS security error. Strange since it's not an ntfs partition. I used to be able to mount it with my password but since using the diskmounter utility to mount my external ntfs partitions I'm getting that error. Exact error is:


Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

Any help would be appreciated.
Thanks
Larry

---

### Post by tom4everitt on 2010-03-24
Try mounting it from the terminal:

sudo mount -t <type> /dev/sdXY /mnt 

<type> can be for example: ext2, ext3, ext4, ntfs, vfat etc.

/dev/sdXY should be the partition you want to mount.


Also look in your /etc/fstab if you have an incorrect entry for your mint partition, that could be the reason. 




As for the grub question, you can overwrite the mint grub with the ubuntu grub (if that is what you want) from ubuntu with the command:

sudo update-grub
sudo grub-install /dev/sda

(if /dev/sda is the hard drive that bios boots).

---

### Post by ajgreeny on 2010-03-24
> **tom4everitt said:**
> Try mounting it from the terminal:

sudo mount -t <type> /dev/sdXY /mnt 

<type> can be for example: ext2, ext3, ext4, ntfs, vfat etc.

/dev/sdXY should be the partition you want to mount.


Also look in your /etc/fstab if you have an incorrect entry for your mint partition, that could be the reason. 




As for the grub question, you can overwrite the mint grub with the ubuntu grub (if that is what you want) from ubuntu with the command:

sudo update-grub
sudo grub-install /dev/sda

(if /dev/sda is the hard drive that bios boots).
You will need to be running ubuntu for the last part of this to work.  Maybe you realised that, but it was not made totally clear in tom4everittt's post.

---

### Post by lorenzippo on 2010-03-24
> **tom4everitt said:**
> Try mounting it from the terminal:

sudo mount -t <type> /dev/sdXY /mnt 



sudo update-grub
sudo grub-install /dev/sda

(if /dev/sda is the hard drive that bios boots).

Thanks for the help. I solved the mount problem by eliminating an incorrect setting in fstab and I used your grub solution and it worked.

---

