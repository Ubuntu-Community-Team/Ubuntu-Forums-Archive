---
title: "win 8 dual boot problem"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by joshua24 on 2014-04-22
so i attempted to install ubuntu alongside windows 8 and i cant get a dual boot screen to log into windows 8, it just shows be the boot options for ubuntu and says nothing about windows 8

[http://paste.ubuntu.com/7310575/](http://paste.ubuntu.com/7310575/)

hopefully this info will be able to shed some light

any help is greatly appriciated.

---

### Post by oldfred on 2014-04-22
It looks like you converted the efi partition to swap.
Swap is unformatted space for RAM overflow. The efi partition holds all you essential boot files for UEFI boot.
But you installed Ubuntu in BIOS boot mode not UEFI.
Do not reformat sdb2, until we are sure we cannot recover it.

Since you may not have used swap yet, you may be able to use testdisk to recover swap partition. Do not use Ubuntu live installer as it uses swap if found to speed up install or live use. If in your install swap is probably mounted. Not sure if you can even unmount it then. Normally we use live installed to have all partitions unmounted, but unmount swap after booting and it will probably then overwrite your efi data.

I might try gparted or parted magic liveCDs as they do not mount swap as part of booting.

IF you cannot recover the efi partition you will need a Windows repair flash drive. Did you create one before installing Ubuntu or do you have the full installer version of Windows?

You should use Boot-Repair to convert BIOS install of Ubuntu to UEFI, but need to have the valid efi partition for the UEFI boot version of grub to be correctly installed.

---

### Post by joshua24 on 2014-04-22
> **oldfred said:**
> It looks like you converted the efi partition to swap.
Swap is unformatted space for RAM overflow. The efi partition holds all you essential boot files for UEFI boot.
But you installed Ubuntu in BIOS boot mode not UEFI.
Do not reformat sdb2, until we are sure we cannot recover it.

Since you may not have used swap yet, you may be able to use testdisk to recover swap partition. Do not use Ubuntu live installer as it uses swap if found to speed up install or live use. If in your install swap is probably mounted. Not sure if you can even unmount it then. Normally we use live installed to have all partitions unmounted, but unmount swap after booting and it will probably then overwrite your efi data.

I might try gparted or parted magic liveCDs as they do not mount swap as part of booting.
i need 
IF you cannot recover the efi partition you will need a Windows repair flash drive. Did you create one before installing Ubuntu or do you have the full installer version of Windows?

You should use Boot-Repair to convert BIOS install of Ubuntu to UEFI, but need to have the valid efi partition for the UEFI boot version of grub to be correctly installed.
sorry to sound like such a noob. but can you explain exactly what i need to do, so i dont screw anything more up? thanks

---

### Post by oldfred on 2014-04-22
If you are currently in your Ubuntu install, do this and reboot. It may give errors about no swap.

      
 sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

      Add # to start of UUID line so it is a comment like the line above it that says swap on /dev/sda2.
>  # swap was on /dev/sda2 during installation
UUID=f25f6252-4270-4f91-9d9d-722a08893ef7 none            swap    sw              0       0
    

Then reboot and you should not be using swap. Hopefully it was not used yet.

Then in testdisk see if you can recover sdb2, may be sda2 with a  different boot. You want the fat32 formatted partition not the  unformatted swap partition that is in the space of sdb2.
testdisk is in repository so you can install it. This is command line, or use Software Center.
sudo apt-get install testdisk

 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 Yours is not exactly a lost partition, but may be similar.
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

On first choice screen with testdisk choose the efi-gpt type of partitioning.
And see if search or deeper search finds a FAT32 partition.


OR:
If you have another computer download and create a new CD or flash drive repair disk. I think they both come with testdisk.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by joshua24 on 2014-04-22
> **oldfred said:**
> If you are currently in your Ubuntu install, do this and reboot. It may give errors about no swap.

      
 sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

      Add # to start of UUID line so it is a comment like the line above it that says swap on /dev/sda2.
    

Then reboot and you should not be using swap. Hopefully it was not used yet.

Then in testdisk see if you can recover sdb2, may be sda2 with a  different boot. You want the fat32 formatted partition not the  unformatted swap partition that is in the space of sdb2.
testdisk is in repository so you can install it. This is command line, or use Software Center.
sudo apt-get install testdisk

 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 Yours is not exactly a lost partition, but may be similar.
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

On first choice screen with testdisk choose the efi-gpt type of partitioning.
And see if search or deeper search finds a FAT32 partition.


OR:
If you have another computer download and create a new CD or flash drive repair disk. I think they both come with testdisk.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)


[ATTACH=CONFIG]252403[/ATTACH]

this is what i saw in that program.. does that help at all?

---

### Post by oldfred on 2014-04-22
On that partition you have highlighted which has the same end as swap, does p for list files show .efi files? A Windows folder with efi files?
Or the next partition which is the same size? It may be the Microsoft reserved which is another space for Microsoft and should have no files, as that is what it is.

---

