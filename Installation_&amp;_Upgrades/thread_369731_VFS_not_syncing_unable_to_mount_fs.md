---
title: "VFS not syncing unable to mount fs"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by ljoslin on 2007-02-24
I recently "Tried" to upgrade from Edgy to Feisty, I say try because now when I boot after selecting Ubuntu in grub I get an error "VFS not syncing unable to mount fs" Any help would be great!  Thanks!

ljoslin

---

### Post by Dylnuge on 2007-02-24
VFS is virtual file system. When this error occurs, you have one of the four following problems:

Error in your /boot/grub/grub.conf file
Error in your /etc/fstab file.
Error in your /boot/grub/device.map file
Error in your kernal.

First off, I need you to load into a LiveCD (Any Version) and open a terminal. Then enter these commands and post the results. (If you have a jump drive, you can mount the drive and export the results to a file on the drive by ending each command with "> <file location>.")

You need to know the locations of your root and boot partitions. Post the results of fdisk -l if you do not.

```
 mkdir /mnt/ubuntu
mkdir /mnt/ubuntu/boot
mount <root partition> /mnt/ubuntu
mount <boot partition> /mnt/ubuntu/boot
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash
```

Next, get the results of these commands, either by copying to a flash drive, or directly to the internet if you can get it from your LiveCD.

```
lspci
fdisk -l
less /etc/fstab
less /boot/grub/grub.conf
less /boot/grub/device.map
```

Post back with the results.

If it is not here, then it is in the kernel (seems most likely, considering the upgrade). There will be a bit of work to do, so lets see what can be done.

PS: I have also seen this as a problem with the hardware. Considering the upgrade, I would probably rule that out. This is essentially an error that is saying Ubuntu is unable to mount the hard drive, because it has the wrong type of file system. If it is referencing a non-mountable hard drive, like a windows drive or a swap partition, this would cause the error. (Wrong hard drive references can come from any of the above mentioned points). If this is not it, then it is because the new kernel either lacks support for the filesystem or support for the drive. If your drive(s) is/are SATA, ATA, or SCSI, then it is likely the second, if they use ReiserFs or some other obscure fs, it is likely the first. Lets rule out the easy one first :-).

---

