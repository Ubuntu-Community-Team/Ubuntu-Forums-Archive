---
title: "Ubuntu install over Fedora - GRUB can't find it"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by jtlanzi on 2008-05-27
I have a XP/Linux dual boot configuration, and wanted to replace my Fedora distro with Hardy. Going through the manual partition installation option, I chose to place my root "/" partition on sda6 (~88GB) (ext3), and used the 2.9GB sda3 partition for swap. The Ubuntu installation failed to install GRUB. 

I already had GRUB installed from my previous Fedora installation. It still properly boots Windows, but I cannot find my /boot/grub/stage1 from the GRUB command line on my (hd0,5) partition. 

From the LiveCD, I can see all of my Ubuntu files when I mount the /dev/sda6 partion. (mount -t ext3 /dev/sda6 /mnt/root). 

I have tried running the grub shell from the command line:
$sudo grub
grub>find /boot/grub/stage1

But, I get an Error 15: File not found. Even though I can see it in /mnt/root/boot/grub after I mount /dev/sda6. 

Therefore, I cannot run grub>setup (hd0)

Please help!! 

Jim




ps: My disk layout is as follows:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        8029    64460812    7  HPFS/NTFS
/dev/sda3           19094       19452     2883667+  82  Linux swap / Solaris
/dev/sda4            8030       19093    88871580    5  Extended
/dev/sda5            8030        8055      208813+  83  Linux
/dev/sda6            8056       19093    88662703+  8e  Linux LVM

Partition table entries are not in disk order

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

---

### Post by jtlanzi on 2008-05-28
Thanks to anyone who has taken a gander at this problem.

Turns out that my old Fedora distro had a separate /boot partition at /dev/sda5. I did not inform the Ubuntu installer of this. To repair the Hardy install, I had to do the following:

1. Using the LiveCD, I mounted the Ubuntu root file system and boot partition:
$sudo mkdir /mnt/root
$sudo mount -t ext3 /dev/sda6 /mnt/root
$sudo mkdir /mnt/boot
$sudo mount -t ext3 /dev/sda5 /mnt/boot

2. Copied the config, vmlinuz, System.map and initrd.img files from the ubuntu root/boot file system to the /boot partition:
$sudo cp /mnt/root/boot/config-2.6.26-16-generic /mnt/boot
$sudo cp /mnt/root/boot/System.map-2.6.26-16-generic /mnt/boot
$sudo cp /mnt/root/boot/initrd.img-2.6.26-16-generic /mnt/boot
$sudo cp /mnt/root/boot/vmlinuz-2.6.26-16-generic /mnt/boot

3. Hand hacked a ubuntu stanza into the menu.lst file:
$sudo gedit /mnt/boot/menu.lst

title Ubuntu
	root (hd0,4)
	kernel /vmlinuz-2.6.24-16-generic ro root=/dev/sda6 rhgb quiet
	initrd /initrd.img-2.6.24-16-generic

Key concepts for me in the solution were:
a. To root grub on the /boot partition (hd0,4) -or- sda5. I initially confused this with the "/" file system at sda6.
b. Properly configuring the root= argument for the kernel. 

Once this was done, ubuntu booted up fine. 

I am left with two annoyances: 
1. To make sure that the update manager installs kernel updates in the right spot, I have to mount the boot partition and bind it to the boot folder in the root file system:
$sudo mkdir /mnt/boot
$sudo mount -t ext3 /dev/sda5 /mnt/boot
$sudo mount --bind /mnt/boot /boot

I suppose I should know how to do this automatically during initialization, but I don't.

2. When I followed the procedure above and loaded the updates, Ubuntu properly installed the files in the boot partition; however, it did not update my menu.lst file. 

Bottom Line: From what I have seen of Ubuntu, it has been worth the effort.

---

