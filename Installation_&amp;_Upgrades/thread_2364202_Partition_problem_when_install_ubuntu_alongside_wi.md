---
title: "Partition problem when install ubuntu alongside win7"
date: 2017-06-20
forum: Installation &amp; Upgrades
---

### Post by magic0000 on 2017-06-20
I wanna install Ubuntu alongside win7.
Now the partitions looks like:

[B]/dev/sda
  /dev/sda1 ntfs   60GB    primary   Windows 7
  /dev/sda5 ntfs   40GB    logical     Windows 7 Recovery Environment
  usable                 120GB[/B]

But when I add the partition  **/** and **swap**
 [B] /dev/sda3 ext4   20GB   /    unknown
  /dev/sda4 swap   4GB          unknown[/B]

 it change to unusable.
  **unusable 96GB**

 I can't add the **/boot** and [B]/home.

[/B]How can I add the partition? 
Thanks

---

### Post by Impavidus on 2017-06-20
I think you hit the 4 primary partition limit on mbr partitioned drives. The solution is that you use logical partitions instead of primary ones.

A /boot partitions is usually not really necessary, but if you wish, you can create one.

---

### Post by magic0000 on 2017-06-20
yeah, it works when I use all logical partition.
Is /boot partition necessary for that I wanna boot win first then grub linux? The ubuntu grub comes first then win boot when I installed using default partitions last time.

---

### Post by Impavidus on 2017-06-20
If you use the classical bios (and you do, and you cannot change that without reinstalling Windows) you always first get the grub menu, which can then transfer control to the Windows boot loader or directly start Linux. The reverse is not possible. The reason is that grub can start Windows, but the Windows boot loader cannot start Linux. (There may be some dirty and not very reliable tricks around that.) It is possible to make Windows the default option in the grub menu.

You only really need a boot partition if you install Linux on LVM or want a fully encrypted Linux system. If you use a /boot partition, make sure it's big enough. The forum is full of threads of people who got a full /boot partition, breaking their package manager.

---

### Post by yancek on 2017-06-20
> Is /boot partition necessary for that I wanna boot win first then grub linux? 

You don't need a boot partition for Ubuntu, explained above.  I"m not sure what you mean by 'boot win first'.  If you want windows to be the default boot you can change that very easily be changed by editing this line in /etc/default/grub:   GRUB_DEFAULT=0  You would change the 0 to whatever number menuentry windows is.  Count begins at zero so if windows is the third entry, you put 2 on the line.  It needs to be edit as root using sudo.

It is possible to use the windows bcdedit bootloader to boot Linux and it is explained at the link below.  If you start reading the information there, you will see that it is a very convoluted process and understand why people who dual-boot use Grub. 

[https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

---

### Post by magic0000 on 2017-06-20
yeah, when I install Ubuntu last time using default partitions, grub menu came first then transferred to windows boot loader to start windows. But I wanna windows boot loader transfer to grub in case of the grub is broken, and I can also erase the partition in windows easily if I don't want the Ubuntu someday. After set the /boot partition, it can be reached by using EasyBCD [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/).
I set the partitions below:
[B]/           20 G
swap     4G
/boot     200M
/home   the rest
[/B]Is that OK?

---

### Post by magic0000 on 2017-06-20
What I mean "boot win first" is that I wanna the windows boot loader transfer to grub, not the grub transfer to win boot loader.
If windows boot loader transfer to grub, I can easily erase the partition in windows if I don't want the Linux someday, or the grub is broken. It can be easily to reached by using EasyBCD [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/) if I set the /boot partition.

---

### Post by yancek on 2017-06-20
When you install Ubuntu you simply need to select the option in Device for bootloader install as the same partition on which you installed Ubuntu rather than accepting the default of /dev/sda which will install Grub code to the MBR.  Since you will be using an MBR install, EasyBCD should work and you should be able to add Ubuntu to it.

It isn't really possible to tell if you have any space on which to install Ubuntu with the information you have posted.  If you can boot the Ubuntu install DVD/flash drive and open a terminal, run this command:

sudo fdisk -l(Lower Case Letter L in the command) then post the output here.


> But I wanna windows boot loader transfer to grub in case of the grub is broken,

The windows bootloader can 'break' as easily as Grub.  You do know that EasyBCD is just a modified version of Grub4Dos which in turn is a modified version of Grub.  You don't need a boot partition, if you use EasyBCD, just point it to the Ubuntu system partition.

---

### Post by magic0000 on 2017-06-21
> **yancek said:**
>  You do know that EasyBCD is just a modified version of Grub4Dos which in turn is a modified version of Grub.  You don't need a boot partition, if you use EasyBCD, just point it to the Ubuntu system partition.
I'm fairly new to Linux. I just followed the online course which says four partitions /, /boot, swap and /home. It also shows I need to select the partition in EasyBCD on Windows 7 where the /boot is.
I have installed Ubuntu successfully with four logical partitions and here the details:
[B]/ 20 G
swap 4G(my RAM is 4G)
/boot 200M
/home the rest about 90G[/B]

---

### Post by Impavidus on 2017-06-21
If there's no /boot partition, /boot can be found in the / partition. I've never used easybcd, but according to yancek, it doesn't really care.

200MB for a /boot partition is small. You have to be very careful not to fill it completely. As stated above, the forum is full of threads by people who filled their /boot partition. I'd make it at least 500MB. There's plenty of space on your hard drive.

---

### Post by yancek on 2017-06-21
There are any number of ways to install Linux.  You can use just one partition for the entire filesystem including a boot directory and a home directory or you can do it the way you have done as well as other options.  If you still are trying to get the windows bootloader to boot first and boot Ubuntu from EasyBCD, you need to write windows code to the MBR of your system and you can't do that from Ubuntu or Linux, you need a windows install DVD or some windows boot software which you might find online.

---

### Post by efflandt on 2017-06-22
I would leave /dev/sda3 as / (forget separate /boot), create /dev/sda4 as extended partition and logical partitions (sda6 & sda7) for swap and /home. Also since rare Win7 updates fail if Win7 does not boot from its MBR (service pack or NET Framework?) and some Win7 programs used to store some data in what they "thought" was an unused part of the MBR which would overwrite part of grub2 (although grub2 tries to work around known programs that do that), I would actually put grub on /dev/sda3 instead of the MBR of /dev/sda. Then make a note of which partition has "boot" flag set (/dev/sda1?), remove that boot flag and set it on /dev/sda3. Then if a Win7 update fails after reboot, temporarily move the boot flag back to where it was originally until Win7 is successful with that update.

The easiest way to remove/set the boot flag on a partition is with "gparted" which comes on the live/install system you originally use to install Ubuntu. It is also handy to install "gparted" on the installed system for use with other or external drive/memory, but that cannot change anything on the drive you are running from at the time.

In my case I have 2 drives and left Dell's utility, Recovery, and OS partitions in place. /dev/sda4 is all of 14.04 with standard Windows MBR and grub on sda4, /dev/sdb1 is all of 16.04 with its grub in MBR of sdb (SSD). So I can boot either drive alone, or everything from either grub as long as that grub has had: sudo update-grub. I have enough RAM and do not hibernate, so I have no swap.```
~$ sudo fdisk -l
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2fb1db22

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1               63     112454     112392  54.9M de Dell Utility
/dev/sda2           112455   24788294   24675840  11.8G  7 HPFS/NTFS/exFAT
/dev/sda3         24788295 1072880064 1048091770 499.8G  7 HPFS/NTFS/exFAT
/dev/sda4  *    1072880065 1953524596  880644532 419.9G 83 Linux


Disk /dev/sdb: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x7e78a7d3

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1  *     2048 1000214527 1000212480  477G 83 Linux
```

---

