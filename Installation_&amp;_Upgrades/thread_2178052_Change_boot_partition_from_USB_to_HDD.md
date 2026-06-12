---
title: "Change boot partition from USB to HDD"
date: 2013-10-01
forum: Installation &amp; Upgrades
---

### Post by webnils on 2013-10-01
Hello!

I have searched but not found a solution to my problem in this forum, even there are threads on similiar topics. I'm a linux/ubuntu beginner (since a few hours) so I really hope someone can help.

I have just bought a HP ProLiant Microserver (N54L) that I plan to use as a LAMP-server. The dist I choosed is Ubuntu Server 12.04. I used Unetbootin (windows) to create a bootable USB. 

I installed using the **Install o**ption (The **Install Ubuntu Server** option didn't work for some reason, complained about not being able to read from CD-ROM, which there is none, and that there was no ethernet card, which there is one, etc so I aborted the installation and tried again with the **Install** option that worked without any error messages.)

I choose to partition the entire disk but not with LVM (mainly due to that I'm not familiar with it), maybe this is was a mistake.

When I try to boot after installation was completed nothing happens. After some investigation I realise that the boot partition was installed on the USB drive while the rest was installed on the HDD. (I don't remember questions about where to install the boot partition, but I might just not paid enough attention). The server boots up fine when the USB drive is connected, however no GRUB or other loader is used, it just boots up directly to the prompt.

The partition scheme now looks like this.
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dfb01

 Device        Boot     Start            End                Blocks          Id    System
/dev/sda1               2048            476078079     238038016   83    Linux
/dev/sda2               476080126   488396799     6158337       5      Extended
/dev/sda5               476080128   488396799     6158336       82     Linux swap / Solaris

Disk /dev/sdb: 2005 MB, 2005925888 bytes
64 heads, 43 sectors/track, 1423 cylinders, total 3917824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

 Device        Boot      Start         End              Blocks       Id  System
/dev/sdb1   *           504           3917823     1958660    6     FAT16

```

obviosly, SDA being the HDD and SDB the USB drive

Now, how do I best fix this? Is there a simple way to do this without doing a complete reinstall? The server is headless (during installation I used a monitor however, but I prefer not to carry around any hardware again) so I now connect to it using putty and ssh from a windows laptop. I figure this might be a good lesson for me to learn some more linux.

---

### Post by oldfred on 2013-10-01
I do not know servers but it should be the same.
Some BIOS promote flash drive to sda and grub defaults to install to the MBR of sda.

If booted into system.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

But grub remembers where to reinstall, so it may have flash drive as reinstall location. Not sure if above fixes it.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

You only get the choice on where to install grub2's boot loader on the partitioning screen with manual install.

---

### Post by webnils on 2013-10-01
I tried grub-install but it seems it is still the usb that is used, see below commands and output:
```

**$ sudo grub-install /dev/sda**
Installation finished. No error reported.
[B]
$ sudo debconf-show grub-pc[/B]
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
*** grub-pc/install_devices: /dev/disk/by-id/usb-General_USB_Flash_Disk_4300000000142037-0:0**
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: splash quiet
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10

**$ sudo fdisk -l**
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dfb01
   Device Boot      Start         End      Blocks   Id  System
/d**ev/sda1            2048   476078079   238038016   83  Linux**
/dev/sda2       476080126   488396799     6158337    5  Extended
/dev/sda5       476080128   488396799     6158336   82  Linux swap / Solaris
Disk /dev/sdb: 2005 MB, 2005925888 bytes
64 heads, 43 sectors/track, 1423 cylinders, total 3917824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18
   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1   *         504     3917823     1958660    6  FAT16**

```

---

### Post by oldfred on 2013-10-01
Then this will reset it. You should check after you run it.
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by webnils on 2013-10-01
ok, I have now done the **dpkg-reconfigure** as well and **debconf-show** now shows a different install device. 

 However **fdisk **still show sdb (usb) as boot partition. (I then also tried a new grub-install afterwards but **fdisk** still show the same)
```
[B]
$ sudo dpkg-reconfigure grub-pc[/B]
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found memtest86+ image: /boot/memtest86+.bin
done

**$ sudo debconf-show grub-pc**
  ...
* grub-pc/install_devices: /dev/disk/by-id/ata-VB0250EAVER_Z3TSA
  ...
[B]
$ sudo fdisk -l[/B]
...
 Device      Boot      Start         End      Blocks          Id  System
/dev/sda1            2048   476078079   238038016   83  Linux
/dev/sda2       476080126   488396799     6158337    5  Extended
/dev/sda5       476080128   488396799     6158336   82  Linux swap / Solaris
...
/dev/sdb1   *         504     3917823     1958660    6  FAT16

```

---

### Post by oldfred on 2013-10-01
That looks like a hard drive entry. I see a 250 embedded in it also. BIOS would show it that way.

This shows detail of device & partition. With mine I get it listed under ata and SCSI and every partition.

ls  /dev/disk/by-id/

Real test is does it boot without flash drive?

---

### Post by webnils on 2013-10-01
Yes, same here. 

But for my understanding. Doesn't the * for boot partition that you see when using fdisk indicate what drive the system will be booting from? 

```
 
Device      Boot      Start         End      Blocks          Id  System
/dev/sdb1   *         504     3917823     1958660    6  FAT16

```

---

### Post by webnils on 2013-10-01
I have now succesfully booted without the USB drive. :) Thank you very much for your help. 

Still I wonder about the boot *-indication when using fdisk. Now I don't have one but the system boots from the HDD. 
   ```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   476078079   238038016   83  Linux
/dev/sda2       476080126   488396799     6158337    5  Extended
/dev/sda5       476080128   488396799     6158336   82  Linux swap / Solaris
$

```

Is this something I need to bother about? I actually would be more comfortable if I had the *-indication next to SDA1...

---

### Post by oldfred on 2013-10-01
Every drive can have a boot partition, but only one per drive on a primary partition. Windows (and Lilo) use boot flag (*) to know which  PBR - partition boot sector to find more boot code. Grub does not use PBR nor then boot flag.
But a few BIOS have to see a boot flag (they expect Windows?) or the will not even start to boot, so we usually suggest a boot flag on a primary partition as we do not know your BIOS.

You may want to think about how you have partitioned. I generally suggest smaller system partitions and large data or separate /home. But I do not use servers and they often have special requirements, even more separate system partitions to isolate issues.

---

