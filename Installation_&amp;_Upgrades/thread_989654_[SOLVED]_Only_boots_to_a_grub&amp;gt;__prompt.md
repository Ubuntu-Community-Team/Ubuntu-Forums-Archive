---
title: "[SOLVED] Only boots to a grub&amp;gt;_ prompt"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2008-11-21
This morning everything was working fine on my duel boot Vista/8.10 machine.

I came home this afternoon and booted the machine and tabbed to the 8.10 boot choice pressed enter and it is landing at a grub>_ prompt and won't go to the familiar GUI interface.

It suggests I can TAB for a list of possible command completions but I am unfamiliar with this system.

Can someone help me boot to the GUI as before? Maybe explain what went wrong? Possible re-install but then I will loose all of my information and settings.

Thanks in advance. Bob.

---

### Post by caljohnsmith on 2008-11-22
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Please post the output of the above commands; that will hopefully help determine what your problem is.

---

### Post by bob brazie on 2008-11-22
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors Units = sectors of 1 * 512 = 512 bytes Disk identifier: 0x52e0c363

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   114822654    57411296    7  HPFS/NTFS

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors Units = sectors of 1 * 512 = 512 bytes Disk identifier: 0x750c2642

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   160071659    80035798+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt ubuntu@ubuntu:~$ ca /mnt/boot/grub/menu.1st
bash: ca: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt cat /mnt/boot/grub/menu.1st
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom, or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ 


I hope this is helpful.

---

### Post by caljohnsmith on 2008-11-22
Did you install Ubuntu inside of Windows? In other words, is your Ubuntu a Wubi install? If you have a C:\ubuntu folder in Vista, then you have a Wubi install. If that is the case, I would recommend booting your Vista Install CD, go to the command line and run:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then try booting Ubuntu again, and let me know exactly what happens.

---

### Post by bob brazie on 2008-11-22
Please stand by. I will do that this afternoon as I am told I need to do some yard work. <g>

Yes it is installed inside Vista as I said in the first post, I didn't know that would make it a Wubi install.

Thanks, longtime windows user looking for a better way. Bob.

---

### Post by bob brazie on 2008-11-22
Chkdsk /r says: Cannot lock current drive.
Windows cannot run disk checking on this volume because it is write protected.

---

### Post by bob brazie on 2008-11-23
I have found out that some person put Windows Vista on this machine back to a restore point which was befoe the 8.10 install.

I think this might ahve been the problem. I re-installed but lost all of my settings.

Oh, well. Thanks for all of the help. Bob.

---

