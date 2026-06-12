---
title: "if i reboot, ubuntu won't start. reconfiguration of grub witout live cd/usb"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by fruitz on 2013-01-22
hi all...i have had the horrible idea of buying a vaio, and im wasting so much time making my ubuntu work.

i managed to install ubuntu, but only the version 12.04 from alternate cd., since it allows me to write the path for the installation of grub.

yesterday i ran an update, grub gets reconfigured, and i get the error message, that grub failed to install properly. So now, as soon as I reboot, i'll have a black screen.

I browsed the same problem on the internet, and all the solutions i came across involve rebooting and fixing with live version. I really dont want to reboot, maybe it is possible to tell grub where to install when my system is still working?

i've attached the results from boot-info. 

thanks in advance

---

### Post by darkod on 2013-01-22
Of course you can install it while ubuntu is working. Most tutorials are for cases that you can't even boot with grub, so they assume using live mode.

You have a raid array with a name /dev/mapper/blahblah_Volume0. You can see the exact name at the top of the bootinfo summary. To install grub2 onto the MBR of the array from a working ubuntu, you simply do in terminal:
```
sudo grub-install /dev/mapper/blahblah_Volume0
```

Use the correct array name, I was too lazy to retype it. :)

On another note, the laptop seems to come with two 128GB SSDs in one 256GB raid0 array using the bios raid (fakeraid). Since you have only ubuntu as far as I can see, it would have been a much better option to destroy that fakeraid array and install with mdadm software raid (if you want to keep the raid at all).

Also note that raid0 doesn't have any redundancy. If one of the two disks dies on you, all is gone, because in raid0 the data is split on both disks and there is no way to recover it from only one disk. Think about regular backups...

Whether you want to destroy this fakeraid and install SW raid is up to you. You would have to use the alternate cd again for SW raid, or the live cd but with a little preparation before you start installing. This is because the alternate cd has the mdadm package by default, and the live cd doesn't.

---

### Post by fruitz on 2013-01-23
i get this:

```
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
```

i would be glad to fix this asap, and then follow your advice, but maintaining the raid (since i suppose it makes the computer faster)

---

### Post by darkod on 2013-01-24
It looks like it doesn't understand your array properly. It says the disk is partitionless which is not true. You have 3 partitions on the array.

I don't know why would it say that and how to fix this.

One way to make it work with raid, is using mdadm SW raid instead of fakeraid. Many people say it even works better than fakeraid. Since you are running only ubuntu, you can use it. You can't use it for dual boot since windows can't understand it.

But this would mean reinstalling from scratch because the disks will be deleted when creating the SW raid0 array. I don't know how you feel about that.

---

### Post by fruitz on 2013-01-24
I am running only ubuntu, and always will :) and i guess fixing this problem at the root would be the best long term solution. 

Could you maybe help me through this process? and can i still use this thread?

---

### Post by SaturnusDJ on 2013-01-24
There are much tutorials about setting up raid with mdadm, it's quite easy.
If you run into problems, starting a new thread is the best.

---

### Post by darkod on 2013-01-24
If you plan to install 12.04 LTS which is recommended because it has long term support, it's better to use the alternate installer. Also, with SW raid0 you have to create small (300-500MB) /boot partition outside the raid0 array, because the boot files have to be outside. You can have one raid1 md device for /boot, and the rest as raid0 md device.

If you want to use 12.10, there is no alternate ISO so you have to use the live cd, add the mdadm package first and configure the md devices, and only then start the installer.

There should be plenty of tutorials on google including on doing it manually. If you get stuck or have questions before you start, ask.

---

### Post by fruitz on 2013-01-24
thanks for all your kind replies!
i'll look for tutorials and see how far i can get myself, but my first question is, since i have to change fakeraid to sw raid, is there something i need to do beforehand on the bios, or i can just go straight with the installation?

---

### Post by fruitz on 2013-01-26
i found this [step-by-step guide]("http://forum.notebookreview.com/sony/702661-clean-install-ubuntu-12-10-sony-vaio-z-svz-2012-how.html") on the internet...do you think this is  what i need to do? could please go through it quickly and tell me if its  my case?

---

### Post by darkod on 2013-01-26
It looks good to me. Only, before step 11 I would remove the fakeraid meta data from the disks. Maybe that is why grub-install to /dev/sda failed. With mdadm grub2 should be on /dev/sda and /dev/sdb, and it shouldn't fail when installing. But since the author of that tutorial never deleted the meta data, it might be a reason for the failure of grub-install to /dev/sda.

So, before step 11 in terminal do:
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb

If it asks you to confirm removal of the meta data, do it and continue with the steps.

After you did that when you reach step 19 you can try leaving the bootloader destination as /dev/sda, as it should be. If it fails, the boot-repair step will fix it anyway.
If you do this (tyr installing grub2 to /dev/sda) and it doesn't give you any error message towards the end of the installation that grub-install failed, you can skip the boot-repair step 21-23. Continue with step 24.

If grub-install does fail in your case too, then you will need to do steps 21-23 too.

EDIT PS: Also, it never mentions whether he disabled RAID in the bios. Since you will not be using the fakeraid, you should really enter the bios and set the sata mode to AHCI. And don't forget to delete the existing fakeraid array in the raid configuration like he explains in step 6. You should delete the existing array and leave the disks as they are, without configuring another array.

---

### Post by fruitz on 2013-01-27
when i am at step 13, the output of the first command is:

mdam: cannot open /dev/sda1 no such file or directory

but when i run 

ls /dev/sda1

it finds the partition...

---

### Post by darkod on 2013-01-27
Can you post the output of:
sudo parted -l

Also, I just noticed in step 13 there is an error in the tutorial. While creating md0 and md1 the raid devices at the end are identical. It should be the partition from the different disks, like for md0 it should be /dev/sda1 and /dev/sdb1, and for md1 it should be like /dev/sda2 and /dev/sdb2.

---

### Post by fruitz on 2013-01-27
i'm not sure what you mean with the error in the tutorial..it seems to me that he creates the md0  in sda1 and md1 in sda2?

anyhow...here the output

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA THNSNC12 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  5244MB  5243MB  primary  ext4
 2      5244MB  126GB   121GB   primary  ext4
 3      126GB   128GB   1573MB  primary  linux-swap(v1)


Model: ATA TOSHIBA THNSNC12 (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  5244MB  5243MB  primary  ext4
 2      5244MB  126GB   121GB   primary  ext4
 3      126GB   128GB   1573MB  primary  linux-swap(v1)


Model: 2.0 Flash Disk (scsi)
Disk /dev/sdc: 3988MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  3987MB  3986MB  primary  fat32        boot, lba

```

---

### Post by darkod on 2013-01-27
He uses the same device sda1 (sda2) two times, that's the error. Try this:
```
sudo mdadm --create /dev/md0 --chunk=32 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
sudo mdadm --create /dev/md1 --chunk=32 --level=0 --raid-devices=2 /dev/sda2 /dev/sdb2
```

See how that goes.

---

### Post by fruitz on 2013-01-27
thanks it worked!! so i went through the installation but again, grub failed to install...so i ran the boot repair but it said an error occourred... [heres the link]("http://paste.ubuntu.com/1576359/") i was given from the error ...

it still says that i can reboot the computer and tell the bios to boot from sda...does it means its fine?

---

### Post by darkod on 2013-01-27
I mentioned it earlier in one of my posts but I forgot to point it out now. For using raid0 you have to have a /boot partition outside the array. I don't think /boot can be inside a raid0 mdadm array.

So, try redoing everything but when creating the partitions first create 500MB partition on both disks, and then continue creating the other partitions.

When creating the md devices, make them like:
md0, level=1, sda1 sdb1, for /boot
md1, level=0, sda2 sdb2, for /
md2, level=0, sda3 sdb3, for /home

When doing the manual partitioning step select the correct mount points for the correct md devices. Leave the bootloader location as /dev/sda.

See if that helps.

If grub-install still fails, you will do it later from live mode.

---

### Post by fruitz on 2013-01-28
It finally worked!! I can't tell you how grateful I am...thank you, really, thank you so much!!! I finally have it working and instructions to do it again in the future, if needed.

THANKS!!!

---

### Post by darkod on 2013-01-28
No problem, enjoy it now. :)

---

