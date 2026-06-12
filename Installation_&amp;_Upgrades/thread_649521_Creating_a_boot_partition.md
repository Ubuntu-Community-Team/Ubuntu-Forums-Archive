---
title: "Creating a boot partition?"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by kachofool on 2007-12-25
Hey... I want to create a boot partition for my system. I don't know how this works exactly but I want my setup to be like this:

HDD
1st partition - Boot Partition (min req'd size, maybe 0.5gb?)
2nd partition - Image of Factory Restore state (6.5gb)
3rd partition - Vista (20gb)
4th partition - ext3 for Ubuntu (6gb?)
5th partition - swap (2gb)
6th partition - media/non program files (NTFS) (60+gb)

I'm going to wipe everything on my system so this is assuming we're starting from a clean slate.

First off, I'm unsure what partition manager to use. I'm guessing GRUB would be a good choice here (or maybe even Vista's bootloader, whatever it is), but if there are any better solutions I'd be open to them as well.

I'd appreciate if I could get a quick overview of how to set up the boot partition. I basically want the system to boot to a list of the OS's on the system to choose from, but I don't want the bootloader to exist on any OS partition.

The main reason I'm setting up a boot partition is to have my boot process independant of the OS boot managers. A recent update of Ubuntu reset my GRUB menu.lst and I don't want stuff like that to happen again (so maybe this is a good point to ask whether or not a bootloader on a seperate partition can change due to an ubuntu update).

Another thing with linux is that everytime the kernel updates, I notice the root: criteria in menu.lst for GRUB changes to reflect the update. Does that mean I'd have to go back and make that change if my bootloader was on another partition?

---

### Post by meierfra on 2007-12-25
A separate boot partition  won't help. You just have to make sure that your menu.lst is not mixed up. I looked at your other thread. I  believe that you recovery partition was listed in the wrong part of menu.lst. Anything between

### BEGIN AUTOMAGIC KERNELS LIST

and 

### END DEBIAN AUTOMAGIC KERNELS LIST

will be rewritten during Kernel upgrades.

To get your recovery partition back, you need to edit "menu.lst". Type 
```

gksudo gedit /boot/grub/menu.lst

```

in a terminal to open the file:

Add the following  at the end of the file

title Recovery 
root (hd0,1)
chainloader +1

This assumes that your recovery partition is the second partition on the first hard drive. If  it is the  third partition on the second hard drive you would have to use "root (hd1,2)" (Grub starts counting at zero, the first number is the drive, the second the partition). If you need further help, post the output of "sudo fdisk -l" and "cat /boot/grub/menu.lst".

---

### Post by meierfra on 2007-12-25
I forget to mentioned that during kernel update your original menu.lst is backed up to the file "/boot/grub/menu.lst~" So  you can restore your original menu.lst  via:

```
cd /boot/grub
sudo cp menu.lst~ menu.lst
```

But you should only do that if your kernel version numbers have not changed.

---

### Post by xeth_delta on 2007-12-25
> **kachofool said:**
> Hey... I want to create a boot partition for my system. I don't know how this works exactly but I want my setup to be like this:

HDD
1st partition - Boot Partition (min req'd size, maybe 0.5gb?)
2nd partition - Image of Factory Restore state (6.5gb)
3rd partition - Vista (20gb)
4th partition - ext3 for Ubuntu (6gb?)
5th partition - swap (2gb)
6th partition - media/non program files (NTFS) (60+gb)

I'm going to wipe everything on my system so this is assuming we're starting from a clean slate.

First off, I'm unsure what partition manager to use. I'm guessing GRUB would be a good choice here (or maybe even Vista's bootloader, whatever it is), but if there are any better solutions I'd be open to them as well.

I'd appreciate if I could get a quick overview of how to set up the boot partition. I basically want the system to boot to a list of the OS's on the system to choose from, but I don't want the bootloader to exist on any OS partition.

The main reason I'm setting up a boot partition is to have my boot process independant of the OS boot managers. A recent update of Ubuntu reset my GRUB menu.lst and I don't want stuff like that to happen again (so maybe this is a good point to ask whether or not a bootloader on a seperate partition can change due to an ubuntu update).

Another thing with linux is that everytime the kernel updates, I notice the root: criteria in menu.lst for GRUB changes to reflect the update. Does that mean I'd have to go back and make that change if my bootloader was on another partition?

I would also suggest allocating more space for your linux partition, from own experience, at least 10GB, better 15 GB. After all it is on that partition where ubuntu programs will be installed. Unless you create a separate partition for /home, it will also be the partition where you will keep a good amount of personal files.

What was changed in grub during that update?

Xeth

---

### Post by klemencic on 2007-12-25
I am having a similar problem
I originally installed Ubuntu on a separate 4GB drive, with my main drive being a 80gb Windows drive
I have now decided to keep using Linux and have installed a 40gb drive for this, so now I have a 4gb, 40gb and 80gb
I have loaded Ubuntu onto the 40gb but am unable to boot to it,  GRUB has only detected the original Ubuntu on the 4gb drive
I have run the live CD again and the partitioning information has given me the following details
   40gb drive HDB
   80gb drive HDC
   4gb drive HDD

 I have spent a couple of hours on /grub/menu.lst but have been unable to get the new drive to boot.  if I try root as (HD2,0) I am told that this drive does not exist

I thought the problem was in /boot/grub/device.map which says hd0   /dev/hdc
When I went sudo gedit /boot/grub/device.map to change hd0 to /dev/hdb  I get the following
   (hd0)	/dev/sda
   (hd1)	/dev/sdb

The partitions I want are
    80gb drive leave as a bootable Windows
   40gb drive to be a bootable Ubuntu
    4gb drive to be a Linux data drive

Any suggestions greatly appreciated

---

### Post by meierfra on 2007-12-25
klemencic: Your problem seems quite different.  You probably do not have to reinstall   to boot ubuntu. Please start a new thread (include "grub" in the title)  and  post the output of 
```
sudo fdisk -l
```


Also post the  file "boot/grub/menu.lst" from your Ubuntu partition.

Does the grub menu appear at boot up?

---

### Post by klemencic on 2007-12-25
Thank you I have started a new thred called

grub not detecting new install/drive

I forgot to mention in the new thread that grub does load and will allow me to boot the 4gb drive and, last time I tried, the Windows drive

---

