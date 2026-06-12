---
title: "I NEED to uninstall Ubuntu but don't know how"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by linuxsam777 on 2012-06-12
I have installed the latest version of Ubuntu on a netbook provided by my school but I don't know how because I cant just delete the partition and install easy-BCD because the netbook has win 7 enterprise and I am only a standard user is there away of removing ubuntu without messing up the boot system. Is there perhaps a way of telling the bios to only listen to the windows boot loader so that I can safely delete the ubuntu partition? :?:

---

### Post by william_lane on 2012-06-12
Does your machine have entries for 7 and Ubuntu and in tacked? What I mean can you boot to both?

---

### Post by linuxsam777 on 2012-06-12
yes it is dual boot. all the partitions work correctly.

---

### Post by cortman on 2012-06-12
Confirm which partitions contain which operating systems, boot from a live CD or USB, and use GParted to delete the Ubuntu partitions.
You can then reclaim the empty space into the Windows partitions by enlarging it in Windows.

---

### Post by linuxsam777 on 2012-06-12
I have done that before on a different machine but when I started the computer it was looking for the ubuntu GRUB (boot loader). However I think by deleting the partition the I wont be able to start the computer and boot to windows because the ubuntu GRUB (boot loader) is saved on the ubuntu partition. I would try your sugestion but I fear that the machine may not start properly.

---

### Post by william_lane on 2012-06-12
I would copy your drive, and back up every thing if you go down this road, I'll try doing it in a vm tonight because it has been a very long time sense I have done this, but you can delete the linux partition/swap but I don't think it will wipe out grub(could be wrong). If it doesn't you'll need to remove grub.Once grub and the partitions are gone you can run the start up repair for windows 7 that will write a new boot loader, after that you can resize the windows partition to take up the rest of the space with a third party utility.
The catch! You need administrative rights, I have done this before but it is a sketchy ride.

---

### Post by Cheesemill on 2012-06-12
Before deleting the Ubuntu partition(s) you need to first restore the windows bootloader.



You can either do this from Ubuntu:

```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```

**Or:**
Boot from a Windows recovery CD to fix the MBR.


Once you have done this then reboot your machine, it should boot straight into Windows without the Grub menu. If this is successful you can then just delete all of your Ubuntu partitions.

---

### Post by linuxsam777 on 2012-06-12
> **Cheesemill said:**
> Before deleting the Ubuntu partition(s) you need to first restore the windows bootloader.



You can either do this from Ubuntu:

```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```

**Or:**
Boot from a Windows recovery CD to fix the MBR.


Once you have done this then reboot your machine, it should boot straight into Windows without the Grub menu. If this is successful you can then just delete all of your Ubuntu partitions.

Thank you!!!! but how do I need to edit this command to suit my system though?

this my partition table :

```
/dev/sda1  ntfs   system reserved   
/dev/sda2  ntfs   windows
/dev/sda3  ntfs   Data
/dev/sda4  extended
  /dev/sda5  ext4
  /dev/sda6  linux-swap
```

---

### Post by Cheesemill on 2012-06-12
> **linuxsam777 said:**
> Thank you!!!! but how do I need to edit this command to suit my system though?

this my partition table :

```
/dev/sda1  ntfs   system reserved   
/dev/sda2  ntfs   windows
/dev/sda3  ntfs   Data
/dev/sda4  extended
  /dev/sda5  ext4
  /dev/sda6  linux-swap
```

You don't need to edit it, use the exact commands that I gave you.

---

### Post by linuxsam777 on 2012-06-12
> **Cheesemill said:**
> You don't need to edit it, use the exact commands that I gave you.

Thank you!!! You are awesome!!!
You have really saved my bottom :D
I will mark this thread as solved in about two weeks when I have tried your method, but I am sure that it will work!!

---

