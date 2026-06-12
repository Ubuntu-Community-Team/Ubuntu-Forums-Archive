---
title: "install of 2nd Distro, grub isn't showing other one"
date: 2014-09-15
forum: Installation &amp; Upgrades
---

### Post by shmish on 2014-09-15
Hello,
Yesterday I installed Kubuntu 14.04 on my laptop. The partition I used for the install used up my whole harddrive, 300gb
Today I installed Ubuntu 14.04. My understanding was that the ubuntu install would recognize my existing installation and add it to the boot loader.  During the install I resized the original partion.  Ubuntu installed on sd1 with a size of 100gb.  At the same time, sda2 (extended partition) was created. I think the extended has two logical partions: sda6 (which holds my original kubunto install, 200gb) and sda5 (4gb), which is a linux swap partition.

The boot loader only gives me options for the new ubuntu OS.  The following is from my /etc/default/grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I'm not very clear on how to modify this file to include the kubuntu OS.  Too be honest, this file doesn't even really match what I see when the bootloader shows up during startup.  During startup there are several entries: ubuntu, ubuntu 14.04 LTS, ubuntu advanced, ubuntu 14.04 LTS on sda1  (or something like this, I'm going from memory)

Any ideas on the path forward? Thanks.

---

### Post by deadflowr on 2014-09-15
You don't need to do anything with that file.
Instead try the update-grub command
```
sudo update-grub
```
See if you get entries for kubuntu.

The kubuntu entries will show up after the entries for memtest.
They might show up as ubuntu, and most likely ubuntu on /dev/sda6.

Post the output if it doesn't make sense, or you need help figuring it out...

---

### Post by fantab on 2014-09-15
Also post the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by grahammechanical on 2014-09-15
> [COLOR=#000000]At the same time, sda2 (extended partition) was created. I think the extended has two logical partions: sda6 (which holds my original kubunto install, 200gb) and sda5 (4gb), which is a linux swap partition.[/COLOR]

That statement troubles me. How can sda6 which holds Kubuntu be inside an Extended partition that the install of Ubuntu just created? It is not possible. If we install Ubuntu or any of its flavours and we let it use the entire disk then, it would be usual for the installer to create 1 primary partition to put the OS in and an Extended partition and in the Extended partition 1 logical partition to use as swap partition.

Notice that the Extended partition is sda2. I think that the install of Kubuntu created the Extended partition and also the swap partition and that Kubuntu was installed in sda1. And now it is overwritten by Ubuntu.

Regards.

---

### Post by shmish on 2014-09-15
sudo update-grub didn't change anything...

```
sluggo@doug-ubuntu:~$ sudo parted -l
[sudo] password for sluggo: 
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  98.3GB  98.3GB  primary   ext4            boot
 2      98.3GB  320GB   222GB   extended
 6      98.3GB  316GB   217GB   logical   ext4
 5      316GB   320GB   4283MB  logical   linux-swap(v1)

```

```
sluggo@doug-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   192066883    96032418   83  Linux
/dev/sda2       192067582   625141759   216537089    5  Extended
/dev/sda5       616775680   625141759     4183040   82  Linux swap / Solaris
/dev/sda6       192067584   616775679   212354048   83  Linux

Partition table entries are not in disk order
sluggo@doug-ubuntu:~$ 

```

thanks

---

### Post by oldfred on 2014-09-15
Then we need to see more details.
Post link to the Boot info report it creates.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by shmish on 2014-09-15
Here is the link: [http://paste.ubuntu.com/8353597/](http://paste.ubuntu.com/8353597/)

I should apologize. With the 4 different entries of "ubuntu" on my bootloader, I thought that I had tried them all. It turns out that "ubuntu 14.04 LTS on sda1" is actually my kubuntu install.

I guess I'd still like to clean things up, at least name sda1 to kubuntu.

I also plan on installing a third distrobution, so if anyone wants to suggest a path forward on this, that would be great. I was thinking of resizing sda6, and creating another extended partion sda7 for which to install xubuntu.

thanks

---

### Post by oldfred on 2014-09-15
The kernels do not know which gui you are using. So both sda1 & sda6 will show Ubuntu.
Your install in sda6 shows the boot entries for both sda6 and sda1.
If you boot into sda1 and run sudo update-grub then that install will show both entries in its grub.

When you have two installs you only have one grub that controls booting. And you have to run sudo update grub in both to get grub menus updated, unless you simplify boot process and manually create boot stanzas to boot the link to the most current kernel in the link in / not the kernel directly.

You also can change the grub distributor entry in grub to show whatever you like.

This is just an example, and I do not know which is which for your install.

 sudo nano -B /etc/default/grub
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="Xubuntu-12.04-amd64 Precise"
sudo update-grub

---

