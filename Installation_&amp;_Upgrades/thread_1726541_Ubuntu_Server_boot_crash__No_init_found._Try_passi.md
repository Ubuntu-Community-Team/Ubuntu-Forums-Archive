---
title: "Ubuntu Server boot crash : No init found. Try passing init= bootarg."
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by dreamlander on 2011-04-11
Hi everyone,

I noticed my Ubuntu 10.04 LTS x86 server crashed this morning and couldn't  restart some services (mysqld, apache ...) as it complained about the file system being readonly. It is running as virtual machine on KVM. 

I rebooted the server but it then it keeps stopping at the following screen:

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
Enter 'help' for a list of built-in commands

(initramfs)

I tried booting from a Live Ubuntu CD (Desktop 10.10) and run :

**$sudo fdisk -l **
Disk /dev/sda: 80.5 GB, 80530636800 bytes
255 heads, 63 sectors/track, 9790 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bbcbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        9791    78391297    5  Extended
/dev/sda5              32        9791    78391296   8e  Linux LVM

**$sudo fsck /dev/sda1**
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda1: clean, 218/124496 files, 62267/248832 blocks

I gave it another try with :

**$sudo e2fsck -C0 -p -v -f /dev/sda1**
218 inodes used (0.18%)
       6 non-contiguous files (2.8%)
       1 non-contiguous directory (0.5%)
         # of inodes with ind/dind/tind blocks: 33/12/0
   62267 blocks used (25.02%)
       0 bad blocks
       0 large files

     205 regular files
       4 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
     209 files

I rebooted the server after that but the problem is still there.
I can mount /dev/sda1 and look inside but I though I should ask for some guidance from you first.
Now I believe there is something wrong with the GRUB bootloader as I read on some forums, but I don't know how to fix it ... :confused:

Please help.
Thank you

---

### Post by dreamlander on 2011-04-12
If anyone will get the same issue in the future ... I managed to fix it but NOT with a Live CD. The problem is that you have to have a read/write OS. I the first instance I recovered the data, but the problem was that a simple mount couldn't do because of the LVM2 type. In the second part fixed the issue :D
So, I installed a new virtual machine (Desktop 10.10) and mounted the disk. In short :

$ sudo apt-get install lvm2 ; install lvm2
$ sudo modprobe dm-mod ; load drivers
$ sudo vgchange -a y ; activate volume groups
$ sudo lvscan ; look for the root partition
$ sudo mkdir /mnt/sdb5 ; create mount point
$ sudo mount /dev/mapper/volume-root /mnt/sdb5 

After that I could browse my old root partition (sda5) in /mnt/sdb5 and got the data out with scp:

$ sudo scp source.files user@1.2.3.4:/home/user ; user is a username on the destination 1.2.3.4 server.

_________________

Returning to the initial problem, it wasn't about /dev/sda1 but /dev/sda5, the root partition
Again had to be done using a read/write OS, because initramfs had to make some changes.
So, no Live CD... The issue was quite easy to fix, from the fresh installed OS with broken disk mounted, run :

$ sudo update-initramfs -u -k all 

this will update your initramfs for all installed kernels. Reboot and change the boot order, to start from the broken disk. 

$ sudo reboot

During boot time fsck will complain about some inconsistencies on the disk (/dev/sda5 now), press F at the question to start fixing. At the end it should report that the OS has been modified and will reboot normally and without any problems.   

That's it !

PS: Still curious what actually happened and how to prevent it in the future ...

---

### Post by neerajranjan on 2013-01-06
Sir,

I'm facing a very similar situation...I"M TRYING TO BOOT FROM usb, but again it's not booting ..it says that 

/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found
unable to open '/dev/sda'

Can you please help me..

Wishes,
Neeraj

---

