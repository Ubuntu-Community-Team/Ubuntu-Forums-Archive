---
title: "Need to remove fedora 12 and install Ubuntu to dual boot with Windows xp"
date: 2015-04-04
forum: Installation &amp; Upgrades
---

### Post by an3urysm on 2015-04-04
Hi guys, I m completely new to Ubuntu.

I used to dual boot my laptop (very old) with **Windows Xp sp3 **and **Fedora 12**. I installed fedora around 4-5 years back, but I do not use it much. 

Now the issue is, I cannot boot windows xp since yesterday, maybe the installation got corrupt. I m trying to use Fedora for my daily use, but many things such as audio/wifi etc are not working regularly.  So I was thinking about removing fedora and installing Ubuntu, so that I can use my laptop till I get a new one (which ll take a few months).

 I was thinking about keeping my windows ntfs partitions intact, coz I have some important files in there. 
P.s. I do suspect if there are bad sectors in the hard disk, but I don't know how to check it in fedora.


My Laptop hardware configuration:
Intel Celeron 2.2GHz
2 GB RAM


So guys, what should I do next?

Which is the most stable version of Ubuntu that ll work in my laptop?
How can I remove fedora and install Ubuntu in the same partition?
Will it effect the bootloader, I think its grub2 or something.

---

### Post by Bucky Ball on 2015-04-04
14.04 LTS is the way to go. Xubuntu may be a smooth ride with that hardware.

Boot from the Ubuntu install media>'Try Ubuntu'>When at a desktop launch Gparted>Delete the Fedora partition.

Yes, it will effect grub if Fedora is running the show. Grub can be, and will be, reinstalled when you install Ubuntu and things should run as they were without you needing to do much/anything.

---

### Post by Skaperen on 2015-04-04
do you have a CD or USB memory stick or camera card (at least 2GB) that can plug into your computer and a BIOS with a boot menu you can activate?  how much RAM?  booting the live mode is a great maintenance tool to have.

---

### Post by an3urysm on 2015-04-04
> **Bucky Ball said:**
> 14.04 LTS is the way to go. Xubuntu may be a smooth ride with that hardware.

Boot from the Ubuntu install media>'Try Ubuntu'>When at a desktop launch Gparted>Delete the Fedora partition.

Yes, it will effect grub if Fedora is running the show. Grub can be, and will be, reinstalled when you install Ubuntu and things should run as they were without you needing to do much/anything.


Ok I m downloading it. 
How will I select Xubuntu, does the option come during install?




> **Skaperen said:**
> do you have a CD or USB memory stick or camera card (at least 2GB) that can plug into your computer and a BIOS with a boot menu you can activate?  how much RAM?  booting the live mode is a great maintenance tool to have.

Yes the CD rom of the laptop is working. I m downloading ubuntu 14.04 now. 
I ve got 2 GB of RAM.

Any idea about any command that I can run to get more hardware info in fedora?

---

### Post by an3urysm on 2015-04-04
I believe the boot order in the bios is put to CD first. 
I don't think this laptop has usb booting in the bios.

---

### Post by Elfy on 2015-04-04
> **an3urysm said:**
> Ok I m downloading it. 
How will I select Xubuntu, does the option come during install?

Any idea about any command that I can run to get more hardware info in fedora?

For Xubuntu you need to grab the xubuntu image [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

lspci and lshw should give you the hardware info

---

### Post by an3urysm on 2015-04-04
> **Elfy said:**
> For Xubuntu you need to grab the xubuntu image [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

lspci and lshw should give you the hardware info

Thanks for the link.

I was thinking if ubuntu will work in this configuration. What do you think?

Also, I know its kinda stupid question... should I burn the .iso in dvd or cd ? since its almost 1 GB I m guessing DVD... :oops:

---

### Post by an3urysm on 2015-04-04
This is how my disk is partitioned.

Anything in particular I need to do while installing?
I read something about EFI in another page, I couldn't understand.

```
# sudo parted -l
Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  52.4GB  52.4GB  primary   ntfs
 2      52.4GB  231GB   179GB   extended               lba
 5      52.4GB  158GB   105GB   logical   ntfs
 6      158GB   231GB   73.5GB  logical   ntfs
 3      231GB   231GB   210MB   primary   ext4         boot
 4      231GB   250GB   18.7GB  primary                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_mobilehost-lv_swap: 4094MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4094MB  4094MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_mobilehost-lv_root: 14.6GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  14.6GB  14.6GB  ext4

```

---

### Post by Siddhartha_Kashyap on 2015-04-04
While you install ubuntu, choose "something else, I'll choose the partions myself. Delete the fedora partion, create a ext4 "/" partition and a swap and install ubuntu on the ext4. Sometimes when one os in dual boot gets removed, the grub menu disappears. I'm also a new user of lubuntu ,hope it helps

---

### Post by an3urysm on 2015-04-04
> **Siddhartha_Kashyap said:**
> While you install ubuntu, choose "something else, I'll choose the partions myself. Delete the fedora partion, create a ext4 "/" partition and a swap and install ubuntu on the ext4. Sometimes when one os in dual boot gets removed, the grub menu disappears. I'm also a new user of lubuntu ,hope it helps

Ok, i m now formatting the fedora partition as ext4 and selected mount point as /.

I think i had made a swap partition already when i installed fedora.

Anyways hope it all goes well... I ll update as soon as the installation is done.

---

### Post by an3urysm on 2015-04-04
How long does it take to format a partition?

It like 10mins n its not over...

Kinda tensed.. Should i restart?

---

### Post by an3urysm on 2015-04-04
It shows:
The creation of swap space partition #1 of LVM VG vg_mobilehost, LV lv_swap failed.


Any idea what causes this?

---

### Post by ajgreeny on 2015-04-04
For ease of use (and everything else) I suggest you do not use LVM but create standard partitions, however it would help if you boot to a live Xubuntu system, open gparted and show us a screenshot of the gparted window.

We can then tell you which partitions to delete in order to make room for Xubuntu, and using the "Something Else" option mentioned above you can make partitions for Xubuntu to replace the Fedora partitions deleted, but in the same space.

At the time you installed Fedora I think its default was to use LVM, which when I tried it some years ago, completely baffled me as I could not figure out how to view any folders in Fedora from my main Ubuntu installation; I knew nothing of LVM at that time, and to be honest, I have not bothered to find out anything since, so I can't really help with more info on that.

---

### Post by an3urysm on 2015-04-04
> **ajgreeny said:**
> For ease of use (and everything else) I suggest you do not use LVM but create standard partitions, however it would help if you boot to a live Xubuntu system, open gparted and show us a screenshot of the gparted window.

We can then tell you which partitions to delete in order to make room for Xubuntu, and using the "Something Else" option mentioned above you can make partitions for Xubuntu to replace the Fedora partitions deleted, but in the same space.

At the time you installed Fedora I think its default was to use LVM, which when I tried it some years ago, completely baffled me as I could not figure out how to view any folders in Fedora from my main Ubuntu installation; I knew nothing of LVM at that time, and to be honest, I have not bothered to find out anything since, so I can't really help with more info on that.

I dont know what is an LVM partition. I m not sure how to use different partitions. 

Now i cant boot in fedora, coz it got wiped out by earlier attempt to install ubuntu.

Right now i m usimg ubuntu live cd. I got the screenshot from gparted as you suggested.

Edit: I m using ubuntu not xubuntu... is there a difference in installation for the two?
Anyways do help me out on what to do next.

[IMG]http://i60.tinypic.com/246mgxz.png[/IMG]



Edit 2:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2c0daa1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   102398309    51199123+   7  HPFS/NTFS/exFAT
/dev/sda2       102398310   451522889   174562290    f  W95 Ext'd (LBA)
/dev/sda3   *   451522890   451932489      204800   83  Linux
/dev/sda4       451932490   488392064    18229787+  8e  Linux LVM
/dev/sda5       102398373   308014244   102807936    7  HPFS/NTFS/exFAT
/dev/sda6       308014308   451522889    71754291    7  HPFS/NTFS/exFAT

Disk /dev/mapper/vg_mobilehost-lv_root: 14.6 GB, 14571012096 bytes
255 heads, 63 sectors/track, 1771 cylinders, total 28459008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_mobilehost-lv_root doesn't contain a valid partition table

Disk /dev/mapper/vg_mobilehost-lv_swap: 4093 MB, 4093640704 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7995392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_mobilehost-lv_swap doesn't contain a valid partition table

```

---

### Post by an3urysm on 2015-04-04
I kinda messed around with gparted and now the partitions looks like this:

[IMG]http://i60.tinypic.com/33yqt8y.png[/IMG]





I was wondering if I should delete the existing lvm 17GB partition.
But this pop up windows comes up...

[IMG]http://i62.tinypic.com/2061liw.png[/IMG]


**Should I delete this and then try to install ubuntu ?**

---

### Post by an3urysm on 2015-04-04
Oh well I went ahead and deleted the lvm partitions. Lol.

But I was able to install ubuntu successfully. Just booted into it for the first time.

Thanks a lot for the help guys... :)

---

