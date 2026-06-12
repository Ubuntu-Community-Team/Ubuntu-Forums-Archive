---
title: "RAID 5 GPT and grub2"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by janmyszkier on 2010-04-11
So here's my problem:

I wanted to merge my 1TB disks into and RAID 5 array, 4 of them in RAID 5 is above 2Terabytes limit of msdos partition tables which grub2 can boot from, so I decided to start up the system from scratch, by building it on GPT partitions, but seems grub2 won't boot from GPT partition because it drops to grub rescue and I can't really do anything from there.

here's my set up:

/dev/md0 (raid 1) - 100MB total: 
- dev/sda1, /dev/sdb1, /dev/sdc1, /dev/sdd1

/dev/md1 (raid 5) - 45GB total: 
- dev/sda2, /dev/sdb2, /dev/sdc2, /dev/sdd2

/dev/md2 (raid 5) - something bit lower than 3TB: 
- dev/sda3, /dev/sdb3, /dev/sdc3, /dev/sdd3

any tips how to have this system up and running? Because I've spent like 3 days jumping over various problems and I thought It's finally time to ask you guys ;)

---

### Post by oldfred on 2010-04-11
I do not know GPT but plan to test it on a small drive. I have saved some links that may help. There are only one or two in the forum that know GPT:

grub2 & GPT info
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by janmyszkier on 2010-04-12
gah, just noticed there was typo in disk setup, 3GB was meant to be 3TB

also, isn't there some other partition table type than gpt I can use and grub boots from flawlessly ?


EDIT:

ok, here's a note for those who may want to try it in the future, I did it using a workaround:
- 4x 1TB have both / and /home (both RAID5)
- 1x 1GB has both /boot and grub (normal disk/partition. This is currently a USB pendrive, but going to switch it for a Compact Flash card in IDE->CF adapter to have everything inside my box) 

hope that helps you people to not have a headache, it may save you 3 days thinking ;)

---

### Post by srs5694 on 2010-04-12
GRUB 2 includes GPT support, so in theory it should work; however:


[list]
[*]GRUB 2 on GPT works best if you've got a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition)
[*]I don't know enough about the BIOS calls to know what pointer size they use. (Certainly very old BIOSes were limited to about 8GiB -- yes GiB (and very old BIOSes even smaller than that) -- but newer BIOSes can handle much bigger disks.) It's conceivable that the BIOS Boot Partition and/or the Linux kernel would have to reside below the 2TiB mark.
[*]If you're using Linux software RAID rather than hardware RAID, you may do well to create a non-RAID /boot partition. GRUB 2 is supposed to include Linux LVM and, IIRC, RAID support; however, I don't know how reliable this support is. Putting /boot in a conventional (non-RAID/non-LVM) partition ensures that it's easily accessible using conventional access methods, which should minimize the risk of running into RAID-related bugs in GRUB 2.
[/list]


Thus, my recommendation would be to create a BIOS Boot Partition and a Linux /boot partition, both below the 2TiB mark. Putting them at the very start of the disk makes the most sense. If you're using software RAID, create both of these as non-RAID partitions.

Also, if you're using Linux's software RAID, then I don't think you need GPT for this, although it also won't hurt, and GPT has minor advantages even for small disks. When using software RAID, Linux sees each physical disk as it is, and the Linux kernel merges them together. With hardware RAID, OTOH, the RAID controller card merges the disk and presents the result to the kernel as if it were one much bigger disk.

---

### Post by psusi on 2010-04-12
If you want to use GPT then you should create the bios grub partition, 64kb should be sufficient, but you don't need to use GPT since the disks you are partitioning are less than 2 TB.

Also if you get the rescue shell, type ls and see what drives grub sees.  Without the bios boot partition, I'm actually surprised you even got the grub rescue shell.

---

### Post by srs5694 on 2010-04-12
The BIOS Boot Partition is recommended, but not required, for GRUB 2 on GPT. As the link I posted earlier describes, it provides a place for GRUB 2 to store extra data that it can use to make its operation more reliable, but it will work without this partition. (I've used it both ways myself.)

---

### Post by psusi on 2010-04-12
> **srs5694 said:**
> The BIOS Boot Partition is recommended, but not required, for GRUB 2 on GPT. As the link I posted earlier describes, it provides a place for GRUB 2 to store extra data that it can use to make its operation more reliable, but it will work without this partition. (I've used it both ways myself.)

More specifically grub installs itself there rather than having the boot sector bootstrap itself by direct block addresses from the filesystem.  In this case, /boot/grub is on the raid so the mbr CAN'T find the core image by blocklist, so the bios boot partition is required.  This is why I'm surprised he even got a rescue prompt.

---

### Post by mirak63 on 2010-04-21
hi, I want to use a full disk for raid 1

mdadm --create --auto=mdp --verbose /dev/md_d0 --level=raid1 --raid-devices=2 /dev/sdb missing

now, if I use LVM, what I am wondering is how the mbr is handled.
so I guess I must create a gpt or ms-dos mbr on /dev/md_d0 , a partition, and use /dev/md_d0p1 as a physicall volume for LVM ?

---

### Post by psusi on 2010-04-22
If you use the whole disk in the raid then there is no mbr.  Is there a reason you want to partition the raid array?  I'd just use /dev/md0 as an lvm pv.

If you want to boot from it though then you have to have an mbr, so you can't use the whole disk.  Instead create a single partition and use that in the raid array.

---

