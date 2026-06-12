---
title: "Detecting existing partitions problem"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by stinkyfax on 2008-10-22
I have asus laptop M51Sr where i got vista installed and hidden partition which is actually "recovery vista", So i have 1 hidden partition, C:\ - vista, D:\ - Data, and 80gb not used space where i want to install Ubuntu.
But when it comes to the step of choosing partition it doesn't show existing partitions and only allows me to install on whole HDD which will result on loosing vista...
I want to install ubuntu without data loss and recreating partitions, any suggestions?
Ubuntu i'm trying to install is 8.04.1 desktop.

---

### Post by Pumalite on 2008-10-22
Get Gparted Live CD and see if you can partition that space:
10 GB for '/'
The rest minus RAM for /home
The amount of your RAM for /swap
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn to disk and boot from it.
If you can do it; then: install, go 'Manual' and use the already prepared partitions.

---

### Post by stinkyfax on 2008-10-23
As you can see on the images, I burned the cd and loaded via this gnome. As the result GParted shows that my whole HDD is unallocated, that's what ubuntu does when i attemp to install it. But from the other hand TestDisk 9.0 which is on that disk too shows correctly every partition and it's information! I'm stuck :confused:

---

### Post by Pumalite on 2008-10-23
Try adding all_generic_ide to your boot line
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) 
OTOH; rescuecd has a partitioner too.

---

### Post by stinkyfax on 2008-10-23
I've tried to put this in the end of boot line for setup, but it still only asks me to make a new partition table and doesn't see existing partitions and 80gb unallocated.

---

### Post by Pumalite on 2008-10-23
The 80 GB cannot be 'unallocated'. They have to be formatted something. Ubuntu cannot be installed in unallocated space. Did you try the partitioner in rescue CD?

---

### Post by stinkyfax on 2008-10-23
I've tried this one you gave:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Also i've tried loading acronis from CD (brought me error: did not detect HDD)
Also tried booting from ubuntu CD desktop and running Partition, it shows that my whole HDD is unallocated.
I've read article about how to install duo boot vista and ubuntu, and there is written that I better make an unallocated space so that ubuntu creates neccessery partitions there, but it find all my HDD as unallocated while i don't want loosing existing partitions.

---

### Post by caljohnsmith on 2008-10-23
Your problem might possibly be that you need to change your BIOS settings for that HDD. If you go into your BIOS, look for HDD BIOS settings like LBA, CHS, RAID, AHCI, etc, and change them one-by-one, and see if it helps. Be sure to write down the original settings so you can revert back if necessary.

---

### Post by stinkyfax on 2008-10-23
Unfortunately this bios seems kind of "lite" The only possible settings for HDD is SATA enhanced or half-mode (forgot the original word which was used), i tried both in any action i made, result was same everywhere..

---

