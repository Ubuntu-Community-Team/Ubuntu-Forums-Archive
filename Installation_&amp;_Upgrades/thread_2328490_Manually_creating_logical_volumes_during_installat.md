---
title: "Manually creating logical volumes during installation"
date: 2016-06-21
forum: Installation &amp; Upgrades
---

### Post by daryl9 on 2016-06-21
I'm installing Edubuntu, 14.04.3.  In the past, I've just let the installer create the file systems using LVM.  However, I decided to manually create my own partition layout. I don't like having one large volume, I prefer to have individual file systems, so I chose "Something else" during the partition creation.

I don't see anyway to create logical volumes, however, the documentation say's that there is an option to do so.  Under the "Use As" I only have options for standard and Journal File systems, swap, encryption and "Do Not Use this partition".   Nothing for logical volumes.  Why?

Thank you.

Daryl

---

### Post by Dennis N on 2016-06-21
Neither gparted or the installer cannot create volume groups or logical volumes. You have to do it using the lvm tools (package is lvm2) before starting to install. 

gparted can format a partition to be a physical volume (pv), but the rest of the job creating the volume group and logical volumes must be done with lvm commands such as vgcreate and lvcreate.

gparted can create a pv from a regular partition with **Partition > format to > lvm2 pv**

---

### Post by daryl9 on 2016-06-21
So....do I boot to a command window to run lvm, or boot on a system rescue disk to create the file system?  This is pretty limited in Ubuntu isn't it?

---

### Post by Dennis N on 2016-06-21
You should be able to do it from the live OS session using its gparted and the terminal if there is no OS already on the HD. When I have done this, I had an OS already installed on my HD (regular install), then worked from that OS to add a new partition with gparted, format it to lvm 2 pv, then used the terminal to create the volume groups and logical volumes I wanted. After that, the installer has the ability to detect the logical volume (choose "something else"), and you can designate it as root for the new install.

---

### Post by daryl9 on 2016-06-21
Dennis,

Thank you for the information.  That sounds like entirely to much work.  I'll give the Live CD a try, but this should be something build into the installation.  

Thank you for the help.

Daryl

---

### Post by Dennis N on 2016-06-21
I imagine the gparted developers are thinking about adding the ability to create volume groups and logical volumes, but it's not there yet.

---

### Post by daryl9 on 2016-06-21
I used Live CD to create the volume groups and logical volumes, and the install is running.  Thank you once again for your help Dennis.

Daryl

---

### Post by Dennis N on 2016-06-21
Hey, thought you gave up. Probably not as difficult as you imagined?

---

### Post by daryl9 on 2016-06-21
> **Dennis N said:**
> Hey, thought you gave up. Probably not as difficult as you imagined?

No, not difficult at all.  I create logical volumes on the command line all the time. However, I'm used to other distributions that include LVM in the installation; where I can carve up the disk how I see fit using LVM during installation.  This just added an additional hoop that I had to jump through, that's all.  Also, since the install will carve up the disk with LVM, creating one large volume, plus a boot and swap, I assumed that I would be able to use LVM to manually carve up the disk.

Thanks.

Daryl

---

