---
title: "after clean install of ubuntu logical drives are hidden"
date: 2020-10-06
forum: Installation &amp; Upgrades
---

### Post by gurubhai2 on 2020-10-06
Dear sir,
Recently, I just install clean Ubuntu. First I delete all hard drives partition and make a single one. After that I create a primary ext4 partition with mount point /. Also I create 3 ext4 partition with mount point respectively /home, /boot and /tmp. After that I create a swap area, EFI. Also the installation was successful and running smoothly. But my 3 logical drives are hidden somewhere. I couldn't find them in Files/Computer, But I can see them in Gparted. Please help to recover my hidden logical drives. Thanks.
[IMG]/home/saurabh/Desktop/2020-10-06 17-52-44.png[/IMG]

---

### Post by oldfred on 2020-10-06
Post this (please use code tags # in advanced editor):
lsblk -f

Most desktops do not need separate system partitions like /boot. 
Standard UEFI install is ESP & / (root). But if larger drive then separate /home and/or data partitions probably should be used.

---

### Post by gurubhai2 on 2020-10-06
not help

---

### Post by grahammechanical on 2020-10-06
In the file manager (Files) and under the heading Computer, Home, Boot, Temp are shown as folders. Open those folders and you will be looking at the contents of the Home, Boot, and Temp partitions.

Every installation of a Linux/Ubuntu operating system will have a Home, Boot and Temp location. They are usually folders coming off of the Root folder/directory. If we make partitions with those labels then Files will still show them as folders coming off the Root directory and not as partitions/disks as would happen if we gave a partition another kind of label such as Data or left it without a label.

In the old days when Linux was closer to its Unix roots it was customary to have system directories in their own partitions. I think this was because hard drives were small compared to present hard drives and a server system would need multiple hard drivers in order to get a functioning operating system. 

If we have /home as a partition we can then reinstall Ubuntu without losing our data and settings stored in /home. Provided we do not format the home partition at installation time.

In the past it was possible to have /boot and root on the same partition but now it is customary to have boot on it own partition. It is the place where the boot loader (Grub) puts its core code. I do not think there is any advantage to giving /Temp it own partition.

Regards

---

### Post by gurubhai2 on 2020-10-07
> **grahammechanical said:**
> In the file manager (Files) and under the heading Computer, Home, Boot, Temp are shown as folders. Open those folders and you will be looking at the contents of the Home, Boot, and Temp partitions.

Every installation of a Linux/Ubuntu operating system will have a Home, Boot and Temp location. They are usually folders coming off of the Root folder/directory. If we make partitions with those labels then Files will still show them as folders coming off the Root directory and not as partitions/disks as would happen if we gave a partition another kind of label such as Data or left it without a label.

In the old days when Linux was closer to its Unix roots it was customary to have system directories in their own partitions. I think this was because hard drives were small compared to present hard drives and a server system would need multiple hard drivers in order to get a functioning operating system. 

If we have /home as a partition we can then reinstall Ubuntu without losing our data and settings stored in /home. Provided we do not format the home partition at installation time.

In the past it was possible to have /boot and root on the same partition but now it is customary to have boot on it own partition. It is the place where the boot loader (Grub) puts its core code. I do not think there is any advantage to giving /Temp it own partition.

Regards


Thanks sir. I got them. But how can i make them a partition like windows, Local DIsk C, D, E , F ?

---

### Post by CelticWarrior on 2020-10-07
> **gurubhai2 said:**
> Thanks sir. I got them. But how can i make them a partition like windows, Local DIsk C, D, E , F ?

You don't. That's not how it works. And why would you want to do it anyway?
As already explained those can be and typically are folder under / (root). Users can make them like you did as separated partitions although there's no point in doing so, it's only a waste of space. But then those partitions are system partitions absolutely NOT intended to be visible or manageable by normal users.

---

