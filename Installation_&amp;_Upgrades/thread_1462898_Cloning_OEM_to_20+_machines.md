---
title: "Cloning OEM to 20+ machines"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by eyelessfade on 2010-04-26
We are giving away 20+ machines to 3rd world county and I was asked from the receiving party to install linux on them. What I don't want is to pop a cd into all of them and do the manually install.

I'm thinking of installing one computer the old fashion way and do the OEM-configuration on it afterwards. It would be nice to just clone the hard drives since the computer is identical right down to the hard drive.

Does anyone have any experience with cloning a working install using dd or any other software?

---

### Post by iponeverything on 2010-04-26
clonezilla might be what you are looking for or you can do it the good fashion way:

Setup one machine the way you like it.

Install the second drive into the system.

Partition the second drive to match the first drive.

Then boot from live CD or USB and rsync from the first drive to the second drive. for example see:
[http://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](http://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync)

install grub on the second drive, boot and test it.

---

### Post by Grenage on 2010-04-26
dd can do it, but iirc Clonezilla has a network clone function for cloning many disks across the network.  It probably uses multicast or the like.

---

### Post by iponeverything on 2010-04-26
The thing I don't like about dd is that it copies everything, blank space and all.. it can be big time sink if you have a lot disks to do.

---

### Post by renkinjutsu on 2010-04-26
> **iponeverything said:**
> The thing I don't like about dd is that it copies everything, blank space and all.. it can be big time sink if you have a lot disks to do.

How else would you **clone** a drive though? isn't it bad to copy only part of a formatted filesystem?

---

### Post by makingtheswitch on 2010-04-26
Clonezilla, definitely.
Just get the first machine exactly how you want it, use Clonezilla to clone it, then copy that clone to each remaining machine.

---

### Post by iponeverything on 2010-04-26
> **renkinjutsu said:**
> How else would you **clone** a drive though? isn't it bad to copy only part of a formatted filesystem?

An exact copy of a physical disk is good for forensics, evidence preservation and little else, imo. And yes, if you dd a image from one size drive to another size drive you might well have some issues.

But there are different types of clones.

- A clone of your data and
- A clone of your disk

rsync'ing one partition to another drive's partition where each drives ends up having the same files with the same md5's, you have created a clone of the data, doing this for entire os disk and you have cloned the os to another drive. And when you rsync you have do it to a formated filesystem, as just data is moving.

---

### Post by eyelessfade on 2010-04-26
Thanks for all your input. I'll look into all the options. The disk is not big (80GB), so even with dd of all the space it wouldn't take much time.

---

