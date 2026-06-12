---
title: "No bootable devices found"
date: 2024-01-23
forum: Installation &amp; Upgrades
---

### Post by bbaltas on 2024-01-23
I'm new to Linux, and I've been asked to install Ubuntu with particular disk partitions.

There are two disks in the system:
    The boot drive is a 460G SSD  (disk 0)
    The data will be a 3 TB spinning disk   (disk 1)

BIOS is set to UEFI

The partitions requested are:
     Disk       Mount point      Size     File System     
       0               /                400G       ext4             
       0              /boot           2G           ext4    
       0             /var              10G         ext4
       1             /opt              200G       ext4
       1             /data             3T          ext4   (or remaining disk)

I designated disk 0 as the boot disk and I created the above partitions and mount points.

When the system boots I get the error:  "No bootable devices found"

If I let the system automatically create partitions, and I don't try to customize the disk 0, the system boots fine.    

The image below shows the configuration that works.  I'm not able to create this manually.
[https://drive.google.com/file/d/12WwISbxEjmNPPpogEFUMWN1Err0GLbtN/view?usp=sharing](https://drive.google.com/file/d/12WwISbxEjmNPPpogEFUMWN1Err0GLbtN/view?usp=sharing)

This next image is what I've done (it's more than I've shown above.  I'm trying multiple things to get this to work).
[https://drive.google.com/file/d/12WyDHUjOo5MNCdadBmzA7-8ZY3qrOMCB/view?usp=sharing](https://drive.google.com/file/d/12WyDHUjOo5MNCdadBmzA7-8ZY3qrOMCB/view?usp=sharing)

I'd appreciate any help on this item.

Thank you
Bill

---

### Post by Dennis N on 2024-01-23
The partition mounted at /boot/efi has to be formatted fat32, not ext4 and also should have the boot flat set (which also automatically sets an esp flag). 
This is partition is called an EFI system partition, and it's required for UEFI installation. It was made when you let the installer do the partitioning.

---

### Post by bbaltas on 2024-01-24
Formatting the /boot/efi as fat32 is not an option.  Is there another format I can try?

---

### Post by MAFoElffen on 2024-01-24
Yes it is, sort of...

When I am doing an "Other" install where I pick and set things like that: (Sort of a work-aroud I came up with for that)

I first select "Try" > Startup GParted, add a GPT partition table to my root bootig disk > create an EFI partition of about 750MB to 1GB > Apply... Then change the flags on that partion as "ESP, Boot"...

Then I'll exit GParted and start up the install, and create / mount what I want to do. I set the boot in the bootem to that root/ booting disk... And it finds the EFI partition...

The reason it failed with how you did it, is that you did "manual" partitioning, but there was no EFI partition in your workflow...

In the Server Edition you can create it in the partitioner, and go on from there. In the Desktop Edition, it's a different partitioner. For some reason, with that one, in manual mode, it has to be there before you start that process. I don't know why. To me, I feel that is a Bug.

It has the ability to create the partition and format it as vfat (FAT32), but doesn't have anything there to change the flags to ESP & boot? 
 
I have a few Bug reports already filed on that partitioner. It's new, and they are doing there best to improve it, and get it going.

If you can tell me which ISO image you are trying to install, I'll file the bug report myself, and you can just join it as affected.

---

### Post by avidandrew on 2024-02-01
You could try using Super Grub Disk ([https://www.supergrubdisk.org/](https://www.supergrubdisk.org/)) to get successfully booted into your partition and from there reinstall grub (I can provide the specific steps to do this if needed).

---

### Post by MAFoElffen on 2024-02-04
Show the output, posted within CODE Tags:
```

lsblk -e7 -o name,label,size,fstype,mountpoint,model
sudo blkid | grep -v 'squashfs'
sudo fdisk -l | grep '^/dev'
for Disks in $(ls /sys/block/ | grep -v 'loop' ); do sudo sgdisk -p /dev/$Disks | grep -E '^Disk |^Model: |^Number |   [0-9]. '; done

```
You are going to want to cut-and-paste the commands as posted into a terminal session booted from an installer LiveUSB. That means also start a Firefox session on it and show this post to copy from it...

---

